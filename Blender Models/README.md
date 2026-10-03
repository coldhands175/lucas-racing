# Digger Dan

Editable construction truck body using the actual Reusable-Monster-Chassis.blend mechanics. Original source/reference files were not changed. Front is Blender -X, up is Z, units are metres. The source opens on the neutral LOD0 studio assembly; enable the three original authoring collections and hide every LOD collection to edit the chassis/body pieces. The new construction kit has 93 meshes plus 8 suspension anchor empties.

Files:

- Digger-Dan.blend — editable body/mechanics, neutral LOD0/1/2 assemblies, lights/cameras.
- DiggerDan.fbx — LOD0, main runtime export.
- DiggerDan_LOD1.fbx and DiggerDan_LOD2.fbx — independent alternatives with equivalent pivot/anchor structures.
- DiggerDan-hero/front/side/rear.png — rendered LOD0 meshes.
- DiggerDan-LOD1-preview.png and DiggerDan-LOD2-preview.png — actual FBXs reimported into the studio.
- DiggerDan-manifest.json — hashes, source component mapping, paint/material slots, model/wheel bounds, radii, wheel and suspension pivot names.
- DiggerDan-verification.json — fresh source reopen and all FBX roundtrip checks.

## Runtime hookup

Use one LOD at a time. Each has 12 rigid mesh assemblies: body, root-level links, 2 axles, 4 shocks, and 4 wheels. All four wheel spin meshes remain children of independent steering and spin empties. Naming pattern: DiggerDan_LOD0_FL_Steer and DiggerDan_LOD0_FL_Spin (substitute LOD index and FL/FR/RL/RR). Steering rotates Blender local Z; spin rotates local Y. Verify actual Unity transform axes following FBX conversion before driving controls.

Each suspension has separately named UpperAnchor and LowerAnchor empties. Upper anchors are children of sprung body; lower anchors are children of their source axle. The shock is an independent mesh and pivot containing spring, piston, damper and perches. None is fused with the body or wheel. Example: DiggerDan_LOD0_FRONT_shock_-1 and its _Geometry child.

Shared source spring perch centres are X = front -1.48 / rear +1.48, Y = left -0.94 / right +0.94, upper Z = 2.222 and lower Z = 1.2706 metres. Rest perch separation is 0.9514 m. The shock has source local lower Z=0.09, upper Z=0.80 and neutral local Z scale 1.34. To drive its length, map those two rest points to the current anchor positions and preserve lateral scale. Scaling only around the original shock origin makes the lower attachment drift. In Unity, derive the local rest endpoints using the imported pivot's inverse transform rather than assuming Blender axes survived unchanged. Lower anchors need wheel-travel offsets (the neutral axle parents do not themselves implement suspension physics).

The per-shock combined mesh supports whole-assembly length adjustment. It does not independently telescope the piston while retaining fixed damper/coil thickness. Root-level links/prop shafts remain combined static neutral artwork. The parent should separate or replace those if accurate individual link articulation is required. No colliders, physics controller, Unity prefab, LODGroup, URP materials or game integration are supplied in this asset-only work.

## Quality and performance

Final Blender FBX reimports have 41,173 / 16,144 / 5,892 triangles, below 45k / 20k / 6k targets. Source meshes have 41,173 / 16,178 / 5,894; FBX roundtrip removes 34 LOD1 and 2 LOD2 faces. Both counts are explicitly recorded rather than assumed equal. All reimported normals are finite and normalized, with no missing materials or zero-area faces. Bounds agree within 0.1 mm and wheel centres within 0.00001 m.

LOD0 retains rounded manufactured edges and bolts. LOD1 visibly coarsens tiny lights, rim hardware and tread. LOD2 protects the body silhouette but removes tiny rim/bolt/grille details and has angular tyres/hubs; use at distance. LOD0/1 have 50 material slots across the 12 meshes, LOD2 40; this is not a draw-call or iPad performance claim. Material consolidation/atlasing and actual device profiling remain integration work. Blender's rubber microtexture is procedural and does not export as a baked normal map.

## Rebuild / verify

Run these in Blender background mode, in order, without closing or modifying a user's interactive Blender session:

1. Tools/fleet/build_digger_dan.py (creates assets and four views; DIGGER_SKIP_RENDER=1 omits unchanged studio images)
2. Tools/fleet/check_digger_dan.py (writes fresh verification and annotates manifest with actual reimport counts)
3. Tools/fleet/render_digger_lods.py (renders actual reimported LOD1/2 FBXs)

The scripts resolve the game folder relative to their own locations. Built and checked with Blender 5.2.0 LTS. No Unity importer/device or runtime collision testing was performed here.
