# S01_SH001 — Video Prompt

## Metadata
- **Shot ID:** S01_SH001
- **Scene:** SC-01 — The Island Before
- **Duration:** 8 seconds
- **Pacing:** slow
- **Clip boundary (next):** continuous
- **Recommended model:** kling3_0
- **Model routing rationale:** Landscape establishing with one-vector pan; camera path dominates; no identity constraints; Kling primary for wide exteriors with clean geometric anchors.
- **Aspect ratio:** 16:9
- **Target resolution:** 1920x1080
- **Resolution parameter:** 1080p
- **Generation strategy:** single_clip

## Frames
- **Start frame:** shots/S01_SH001/start.png
- **End frame:** shots/S01_SH001/end.png
- **Key frames:** None

## Reference Roles
- **start_image:** shots/S01_SH001/start.png
- **end_image:** shots/S01_SH001/end.png
- **image (style):** scene-pack/refs/style_anchor_01.png

## Reference Audit
- Style anchor: present (style_anchor_01.png)
- Location ref: not required (storyboard frames carry location)
- Character refs: none (no characters in shot)
- Prop refs: none (no props in shot)
- Recurring visual elements: none

## Prompt

[STYLE] Cold Harboured Light — cool-neutral, desaturated, overcast Scottish Hebridean atmosphere
[FILMSTOCK] 35 mm spherical, Kodak Vision3 250D characteristics, fine-to-medium organic grain, accurate daylight balance, slightly desaturated shadows with blue-grey undertone, gentle highlight rolloff, standard C-41 process, lifted blacks at 10–12 IRE, low-medium contrast
[SCENE] flat pewter Atlantic overcast, no direct sun, wet peat and stone surfaces, fence posts leaning eastward under wind, diffused ambient with no hard shadows, lifted blacks, grey-green grass desaturated, no blue sky, no trees, no dual carriageways, single-track road
[FRAMING] Extra-wide shot, 28mm spherical lens, tripod mount, slow pan right revealing more moorland
[PACING] Slow, contemplative establishing pan across landscape
[ACTION] Camera pans slowly right across treeless Lewis moorland under flat pewter overcast. Fence posts lean eastward in the foreground, dark against grey-green peat. A narrow single-track road curves through the middle distance, wet with rain, entirely empty. The sky fills the upper two-thirds of frame — unbroken grey-white cloud. Wind moves the sparse grass throughout. Fence posts exit left of frame as new ones enter right. No trees, no structures, no people. The landscape is ancient, patient, and wet.
[SUBJECT] Treeless Lewis moorland — wet peat, leaning fence posts, single-track road, pewter overcast sky
[AUDIO] Wind (constant, moderate); rain on grass (light bed); distant sheep. No background music. No narration.
[DURATION] 8 seconds

## Audio Generation Preferences
- **Source:** none
- **Rationale:** Narration and ambient audio handled externally; model should not generate audio.

## Consistency Notes
- No trees; no blue sky; establish baseline landscape
- Global negatives: no trees, no blue sky, no hard shadows outside, left-hand traffic for vehicles, no US signage
- This is the opening shot; sets visual grammar for entire production

## Generation Prompt

Pre-dawn Lewis moorland establishing shot. Camera pans slowly right across treeless moorland under flat pewter overcast sky. Fence posts lean eastward in the foreground, dark against grey-green peat. A narrow single-track road curves through the middle distance, wet with rain, entirely empty. The sky fills the upper two-thirds of frame — unbroken grey-white cloud. Wind moves sparse grass. Fence posts exit left of frame as new ones enter right. No trees, no structures, no people. The landscape is flat, ancient, patient, and wet.

Extra-wide shot, 28mm spherical lens, tripod mount, slow steady pan right. Deep focus throughout. 8 seconds, slow pacing.

No trees. No blue sky. No hard shadows. No buildings. No people.

35 mm spherical, Kodak Vision3 250D, fine-to-medium organic grain, slightly desaturated shadows with blue-grey undertone, lifted blacks, low-medium contrast.

The start image is the first frame. The end image is the final frame. Preserve all supplied reference-image identities and layouts throughout. No narration.
