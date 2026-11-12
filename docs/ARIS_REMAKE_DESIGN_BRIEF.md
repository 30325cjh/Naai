# Aris Remake — Upper-Body Live2D Production Brief

**Target:** Live2D Cubism model for a future Android app  
**Scope:** head, shoulders, torso, waist/upper-skirt edge  
**Status:** design specification only; no finished artwork or Cubism export yet.

## 1. Remake direction

Create a clean, slightly simplified anime rendition that reads as Aris at a glance without attempting a pixel-perfect recreation.

### Preserve these identity anchors
1. Very dark charcoal/navy hair with cool slate and muted teal highlights.
2. Long tapered center fringe falling diagonally across the face. Preserve this asymmetry.
3. Large luminous cyan-blue eyes with concentric, digital-looking ring highlights.
4. Dark headset band and distinctive teal-blue ear-side module.
5. White shirt, cyan tie, blue/black outer jacket with white panels and dark straps.

### Simplify for animation
- Group thin strands into broad overlapping hair clumps.
- Use three main fringe pieces and two side locks.
- Split each side ponytail into root, middle, and tip.
- Reduce tiny jacket seams, zippers, insignia, and text to simple graphic shapes.
- Use 2–3 cel-shading tones per material.
- Default pose: relaxed, front-facing, slight friendly smile.
- Crop: top of head to waist/upper-skirt edge.

## 2. Palette guide

| Element | Suggested color |
|---|---|
| Main hair | #252B3A |
| Hair midtone | #59677D |
| Hair highlight | #879EAA |
| Iris | #39C9F2 with deep blue rim |
| Headset | #171E2D |
| Headset accent | #087C9C |
| Tie | cyan |
| Jacket | deep navy, saturated blue, cool white |
| Shirt | cool white with pale blue shadow |
| Skin | pale warm neutral with soft pink blush |

These are starting colors for the remake, not sampled official values.

## 3. PSD source layout

Recommended canvas: **3000 × 3600 px**, transparent background, sRGB. Leave at least 8% transparent breathing room around moving hair.

Organize groups back-to-front:

```text
Aris_Remake.psd
├── 00_GUIDES
├── 01_BACK_HAIR
│   ├── BackHair_Base
│   ├── BackHair_LeftClump
│   ├── BackHair_RightClump
│   ├── BackHair_Highlights
│   ├── Ponytail_Far_Root / Mid / Tip
│   └── Ponytail_Near_Root / Mid / Tip
├── 02_BODY_BACK
│   ├── Neck
│   ├── Body_Base
│   └── Shoulder_Shadow
├── 03_FACE
│   ├── Face_Base
│   ├── Ear_L / Ear_R
│   ├── Nose
│   └── Blush_L / Blush_R
├── 04_EYES
│   ├── Eye_L_White / Iris / Pupil / Ring / Highlight / UpperLid / LowerLid
│   └── Eye_R_White / Iris / Pupil / Ring / Highlight / UpperLid / LowerLid
├── 05_BROWS_AND_MOUTH
│   ├── Brow_L / Brow_R
│   ├── Mouth_Closed
│   ├── Mouth_Open
│   ├── Mouth_Inside / Teeth / Tongue
├── 06_FRONT_HAIR
│   ├── Bang_Left
│   ├── Bang_Center_Signature
│   ├── Bang_Right
│   └── SideLock_Left / SideLock_Right
├── 07_HEADSET
│   ├── Headset_Band_Back
│   ├── Headset_EarModule
│   └── Headset_Details
└── 08_OUTFIT_FRONT
    ├── Shirt
    ├── Collar_Left / Collar_Right
    ├── Tie_Knot / Tie_Body
    ├── Jacket_BackPanels
    ├── Jacket_LeftPanel / Jacket_RightPanel
    ├── Sleeve_Left / Sleeve_Right
    ├── Strap
    └── Small_Details
```

### PSD construction rules
- Every moving part must be independent with transparency.
- Paint hidden overlap areas behind fringe, face, neck, shoulders, and jacket edges.
- Keep eyes, brows, side locks, and ponytail pieces independent left/right.
- Do not merge eye or hair highlights into base layers.
- Use descriptive ASCII layer names.
- Keep line art and color fills grouped by part where practical.

## 4. Cubism parameter plan

| Parameter ID | Range | Purpose |
|---|---:|---|
| ParamAngleX | -30..30 | face yaw |
| ParamAngleY | -20..20 | face pitch |
| ParamAngleZ | -20..20 | face roll |
| ParamBodyAngleX | -10..10 | upper-body turn |
| ParamBodyAngleY | -5..5 | upper-body lift |
| ParamBodyAngleZ | -8..8 | shoulder tilt |
| ParamEyeLOpen | 0..1 | left blink |
| ParamEyeROpen | 0..1 | right blink |
| ParamEyeBallX | -1..1 | gaze horizontal |
| ParamEyeBallY | -1..1 | gaze vertical |
| ParamBrowLY | -1..1 | left brow |
| ParamBrowRY | -1..1 | right brow |
| ParamMouthOpenY | 0..1 | mouth opening |
| ParamMouthForm | -1..1 | smile/frown |
| ParamBreath | 0..1 | breathing |
| Custom_HairFrontX | -1..1 | signature fringe sway |
| Custom_SideLockLX | -1..1 | left side lock |
| Custom_SideLockRX | -1..1 | right side lock |
| Custom_PonytailNear | -1..1 | near ponytail chain |
| Custom_PonytailFar | -1..1 | far ponytail chain |
| Custom_TieSway | -1..1 | tie response |

## 5. Expression set

Author these as parameter combinations in Cubism Editor and export genuine `.exp3.json` files:

1. Normal — neutral eyes, small closed smile.
2. Smile — softer eyes, raised mouth corners.
3. Happy — both eyes closed, wide smile, light blush.
4. Surprised — eyes wide, brows raised, mouth open.
5. Angry — brows lowered inward, narrowed eyes, firm mouth.
6. Sad — brows tilted upward in the center, mouth corners down.
7. Shy — blush, averted gaze, small smile.
8. Sleepy — half-lidded eyes, relaxed brows.
9. Wink — one eye closed, other open.
10. Confused — asymmetric brows, side gaze, uncertain mouth.

## 6. Motion and physics

### Motions
- Idle: subtle breathing, slow blink, minimal head sway.
- Talk: mouth movement driven by app audio/viseme input; small head motion.
- Greeting: short head dip and return.
- Listen: slight head tilt and gaze shift.
- Surprise: quick, restrained eye/head reaction.

### Physics groups
- Hair_Side_Left and Hair_Side_Right: short side-lock chains.
- Ponytail_Near and Ponytail_Far: root → middle → tip.
- Tie: small delayed sway.
- Jacket panels: very subtle movement only.

Keep the signature center bang's movement restrained so it does not cover both eyes during turns.

## 7. Final export layout

```text
Aris_Remake_Live2D/
├── Source/Aris_Remake.psd
├── Model/Aris_Remake.moc3
├── Model/Aris_Remake.model3.json
├── Model/Aris_Remake.physics3.json
├── Model/Aris_Remake.cdi3.json
├── Model/textures/texture_00.png
├── Expressions/*.exp3.json
└── Motions/*.motion3.json
```

## 8. Validation checklist

- Head yaw/pitch/roll does not expose gaps.
- Both eyes blink independently and wink correctly.
- Gaze tracking does not detach iris highlights.
- Mouth-open and mouth-form combinations do not create gaps.
- Fringe and side hair remain coherent at angle extremes.
- Ponytail physics settles without jitter.
- All expressions and motions load in Cubism Viewer.
- Model loads in a minimal Android Cubism SDK test app.

## 9. Production boundary

The supplied images define the visual direction but are flattened references, not layered source artwork. This document is a design/production brief only. The separated illustration, Cubism mesh/deformer rigging, physics tuning, and Cubism export still need to be created and tested. Do not label the model complete until the exported `.moc3` passes validation.
