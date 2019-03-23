# Library File torx\_drive.scad

Torx driver bits
To use, add these lines to the top of your file:
```
include <BOSL/constants.scad>
use <BOSL/torx_drive.scad>
```

---

# Table of Contents

1. [Functions](#functions)
    - [`torx_outer_diam()`](#torx_outer_diam)
    - [`torx_inner_diam()`](#torx_inner_diam)
    - [`torx_depth()`](#torx_depth)
    - [`torx_tip_radius()`](#torx_tip_radius)
    - [`torx_rounding_radius()`](#torx_rounding_radius)

2. [Modules](#modules)
    - [`torx_drive2d()`](#torx_drive2d)
    - [`torx_drive()`](#torx_drive)

---

# 1. Functions

### torx\_outer\_diam()

**Description**:
Get the typical outer diameter of Torx profile.

Argument        | What it does
--------------- | ------------------------------
`size`          | Torx size.

---

### torx\_inner\_diam()

**Description**:
Get typical inner diameter of Torx profile.

Argument        | What it does
--------------- | ------------------------------
`size`          | Torx size.

---

### torx\_depth()

**Description**:
Gets typical drive hole depth.

Argument        | What it does
--------------- | ------------------------------
`size`          | Torx size.

---

### torx\_tip\_radius()

**Description**:
Gets minor rounding radius of Torx profile.

Argument        | What it does
--------------- | ------------------------------
`size`          | Torx size.

---

### torx\_rounding\_radius()

**Description**:
Gets major rounding radius of Torx profile.

Argument        | What it does
--------------- | ------------------------------
`size`          | Torx size.

---

# 2. Modules

### torx\_drive2d()

**Description**:
Creates a torx bit 2D profile.

Argument        | What it does
--------------- | ------------------------------
`size`          | Torx size.

**Example**:

    torx_drive2d(size=30, $fa=1, $fs=1);

![torx\_drive2d() Example](images/torx_drive/torx_drive2d.png)

---

### torx\_drive()

**Description**:
Creates a torx bit tip.

Argument        | What it does
--------------- | ------------------------------
`size`          | Torx size.
`l`             | Length of bit.
`center`        | If true, centers bit vertically.

**Example**:

    torx_drive(size=30, l=10, $fa=1, $fs=1);

![torx\_drive() Example](images/torx_drive/torx_drive.png)

---

