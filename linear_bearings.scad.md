# Library File linear\_bearings.scad

Linear Bearing clips/holders.
To use, add these lines to the top of your file:
```
include <BOSL/constants.scad>
use <BOSL/linear_bearings.scad>
```

---

# Table of Contents

1. [Functions](#1-functions)
    - [`get_lmXuu_bearing_diam()`](#get_lmxuu_bearing_diam)
    - [`get_lmXuu_bearing_length()`](#get_lmxuu_bearing_length)
    - [`linear_bearing_housing()`](#linear_bearing_housing)
    - [`lmXuu_housing()`](#lmxuu_housing)

---

# 1. Functions

### get\_lmXuu\_bearing\_diam()

**Description**:
Get outside diameter, in mm, of a standard lmXuu bearing.

Argument        | What it does
--------------- | ------------------------------
`size`          | Inner size of lmXuu bearing, in mm.

---

### get\_lmXuu\_bearing\_length()

**Description**:
Get length, in mm, of a standard lmXuu bearing.

Argument        | What it does
--------------- | ------------------------------
`size`          | Inner size of lmXuu bearing, in mm.

---

### linear\_bearing\_housing()

**Description**:
Creates a model of a clamp to hold a generic linear bearing cartridge.

Argument        | What it does
--------------- | ------------------------------
`d`             | Diameter of linear bearing. (Default: 15)
`l`             | Length of linear bearing. (Default: 24)
`tab`           | Clamp tab height. (Default: 7)
`tabwall`       | Clamp Tab thickness. (Default: 5)
`wall`          | Wall thickness of clamp housing. (Default: 3)
`gap`           | Gap in clamp. (Default: 5)
`screwsize`     | Size of screw to use to tighten clamp. (Default: 3)
`orient`        | Orientation of the housing.  Use the `ORIENT_` constants from `constants.scad`.  Default: `ORIENT_X`.
`align`         | Alignment of the housing by the axis-negative (size1) end.  Use the `V_` constants from `constants.scad`.  Default: `V_UP`

**Example**:

    linear_bearing_housing(d=19, l=29, wall=2, tab=6, screwsize=2.5);

![linear\_bearing\_housing() Example](images/linear_bearings/linear_bearing_housing.png)

---

### lmXuu\_housing()

**Description**:
Creates a model of a clamp to hold a standard sized lmXuu linear bearing cartridge.

Argument        | What it does
--------------- | ------------------------------
`size`          | Standard lmXuu inner size.
`tab`           | Clamp tab height.  Default: 7
`tabwall`       | Clamp Tab thickness.  Default: 5
`wall`          | Wall thickness of clamp housing.  Default: 3
`gap`           | Gap in clamp.  Default: 5
`screwsize`     | Size of screw to use to tighten clamp.  Default: 3
`orient`        | Orientation of the housing.  Use the `ORIENT_` constants from `constants.scad`.  Default: `ORIENT_X`.
`align`         | Alignment of the housing by the axis-negative (size1) end.  Use the `V_` constants from `constants.scad`.  Default: `V_UP`

**Example**:

    lmXuu_housing(size=10, wall=2, tab=6, screwsize=2.5);

![lmXuu\_housing() Example](images/linear_bearings/lmXuu_housing.png)

---

