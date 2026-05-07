# Generation Log

## The Strawberry Bunkers of Lewis

| Shot ID | Sub-clip | Local file | Duration seconds | Status | Review | Take | Model | Job ID | Scene ID | File size | Actual resolution | Prompt hash | Prompt file | Transition type | Transition duration | Mute generated audio | Forced generated audio | Continuity flags | Notes |
|---------|----------|------------|------------------|--------|--------|------|-------|--------|----------|-----------|-------------------|-------------|-------------|-----------------|---------------------|----------------------|------------------------|------------------|-------|
| S01_SH001 | — | generated/S01_SH001/selected.mp4 | 8 | completed | accepted | v1 | kling3_0 | 6ec7ca85-d401-4ae1-af82-10086e7b87ff | S01 | 8.8MB | 1284x716 | | prompts/S01_SH001_prompt.md | | | false | true | | Landscape establishing; sound=on auto-set; H.264 Main |
| S01_SH002 | — | generated/S01_SH002/selected.mp4 | 6 | completed | accepted | v1 | seedance_2_0 | 9ee3d73d-d96e-4dc1-a99f-bd26602b70ba | S01 | 8.1MB | 1920x1080 | | prompts/S01_SH002_prompt.md | | | false | true | | Static camera plume; generate_audio=true auto-set; H.264 High |
| S01_SH003 | — | generated/S01_SH003/selected.mp4 | 6 | completed | accepted | v1 | kling3_0 | d92295b5-f0c6-4fa9-b300-a858c71d3e32 | S01 | 5.6MB | 1284x716 | | prompts/S01_SH003_prompt.md | | | false | true | | Pre-dawn convoy L→R; sound=on auto-set; H.264 Main |
| S01_SH004 | — | generated/S01_SH004/selected.mp4 | 6 | completed | accepted | v2 | seedance_2_0 | abb7ef44-227e-47ed-ad0f-6e3e054adf62 | S01 | 4.8MB | 1920x1080 | | prompts/S01_SH004_prompt.md | | | false | true | | Retake v2: corrected L→R direction; H.264 High |
| S02_SH001 | — | generated/S02_SH001/selected.mp4 | 8 | completed | accepted | v1 | kling3_0 | 61c19e48-b841-4f81-81de-e3617cb3cf07 | S02 | 9.5MB | 1284x716 | | scene-pack/prompts/shot_S02_SH001_prompt.md | | | false | true | | Bunker establishing dolly; sound=on auto-set; H.264 Main |
| S02_SH002 | — | generated/S02_SH002/selected.mp4 | 6 | completed | accepted | v1 | seedance_2_0 | f56e0ef8-eb06-4971-a7ba-ab9fff39c2b4 | S02 | 6.1MB | 1920x1080 | | scene-pack/prompts/shot_S02_SH002_prompt.md | | | false | true | | Strawberry CU; generate_audio=true auto-set; H.264 High |
| S02_SH003 | — | generated/S02_SH003/selected.mp4 | 6 | completed | accepted | v1 | seedance_2_0 | d30b610b-e8d4-4f8b-901f-c8a30eb6e592 | S02 | 4.6MB | 1920x1080 | | scene-pack/prompts/shot_S02_SH003_prompt.md | | | false | true | | Robot tracking; robot ref 837bc15a; H.264 High |
| S02_SH004 | — | generated/S02_SH004/selected.mp4 | 6 | completed | accepted | v2 | seedance_2_0 | 6652d7cc-d62b-4e7f-b6bf-2f2f6a0bb1ce | S02 | 2.9MB | 1920x1080 | | scene-pack/prompts/shot_S02_SH004_prompt.md | | | false | true | | Bee flight retake: extended to 6s on Seedance 2.0 for fuller bee takeoff; H.264 High |

---

## Superseded Takes

| Shot ID | Sub-clip | Local file | Duration seconds | Status | Review | Take | Model | Job ID | Notes |
|---------|----------|------------|------------------|--------|--------|------|-------|--------|-------|
| S01_SH004 | — | generated/S01_SH004/v1.mp4 | 6 | completed | superseded | v1 | seedance_2_0 | 95ebaafa-6129-48a8-906d-7d77e1a71aea | Vehicles facing wrong direction; superseded by v2 |
| S02_SH004 | — | generated/S02_SH004/v1.mp4 | 4 | completed | superseded | v1 | kling3_0 | 61672e4f-5f5e-4f01-aa5b-38f05467833e | 4s Kling; bee flight too brief; superseded by 6s Seedance v2 |

---

## Observations

### Resolution Varies by Model (corrected via ffprobe)
- **Kling 3.0:** Actual output is **1284x716** (H.264 Main profile).
- **Seedance 2.0:** Actual output is **1920x1080** (H.264 High profile).
- Kling clips need upscaling for a 1080p timeline.

### Audio Override Unavailable
- Seedance: `generate_audio: true` auto-set; no parameter to disable
- Kling: `sound: "on"` auto-set; no parameter to disable
- Both models produce audio on every clip regardless of manifest preferences

### Timing
- Kling 3.0: ~90s per job
- Seedance 2.0: ~120-180s per job (serial queue)
- Interleaving strategy (Kling→Seedance→Kling→Seedance) effective

## Media Manifest

| File | Media ID | Role | Used In |
|------|----------|------|---------|
| shots/S01_SH001/start.png | 8cc1dd27-4855-495b-a8b8-c48e1147de11 | start_image | S01_SH001 |
| shots/S01_SH001/end.png | 2cc94e00-3cfb-4997-92b0-765374e7f96e | end_image | S01_SH001 |
| shots/S01_SH002/start.png | 819afa05-d02b-4c63-b978-e0807ffbd278 | start_image | S01_SH002 |
| shots/S01_SH002/end.png | f752c7ad-cfa2-450f-b6a9-9d3f0301442d | end_image | S01_SH002 |
| shots/S01_SH003/start.png | 730b7785-bcb6-4a42-8c3f-483a9b2f8c9f | start_image | S01_SH003 |
| shots/S01_SH003/end.png | 6880a2e2-fb51-440f-8bb2-1b6ad3e696f9 | end_image | S01_SH003 |
| shots/S01_SH004/start.png (v2) | 74d3552d-62c0-4166-9e70-6455f09e0de9 | start_image | S01_SH004 v2 |
| shots/S01_SH004/end.png (v2) | 57cdf96b-09d0-438f-b9df-c90e8b8ad19b | end_image | S01_SH004 v2 |
| shots/S02_SH001/start.png | 2e7efc7d-c869-41d7-8f17-15d1318a1531 | start_image | S02_SH001 |
| shots/S02_SH001/end.png | c0f90e89-8fc6-412e-bff6-c10dd01204da | end_image | S02_SH001 |
| shots/S02_SH002/start.png | 86e4c8b6-2c43-4ca7-a710-963628233101 | start_image | S02_SH002 |
| shots/S02_SH002/end.png | 08a95244-0ecb-4086-82b0-b815ef182e6e | end_image | S02_SH002 |
| shots/S02_SH003/start.png | 0a1df13a-8ffe-4092-8f50-a5d3172cde7f | start_image | S02_SH003 |
| shots/S02_SH003/end.png | ce609986-c95b-4a1d-b475-105df423984a | end_image | S02_SH003 |
| shots/S02_SH004/start.png | 81aa7b85-cc9b-411a-9440-fa0b82f1993a | start_image | S02_SH004 |
| shots/S02_SH004/end.png | e1d1ee10-493f-4e9b-9c82-ec0f0c5d720e | end_image | S02_SH004 |
| scene-pack/refs/style_anchor_01.png | 86d4015e-e07c-4271-a883-5fb105618a8f | image (style) | S01_SH002 |
| scene-pack/refs/ref_loc_moorland_road_pre_dawn.png | 47beb08d-3071-4dd1-b97e-556d1e4623da | image (location) | S01_SH004 |
| scene-pack/refs/ref_rve_inspection_robot_primary.png | 837bc15a-ae35-48a6-9460-a6fb4cce20a9 | image (subject ref) | S02_SH003 |

## Schema Notes

See `generated/mcp_schema_notes.md` for full MCP schema observations.
