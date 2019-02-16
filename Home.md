## Belfry OpenScad Library Documentation

The library files are as follows:

### Commonly Used
  - [`transforms.scad`](transforms.scad): The most commonly used transformations, manipulations, and shortcuts are in this file.
  - [`shapes.scad`](shapes.scad): Common useful shapes and structured objects.
  - [`masks.scad`](masks.scad): Shapes that are useful for masking with `difference()` and `intersect()`.
  - [`threading.scad`](threading.scad): Modules to make triangular and trapezoidal threaded rods and nuts.
  - [`paths.scad`](paths.scad): Functions and modules to work with arbitrary 3D paths.
  - [`beziers.scad`](beziers.scad): Functions and modules to work with bezier curves.

### Standard Parts
  - [`involute_gears.scad`](involute_gears.scad): Modules and functions to make involute gears and racks.
  - [`joiners.scad`](joiners.scad): Modules to make joiner shapes for connecting separately printed objects.
  - [`sliders.scad`](sliders.scad): Modules for creating simple sliders and rails.
  - [`metric_screws.scad`](metric_screws.scad): Functions and modules to make metric screws, nuts, and screwholes.
  - [`linear_bearings.scad`](linear_bearings.scad): Modules to make mounts for LMxUU style linear bearings.
  - [`nema_steppers.scad`](nema_steppers.scad): Modules to make mounting holes for NEMA motors.
  - [`phillips_drive.scad`](phillips_drive.scad): Modules to create Phillips screwdriver tips.
  - [`torx_drive.scad`](torx_drive.scad): Functions and Modules to create Torx bit drive holes.
  - [`wiring.scad`](wiring.scad): Modules to render routed bundles of wires.

### Miscellaneous
  - [`math.scad`](math.scad): Useful helper functions.
  - [`constants.scad`](constants.scad): Useful constants for vectors, edges, etc.
  - [`quaternions.scad`](quaternions.scad): Functions to work with quaternion rotations.
  - [`debug.scad`](debug.scad): Modules to help debug creation of beziers, `polygons()`s and `polyhedron()`s

## Terminology
For purposes of these library files, the following terms apply:
- **Left**: Towards X-
- **Right**: Towards X+
- **Front**/**Forward**: Towards Y-
- **Back**/**Behind**: Towards Y+
- **Bottom**/**Down**/**Below**: Towards Z-
- **Top**/**Up**/**Above**: Towards Z+
