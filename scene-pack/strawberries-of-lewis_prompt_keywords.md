# Prompt Keyword Library — The Strawberry Bunkers of Lewis

## Global Style Phrase

"35 mm spherical, Kodak Vision3 250D characteristics, fine-to-medium organic grain, accurate daylight balance, slightly desaturated shadows with blue-grey undertone, gentle highlight rolloff, standard C-41 process, lifted blacks at 10–12 IRE, low-medium contrast"

## Per-Location-Type Vocabulary

### Exterior moor/road
"flat pewter Atlantic overcast, no direct sun, wet peat and stone surfaces, fence posts leaning eastward under wind, diffused ambient with no hard shadows, lifted blacks, grey-green grass desaturated, no blue sky, no trees, no dual carriageways, single-track road"

### Bunker interior (warm)
"warm amber-gold grow-light from above, artificial mid-summer feel, high humidity haze visible in light shafts, strawberry scarlet at full vibrancy against amber surround, clean concrete floor, polycarbonate arched roof overhead, no natural light from windows"

### Control room
"cool blue-green monitor glow from multiple screens, faces underlit by screens, dim overhead fluorescent tubes, corrugated metal walls, ergonomic chairs, shipping-container-width interior, cables and server racks visible, dark overall with screen illumination dominant"

### Launch strip exterior
"flat grey tarmac, wet with rain, low scrubby moorland surrounding, no trees, aviation strip markings faded, distant container buildings, overcast sky filling upper frame"

### MOD listening station
"brutalist concrete bunker on open moor, abandoned Cold War architecture, concrete bay doors, lichen-stained surfaces, sheep-cropped grass, rusted aerials, grey sky"

### Sea/Minch
"grey-green choppy water, white foam crests, cloud shelf low on horizon, rain visibility, no boats unless specified, strong lateral wind indicated by spray direction"

## Per-Lighting-Condition Vocabulary

### Pre-dawn (05:40–06:10)
"near-dark pre-dawn, sodium-orange practicals on launch strip, deep grey-blue surround, rain halos visible around point light sources, wet tarmac reflecting orange sodium, headlights of vans crawling, no ambient daylight yet"

### Morning overcast (06:10–09:00)
"grey diffused morning light, full overcast, no shadows, everything flat-lit, colours muted, visibility moderate in rain, pewter sky"

### Screen glow interior (any time)
"blue-green monitor glow dominant, multiple screens casting cool light upward onto faces, desk lamps small warm pools, overall darkness with screen islands of light, wall screens casting rectangles of colour on metal walls"

### Amber grow-light (bunker interior)
"warm amber-gold from LED strip arrays above, high humidity haze catching light in visible shafts, warm overall with no cool elements, concrete floor reflecting amber, no competing light sources"

## Global Negative Constraints

- no trees (Lewis moor is treeless inland; only occasional stunted scrub)
- no dual carriageways or motorway-style road markings
- no blue sky (always overcast; pewter or grey-white)
- no hard exterior shadows (overcast = no sun = no shadows)
- no US electrical sockets, signage, or road markings
- left-hand traffic only (Scotland drives on the left; steering wheels on right of vehicle)
- no palm trees, deciduous woodland, or Mediterranean vegetation
- no text, no watermarks, no logos, no labels, no annotations (generation artefact suppression)

## Selective Saturation Rules

- Strawberry Scarlet is exempt from the global 15–20% desaturation pass; maintain full vibrancy and push selectively against all surrounding desaturated elements
- Sodium-orange practicals retain warmth at full saturation in pre-dawn scenes
- Screen colours (blue-green) retain moderate saturation within the control room

## POV-Specific Overrides

### Drone/gannet POV
"digital-flat image, no film grain, deep focus throughout, gimbal-stabilised, no organic camera movement, machine-vision rendering — clean, clinical, no atmospheric haze, slight barrel distortion at edges from wide-angle fixed lens"

### Drone camera feed (as seen on monitors)
"compressed video feed, slight blockiness, telemetry overlay graphics, reduced colour depth, scan lines optional"
