Common useful shapes and structured objects.
To use, add the following line to the beginning of your file:

    use <BOSL/shapes.scad>
    include <BOSL/constants.scad>


## Table of Contents

- [Cube Variants](#cube-variants)
    - [`cuboid()`](#cuboid)
    - [`cube2pt()`](#cube2pt)
    - [`span_cube()`](#span_cube)
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
    - [`prismoid()`](#prismoid)
    - [`rounded_prismoid()`](#rounded_prismoid)
    - [`pyramid()`](#pyramid)
    - [`right_triangle()`](#right_triangle)
- [Cylinder Variants](#cylinder-variants)
    - [`cyl()`](#cyl)
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
    - [`interior_fillet()`](#interior_fillet)
    - [`slot()`](#slot)
    - [`arced_slot()`](#arced_slot)



## Cube Variants

### cuboid()

- cuboid(size, [align])
- cuboid(size, chamfer, [edges], [trimcorners], [align])
- cuboid(size, fillet, [edges], [trimcorners], [align])

Creates a cube or cuboid object.

Arg         | What it does
----------- | --------------------------
size        | The size of the cube.
align       | The side of the origin to align to.  Use `V_` constants from `constants.scad`.
chamfer     | Size of chamfer, inset from sides.  Default: No chamferring.
fillet      | Radius of fillet for edge rounding.  Default: No filleting.
edges       | Edges to chamfer/fillet.  Use `EDGE_` constants from `constants.scad`. Default: `EDGES_ALL`
trimcorners | If true, rounds or chamfers corners where three chamferred/filleted edges meet.  Default: true

Examples:

    cuboid(40);
    cuboid(40, align=V_UP+V_BACK);
    cuboid([20,40,60]);
    cuboid([30,40,60], chamfer=5);
    cuboid([30,40,60], fillet=10);
    cuboid([30,40,60], chamfer=5, edges=EDGE_TOP_FR+EDGE_TOP_RT+EDGE_FR_RT, $fn=24);
    cuboid([30,40,60], fillet=5, edges=EDGE_TOP_FR+EDGE_TOP_RT+EDGE_FR_RT, $fn=24);

![cuboid](images/shapes/cuboid.png)



### cube2pt()

- cube2pt(p1, p2)

Makes a cube with opposing corners at two given points.

Arg      | What it does
-------- | --------------------------
p1       | Coordinate point of one cube corner.
p2       | Coordinate point of opposite cube corner.

Example:

    cube2pt([10,20,30], [40,-10,10]);

![cube2pt](images/shapes/cube2pt.png)



### span\_cube()

- span\_cube(xspan, yspan, zspan)

Creates a cube that spans the X, Y, and Z ranges given.

Arg      | What it does
-------- | --------------------------
xspan    | [min, max] X axis range.
yspan    | [min, max] Y axis range.
zspan    | [min, max] Z axis range.

Example:

    span_cube([10,40], [-10, 20], [10,30]);

![span\_cube](images/shapes/span_cube.png)



### offsetcube()

- offsetcube(size, v)

**DEPRECATED**:  Use cuboid() instead.

Makes a cube that is offset along the given vector by half
the cube's size.  For example, if v=[-1,1,0], the cube's
front right edge will be centered at the origin.  It is
highly recommended that you use the V\_ constants from
`BOSL/constants.scad`.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])
v        | vector to offset along.

Example:

    offsetcube([3,4,5], [-1,1,0]);

    include <BOSL/constants.scad>
    offsetcube([3,4,5], V_LEFT+V_BACK);

![offsetcube](images/shapes/offsetcube.png)



### leftcube()

- leftcube(size)

Makes a cube that has its right face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    leftcube([10, 10, 10]);

![leftcube](images/shapes/leftcube.png)



### rightcube()

- rightcube(size)

Makes a cube that has its left face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    rightcube([10, 10, 10]);

![rightcube](images/shapes/rightcube.png)



### fwdcube()

- fwdcube(size)

Makes a cube that has its back face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    fwdcube([10, 10, 10]);

![fwdcube](images/shapes/fwdcube.png)



### backcube()

- backcube(size)

Makes a cube that has its front face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    backcube([10, 10, 10]);

![backcube](images/shapes/backcube.png)



### downcube()

- downcube(size)

Makes a cube that has its top face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    downcube([10, 10, 10]);

![downcube](images/shapes/downcube.png)



### upcube()

- upcube(size)

Makes a cube that has its bottom face centered at the origin.

Arg      | What it does
-------- | --------------------------
size     | size of cube [X,Y,Z].  (Default: [1,1,1])

Example:

    upcube([4, 5, 3]);

![upcube](images/shapes/upcube.png)



### chamfcube()

- chamfcube(size, chamfer, [chamfaxes], [chamfcorners])


**DEPRECATED**:  Use cuboid() instead.

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

- rrect(size, r, [center])

**DEPRECATED**:  Use cuboid() instead.

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

- rcube(size, r, [center])

**DEPRECATED**:  Use cuboid() instead.

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

**DEPRECATED**:  Use cyl() instead.

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
**DEPRECATED**: renamed to `prismoid()`


### prismoid()

- prismoid(size1, size2, h, [orient], [align])

Creates a rectangular prismoid shape.

Arg     | What it does
------- | -----------------------------------
size1   | [width, length] of the bottom of the prism.
size2   | [width, length] of the top of the prism.
h       | Height of the prism.
orient  | Orientation of the prismoid.  Use the `ORIENT_` constants from `constants.h`.  Default: vertical.
align   | Alignment of the prismoid.  Use the `V_` constants from `constants.h`.  Default: centered.  The `center` argument overrides `align`.
center  | Vertically center the prism.  DEPRECATED ARGUMENT.  Use `align` instead.

Example:

    prismoid(size1=[2,6], size2=[4,0], h=4, center=false);
    prismoid(size1=[1,4], size2=[4,1], h=4, center=false);

![prismoid](images/shapes/prismoid.png)



### rounded\_prismoid()

- rounded\_prismoid(size1, size2, h, r, [orient], [align])
- rounded\_prismoid(size1, size2, h, r1, r2, [orient], [align])

Creates a rectangular prismoid shape with rounded vertical edges.

Arg     | What it does
------- | -----------------------------------
size1   | Size [width, length] of the bottom of the prism.
size2   | Size [width, length] of the top of the prism.
h       | Height of the prism.
r       | Radius of vertical edge fillets.
r1      | Radius of vertical edge fillets at bottom.
r2      | Radius of vertical edge fillets at top.
orient  | Orientation of the prismoid.  Use the `ORIENT_` constants from `constants.h`.  Default: vertical.
align   | Alignment of the prismoid.  Use the `V_` constants from `constants.h`.  Default: centered.  The `center` argument overrides `align`.
center  | Vertically center the prismoid.  DEPRECATED ARGUMENT.  Use `align` instead.

Example:

    rounded_prismoid(size1=[40,40], size2=[0,0], h=40, r=5, center=false);
    rounded_prismoid(size1=[20,60], size2=[40,30], h=40, r1=5, r2=10, center=false);
    rounded_prismoid(size1=[40,60], size2=[35,55], h=40, r1=0, r2=10, center=true);

![rounded\_prismoid](images/shapes/rounded_prismoid.png)



### pyramid()

- pyramid(n, h, l, [circum])
- pyramid(n, h, r, [circum])
- pyramid(n, h, d, [circum])

**DEPRECATED**:  Use cyl() instead.

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

- right\_triangle(size, [center])

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

### cyl()

**Normal cylinder usage:**
    - cyl(l, r|d, [circum], [orient], [align], [realign])
    - cyl(l, r1|d1, r2|d2, [circum], [orient], [align], [realign])

**Chamferred cylinder usage:**
    - cyl(l, r|d, chamfer, [chamfang], [from\_end], [circum], [orient], [align], [realign])
    - cyl(l, r1|d1, r2|d2, chamfer1, chamfer2, chamfang1, chamfang2, [from\_end], [circum], [orient], [align], [realign])

**Filleted cylinder usage:**
    - cyl(l, r|d, fillet, [circum], [orient], [align], [realign])
    - cyl(l, r1|d1, r2|d2, fillet1, fillet2, [circum], [realign], [orient], [align])

**Mixed usage:**
    - cyl(l, r1|d1, r2|d2, fillet1, chamfer2, chamfang2, [from\_end], [circum], [orient], [align], [realign])
    - cyl(l, r1|d1, r2|d2, chamfer1, fillet2, [chamfang1], [from\_end], [circum], [orient], [align], [realign])

Creates cylinders in various alignments and orientations,
with optional fillets and chamfers.

Arg       | What it does
--------- | -----------------------------------
l         | Length of cylinder along axis.
r         | Radius of cylinder.
r1        | Radius of the axis-negative (X-, Y-, Z-) end of cylinder.
r2        | Radius of the axis-positive (X+, Y+, Z+) end of cylinder.
d         | Diameter of cylinder.
d1        | Diameter of the axis-negative (X-, Y-, Z-) end of cylinder.
d2        | Diameter of the axis-positive (X+, Y+, Z+) end of cylinder.
circum    | If true, cylinder should circumscribe the circle of the given size.  Otherwise inscribes.  Default: false
chamfer   | The size of the chamfers on the ends of the cylinder, inset from end.  Default: none.
chamfer1  | The size of the chamfer on the axis-negative (X-, Y-, Z-) end of the cylinder, inset from end.  Default: none.
chamfer2  | The size of the chamfer on the axis-positive (X+, Y+, Z+) end of the cylinder, inset from end.  Default: none.
chamfang  | The angle in degrees of the chamfers on the ends of the cylinder, as measured towards the axis.  Default: half the edge angle.
chamfang1 | The angle in degrees of the chamfers on the axis-negative (X-, Y-, Z-) end of the cylinder, as measured towards the axis.
chamfang2 | The angle in degrees of the chamfers on the axis-positive (X+, Y+, Z+) end of the cylinder, as measured towards the axis.
from\_end | If true, chamfer is measured from the end of the cylinder, instead of inset from the edge.  Default: false.
fillet    | The radius of the fillets on the ends of the cylinder.  Default: none.
fillet1   | The radius of the fillet on the axis-negative end of the cylinder.
fillet2   | The radius of the fillet on the axis-positive end of the cylinder.
realign   | If true, rotate the cylinder by half the angle of one face.
orient    | Orientation of the cylinder.  Use the ORIENT\_ constants from constants.h.  Default: vertical.
align     | Alignment of the cylinder.  Use the V\_ constants from constants.h.  Default: centered.

Examples:

    cyl(l=100, r=25);
    cyl(l=100, r=25, orient=ORIENT_Y);
    cyl(l=100, d1=50, d2=20);
    cyl(l=100, r=25, chamfer=10);
    cyl(l=100, r=25, fillet=10);
    cyl(l=100, d1=50, d2=30, chamfer1=10, fillet2=8, from_end=true);

![cyl](images/shapes/cyl.png)



### chamf\_cyl()
### chamferred\_cylinder()

- chamf\_cyl(h, r|d, chamfer|chamfedge, [center], [top], [bottom])
- chamferred\_cylinder(h, r|d, chamfer|chamfedge, [center], [top], [bottom])

**DEPRECATED**:  Use cyl() instead.

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

- downcyl(h, r|d)
- downcyl(h, r1|d1, r2|d2)

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

- xcyl(l, r|d, [align])
- xcyl(l, r1|d1, r2|d2, [align])

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

- ycyl(l, r|d, [align])
- ycyl(l, r1|d1, r2|d2, [align])

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

- zcyl(l, r|d, [align])
- zcyl(l, r1|d1, r2|d2, [align])

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

**DEPRECATED**:  Use cyl() instead.

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

- tube(h, r|d, wall, [orient], [align])
- tube(h, ir|id, wall, [orient], [align])
- tube(h, r1|d1, r2|d2, wall, [orient], [align])
- tube(h, ir1|id1, ir2|id2, wall, [orient], [align])
- tube(h, r|d, ir|id, [orient], [align])
- tube(h, r|d, ir1|id1, ir2|id2, [orient], [align])
- tube(h, r1|d1, r2|d2, ir|id, [orient], [align])
- tube(h, r1|d1, r2|d2, ir1|id1, ir2|id2, [orient], [align])

Makes a hollow tube.

Arg    | What it does
------ | -----------------------------------
h      | height of tube. (Default: 1)
r      | Outer radius of tube.  (Default: 1)
r1     | Outer radius of bottom of tube.
r2     | Outer radius of top of tube.
d      | Outer diameter of tube.
d1     | Outer diameter of bottom of tube.
d2     | Outer diameter of top of tube.
wall   | horizontal thickness of tube wall. (Default 0.5)
ir     | Inner radius of tube.  (Default: 1)
ir1    | Inner radius of bottom of tube.
ir2    | Inner radius of top of tube.
id     | Inner diameter of tube.
id1    | Inner diameter of bottom of tube.
id2    | Inner diameter of top of tube.
orient | Orientation of the tube.  Use the `ORIENT_` constants from `constants.h`.  Default: vertical.
align  | Alignment of the tube.  Use the `V_` constants from `constants.h`.  Default: centered.

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

- teardrop2d(r|d, [ang], [cap\_h])

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

- teardrop(r|d, h, [ang], [cap\_h])

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

- narrowing\_strut(w, l, wall, [ang])

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

- nil()

For when you MUST pass a child to a module, but you want it to be nothing.



### interior\_fillet()

- interior\_fillet(l, r, [ang], [overlap])

Creates a shape that can be unioned into a concave joint between
two faces, to fillet them.  Center this part along the edge to
be chamferred and union it in.

Arg     | What it does
------- | -----------------------------------
l       | Length of edge to fillet.
r       | Radius of fillet.
ang     | Angle between faces to fillet.  Default: 90
overlap | Overlap size for unioning with faces.  Default: 0.01

Example:

    union() {
        translate([0,-5,-10]) upcube([20, 10, 30]);
        translate([0,10,-5]) upcube([20, 20, 10]);
        color("green") interior_fillet(l=20, r=10, ang=60);
    }

![interior\_fillet](images/shapes/interior_fillet.png)



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

