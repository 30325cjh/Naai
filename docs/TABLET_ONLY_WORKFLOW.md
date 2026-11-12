# Tablet-only production route

## Constraint
This project is being prepared from an Android tablet only. Live2D Cubism Editor is officially documented for Windows and macOS desktop environments, so do not assume it can be installed or operated natively on Android.

## Browser-based rigging candidate
Ikimotion Studio (https://ikimotion.com/) advertises browser-based 2D rigging and animation on desktop, tablet, and phone, including layered PSD import, meshes, deformers, parameters, physics, expressions, animation, and export of a moc3/model3.json package.

This is a third-party service, not a Live2D product. Before relying on it:
1. Open the site in Chrome on the tablet.
2. Confirm the editor UI is usable in landscape mode.
3. Check whether project creation and export are available on the free tier.
4. Confirm the exported package is genuinely compatible with the intended Cubism SDK runtime.
5. Do not upload private or sensitive artwork unless comfortable with the service's terms and storage policy.

## Artwork requirement
Rigging requires separated artwork. The supplied reference images are flattened images, not separated layers. The project still needs a newly drawn, simplified remake artwork with independently editable layers for:
- face and ears
- left/right eyes, irises, highlights, eyelids
- brows and mouth
- front/side/back hair and ponytail segments
- headset
- neck, shirt, tie, jacket and straps

Do not label the model complete until actual artwork has been created, rigged, exported, and tested.

## Current status
- [x] Tablet-only workflow selected
- [x] Browser-based rigging candidate documented
- [ ] Verify Ikimotion works on this exact Android tablet
- [ ] Create separated remake artwork
- [ ] Rig parameters, expressions and physics
- [ ] Export and validate model package
