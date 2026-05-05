# Consistency Report — The Strawberry Bunkers of Lewis

**Generated:** 2026-05-05
**Total shots inspected:** 23 (57 frames including key frames)
**Reference images verified against:** 19

---

## Summary

| Severity | Count |
|----------|-------|
| **BLOCK** | 0 |
| **WARN** | 10 |

**No BLOCK issues.** All WARN issues are logged for human review but do not prevent video prompt assembly.

---

## WARN Issues

### CA-001: Switch headphone position variability
- **Shot(s):** S04_SH001_start vs S04_SH006_start
- **Check:** Character consistency — headphone placement
- **Description:** In the primary ref, headphones sit on ears. In S04_SH001_start, headphones are correctly around neck (as specified). In S04_SH006_start, headphones are on ears (correct for that scene beat). Transitions are story-driven but the headphone design varies slightly in colour saturation between shots — slightly more vivid pink in S04_SH006.
- **Severity:** WARN
- **Action:** Acceptable — lighting conditions differ (door-light mix vs pure screen glow); the pink reads consistently enough.

### CA-002: Gannet UAV wing configuration minor variation
- **Shot(s):** S04_SH004_start vs S06_SH003_start
- **Check:** Cross-shot prop identity — gannet UAV
- **Description:** The gannet's wing fold geometry differs subtly between the two ground-level launch shots. In S04_SH004 the wings are slightly more swept; in S06_SH003 the wings appear more level. Both are recognisably the same aircraft type.
- **Severity:** WARN
- **Action:** Acceptable for different production days/units. The white body, black wingtips, cargo pod rack, and VTOL rotors are consistent.

### CA-003: Control room wall screen layout variation
- **Shot(s):** S04_SH001_end vs S04_SH003_start
- **Check:** Recurring visual element consistency — monitor bank
- **Description:** The wall screen arrangement (number of screens, relative positions) shifts slightly between the medium shot of Switch entering (end frame) and the wide establishing shot. The number of visible screens differs.
- **Severity:** WARN
- **Action:** Acceptable — different camera angles and focal lengths naturally show different portions of the monitor bank. The corrugated walls, cable runs, and screen glow colour are consistent.

### CA-004: Bunker interior stone texture
- **Shot(s):** S02_SH001_start vs S06_SH002_start
- **Check:** Location consistency — bunker interior
- **Description:** The arch structure shows stone/masonry texture at the base in both shots, which is consistent. However, the degree of visible stone varies slightly — S06_SH002 shows marginally more stone texture at the arch base.
- **Severity:** WARN
- **Action:** Acceptable — years have passed in-story between these scenes; minor weathering is plausible.

### CA-005: MOD station concrete bay proportions
- **Shot(s):** S05_SH005_start (drone POV) vs S05_SH006_start (ground level)
- **Check:** Cross-shot location consistency — MOD station
- **Description:** The concrete bay viewed from above (drone POV) appears slightly wider relative to height than in the ground-level shot. Perspective foreshortening from the aerial angle accounts for most of this.
- **Severity:** WARN
- **Action:** Acceptable — the aerial view naturally compresses vertical proportions. The lichen-stained concrete, open moor, and bay opening are all consistent.

### CA-006: Inspection robot scale variation
- **Shot(s):** S02_SH001_start vs S02_SH003_start
- **Check:** Recurring visual element consistency — inspection robot
- **Description:** The robot appears slightly larger in S02_SH003 (low angle medium shot) than in S02_SH001 (dolly-forward wide). This is expected given the different focal lengths and camera positions but may read as a scale inconsistency if intercut quickly.
- **Severity:** WARN
- **Action:** Acceptable — the robot's design (wheeled base, sensor array, dark metallic body) is consistent. Scale variation is within normal lens-perspective range.

### CA-007: Coffee cup design variation
- **Shot(s):** S04_SH001_start vs S04_SH001_end
- **Check:** Prop consistency — coffee cup
- **Description:** Switch's coffee cup appears as a dark travel mug in the start frame but is slightly different in the end frame (lighter colour, different shape). The cup is small in frame and partially obscured.
- **Severity:** WARN
- **Action:** Acceptable at frame size — the cup is a background element in both frames and not featured in close-up. If a dedicated coffee cup insert were needed, a reference regeneration would be required.

### CA-008: Cardboard sign text rendering
- **Shot(s):** S05_SH006_start
- **Check:** Prop consistency — cardboard sign text
- **Description:** The sign text reads "SORRY. NEEDED TO TEST SYSTEM." which is close to but not exactly the scripted "SORRY. NEEDED TO TEST SYSTEM." — minor formatting difference. The reverse side "ALSO WE WERE BORED." renders correctly.
- **Severity:** WARN
- **Action:** Acceptable — the core message is legible and correct in meaning. AI text rendering limitations are known.

### CA-009: S05_SH003 start-to-end posture jump
- **Shot(s):** S05_SH003_start vs S05_SH003_end
- **Check:** Start–end interpolatability
- **Description:** The shift from relaxed seated pilots to tense standing/turning pilots is a large change for 8 seconds. The key frame at 4s (one pilot turning) provides an intermediate state. The interpolation path is achievable but requires the video model to handle multiple simultaneous body movements.
- **Severity:** WARN
- **Action:** Acceptable — the 8-second duration and key frame provide sufficient time and guidance. The scene is meant to show collective reaction.

### CA-010: Treeline absence verification
- **Shot(s):** All exterior shots
- **Check:** Global negative constraint — no trees
- **Description:** All exterior shots verified: no trees present. Some shots show low scrubby vegetation at moorland edges which is appropriate for Lewis. No planted or deciduous trees visible in any frame.
- **Severity:** WARN (positive verification logged)
- **Action:** Constraint satisfied. Logged for completeness.

---

## Checks Passed (No Issues)

| Check | Shots Verified |
|-------|---------------|
| Character identity — Switch | S04_SH001, S04_SH006, S05_SH002, S06_SH001 |
| Character identity — Iain | S04_SH002 |
| Character identity — Morag | S05_SH006 |
| Location — Bunker interior architecture | S02_SH001–SH004, S06_SH002 |
| Location — Control room architecture | S04_SH001–SH003, S04_SH006, S05_SH001–SH003 |
| Location — Launch strip | S03_SH001, S03_SH004, S04_SH004, S06_SH003 |
| Location — MOD station | S05_SH005, S05_SH006 |
| Location — Minch drone POV | S04_SH005 |
| Prop — Gannet UAV identity | S03_SH001, S03_SH004, S04_SH004, S05_SH005, S05_SH006, S06_SH003 |
| Prop — Cargo pod identity | S03_SH002, S03_SH003, S03_SH004 |
| Prop — Cardboard sign | S05_SH006 (both sides) |
| Prop — Rubber duck persistence | S04_SH001_end, S06_SH001_start |
| Drone POV override — no grain | S04_SH005, S05_SH005 |
| Intra-shot lighting consistency | All 23 shots |
| Left-hand traffic | S01_SH003, S03_SH001, S03_SH004 |
| Overcast sky — no blue | All exterior shots |
| Strawberry saturation exemption | S02_SH002, S03_SH002 |

---

## Conclusion

No BLOCK-level issues found. The 10 WARN issues are minor variations within acceptable tolerance for AI-generated imagery. All critical continuity chains (character identity, prop identity, location architecture, negative constraints) pass verification. The scene pack is ready for video prompt assembly (Phase 14).
