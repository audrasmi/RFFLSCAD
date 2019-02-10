Common useful shapes and structured objects.

## Table of Contents

- [Cube Variants](#cube-variants)
    - [`offsetcube()`](#offsetcube)
    - [`leftcube()`](#leftcube)
    - [`rightcube()`](#rightcube)
    - [`fwdcube()`](#fwdcube)
    - [`backcube()`](#backcube)
    - [`downcube()`](#downcube)
    - [`upcube()`](#upcube)
    - [`chamfcube()`](#chamfcube)
    - [`rrect()`](#rrect)
    - [`rcube()`](#rcube)
- [Prisms and Such](#prisms-and-such)
    - [`prism()`](#prism)
    - [`trapezoid()`](#trapezoid)
    - [`pyramid()`](#pyramid)
    - [`right_triangle()`](#right_triangle)
- [Cylinder Variants](#cylinder-variants)
    - [`chamf_cyl()`](#chamf_cyl)
    - [`chamferred_cylinder()`](#chamferred_cylinder)
    - [`downcyl()`](#downcyl)
    - [`xcyl()`](#xcyl)
    - [`ycyl()`](#ycyl)
    - [`zcyl()`](#zcyl)
    - [`rcylinder()`](#rcylinder)
    - [`filleted_cylinder()`](#filleted_cylinder)
    - [`tube()`](#tube)
    - [`torus()`](#torus)
    - [`pie_slice()`](#pie_slice)
- [3D Printing Constructs](#3d-printing-constructs)
    - [`teardrop2d()`](#teardrop2d)
    - [`teardrop()`](#teardrop)
    - [`onion()`](#onion)
    - [`narrowing_strut()`](#narrowing_strut)
    - [`thinning_triangle()`](#thinning_triangle)
    - [`thinning_brace()`](#thinning_brace)
    - [`thinning_wall()`](#thinning_wall)
    - [`corrugated_wall()`](#corrugated_wall)
    - [`sparse_strut()`](#sparse_strut)
    - [`sparse_strut3d()`](#sparse_strut3d)
- [Miscellaneous](#miscellaneous)
    - [`nil()`](#nil)
    - [`slot()`](#slot)
    - [`arced_slot()`](#arced_slot)



## Cube Variants

### offsetcube()

Makes a cube that is offset along the given vector by half
the cube's size.  For example, if v=[-1,1,0], the cube's
front right edge will be centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])
v        | vector to offset along.

Example:

    offsetcube([3,4,5], [-1,1,0]);

![offsetcube](images/shapes/offsetcube.png)



### leftcube()
Makes a cube that has its right face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    leftcube([10, 10, 10]);

![leftcube](images/shapes/leftcube.png)



### rightcube()
Makes a cube that has its left face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    rightcube([10, 10, 10]);

![rightcube](images/shapes/rightcube.png)



### fwdcube()

Makes a cube that has its back face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    fwdcube([10, 10, 10]);

![fwdcube](images/shapes/fwdcube.png)



### backcube()
Makes a cube that has its front face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    backcube([10, 10, 10]);

![backcube](images/shapes/backcube.png)



### downcube()
Makes a cube that has its top face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    downcube([10, 10, 10]);

![downcube](images/shapes/downcube.png)



### upcube()
Makes a cube that has its bottom face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    upcube([4, 5, 3]);

![upcube](images/shapes/upcube.png)



### chamfcube()
Makes a cube with chamfered edges.

Arg          | What it does
------------ | --------------------------
size         | size of cube [X,Y,Z].  (Default: [1,1,1])
chamfer      | chamfer inset along axis.  (Default: 0.25)
chamfaxes    | Array [X, Y, Z] of boolean values to specify which axis edges should be chamfered.
chamfcorners | boolean to specify if corners should be flat chamferred.

Example:

    chamfcube(size=[10,20,30], chamfer=1, chamfaxes=[1,1,1], chamfcorners=true);

![chamfcube](images/shapes/chamfcube.png)



### rrect()
Makes a cube with rounded (filletted) vertical edges.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])
r        | radius of edge/corner rounding.  (Default: 0.25)
center   | if true, object will be centered.  If false, sits on top of XY plane.

Examples:

    rrect(size=[9,4,1], r=1, center=true);
    rrect(size=[5,7,3], r=1, $fn=24);

![rrect](images/shapes/rrect.png)



### rcube()
Makes a cube with rounded (filletted) edges and corners.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])
r        | radius of edge/corner rounding.  (Default: 0.25)
center   | if true, object will be centered.  If false, sits on top of XY plane.

Examples:

    rcube(size=[9,4,1], r=0.333, $fn=24);
    rcube(size=[5,7,3], r=1, center=true);

![rcube](images/shapes/rcube.png)



## Prisms and Such

### prism()

- prism(n, h, l, [circum])
- prism(n, h, r, [circum])
- prism(n, h, d, [circum])

Creates a vertical prism with a given number of sides.

Arg     | What it does
------- | -----------------------------------
n       | number of sides.
h       | height of the prism.
l       | length of one side of the prism. (optional)
r       | radius of the prism. (optional)
d       | diameter of the prism. (optional)
circum  | prism circumscribes the circle of the given radius or diam.

Example:

    prism(n=6, h=3, d=4, circum=true);

![prism](images/shapes/prism.png)



### trapezoid()
Creates a trapezoidal prism.

Arg     | What it does
------- | -----------------------------------
size1   | [width, length] of the bottom of the prism.
size2   | [width, length] of the top of the prism.
h       | Height of the prism.
center  | vertically center the prism if true.  Sits on top of XY plane if false.

Example:

    trapezoid(size1=[2,6], size2=[4,0], h=4, center=false);
    trapezoid(size1=[1,4], size2=[4,1], h=4, center=false);

![trapezoid](images/shapes/trapezoid.png)



### pyramid()

- pyramid(n, h, l, [circum])
- pyramid(n, h, r, [circum])
- pyramid(n, h, d, [circum])

Creates a pyramidal prism with a given number of sides.

Arg     | What it does
------- | -----------------------------------
n       | number of pyramid sides.
h       | height of the pyramid.
l       | length of one side of the pyramid. (optional)
r       | radius of the base of the pyramid. (optional)
d       | diameter of the base of the pyramid. (optional)
circum  | base circumscribes the circle of the given radius or diam.

Example:

    pyramid(h=10, l=5, n=4);
    pyramid(h=10, r=5, n=5);
    pyramid(h=3, d=4, n=6, circum=true);

![pyramid](images/shapes/pyramid.png)



### right\_triangle()
Creates a right triangle, with the hypotenuse on the right (X+) side.

Arg     | What it does
------- | -----------------------------------
size    | [width, thickness, height]
center  | true if triangle will be centered.

Examples:

    right_triangle([4, 1, 6], center=true);
    right_triangle([4, 1, 9]);

![right\_triangle](images/shapes/right_triangle.png)



## Cylinder Variants

### chamf\_cyl()
### chamferred\_cylinder()

- chamf\_cyl(h, r|d, chamfer|chamfedge, [center], [top], [bottom])
- chamferred\_cylinder(h, r|d, chamfer|chamfedge, [center], [top], [bottom])

Creates a cylinder with chamferred edges.

Arg       | What it does
--------- | -----------------------------------
h         | height of cylinder. (Default: 1.0)
r         | radius of cylinder. (Default: 1.0)
d         | diameter of cylinder. (use instead of r)
chamfer   | radial inset of the edge chamfer. (Default: 0.25)
chamfedge | length of the chamfer edge. (Use instead of chamfer)
center    | boolean.  If true, cylinder is centered. (Default: false)
top       | boolean.  If true, chamfer the top edges. (Default: True)
bottom    | boolean.  If true, chamfer the bottom edges. (Default: True)

Example:

    chamf_cyl(h=50, d=40, chamfer=5, angle=45, bottom=false, center=true);
    chamferred_cylinder(h=50, r=20, chamfedge=10, angle=30, center=true);

![chamf\_cyl](images/shapes/chamf_cyl.png)



### downcyl()

- downcyl(h, r)
- downcyl(h, r1, r2)
- downcyl(h, d)
- downcyl(h, d1, d2)

Creates a cylinder with its top face centered at the origin.

Arg  | What it does
---- | -----------------------------------
h    | height of cylinder. (Default: 1.0)
r    | radius of cylinder. (Default: 1.0)
r1   | bottom radius of cone. (use with `r2` instead of `r`)
r2   | top radius of cone. (use with `r1` instead of `r`)
d    | diameter of cylinder. (use instead of `r`)
d1   | bottom diameter of cone. (use with `d2` instead of `d` or `r`)
d2   | top diameter of cone. (use with `d1` instead of `d` or `r`)

Example:

    downcyl(r=10, h=50);
    downcyl(r1=15, r2=5, h=45);
    downcyl(d=15, h=40);

![downcyl](images/shapes/downcyl.png)



### xcyl()

- xcyl(l, r, [align])
- xcyl(l, r1, r2, [align])
- xcyl(l, d, [align])
- xcyl(l, d1, d2, [align])

Creates a cylinder oriented along the X axis.  Use like the
built-in `cylinder()` module, except use `l` instead of `h`.

Arg   | What it does
----- | -----------------------------------
l     | Length of cylinder. (Default: 1.0)
r     | Radius of cylinder.
r1    | Optional radius of left (X-) end of cylinder.
r2    | Optional radius of right (X+) end of cylinder.
d     | Optional diameter of cylinder. (use instead of r)
d1    | Optional diameter of left (X-) end of cylinder.
d2    | Optional diameter of right (X+) end of cylinder.
align | Alignment relative to the origin.  `+1` for right of, `0` for centered, `-1` for left of.  Default: `0` (center)

Examples:

    xcyl(d1=5, d2=15, l=20, align=-1);
    xcyl(d=10, l=25);

![xcyl](images/shapes/xcyl.png)



### ycyl()

- ycyl(l, r, [align])
- ycyl(l, r1, r2, [align])
- ycyl(l, d, [align])
- ycyl(l, d1, d2, [align])

Creates a cylinder oriented along the Y axis.  Use like the
built-in `cylinder()` module, except use `l` instead of `h`.

Arg   | What it does
----- | -----------------------------------
l     | length of cylinder. (Default: 1.0)
r     | radius of cylinder.
r1    | optional radius of front (Y-) end of cylinder.
r2    | optional radius of back (Y+) end of cylinder.
d     | optional diameter of cylinder. (use instead of r)
d1    | optional diameter of front (Y-) end of cylinder.
d2    | optional diameter of back (Y+) end of cylinder.
align | Alignment relative to the origin.  `+1` for behind, `0` for centered, `-1` for before.  Default: `0` (center)

Examples:

    ycyl(d1=5, d2=15, l=20, align=-1);
    ycyl(d=10, l=25);

![ycyl](images/shapes/ycyl.png)



### zcyl()

- zcyl(l, r, [align])
- zcyl(l, r1, r2, [align])
- zcyl(l, d, [align])
- zcyl(l, d1, d2, [align])

Creates a cylinder oriented along the Z axis.  Use like the
built-in `cylinder()` module, except use `l` instead of `h`.
This module exists for symmetry with `xcyl()` and `ycyl()`

Arg   | What it does
----- | -----------------------------------
l     | length of cylinder. (Default: 1.0)
r     | radius of cylinder.
r1    | optional radius of bottom (Z-) end of cylinder.
r2    | optional radius of top (Z+) end of cylinder.
d     | optional diameter of cylinder. (use instead of r)
d1    | optional diameter of bottom (Z-) end of cylinder.
d2    | optional diameter of top (Z+) end of cylinder.
align | Alignment relative to the origin.  `+1` for above, `0` for centered, `-1` for below.  Default: `0` (center)

Examples:

    zcyl(d1=5, d2=15, l=20, align=-1);
    zcyl(d=10, l=25);

![zcyl](images/shapes/zcyl.png)



### rcylinder()
### filleted\_cylinder()

- rcylinder(h, r|d, fillet, [center])
- rcylinder(h, r1|d1, r2|d2, fillet, [center])
- filleted\_cylinder(h, r|d, fillet, [center])
- filleted\_cylinder(h, r1|d1, r2|d2, fillet, [center])

Creates a cylinder with filleted (rounded) ends.  If `r1`/`r2`
or `d1`/`d2` are used, creates a cone with filleted ends.

Arg     | What it does
------- | -----------------------------------
h       | height of cylinder. (Default: 1.0)
r       | radius of cylinder. (Default: 1.0)
d       | diameter of cylinder. (Use instead of `r`)
r1      | radius of cylinder bottom. (Use with `r2` instead of `r`)
r2      | radius of cylinder top. (Use with `r1` instead of `r`)
d1      | diameter of cylinder bottom. (Use with `d2` instead of `d` or `r`)
d2      | diameter of cylinder top. (Use with `d1` instead of `d` or `r`)
fillet  | radius of the edge filleting. (Default: 0.25)
center  | boolean.  If true, cylinder is centered. (Default: false)

Example:

    rcylinder(h=50, r=20, fillet=5, center=true, $fa=1, $fs=1);

![rcylinder](images/shapes/rcylinder.png)



### tube()

- tube(h, r, wall)
- tube(h, r1, r2, wall)

Makes a hollow tube with the given outer size and wall thickness.

Arg    | What it does
------ | -----------------------------------
h      | height of tube. (Default: 1)
r      | Outer radius of tube.  (Default: 1)
r1     | Outer radius of bottom of tube.  (Default: value of r)
r2     | Outer radius of top of tube.  (Default: value of r)
wall   | horizontal thickness of tube wall. (Default 0.5)

Example:

    tube(h=6, r=4, wall=2, $fn=6);
    tube(h=3, r1=5, r2=7, wall=2, center=true);
    tube(h=3, r=4, wall=1, center=true);

![tube](images/shapes/tube.png)



### torus()

- torus(r|d, r2|d2)
- torus(ir|id, or|od)

Creates a torus shape.

Arg    | What it does
------ | -----------------------------------
r      | major radius of torus ring. (use with of 'r2', or 'd2')
r2     | minor radius of torus ring. (use with of 'r', or 'd')
d      | major diameter of torus ring. (use with of 'r2', or 'd2')
d2     | minor diameter of torus ring. (use with of 'r', or 'd')
or     | outer radius of the torus. (use with 'ir', or 'id')
ir     | inside radius of the torus. (use with 'or', or 'od')
od     | outer diameter of the torus. (use with 'ir' or 'id')
id     | inside diameter of the torus. (use with 'or' or 'od')

Example:

    torus(r=30, r2=5);
    torus(d=50, r2=5);
    torus(d=60, d2=15);
    torus(od=60, ir=15);
    torus(or=30, ir=20, $fa=1, $fs=1);

![torus](images/shapes/torus.png)



### pie\_slice()

- pie\_slice(ang, h, r|d, [center])
- pie\_slice(ang, h, r1|d1, r2|d2, [center])

Creates a pie slice shape.

Arg    | What it does
------ | -----------------------------------
ang    | pie slice angle in degrees.
h      | height of pie slice.
r      | radius of pie slice.
r1     | bottom radius of pie slice.
r2     | top radius of pie slice.
d      | diameter of pie slice.
d1     | bottom diameter of pie slice.
d2     | top diameter of pie slice.
center | if true, centers pie slice vertically. Default: false

Example:

    pie_slice(ang=45, h=30, r1=100, r2=80);

![pie\_slice](images/shapes/pie_slice.png)



## 3D Printing Constructs

### teardrop2d()
Makes a 2D teardrop shape. Useful for extruding into 3D printable holes.

Arg    | What it does
------ | -----------------------------------
r      | radius of circular part of teardrop.  (Default: 1)
d      | diameter of spherical portion of bottom. (Use instead of r)
ang    | angle of hat walls from the Y axis.  (Default: 45 degrees)
cap\_h | if given, height above center where the shape will be truncated.

Example:

    teardrop2d(r=30, ang=30);
    teardrop2d(r=35, ang=45, cap_h=40);

![teardrop2d](images/shapes/teardrop2d.png)



### teardrop()

- teardrop(r|d, h, [ang], [cap_h])

Makes a teardrop shape in the XZ plane. Useful for 3D printable holes.

Arg    | What it does
------ | -----------------------------------
r      | Radius of circular part of teardrop.  (Default: 1)
d      | Diameter of spherical portion of bottom. (Use instead of r)
h      | Thickness of teardrop. (Default: 1)
ang    | Angle of hat walls from the Y axis.  (Default: 45 degrees)
cap\_h | If given, height above center where the shape will be truncated.

Example:

    teardrop(r=3, h=2, ang=30);

![teardrop](images/shapes/teardrop.png)



### onion()

- onion(r|d, [maxang], [h])
Created a sphere with a conical hat, to make a 3D teardrop.

Arg    | What it does
------ | -----------------------------------
r      | radius of spherical portion of the bottom. (Default: 1)
d      | diameter of spherical portion of bottom. (Use instead of r)
h      | height above sphere center to truncate teardrop shape. (Default: 1)
maxang | angle of cone on top from vertical.

Example:

    onion(h=15, r=10, maxang=30);

![onion](images/shapes/onion.png)



### narrowing\_strut()
Makes a rectangular strut with the top side narrowing in a triangle.
The shape created may be likened to an extruded home plate from baseball.
This is useful for constructing parts that minimize the need to support
overhangs.

Arg    | What it does
------ | -----------------------------------
w      | Width (thickness) of the strut.
l      | Length of the strut.
wall   | height of rectangular portion of the strut.
ang    | angle that the trianglar side will converge at.

Example:

    narrowing_strut(w=10, l=100, wall=5, ang=30);

![narrowing\_strut](images/shapes/narrowing_strut.png)



### thinning\_triangle()

- thinning\_triangle(h, l, thick, wall, strut, [ang], [diagonly], [center])

Makes a triangular wall with thick edges, which thins to a smaller width in
the center, with angled supports to prevent critical overhangs.

Arg      | What it does
-------- | -----------------------------------
h        | Height of wall.
l        | Length of wall.
thick    | Thickness of wall.
ang      | Maximum overhang angle of diagonal brace in degrees.  Default: 30
strut    | The width of the diagonal brace.
wall     | The thickness of the thinned portion of the wall.
diagonly | Boolean, which denotes only the diagonal brace should be thick.  Default: false
center   | If true, center at origin.  Else, align edges to Y and Z axes.  Default: true

Examples:

    thinning_triangle(h=50, l=100, thick=4, ang=30, strut=5, wall=2, diagonly=true);
    thinning_triangle(h=60, l=75, thick=4, ang=30, strut=5, wall=2);

![thinning\_triangle](images/shapes/thinning_triangle.png)



### thinning\_brace()

- thinning\_brace(h, l, thick, wall, strut, [ang], [center])

Makes a triangular wall which thins to a smaller width in the center,
with angled supports to prevent critical overhangs.  Basically an alias
of `thinning_triangle()`, with `diagonly` set to true.

Arg    | What it does
------ | -----------------------------------
h      | height of wall.
l      | length of wall.
thick  | thickness of wall.
wall   | the thickness of the thinned portion of the wall.
strut  | the width of the diagonal brace.
ang    | maximum overhang angle of diagonal brace.
center | If true, center at origin.  Else, align edges to Y and Z axes.

Example:

    thinning_brace(h=50, l=100, thick=4, ang=30, strut=5, wall=2);

![thinning\_brace](images/shapes/thinning_brace.png)



### thinning\_wall()

- thinning\_wall(h, l, thick, wall, strut, [ang])

Makes a rectangular wall which thins to a smaller width in the center,
with angled supports to prevent critical overhangs.

Arg    | What it does
------ | -----------------------------------
h      | height of wall.
l      | length of wall.
thick  | thickness of wall.
wall   | the thickness of the thinned portion of the wall.
strut  | the width of the diagonal brace.
ang    | maximum overhang angle of diagonal brace.

Example:

    thinning_wall(h=50, l=100, thick=4, ang=30, strut=5, wall=2);

![thinning\_wall](images/shapes/thinning_wall.png)



### corrugated\_wall()

- corrugated\_wall(h, l, thick, wall, strut)

Makes a corrugated wall which relieves contraction stress while still
providing support strength.  Designed with 3D printing in mind.

Arg    | What it does
------ | -----------------------------------
h      | height of strut wall.
l      | length of strut wall.
thick  | thickness of strut wall.
wall   | thickness of corrugations.
strut  | the width of the cross-braces.

Example:

    corrugated_wall(h=50, l=100, thick=4, strut=5, wall=2);

![corrugated\_wall](images/shapes/corrugated_wall.png)



### sparse\_strut()

- sparse\_strut(h, l, thick, strut, [maxang], [max\_bridge])

Makes an open rectangular strut with X-shaped cross-bracing, designed with 3D printing in mind.

Arg         | What it does
----------- | -----------------------------------
h           | height of strut wall.
l           | length of strut wall.
thick       | thickness of strut wall.
strut       | the width of the cross-braces.
maxang      | maximum overhang angle of cross-braces.
max\_bridge | maximum bridging distance between cross-braces.

Example:

    sparse_strut(h=40, l=120, thick=4, maxang=30, strut=5, max_bridge=20);

![sparse\_strut](images/shapes/sparse_strut.png)



### sparse\_strut3d()

- sparse\_strut3d(h, w, l, thick, strut, [maxang], [max\_bridge])

Makes an open rigid strut with X-shaped cross-bracing, designed with 3D printing in mind.

Arg         | What it does
----------- | -----------------------------------
h           | Z size of strut.
w           | X size of strut.
l           | Y size of strut.
thick       | thickness of strut walls.
strut       | the width of the cross-braces.
maxang      | maximum overhang angle of cross-braces.
max\_bridge | maximum bridging distance between cross-braces.

Example:

    sparse_strut3d(h=40, w=40, l=120, thick=4, maxang=30, strut=5, max_bridge=20);

![sparse\_strut3d](images/shapes/sparse_strut3d.png)



## Miscellaneous

### nil()
For when you MUST pass a child to a module, but you want it to be nothing.



### slot()

- slot(p1, p2, h, r|d, [center])
- slot(p1, p2, h, r1|d1, r2|d2, [center])
- slot(l, h, r|d, [center])
- slot(l, h, r1|d1, r2|d2, [center])

Makes a linear slot with rounded ends, appropriate for bolts to slide along.

Arg    | What it does
------ | -----------------------------------
p1     | center of starting circle of slot.  (Default: [0,0,0])
p2     | center of ending circle of slot.  (Default: [1,0,0])
l      | length of slot along the X axis.  Use instead of p1 and p2.
h      | height of slot shape. (default: 1.0)
r      | radius of slot circle. (default: 0.5)
r1     | bottom radius of slot cone. (use instead of r)
r2     | top radius of slot cone. (use instead of r)
d      | diameter of slot circle. (default: 1.0)
d1     | bottom diameter of slot cone. (use instead of d)
d2     | top diameter of slot cone. (use instead of d)
center | if true (default) centers vertically.  Else, drops flush with XY plane.

Examples:

    slot(l=50, h=5, d1=8, d2=10, center=false);
    slot([0,0,0], [50,50,0], h=5, d=10);

![slot](images/shapes/slot.png)



### arced\_slot()

- arced\_slot(h, r|d, sr|sd, [cp], [sa], [ea])
- arced\_slot(h, r1|d1, r2|d2, sr|sd, [cp], [sa], [ea])
- arced\_slot(h, r|d, sr1|sd1, sr2|sd2, [cp], [sa], [ea])
- arced\_slot(h, r1|d1, r2|d2, sr1|sd1, sr2|sd2, [cp], [sa], [ea])

Makes an arced slot, appropriate for bolts to slide along.

Arg    | What it does
------ | -----------------------------------
cp     | centerpoint of slot arc. (default: [0, 0, 0])
h      | height of slot arc shape. (default: 1.0)
r      | radius of slot arc. (default: 0.5)
d      | diameter of slot arc. (default: 1.0)
sr     | radius of slot channel. (default: 0.5)
sd     | diameter of slot channel. (default: 0.5)
sr1    | bottom radius of slot channel cone. (use instead of sr)
sr2    | top radius of slot channel cone. (use instead of sr)
sd1    | bottom diameter of slot channel cone. (use instead of sd)
sd2    | top diameter of slot channel cone. (use instead of sd)
sa     | starting angle. (Default: 0.0)
ea     | ending angle. (Default: 90.0)

Examples:

    arced_slot(r=100, h=10, sd1=30, sd2=10, sa=45, ea=180, $fa=5, $fs=2);
    arced_slot(d=100, h=15, sd=10, sa=60, ea=280);

![arced\_slot](images/shapes/arced_slot.png)

