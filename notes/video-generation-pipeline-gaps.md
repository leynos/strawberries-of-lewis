# Video Generation Pipeline — Gap Analysis

**Date:** 2026-05-05
**Context:** Attempted to generate S01 (4 shots) via Higgsfield MCP from scene-pack prompt files. Auth token was expired; generation blocked. Analysis below is based on model capability inspection and prompt file structure review.

---

## 1. Prompt Format Mismatch (Critical)

The scene-inventory-extractor-v2 produces prompts in a structured `[TAG] content` format designed for human readability and downstream tooling. Higgsfield's `generate_video` takes a single `prompt` string field. There's no defined **translation layer** between the structured prompt and what the model actually receives.

**Gap:** The skill needs to either:
- Produce a second, model-native prompt variant per shot (a plain-text "generation prompt" flattened from the structured tags), or
- Define a canonical flattening algorithm in the video-prompt-guide reference (e.g. concatenate `[ACTION]` + `[SUBJECT]` + `[STYLE]` in that priority order, truncated to model's token limit)

---

## 2. Model Routing (Critical)

The prompt files don't specify which video generation model to use. The manifest records duration and pacing but not model selection. Different shots have different requirements:

| Shot type | Best model fit | Reason |
|-----------|---------------|--------|
| Landscape pan (S01_SH001) | Seedance 2.0 or Cinema Studio v2 | Start+end frames, long duration, cinematic |
| Static CU (S02_SH002) | Any — minimal motion | Low complexity |
| Character-centric (S04_SH001) | Seedance 2.0 | Identity preservation via reference |
| Action/movement (S04_SH004) | Seedance 2.0 at 1080p | Complex interpolation with key frame |
| Drone POV (S04_SH005) | Kling 3.0 or Seedance 2.0 | Smooth forward motion |

**Gap:** The skill should produce a **model routing recommendation** per shot in the manifest, based on:
- Whether start+end frames are both needed (most models support this)
- Whether key frames exist (no current model supports mid-clip anchoring natively — this is a workflow problem)
- Complexity of interpolation (large pose changes need better models)
- Duration (model min/max constraints)
- Genre/mood parameters available

---

## 3. Key Frame Handling (Critical — No Model Support)

Three shots (S04_SH004, S05_SH001, S05_SH003) have key frames specifying intermediate states. **No Higgsfield model accepts mid-clip key frames.** The available roles are `start_image` and `end_image` only.

**Gap:** The skill needs a **key-frame decomposition strategy** section:
- Split a shot with key frame at time T into two sub-clips: `[start→key]` and `[key→end]`
- S04_SH004 (6s, key at 2s) → clip A (2s, start→key01) + clip B (4s, key01→end)
- But: Seedance 2.0 minimum is 4s. So either extend clip A to 4s or merge the motion.
- Document model constraints (min duration, max duration) and the decomposition rules

---

## 4. Media Upload Pipeline (Important)

The workflow needs to:
1. Upload start frame → get media UUID
2. Upload end frame → get media UUID
3. (Optional) Upload style reference → get media UUID
4. Call `generate_video` with media UUIDs in the correct roles

**Gap:** The prompt files reference images by relative path (`shots/shot_S01_SH001_start.png`). A **generation skill** needs to:
- Resolve paths to absolute
- Handle upload → confirm → UUID pipeline
- Cache UUIDs for images used across multiple generations (style anchors, references)
- Track upload state to avoid re-uploading on retry

---

## 5. Aspect Ratio and Resolution Mapping (Important)

The cinematography spec defines 16:9. Models support this, but the mapping from spec to parameter isn't codified. The skill should emit the `aspect_ratio` and target `resolution` as machine-readable fields in the manifest.

---

## 6. Duration Constraint Validation (Important)

The scene-pack allocates 4s, 6s, or 8s per shot. Seedance 2.0 supports 4–15s. Cinema Studio v2 supports 3–12s. These happen to align, but the skill should **validate shot durations against model constraints** at manifest time rather than discovering violations at generation time.

---

## 7. Clip Boundary / Concatenation Metadata (Nice-to-have)

The manifest records `continuous` vs `scene_cut` boundaries. A generation skill should use this to:
- For `continuous`: ensure the end frame of shot N matches the start frame of shot N+1 (already handled by the extraction skill's cross-shot verification)
- For post-production: emit an EDL or assembly-order file that a video editor can import

---

## 8. Generation State Tracking (Important for Production)

A 27-shot sequence involves 27+ generation jobs, each taking 60–180s. The pipeline needs:
- Job ID tracking per shot
- Status polling with backoff
- Retry logic for failures
- A generation log that records: shot ID → job ID → status → output URL → local file path
- Resume capability (don't regenerate shots that already succeeded)

---

## Recommendation: A `video-generator` Skill

A new skill covering the gap between scene-pack output and actual video generation:

```
video-generator/
├── references/
│   ├── model-routing.md          # Which model for which shot type
│   ├── prompt-flattening.md      # How to flatten [TAG] format to plain text
│   ├── key-frame-decomposition.md # Splitting shots at key frames
│   └── duration-constraints.md   # Model min/max and adjustment rules
├── templates/
│   ├── generation-log.md         # Per-shot job tracking
│   └── assembly-order.md         # EDL-equivalent for final cut
└── skill.md                      # Main workflow
```

---

## Extensions Needed in scene-inventory-extractor-v2

1. **Manifest additions:** Per-shot fields for `recommended_model`, `aspect_ratio`, `resolution`, `generation_strategy` (single-clip vs split-at-keyframe)
2. **Prompt flattening:** A `[GENERATION_PROMPT]` field in each prompt file containing the model-ready plain-text version
3. **Key-frame split plan:** For shots with key frames, pre-compute the sub-clip boundaries and durations, noting model minimum constraints
4. **Media manifest:** A machine-readable file mapping each frame/reference to its intended upload role (`start_image`, `end_image`, `image`), ready for batch upload

---

## Generation Plan for S01 (When Auth Restored)

```
For each shot in S01:
  1. Upload start.png → UUID_start
  2. Upload end.png → UUID_end
  3. generate_video(model="seedance_2_0", prompt=<flattened>,
     aspect_ratio="16:9", duration=N, resolution="1080p",
     genre="drama", medias=[
       {value: UUID_start, role: "start_image"},
       {value: UUID_end, role: "end_image"}
     ])
  4. Poll job_status until terminal
  5. Download result
```

### Flattened Prompts for S01

**S01_SH001 (8s):**
> Camera pans slowly right across treeless Lewis moorland under overcast pewter sky. Wet peat, fence posts leaning eastward, single-track road in mid-ground. In the final seconds, a white plume of steam appears above the horizon at right edge. 35mm film, Kodak Vision3 250D, fine organic grain, cool-neutral desaturated tones, lifted blacks, no hard shadows. No trees. No blue sky.

**S01_SH002 (6s):**
> Static wide shot of treeless moorland. White steam plume rises from behind the horizon, growing taller against pewter overcast sky. Wet peat, fence posts in foreground. 35mm film grain, cool-neutral, desaturated. No trees. No blue sky.

**S01_SH003 (6s):**
> Pre-dawn darkness. A convoy of vehicles approaches on a single-track road from left, headlights piercing rain. Police escort with blue flashing lights leads. Flatbed trucks carrying cylindrical reactor sections. Vehicles travel left-to-right on the left side of the road (UK left-hand traffic). Rain visible in headlight beams. Sodium-orange practicals, deep grey-blue surround. 35mm film grain.

**S01_SH004 (6s):**
> Low angle, wide shot. A flatbed truck passes frame left to right carrying a large cylindrical reactor section. Rain streams off the steel cylinder. Blue police lights flash in background. Wet road surface reflects orange-sodium lighting. Pre-dawn darkness, deep grey-blue sky. 35mm film grain. Left-hand traffic — vehicle on left side of road.

---

## Available Models (Higgsfield, as of 2026-05-05)

| Model | Provider | Start+End | Duration | Res | Notes |
|-------|----------|-----------|----------|-----|-------|
| seedance_2_0 | Bytedance | Yes | 4–15s | 480/720/1080p | Genre, mode, audio ref |
| cinematic_studio_video_v2 | Higgsfield | Yes | 3–12s | — | Genre, mode (pro/std) |
| kling3_0 | Kling | Yes | 3–15s | — | Multi-shot, motion transfer |
| cinematic_studio_video | Higgsfield | Yes | 5 or 10s | — | Slow-motion, sound |
