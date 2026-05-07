# S01 Generation — Process Observations

**Date:** 2026-05-05
**Shots generated:** 4 (S01_SH001–SH004)
**Models tested:** Kling 3.0 (2 shots), Seedance 2.0 (2 shots)
**Total generation time:** ~5 minutes wall-clock (including queue waits)

---

## Timing Observations

| Model | Shot | Actual gen time | Queue wait |
|-------|------|-----------------|------------|
| Kling 3.0 | S01_SH001 (8s) | ~90s | Minimal |
| Kling 3.0 | S01_SH003 (6s) | ~90s | Minimal |
| Seedance 2.0 | S01_SH002 (6s) | ~180s | Minimal |
| Seedance 2.0 | S01_SH004 (6s) | ~90s active | ~90s queued behind SH002 |

**Finding:** Kling 3.0 is consistently faster (~90s). Seedance 2.0 takes roughly 2×
longer but was queued (only one Seedance job processed at a time). For a 27-shot
production, this means Kling-heavy routing will complete faster. For Seedance-heavy
routing, jobs should be submitted in batches with queue tolerance.

---

## Skill Cross-Reference Gaps Identified

### 1. scene-inventory-extractor-v2 → shot-specifier handoff

**Problem:** The extraction skill (Phase 14) produces human-readable structured prompts
(`[STYLE]`, `[ACTION]`, etc.) and the shot-specifier's model-routing reference expects
to *receive* a scene inventory + shot list as input and *produce* generation-ready
prompts. But the extraction skill already wrote prompts in Phase 14 before the
shot-specifier was invoked.

**Resolution needed:** Either:
- (a) The extraction skill stops at Phase 13 (consistency check) and explicitly hands
  off to shot-specifier for Phase 14+, OR
- (b) The extraction skill's Phase 14 output is treated as a *draft* that the
  shot-specifier refines into model-specific generation prompts.

**Recommendation:** Option (a). The extraction skill should stop after Phase 13 and emit
a "ready for shot-specifier" signal. The shot-specifier picks up from there with its own
Phases 2–8. This avoids duplicate work and conflicting prompt formats.

### 2. Prompt flattening is undefined

**Problem:** The structured `[TAG] content` format doesn't map to any model's input
directly. During this test I manually flattened prompts into plain-text generation
prompts. The flattening logic was:
- Take `[ACTION]` as the body (it's the most concrete description)
- Append lens/camera language from `[FRAMING]`
- Append negative constraints
- Drop `[STYLE]` and `[FILMSTOCK]` (these are expressed via reference images, not text)

**Resolution needed:** The shot-specifier skill's `references/model-routing.md` should
include a **prompt flattening algorithm** per model. Different models respond differently
to style-heavy vs action-heavy prompts.

### 3. Model parameters not in scene-inventory output

**Problem:** The extraction skill's prompt files don't include:
- `aspect_ratio` (must be derived from cinematography spec)
- `resolution` (1080p vs 720p)
- `mode` (pro vs std)
- `genre` (drama, auto, etc.)

**Resolution needed:** The shot-specifier should emit these as machine-readable fields
per shot, not leave them to be inferred at generation time.

### 4. Upload/media pipeline has no skill coverage

**Problem:** The entire upload → confirm → UUID → generate → poll → download cycle was
manual. For 27 shots this is unsustainable. The shot-specifier's `asset-pipeline.md`
describes the *output structure* but not the *operational pipeline* to get there.

**Resolution needed:** Either:
- A third skill (`video-generator`) that takes shot-specifier output and drives the
  Higgsfield MCP through the complete upload/generate/poll/download cycle, OR
- The shot-specifier Phase 8 is extended with an "execution" sub-phase that actually
  performs generation rather than just describing the file naming convention.

### 5. Seedance 2.0 `generate_audio: true` was auto-set

**Observation:** The Higgsfield MCP auto-set `generate_audio: true` on Seedance 2.0
jobs. This wasn't requested in the shot-specifier output. For shots where audio is
"wind + rain" ambient, generated audio might be acceptable. For shots with specific
audio direction (diesel engines, blue-light sirens), generated audio is unpredictable.

**Resolution needed:** The shot-specifier should emit an explicit `audio: generated |
none | supplied` field per shot. The generation pipeline should respect this and
suppress auto-audio where inappropriate.

### 6. Kling 3.0 auto-set `sound: "on"` and `cfg_scale: 0.5`

**Observation:** Parameters not specified in the generation call were auto-filled by
the API. The `cfg_scale` at 0.5 means the model leans heavily toward the prompt rather
than the reference images. For landscape shots this may be fine; for identity-critical
shots it could be problematic.

**Resolution needed:** Document default parameter behaviour per model in
`references/model-routing.md`. Where a default is undesirable, the generation call
should explicitly override it.

### 7. Resolution negotiation

**Observation:** Kling 3.0 produced clips at 1344×768 (non-standard 16:9 at ~768p).
Seedance 2.0 was requested at 1080p but the actual output resolution needs verification.
The extraction skill's cinematography spec says "16:9" but doesn't specify pixel
dimensions.

**Resolution needed:** Add a `target_resolution` field to the cinematography spec.
The shot-specifier should validate that the requested resolution is achievable on the
routed model before submitting the job.

---

## What Worked Well

1. **Start + end frame anchoring.** Both models accepted the dual-anchor workflow
   without issue. The frames were uploaded, confirmed, and used as intended.

2. **Model routing logic was sound.** Kling 3.0 for landscape/environment, Seedance 2.0
   for reference-driven identity — this split felt correct for S01. The Kling shots
   completed faster and (being landscape) didn't need the identity-preservation that
   Seedance provides.

3. **Generation log format.** Having the log in place before submitting jobs meant
   nothing was lost. The job IDs were immediately traceable.

4. **Prompt vocabulary from keyword library.** The negative constraints ("No trees. No
   blue sky. No cuts. No zoom.") are effective prompt hygiene.

---

## What Needs Improvement Before Full Production

1. **Automate the upload/confirm/generate/poll/download cycle.** Manual operation for
   4 shots was manageable. For 27+ it would be error-prone.

2. **Define when to review before proceeding.** The current workflow has no QA gate
   between generation and selection. For v1 takes of landscape shots this is fine;
   for character-centric or continuity-critical shots, the pipeline needs a review step.

3. **Batch submission strategy for Seedance.** Since Seedance jobs queue behind each
   other, submitting all Seedance shots simultaneously means the last one waits for
   all preceding ones. Interleave Kling and Seedance submissions, or accept serial
   processing.

4. **File size variance.** S01_SH004 at 4.3MB vs S01_SH001 at 21MB is a 5× difference
   for similar duration. This likely reflects bitrate differences between models.
   Document expected file sizes per model/duration for capacity planning.
