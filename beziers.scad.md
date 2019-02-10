Bezier functions and modules.


# Table of Contents

- [Functions](#functions)
    - [`bez_point(curve, u)`](#bez_pointcurve-u)
    - [`bezier_polyline(bezier, splinesteps, N)`](#bezier_polylinebezier-splinesteps-n)
    - [`fillet3pts(p0, p1, p2, r)`](#fillet3ptsp0-p1-p2-r)
    - [`fillet_path(pts, fillet)`](#fillet_pathpts-fillet)
    - [`bezier_close_to_axis(bezier, N)`](#bezier_close_to_axisbezier-n)
    - [`bezier_offset(inset, bezier, N)`](#bezier_offsetinset-bezier-n)
- [Modules](#modules)
    - [`bezier_polygon(bezier, splinesteps, N)`](#bezier_polygonbezier-splinesteps-n)
    - [`linear_extrude_bezier(bezier, splinesteps, N, center, convexity, twist, scale, slices)`](#linear_extrude_bezierbezier-splinesteps-n-center-convexity-twist-scale-slices)
    - [`rotate_extrude_bezier(bezier, slinesteps, N, convexity, angle)`](#rotate_extrude_bezierbezier-slinesteps-n-convexity-angle)
    - [`revolve_bezier(bezier, splinesteps, N)`](#revolve_bezierbezier-splinesteps-n)
    - [`revolve_bezier_solid_to_axis(bezier, splinesteps, N)`](#revolve_bezier_solid_to_axisbezier-splinesteps-n)
    - [`revolve_bezier_offset_shell(bezier, offset, splinesteps, N)`](#revolve_bezier_offset_shellbezier-offset-splinesteps-n)
    - [`extrude_2d_shapes_along_bezier(bezier, splinesteps, N)`](#extrude_2d_shapes_along_bezierbezier-splinesteps-n)
    - [`extrude_bezier_along_bezier(bezier, path, pathsteps, bezsteps, bezN, pathN)`](#extrude_bezier_along_bezierbezier-path-pathsteps-bezsteps-bezn-pathn)



# Functions

## bez\_point(curve, u)
Formula to calculate points on an N-point bezier curve. N=len(curve)-1

Arg         | What it is
----------- | --------------------------------
curve       | An array of control point vectors.
u           | Part of curve to get point of.  0 <= u <= 1

![bez\_point](images/beziers/bez_point.png)



## bezier\_polyline(bezier, splinesteps, N)
Takes an array of bezier points and converts it into a 3D polyline.

Arg         | What it is
----------- | --------------------------------
bezier      | The array of bezier points.
splinesteps | The number of line segments to divide each bezier segment into.
N           | The number of points in each bezier segment.  Default=3 (cubic bezier)

![bezier\_polyline](images/beziers/bezier_polyline.png)



## fillet3pts(p0, p1, p2, r)
Generate a cubic (N=3) bezier curve to fillet 2 line segments between 3 points.
Returns two path points with surrounding cubic (N=3) bezier control points.

Arg  | What it is
---- | --------------------------------
p0   | The first point.
p1   | The second point.
p2   | The third point.
r    | The radius of the fillet.

![fillet3pts](images/beziers/fillet3pts.png)



## fillet\_path(pts, fillet)
Takes a 3D polyline path and fillets the corners, returning a 3d cubic (N=3) bezier path.

Arg     | What it is
------- | --------------------------------
pts     | The array of path points.
fillet  | Radius of fillets to make.

![fillet\_path](images/beziers/fillet_path.png)



## bezier\_close\_to\_axis(bezier, N)
Takes a 2D bezier path and closes it to the X axis.

Arg         | What it is
----------- | --------------------------------
bezier      | The array of bezier points.
N           | The number of points in each bezier segment.  Default=3 (cubic bezier)

![bezier\_close\_to\_axis](images/beziers/bezier_close_to_axis.png)



## bezier\_offset(inset, bezier, N)
Takes a bezier curve and closes it with a matching path that is lowered by a given amount towards the X axis.

Arg         | What it is
----------- | --------------------------------
inset       | Amount to inset return path towards the X axis.
bezier      | The array of bezier points.
N           | The number of points in each bezier segment.  Default=3 (cubic bezier)

![bezier\_offset](images/beziers/bezier_offset.png)



# Modules

## bezier\_polygon(bezier, splinesteps, N)
Takes a closed 2D bezier path, and creates a 2D polygon from it.

Arg         | What it is
----------- | --------------------------------
bezier      | The closed array of 2D bezier points.
splinesteps | The number of line segments to divide each bezier segment into.
N           | The number of points in each bezier segment.  Default=3 (cubic bezier)

![bezier\_polygon](images/beziers/bezier_polygon.png)



## linear\_extrude\_bezier(bezier, splinesteps, N, center, convexity, twist, scale, slices)

Takes a closed 2D bezier path, centered on the XY plane, and
extrudes it linearly upwards, forming a solid.

Arg         | What it is
----------- | --------------------------------
bezier      | Array of 2D points of a bezier path, to be extruded.
splinesteps | Number of steps to divide each bezier segment into. Default: 16
N           | Number of points in each extruded bezier segment.  Default: 3 (cubic)
center      | If true, the extruded solid is centered vertically at z=0.
convexity   | Max number of walls a line could pass through, for preview.  Default: 10
twist       | Degrees to twist over length of extrusion.  Default: 0
scale       | Relative size of top of extrusion to the bottom.  Default: 1.0
slices      | Number of vertical slices to use for twisted extrusion.  Default: 20

Example:

    bez = [
        [-10,   0],  [-15,  -5],
        [ -5, -10],  [  0, -10],  [ 5, -10],
        [ 10,  -5],  [ 15,   0],  [10,   5],
        [  5,  10],  [  0,  10],  [-5,  10],
        [ 25, -15],  [-10,   0]
    ];
    linear_extrude_bezier(bez, height=20, splinesteps=32);

![linear\_extrude\_bezier](images/beziers/linear_extrude_bezier.png)



## rotate\_extrude\_bezier(bezier, slinesteps, N, convexity, angle)

Takes a closed 2D bezier and rotates it around the Z axis, forming a solid.
Behaves like `rotate_extrude()`, except for beziers instead of shapes.

Arg         | What it is
----------- | --------------------------------
bezier      | Array of 2D points for the bezier path to rotate.
splinesteps | Number of line segments to divide each bezier segment into.
N           | The number of points in each bezier segment.  Default=3 (cubic bezier)
convexity   | Max number of walls a line could pass through, for preview.  Default: 10
angle       | Degrees of sweep to make.  (Requires OpenSCAD 2016.XX or higher) Default: 360

Example:

    path = [
      [  0, 10], [ 50,  0], [ 50, 40],
      [ 95, 40], [100, 40], [100, 45],
      [ 95, 45], [ 66, 45], [  0, 20],
      [  0, 12], [  0, 12], [  0, 10],
      [  0, 10]
    ];
    rotate_extrude_bezier(path, splinesteps=32, $fn=180);

![rotate\_extrude\_bezier](images/beziers/rotate_extrude_bezier.png)



## revolve\_bezier(bezier, splinesteps, N)
Takes a closed 2D bezier and rotates it around the X axis, forming a solid.

Arg         | What it is
----------- | --------------------------------
bezier      | Array of points for the bezier path to rotate.
splinesteps | Number of segments to divide each bezier segment into.
N           | The number of points in each bezier segment.  Default=3 (cubic bezier)

Example:

    path = [
        [  0, 10], [ 50,  0], [ 50, 40],
        [ 95, 40], [100, 40], [100, 45],
        [ 95, 45], [ 66, 45], [  0, 20],
        [  0, 12], [  0, 12], [  0, 10],
        [  0, 10]
    ];
    revolve_bezier(path, splinesteps=32, $fn=180);

![revolve\_bezier](images/beziers/revolve_bezier.png)



## revolve\_bezier\_solid\_to\_axis(bezier, splinesteps, N)
Takes a 2D bezier and rotates it around the X axis, forming a solid.

Arg         | What it is
----------- | --------------------------------
bezier      | array of points for the bezier path to rotate.
splinesteps | number of segments to divide each bezier segment into.
N           | The number of points in each bezier segment.  Default=3 (cubic bezier)

Example:

    path = [ [0, 10], [33, 10], [66, 40], [100, 40] ];
    revolve_bezier_solid_to_axis(path, splinesteps=32, $fn=72);

![revolve\_bezier\_solid\_to\_axis](images/beziers/revolve_bezier_solid_to_axis.png)



## revolve\_bezier\_offset\_shell(bezier, offset, splinesteps, N)
Takes a 2D bezier and rotates it around the X axis, into a hollow shell.

Arg         | What it is
----------- | --------------------------------
bezier      | array of points for the bezier path to rotate.
offset      | the thickness of the created shell.
splinesteps | number of segments to divide each bezier segment into.
N           | The number of points in each bezier segment.  Default=3 (cubic bezier)

Example:

    path = [ [0, 10], [33, 10], [66, 40], [100, 40] ];
    revolve_bezier_offset_shell(path, offset=1, splinesteps=32, $fn=72);

![revolve\_bezier\_offset\_shell](images/beziers/revolve_bezier_offset_shell.png)



## extrude\_2d\_shapes\_along\_bezier(bezier, splinesteps, N)
Extrudes 2D children along a bezier path.

Arg         | What it is
----------- | --------------------------------
bezier      | array of points for the bezier path to extrude along.
splinesteps | number of segments to divide each bezier segment into.
N           | The number of points in each bezier segment.  Default=3 (cubic bezier)

Example:

    path = [ [0, 0, 0], [33, 33, 33], [66, -33, -33], [100, 0, 0] ];
    extrude_2d_shapes_along_bezier(path) {
        difference() {
            circle(r=10);
            left(10/2) circle(r=8);
        }
    }

![extrude\_2d\_shapes\_along\_bezier](images/beziers/extrude_2d_shapes_along_bezier.png)



## extrude\_bezier\_along\_bezier(bezier, path, pathsteps, bezsteps, bezN, pathN)
Takes a closed 2D bezier path, centered on the XY plane, and
extrudes it perpendicularly along a 3D bezier path, forming a solid.

Arg         | What it is
----------- | --------------------------------
bezier      | Array of points of a bezier path, to be extruded.
path        | Array of points of a bezier path, to extrude along.
pathsteps   | number of steps to divide each path segment into.
bezsteps    | number of steps to divide each bezier segment into.
bezN        | The number of points in each extruded bezier segment.  Default=3 (cubic bezier)
pathN       | The number of points in each path bezier segment.  Default=3 (cubic bezier)

Example:

    bez = [
        [-10,   0],  [-15,  -5],
        [ -5, -10],  [  0, -10],  [ 5, -10],
        [ 10,  -5],  [ 15,   0],  [10,   5],
        [  5,  10],  [  0,  10],  [-5,  10],
        [ 25, -15],  [-10,   0]
    ];
    path = [ [0, 0, 0], [33, 33, 33], [66, -33, -33], [100, 0, 0] ];
    extrude_bezier_along_bezier(bez, path, pathsteps=32, bezsteps=16);

![extrude\_bezier\_along\_bezier](images/beziers/extrude_bezier_along_bezier.png)



