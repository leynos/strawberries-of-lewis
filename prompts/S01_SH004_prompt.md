# S01_SH004 — Video Prompt

## Metadata
- **Shot ID:** S01_SH004
- **Scene:** SC-02 — The Reactor Arrives
- **Duration:** 6 seconds
- **Pacing:** moderate
- **Clip boundary (next):** scene_cut
- **Recommended model:** seedance_2_0
- **Model routing rationale:** Reference-driven (reactor prop at close range); start+end anchor for consistent cylinder detail; Seedance for identity consistency where visual references define the subject.
- **Aspect ratio:** 16:9
- **Target resolution:** 1920x1080
- **Resolution parameter:** 1080p
- **Generation strategy:** single_clip

## Frames
- **Start frame:** shots/S01_SH004/start.png
- **End frame:** shots/S01_SH004/end.png
- **Key frames:** None

## Reference Roles
- **start_image:** shots/S01_SH004/start.png
- **end_image:** shots/S01_SH004/end.png
- **image (location):** scene-pack/refs/ref_loc_moorland_road_pre_dawn.png

## Reference Audit
- Style anchor: omitted (pre-dawn override; location ref carries scene identity)
- Location ref: present (ref_loc_moorland_road_pre_dawn.png)
- Character refs: none (engineers too distant/anonymous for identity)
- Prop refs: none dedicated (reactor captured in storyboard frames; no separate reactor ref exists)
- Recurring visual elements: none

## Prompt

[STYLE] Cold Harboured Light — cool-neutral, desaturated, overcast Scottish Hebridean atmosphere
[FILMSTOCK] 35 mm spherical, Kodak Vision3 250D characteristics, fine-to-medium organic grain, accurate daylight balance, slightly desaturated shadows with blue-grey undertone, gentle highlight rolloff, standard C-41 process, lifted blacks at 10–12 IRE, low-medium contrast
[SCENE] near-dark pre-dawn, sodium-orange practicals on launch strip, deep grey-blue surround, rain halos visible around point light sources, wet tarmac reflecting orange sodium
[FRAMING] Medium shot, 50mm spherical lens, tripod mount, static camera, roadside angle
[PACING] Moderate — truck passes steadily through frame
[ACTION] A thick dull-grey metal cylinder — a reactor section — passes from left to right on a flatbed truck, close enough to fill the lower frame. Rain beads cling to and stream across its surface. Two figures in high-visibility jackets and hard hats walk alongside at truck pace, faces lit by tablet screens they study intently. The figures take several steps rightward over six seconds. The wet road and dark moorland are visible beneath and behind the flatbed. Blue police lights flash from escort vehicle behind. No branding is visible on the cylinder. The movement is steady, industrial, unhurried.
[SUBJECT] Flatbed truck carrying large cylindrical reactor section — smooth industrial grey cylinder, rain-beaded surface, walking engineers with illuminated tablets alongside, blue police lights behind
[AUDIO] Heavy diesel engine passing; rain on metal; footsteps; tablet tap. No background music. No narration.
[DURATION] 6 seconds

## Audio Generation Preferences
- **Source:** none
- **Rationale:** Narration and ambient audio handled externally; model should not generate audio.

## Consistency Notes
- Left-hand traffic; engineers with tablets
- Sodium-orange retains warmth at full saturation in pre-dawn
- Global negatives: no trees, left-hand traffic for vehicles, no US signage
- Reactor cylinder must be consistently dull grey metal, no branding, no markings
- This shot is review-gated (required) — reactor detail is continuity-critical for later scenes

## Generation Prompt

Medium shot from roadside. A thick dull-grey metal cylinder — a reactor section — passes from left to right on a flatbed truck, close enough to fill the lower frame. Rain beads cling to and stream across its surface. Two figures in high-visibility jackets and hard hats walk alongside at truck pace, faces lit by tablet screens. The figures take several steps rightward over six seconds. Wet road and dark moorland visible beneath and behind the flatbed. Blue police lights flash from escort vehicle behind. No branding on the cylinder. Movement is steady, industrial, unhurried.

The start image shows the cylinder entering frame left. The end image shows it further right with trailing end visible.

Medium shot, 50mm spherical, static tripod at roadside. No camera movement. No cuts. No zoom. 6 seconds, moderate pacing.

Pre-dawn, sodium-orange halos, deep grey-blue surround. No ambient daylight.

35 mm, Kodak Vision3 250D, fine-to-medium organic grain, desaturated shadows, lifted blacks.

The start image is the first frame. The end image is the final frame. Preserve all supplied reference-image identities and layouts throughout. No narration.
