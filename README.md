# stl-mass-properties

Compute mass properties, meaning volume, surface area, centre of mass, and the inertia tensor, from an STL mesh, in C.

## Why

CAD will not report mass properties for a surface-only model, because there is no closed solid. The divergence theorem does not need a closed solid in that sense. Given a closed, consistently oriented triangle mesh, the volume comes straight out. When the mesh is not closed, this tool reports where the gaps are, which is what you need to fix it.

Tags: algorithms-data-structures

## Status

In progress. Shipped units are tagged (v0.1, v0.2, and so on).

| Unit | What | Done when |
|------|------|-----------|
| 1 | Parse binary STL, triangle count, bounding box | Reads a known file and the counts match |
| 2 | Volume and surface area by the divergence theorem | A unit cube reads volume 1.000 and a sphere matches 4/3 pi r cubed |
| 3 | Centre of mass | The centre of a symmetric part lands on its axis of symmetry |
| 4 | Inertia tensor and principal axes | Matches the closed form tensor of a box |
| 5 | Vertex weld and watertight check | Reports boundary edges and open loops on a broken mesh |

## Reference answers

Closed form primitives such as a cube, sphere, and cylinder give exact values to check against. Autodesk Inventor reports volume, mass, and centre of gravity for the same part.

## Build

Added with unit 1, using CMake and Unity tests, with AddressSanitizer on test builds.

## Workflow

Work on a branch, open a pull request, let CI run, then merge. Keep main green.
