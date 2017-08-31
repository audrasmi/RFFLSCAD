Bezier functions and modules.


# Functions

## bez\_point(curve,u)
Formula to calculate points on a cubic bezier curve.



## bezier\_polyline(bezier, splinesteps=16)
Takes an array of bezier points and converts it into a 3D polyline.



## bezier\_polygon(bezier, splinesteps=16)
Takes a closed 2D bezier path, and creates a 2D polygon from it.



## fillet3pts(p0, p1, p2, r)
Generate bezier curve to fillet 2 line segments between 3 points.
Returns two path points with surrounding cubic bezier control points.



## fillet\_path(pts, fillet)
Takes a 3D polyline path and fillets it into a 3d cubic bezier path.



## bezier\_close\_to\_axis(bezier)
Takes a bezier path and closes it to the X axis.



## bezier\_offset(inset, bezier)
Takes a bezier curve and closes it with a matching path that is lowered by a given amount towards the X axis.



# Modules

## revolve\_bezier()
Takes a closed 2D bezier and rotates it around the X axis, forming a solid.

Arg         | What it is
----------- | --------------------------------
bezier      | Array of points for the bezier path to rotate.
splinesteps | Number of segments to divide each bezier segment into.

Example:

    path = [
        [  0, 10], [ 50,  0], [ 50, 40],
        [ 95, 40], [100, 40], [100, 45],
        [ 95, 45], [ 66, 45], [  0, 20],
        [  0, 12], [  0, 12], [  0, 10],
        [  0, 10]
    ];
    revolve_bezier(path, splinesteps=32, $fn=180);



## revolve\_bezier\_solid\_to\_axis()
Takes a 2D bezier and rotates it around the X axis, forming a solid.

Arg         | What it is
----------- | --------------------------------
bezier      | array of points for the bezier path to rotate.
splinesteps | number of segments to divide each bezier segment into.

Example:

    path = [ [0, 10], [33, 10], [66, 40], [100, 40] ];
    revolve_bezier_solid_to_axis(path, splinesteps=32, $fn=72);



## revolve\_bezier\_offset\_shell()
Takes a 2D bezier and rotates it around the X axis, into a hollow shell.

Arg         | What it is
----------- | --------------------------------
bezier      | array of points for the bezier path to rotate.
offset      | the thickness of the created shell.
splinesteps | number of segments to divide each bezier segment into.

Example:

    path = [ [0, 10], [33, 10], [66, 40], [100, 40] ];
    revolve_bezier_offset_shell(path, offset=1, splinesteps=32, $fn=72);



## extrude\_2d\_shapes\_along\_bezier()
Extrudes 2D children along a bezier path.

Arg         | What it is
----------- | --------------------------------
bezier      | array of points for the bezier path to extrude along.
splinesteps | number of segments to divide each bezier segment into.

Example:

    path = [ [0, 0, 0], [33, 33, 33], [66, -33, -33], [100, 0, 0] ];
    extrude_2d_shapes_along_bezier(path, splinesteps=32) {
        circle(r=10, center=true);
    }



## extrude\_bezier\_along\_bezier()
Takes a closed 2D bezier path, centered on the XY plane, and
extrudes it perpendicularly along a 3D bezier path, forming a solid.

Arg         | What it is
----------- | --------------------------------
bezier      | Array of points of a bezier path, to be extruded.
path        | Array of points of a bezier path, to extrude along.
pathsteps   | number of steps to divide each path segment into.
bezsteps    | number of steps to divide each bezier segment into.

Example:

    bez = [
        [-15,   0],  [ 25, -15],
        [ -5,  10],  [  0,  10],  [ 5,  10],
        [ 10,   5],  [ 15,   0],  [10,  -5],
        [  5, -10],  [  0, -10],  [-5, -10],
        [-10,  -5],  [-15,   0]
    ];
    path = [ [0, 0, 0], [33, 33, 33], [66, -33, -33], [100, 0, 0] ];
    extrude_bezier_along_bezier(bez, path, pathsteps=64, bezsteps=32);



