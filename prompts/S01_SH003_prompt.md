# S01_SH003 — Video Prompt

## Metadata
- **Shot ID:** S01_SH003
- **Scene:** SC-02 — The Reactor Arrives
- **Duration:** 6 seconds
- **Pacing:** moderate
- **Clip boundary (next):** continuous
- **Recommended model:** kling3_0
- **Model routing rationale:** Pre-dawn low-light exterior; vehicle motion L→R; camera structure and geometric anchors dominate; Kling primary for scene structure with approaching headlights.
- **Aspect ratio:** 16:9
- **Target resolution:** 1920x1080
- **Resolution parameter:** 1080p
- **Generation strategy:** single_clip

## Frames
- **Start frame:** shots/S01_SH003/start.png
- **End frame:** shots/S01_SH003/end.png
- **Key frames:** None

## Reference Roles
- **start_image:** shots/S01_SH003/start.png
- **end_image:** shots/S01_SH003/end.png
- **image (location):** scene-pack/refs/ref_loc_moorland_road_pre_dawn.png

## Reference Audit
- Style anchor: omitted (pre-dawn override; location ref carries scene identity)
- Location ref: present (ref_loc_moorland_road_pre_dawn.png)
- Character refs: none (no characters visible at this distance)
- Prop refs: none (vehicles too distant for prop-level identity)
- Recurring visual elements: none

## Prompt

[STYLE] Cold Harboured Light — cool-neutral, desaturated, overcast Scottish Hebridean atmosphere
[FILMSTOCK] 35 mm spherical, Kodak Vision3 250D characteristics, fine-to-medium organic grain, accurate daylight balance, slightly desaturated shadows with blue-grey undertone, gentle highlight rolloff, standard C-41 process, lifted blacks at 10–12 IRE, low-medium contrast
[SCENE] near-dark pre-dawn, sodium-orange practicals on launch strip, deep grey-blue surround, rain halos visible around point light sources, wet tarmac reflecting orange sodium, headlights of vans crawling, no ambient daylight yet
[FRAMING] Wide shot, 35mm spherical lens, tripod mount, static camera, road-level perspective
[PACING] Moderate — convoy movement provides steady approach energy
[ACTION] Pre-dawn blue-grey darkness on a narrow Lewis road. In the far distance, a cluster of headlights approaches steadily — a convoy of heavy vehicles escorted by police cars with flashing blue lights. Over six seconds the convoy grows closer, headlights brightening, and the shapes of flatbed trucks carrying thick industrial cylinders become visible in the spill of light on wet tarmac. The road is narrow and wet, reflecting the approaching lights. The surrounding moorland remains dark and featureless. The blue police lights pulse throughout. Vehicles travel on the left side of the road (UK left-hand traffic).
[SUBJECT] Convoy of vehicles — police escort with blue lights, flatbed trucks carrying cylindrical reactor sections, headlights piercing rain on wet single-track road
[AUDIO] Diesel engines (distant); rain; blue-light siren (faint). No background music. No narration.
[DURATION] 6 seconds

## Audio Generation Preferences
- **Source:** none
- **Rationale:** Narration and ambient audio handled externally; model should not generate audio.

## Consistency Notes
- Left-hand traffic critical; vehicles on left side of road
- Sodium-orange retains warmth at full saturation in pre-dawn
- Global negatives: no trees, left-hand traffic for vehicles, no US signage
- Convoy approaches — do not have it pass camera (that's SH004)

## Generation Prompt

Pre-dawn darkness, narrow wet Lewis road. Wide shot, 35mm spherical, static tripod at road level. A convoy of heavy vehicles approaches from the distance with headlights piercing rain. Police escort with flashing blue lights leads. Flatbed trucks carrying thick industrial cylinders become visible in headlight spill on wet tarmac. Over six seconds the convoy grows closer, headlights brightening, vehicle shapes becoming clearer. Road is narrow and wet, reflecting approaching lights. Surrounding moorland remains dark and featureless. Blue police lights pulse throughout. Vehicles on the left side of road (UK left-hand traffic).

6 seconds, moderate pacing. No cuts. No zoom. No camera movement.

No trees. No ambient daylight. Deep grey-blue pre-dawn surround. Sodium-orange halos around point light sources.

35 mm spherical, Kodak Vision3 250D, fine-to-medium organic grain, lifted blacks, low-medium contrast.

The start image is the first frame. The end image is the final frame. Preserve all supplied reference-image identities and layouts throughout. No narration.
