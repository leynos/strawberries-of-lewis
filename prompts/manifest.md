# Shot Generation Manifest — S01 "The Old Arithmetic"

**Generated:** 2026-05-05
**Skill:** shot-specifier (revised)
**Sequence:** S01
**Shots:** 4
**Total duration:** 26s

---

| Shot ID | Scene | Duration | Aspect | Target Resolution | Resolution Param | Model | Routing Rationale | Strategy | Audio Prefs | Model Overrides | Count | Required Refs | Review Gate | Start | End | Keys | Prompt File |
|---------|-------|----------|--------|-------------------|------------------|-------|-------------------|----------|-------------|-----------------|-------|---------------|-------------|-------|-----|------|-------------|
| S01_SH001 | SC-01 | 8s | 16:9 | 1920x1080 | 1080p | kling3_0 | Landscape establishing; one-vector pan; camera path dominates over identity refs | single_clip | none | sound=off;cfg_scale=0.5 | 1 | style_anchor_01 | optional | shots/S01_SH001/start.png | shots/S01_SH001/end.png | None | prompts/S01_SH001_prompt.md |
| S01_SH002 | SC-01 | 6s | 16:9 | 1920x1080 | 1080p | seedance_2_0 | Static camera; minimal motion (plume only); start+end anchor; reference-driven | single_clip | none | generate_audio=false;quality=standard;genre=auto | 1 | style_anchor_01 | optional | shots/S01_SH002/start.png | shots/S01_SH002/end.png | None | prompts/S01_SH002_prompt.md |
| S01_SH003 | SC-02 | 6s | 16:9 | 1920x1080 | 1080p | kling3_0 | Pre-dawn low-light exterior; vehicle motion L→R; camera structure + geometric anchors dominate | single_clip | none | sound=off;cfg_scale=0.5 | 1 | ref_loc_moorland_road_pre_dawn | optional | shots/S01_SH003/start.png | shots/S01_SH003/end.png | None | prompts/S01_SH003_prompt.md |
| S01_SH004 | SC-02 | 6s | 16:9 | 1920x1080 | 1080p | seedance_2_0 | Reference-driven (reactor prop detail); start+end anchor; identity consistency matters | single_clip | none | generate_audio=false;quality=standard;genre=auto | 1 | ref_loc_moorland_road_pre_dawn | required | shots/S01_SH004/start.png | shots/S01_SH004/end.png | None | prompts/S01_SH004_prompt.md |

---

## Notes

- S01_SH001 and S01_SH003 route to Kling 3.0: landscape/camera-move dominance, no identity constraints.
- S01_SH002 and S01_SH004 route to Seedance 2.0: reference preservation (plume continuity, reactor detail).
- All shots are `single_clip` — no key frames in S01.
- Audio preference `none` on all shots — narration/ambient handled externally.
- S01_SH004 is `review_gate=required` due to reactor prop detail being continuity-critical.
