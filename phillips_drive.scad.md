# Library File phillips\_drive.scad

Phillips driver bits
To use, add these lines to the top of your file:
```
include <BOSL/constants.scad>
use <BOSL/phillips_drive.scad>
```

---

# Table of Contents

1. [Modules](#modules)
    - [`phillips_drive()`](#phillips_drive)

---

# 1. Modules

### phillips\_drive()

**Description**:
Creates a model of a phillips driver bit of a given named size.

Argument        | What it does
--------------- | ------------------------------
`size`          | The size of the bit.  "#1", "#2", or "#3"
`shaft`         | The diameter of the drive bit's shaft.
`l`             | The length of the drive bit.

**Example**:

    xdistribute(10) {
       phillips_drive(size="#1", shaft=4, l=20);
       phillips_drive(size="#2", shaft=6, l=20);
       phillips_drive(size="#3", shaft=6, l=20);
    }

![phillips\_drive() Example](images/phillips_drive/phillips_drive.png)

---

