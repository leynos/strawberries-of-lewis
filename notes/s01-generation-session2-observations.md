# S01 Generation Session 2 — Revised Skills Assessment

**Date:** 2026-05-05
**Skills used:** shot-specifier (revised) → video-generator (new)
**Shots generated:** 4 (S01_SH001–SH004)
**Models:** Kling 3.0 (2 shots), Seedance 2.0 (2 shots)

---

## What the Revised Skills Changed

### Prompt Format
- **Before (Session 1):** Structured `[TAG]` prompts manually flattened at generation time.
- **After (Session 2):** Structured `[TAG]` block preserved for review + `## Generation Prompt` section written by shot-specifier using model-specific flattening (Kling: camera/structure first; Seedance: action/reference first).
- **Impact:** Eliminated ad-hoc prompt flattening. Prompts are now reviewable in both forms.

### Manifest
- **Before:** Simple table with shot ID, duration, frames, prompt file.
- **After:** Full table with model, routing rationale, strategy, aspect ratio, target resolution, resolution parameter, audio prefs, model overrides, count, required refs, review gate.
- **Impact:** Every decision is explicit and traceable. No inference needed at generation time.

### Directory Structure
- **Before:** Flat files in `scene-pack/shots/` and `scene-pack/prompts/`.
- **After:** Canonical `shots/{shot_id}/start.png` + `prompts/{shot_id}_prompt.md` at project root.
- **Impact:** Cleaner path contracts between skills. Video-generator knows exactly where to find files.

### MCP Schema Check
- **Before:** Discovered parameter limitations at generation time.
- **After:** Explicit schema inspection step before first job. Recorded in `generated/mcp_schema_notes.md`.
- **Impact:** Known limitations documented before submission rather than discovered after.

### Audio Preferences
- **Before:** Not specified; models auto-set audio; discovered post-hoc.
- **After:** `audio_generation_preferences: none` explicit in manifest. Still cannot override on either model, but the intent is recorded and the gap is documented.

### Review Gates
- **Before:** All shots treated equally.
- **After:** S01_SH004 marked `review_gate=required` (reactor prop continuity). Others `optional`.

---

## What Remains Unresolved Despite Revised Skills

### 1. Resolution: 1344×768 is the actual output
Both models produce 1344×768 regardless of parameters:
- Kling: no resolution parameter exposed at all
- Seedance: `resolution=1080p` accepted as input but output is still 1344×768

The manifest's `target_resolution: 1920x1080` is aspirational, not achievable on the current MCP surface. The skill should note this as an empirical constraint.

**Recommendation for skills:** Add to the empirical constraints registry: "Actual output resolution is 1344×768 on the current Higgsfield MCP surface for both models. The `resolution` parameter on Seedance may affect internal processing quality but not output pixel dimensions."

### 2. Audio generation cannot be disabled
- Seedance: `generate_audio=true` auto-set; parameter not available for input
- Kling: `sound="on"` auto-set; parameter not available for input
- The video-generator skill's stop condition says "stop rather than letting the model auto-generate unwanted audio" — but this would mean NO generation is possible on this surface for silent shots.

**Recommendation for skills:** Amend the stop condition to: "For landscape/environment shots where generated ambient audio is acceptable, proceed with a logged note. For dialogue or narration shots where unwanted generated audio would conflict with external audio, STOP."

### 3. Reference image limitations on Kling
Kling 3.0 only accepts `start_image` and `end_image` — no generic `image` role. This means:
- Style anchor cannot be passed to Kling shots
- Location reference cannot be passed to Kling shots
- Character/prop references cannot be passed to Kling shots
- Only the storyboard frames carry visual consistency for Kling jobs

**Recommendation for skills:** The video-generator's reference image discipline section should note: "Kling 3.0 on the current surface accepts only start_image and end_image. All continuity information for Kling shots must be baked into the storyboard frames during shot-specifier Phase 5. The storyboard generation step is therefore more critical for Kling-routed shots than for Seedance-routed shots."

### 4. cfg_scale/reference adherence not controllable
Kling auto-sets `cfg_scale=0.5` — this cannot be overridden. The manifest's `model_overrides` for cfg_scale are aspirational.

### 5. File size variance between sessions
The same shot (S01_SH001, Kling 3.0, 8s) was 21MB in Session 1 and 8.8MB in Session 2 — a 2.4× difference. This is not explained by any parameter change. It may indicate model version updates, non-deterministic encoding, or infrastructure changes.

---

## Process Efficiency

| Metric | Session 1 (manual) | Session 2 (revised skills) |
|--------|--------------------|-----------------------------|
| Prompt format | Ad-hoc flattening | Pre-written `## Generation Prompt` |
| Schema check | Discovered post-hoc | Explicit pre-flight step |
| Media upload | Manual per-file | Batch (10 files, one call) |
| Job submission | Manual per-shot | 2 parallel submissions (interleaved) |
| Logging | Post-completion | Immediate on submission |
| Assembly order | Not produced | Written with boundary annotations |
| Review gating | Not differentiated | Per-shot `review_gate` field |

---

## Skill Feedback for Next Revision

1. **The `resolution` parameter in the manifest is misleading.** It implies controllability that doesn't exist. Consider renaming to `resolution_hint` or adding a `resolution_verified` field populated after download.

2. **The audio stop condition is too aggressive.** On the current MCP surface, it would prevent all generation. Need a severity-based approach: landscape (proceed+log), dialogue (stop).

3. **Kling's reference limitation should feed back into shot-specifier Phase 5.** If a shot routes to Kling, the storyboard frame quality is the ONLY continuity mechanism. Phase 5 should note this.

4. **The `model_overrides` field works in principle but all overrides are currently unsupported.** The field is correctly designed for a future MCP surface that exposes these controls. For now, it documents intent.

5. **Interleaving strategy works.** Submitting Kling→Seedance→Kling→Seedance avoided Seedance serial queue blocking. The skill's step 8 guidance is correct.

6. **Batch media upload + confirm is dramatically faster** than the per-file approach used in Session 1. The `media_upload` tool's `files[]` parameter handles this well.
