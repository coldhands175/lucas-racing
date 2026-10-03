# Flame pickup — Blender modelling trial

An original, editable 3D interpretation of your red flame pickup concept. The model has a rounded vintage bonnet and cab, an open pickup bed, separate flame artwork, chrome grille and exhausts, detailed tyres, and exposed suspension.

## Open and explore

Open **Flame-Pickup-Trial.blend** in Blender. The scene opens with the hero camera selected. Use the mouse wheel/middle mouse to explore the model, or render with F12. Press Space with the pointer over the 3D viewport to play the assembly demonstration. Frame 1 is the neutral pose.

The **START HERE** text inside the Blender file explains its organisation. The reference is an artistic guide rather than an exact engineering blueprint; this trial interprets its shapes and proportions.

## What can be reused

| Component | How it is organised | Reuse for another truck |
|---|---|---|
| Tyres and chevron tread | Four wheel assemblies share the same mesh data | Edit one tyre mesh to update all four; reuse across the fleet |
| Rims, hubs, bolts and bead rings | Separate linked components with their own materials | Recolour the rims or replace their design |
| Steering and wheel spin | Each wheel has a centred steering parent and a separate spin control | Connect these controls to the eventual vehicle controller |
| Frame, axles and differentials | Separate parts in the reusable mechanical collection | Retain the basic assembly; adjust wheelbase and mounting points for different bodies |
| Springs and shocks | Separate components with a short travel demonstration | Reuse their design, then connect their movement to the game suspension |
| Body mounting points | Named mounts beneath the shell | Align replacement body kits to a consistent base |
| Paint and trim | Individually named materials | Change body colour, orange trim, wheel colour, chrome and glass independently |

**Reusable-Monster-Chassis.blend** contains the mechanics and wheel controls with the flame body removed. Start future truck designs from this file.

The vintage cab, bonnet, fenders, bed, flames, grille and exhaust layout form this truck's body kit. Their materials and some trim pieces can be reused, but the dinosaur, shark, ice and other trucks need their own distinctive shells.

## Included files

- **Flame-Pickup-Trial.blend** — editable source, studio, four cameras and animation.
- **Reusable-Monster-Chassis.blend** — separate editable base for future truck bodies.
- **Flame-Pickup-Trial.glb** — static neutral-pose model with materials; studio excluded.
- **Flame-Pickup-Trial.fbx** — static exchange file for a conventional game asset workflow; studio excluded.
- **Flame-Pickup-Hero.png**, **Front.png**, **Side.png**, **Rear.png** — rendered review views (each filename has the Flame-Pickup prefix).
- **Reusable-Mechanical-Assembly.png** — the reusable base without bodywork.
- **Model-Verification.json** — scale, mesh counts, dependency checks and export verification.

## Animation and game integration

Frames 1–96 contain wheel rotation, front steering, and body/spring travel at 24 fps. This is a keyframed assembly demonstration, not simulated driving. The simplified visual control arms and prop shafts have baked movement to follow the body travel; they are not a physical simulation. The two export files intentionally contain the neutral pose; the editable animation stays in Blender.

The model uses metres and faces Blender's -X direction, with Z up. The measured full size is approximately **5.22 m long × 4.14 m wide × 3.95 m high**. glTF exports in its conventional Y-up coordinates.

This presentation version evaluates to **271,716 triangles across all instances**. It deliberately retains separate parts for editing. Before iPad integration, reduce detail into distance-based versions, combine stationary pieces into fewer meshes/material batches, prepare UV layouts and baked textures where needed, create simple collision shapes, and profile on the actual iPad. Vehicle handling remains a separate implementation task.

There are no external image dependencies. Rubber has subtle procedural surface detail in Blender; that microtexture is not baked into the exports. Exported rubber keeps its base colour and roughness. FBX material appearance should be checked when assigning the final Unity shaders.

The Blender source was reopened and its four wheel hierarchies and animation checked. GLB and FBX were re-imported in Blender to check their structure; this does not establish Unity or iPad runtime performance.
