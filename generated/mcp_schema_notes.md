# MCP Schema Notes — 2026-05-05 (Session 2)

## Higgsfield MCP Live Schema

### generate_video tool
- Tool name: `generate_video`
- Model parameter: `model` (string)
- Prompt field: `prompt` (string; no explicit length limit documented)
- Aspect ratio: `aspect_ratio` (string)
- Duration: `duration` (integer, seconds)
- Count: `count` (integer, 1-4)
- Media: `medias` array with `{value, role}` objects

### Seedance 2.0 (`seedance_2_0`)
- **Duration range:** 4–15s
- **Aspect ratios:** auto, 21:9, 16:9, 4:3, 1:1, 3:4, 9:16
- **Resolution:** 480p, 720p, 1080p (default: 720p) — **MUST set explicitly to 1080p**
- **Mode:** std, fast (default: std)
- **Genre:** auto, action, horror, comedy, noir, drama, epic (default: auto)
- **Media roles:** image, start_image, end_image, video, audio
- **CRITICAL:** Description says "no generate_audio param" — **cannot disable audio generation**
- **Schema implication:** Audio-generation preferences in manifest cannot be honoured. The model may auto-generate audio. This is a known limitation; proceed for landscape/environment shots where generated ambient is acceptable. Flag for character/dialogue shots where unwanted audio would be problematic.

### Kling 3.0 (`kling3_0`)
- **Duration range:** 3–15s
- **Aspect ratios:** 16:9, 9:16, 1:1
- **Mode:** pro, std (default: std)
- **Media roles:** start_image, end_image **ONLY** — no generic `image` reference role
- **CRITICAL:** No `sound`, `cfg_scale`, `resolution`, or `quality` parameters exposed
- **Schema implication:** Cannot pass style anchor or location reference images to Kling. Cannot control audio generation, reference adherence, or output resolution. Must rely entirely on start/end frames and prompt text to carry the shot. For landscape shots this is acceptable. For identity-critical shots this would be a routing stop condition.

## Model Override Availability

| Manifest Override | Seedance 2.0 | Kling 3.0 |
|-------------------|--------------|-----------|
| generate_audio=false | NOT AVAILABLE | NOT AVAILABLE |
| sound=off | N/A | NOT AVAILABLE |
| cfg_scale | N/A | NOT AVAILABLE |
| resolution=1080p | YES | NOT AVAILABLE |
| mode=std | YES | YES (std/pro) |
| genre=auto | YES | N/A |
| quality=standard | N/A (use mode=std) | N/A |

## Decision: Proceed or Stop?

Per video-generator stop conditions:
- "explicit audio-generation preferences cannot be honoured and the model would auto-generate unwanted audio" → For S01 (landscape/environment shots only), proceed. Generated ambient (wind, rain) is acceptable. Flag if character shots were involved.
- "model-specific defaults would alter audio, reference adherence, mode, or resolution and the live MCP schema does not expose an override" → For Kling cfg_scale: proceed for landscape where reference adherence is lower priority. Would STOP for identity-critical Kling shots.

**Decision: PROCEED for S01 with noted limitations.**
