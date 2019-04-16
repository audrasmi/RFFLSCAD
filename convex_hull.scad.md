# Library File convex\_hull.scad

Functions to create 2D and 3D convex hulls.
To use, add the following line to the beginning of your file:
```
include <BOSL/convex_hull.scad>
```
Derived from Linde's Hull:
- https://github.com/openscad/scad-utils

---

# Table of Contents

1. [Generalized Hull](#1-generalized-hull)
    - [`convex_hull()`](#convex_hull)

2. [2D Hull](#2-2d-hull)
    - [`convex_hull2d()`](#convex_hull2d)

3. [3D Hull](#3-3d-hull)
    - [`convex_hull3d()`](#convex_hull3d)

---

# 1. Generalized Hull

### convex\_hull()

**Usage**:
- convex\_hull(points)

**Description**:
When given a list of 3D points, returns a list of faces for
the minimal convex hull polyhedron of those points.  Each face
is a list of indexes into `points`.
When given a list of 2D points, or 3D points that are all
coplanar, returns a list of indices into `points` for the path
that forms the minimal convex hull polygon of those points.

Argument        | What it does
--------------- | ------------------------------
`points`        | The list of points to find the minimal convex hull of.

---

# 2. 2D Hull

### convex\_hull2d()

**Usage**:
- convex\_hull2d(points)

**Description**:
Takes a list of arbitrary 2D points, and finds the minimal convex
hull polygon to enclose them.  Returns a path as a list of indices
into `points`.

---

# 3. 3D Hull

### convex\_hull3d()

**Usage**:
- convex\_hull3d(points)

**Description**:
Takes a list of arbitrary 3D points, and finds the minimal convex
hull polyhedron to enclose them.  Returns a list of faces, where
each face is a list of indexes into the given `points` list.
If all points passed to it are coplanar, then the return is the
list of indices of points forming the minimal convex hull polygon.

---

