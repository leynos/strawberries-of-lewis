# S01_SH002 — Video Prompt

## Metadata
- **Shot ID:** S01_SH002
- **Scene:** SC-01 — The Island Before
- **Duration:** 6 seconds
- **Pacing:** slow
- **Clip boundary (next):** scene_cut
- **Recommended model:** seedance_2_0
- **Model routing rationale:** Static camera; minimal motion (plume only); start+end anchor mode ideal; Seedance for reference-driven continuity where plume is the sole dynamic element.
- **Aspect ratio:** 16:9
- **Target resolution:** 1920x1080
- **Resolution parameter:** 1080p
- **Generation strategy:** single_clip

## Frames
- **Start frame:** shots/S01_SH002/start.png
- **End frame:** shots/S01_SH002/end.png
- **Key frames:** None

## Reference Roles
- **start_image:** shots/S01_SH002/start.png
- **end_image:** shots/S01_SH002/end.png
- **image (style):** scene-pack/refs/style_anchor_01.png

## Reference Audit
- Style anchor: present (style_anchor_01.png)
- Location ref: not required (storyboard frames carry location)
- Character refs: none (no characters in shot)
- Prop refs: none (plume is environmental, not a prop)
- Recurring visual elements: none

## Prompt

[STYLE] Cold Harboured Light — cool-neutral, desaturated, overcast Scottish Hebridean atmosphere
[FILMSTOCK] 35 mm spherical, Kodak Vision3 250D characteristics, fine-to-medium organic grain, accurate daylight balance, slightly desaturated shadows with blue-grey undertone, gentle highlight rolloff, standard C-41 process, lifted blacks at 10–12 IRE, low-medium contrast
[SCENE] flat pewter Atlantic overcast, no direct sun, wet peat and stone surfaces, fence posts leaning eastward under wind, diffused ambient with no hard shadows, lifted blacks, grey-green grass desaturated, no blue sky, no trees
[FRAMING] Wide shot, 35mm spherical lens, tripod mount, static camera
[PACING] Slow, observational — plume as sole dynamic element
[ACTION] Static wide of Lewis moorland horizon. A white steam plume rises vertically from the SMR site at right-centre of frame — the only vertical element in a horizontal landscape. Over six seconds the plume climbs higher and begins to feather at its top edge, drifting slightly right with the wind. The moorland, fence posts, wet road, and grey sky remain completely static throughout. The plume is the sole moving element — quiet, persistent, transformative.
[SUBJECT] White steam plume rising from SMR against horizontal moorland — sole vertical element in flat landscape
[AUDIO] Wind (steady); faint industrial hum from distance. No background music. No narration.
[DURATION] 6 seconds

## Audio Generation Preferences
- **Source:** none
- **Rationale:** Narration and ambient audio handled externally; model should not generate audio.

## Consistency Notes
- Plume is the only change; everything else static
- Global negatives: no trees, no blue sky, no hard shadows outside
- Plume must be white (not grey or dark) — it is steam, not smoke

## Generation Prompt

Static wide shot of Lewis moorland under overcast sky. A white steam plume rises steadily from the SMR site at right-centre of frame — the only vertical element in the flat horizontal landscape. Over six seconds the plume climbs higher and begins to feather at its top edge, drifting slightly right with the wind. The moorland, fence posts, wet road, and grey sky remain completely static. The plume is the sole moving element — quiet, persistent.

The start image is the opening frame. The end image shows the plume slightly taller and feathered at top.

Wide shot, 35mm spherical, static tripod. No camera movement. No cuts. No zoom. 6 seconds, slow pacing.

No trees. No blue sky. No hard shadows. Plume is white steam, not smoke.

35 mm, Kodak Vision3 250D, fine-to-medium organic grain, desaturated shadows, lifted blacks.

The start image is the first frame. The end image is the final frame. Preserve all supplied reference-image identities and layouts throughout. No narration.
