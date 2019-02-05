Math helper functions.


# Table of Contents

- [Functions](#functions)
    - [`Cpi()`](#cpi)
    - [`quant(x,y)`](#quantxy)
    - [`quantdn(x,y)`](#quantdnxy)
    - [`quantup(x,y)`](#quantupxy)
    - [`segs(r)`](#segsr)
    - [`lerp(a,b,u)`](#lerpabu)
    - [`hypot(x,y)`](#hypotxy)
    - [`hypot3(x,y,z)`](#hypot3xyz)
    - [`cdr(list)`](#cdrlist)
    - [`reverse(list)`](#reverselist)
    - [`wrap_range(list, start, end)`](#wrap_rangelist-start-end)
    - [`flatten(l)`](#flattenl)
    - [`sum(v)`](#sumv)
    - [`sum_of_squares(v)`](#sum_of_squaresv)
    - [`point3d(p)`](#point3dp)
    - [`path3d(points)`](#path3dpoints)
    - [`distance(p1, p2)`](#distancep1-p2)
    - [`ident(n)`](#identn)
    - [`mat3_to_mat4(m)`](#mat3_to_mat4m)
    - [`matrix3_xrot(ang)`](#matrix3_xrotang)
    - [`matrix4_xrot(ang)`](#matrix4_xrotang)
    - [`matrix3_yrot(ang)`](#matrix3_yrotang)
    - [`matrix4_yrot(ang)`](#matrix4_yrotang)
    - [`matrix3_zrot(ang)`](#matrix3_zrotang)
    - [`matrix4_zrot(ang)`](#matrix4_zrotang)
    - [`matrix3_rot_by_axis(u, ang)`](#matrix3_rot_by_axisu-ang)
    - [`matrix4_rot_by_axis(u, ang)`](#matrix4_rot_by_axisu-ang)
    - [`translate_points(pts, v)`](#translate_pointspts-v)
    - [`scale_points(pts, v, cp)`](#scale_pointspts-v-cp)
    - [`rotate_points2d(pts, ang, cp)`](#rotate_points2dpts-ang-cp)
    - [`rotate_points3d(pts, v, cp)`](#rotate_points3dpts-v-cp)
    - [`rotate_points3d_around_axis(pts, ang, u, cp)`](#rotate_points3d_around_axispts-ang-u-cp)
    - [`sum_of_sines(a,sines)`](#sum_of_sinesasines)
    - [`constrain(v, minval, maxval)`](#constrainv-minval-maxval)
    - [`normalize(v)`](#normalizev)
    - [`vector2d_angle(v1,v2)`](#vector2d_anglev1v2)
    - [`vector3d_angle(v1,v2)`](#vector3d_anglev1v2)
    - [`slice(arr,st,end)`](#slicearrstend)



# Functions


## Cpi()
Returns the value of pi, 3.1415926535897932.  **Deprecated.  Use the variable `PI` instead.**



## quant(x,y)
Quantize a value `x` to an integer multiple of `y`, rounding to the nearest multiple.



## quantdn(x,y)
Quantize the value `x` to an integer multiple of `y`, rounding down to the previous multiple.



## quantup(x,y)
Quantize the value `x` to an integer multiple of `y`, rounding up to the next multiple.



## segs(r)
Calculate OpenSCAD standard number of segments for a circle of radius `r`, based on `$fn`, `$fa`, and `$fs`.



## lerp(a,b,u)
Interpolate between two values or vectors, `a` and `b`.  The alpha value `u` is between 0 and 1.
When `u` == 0, returns the value of `a`.  When `u` == 1, returns the value of `b`.
When `u` is between 0 and 1, returns the interpolated value between `a` and `b`.



## hypot(x,y)
Calculate hypotenuse length of 2D triangle.



## hypot3(x,y,z)
Calculate hypotenuse length of 3D triangle.



## cdr(list)
Returns all but the first item of a given array.



## reverse(list)
Reverses a list/array.



## wrap\_range(list, start, end)
Returns a slice of the given array, wrapping around to the beginning, if end < start



## flatten(l)
Takes an array of arrays and flattens it by one level.

Example:

    flatten([[1,2,3], [4,5,[6,7,8]]]);
    // returns [1,2,3,4,5,[6,7,8]]



## sum(v)
Returns the sum of all entries in the given array.
If passed an array of vectors, returns a vector of sums of each part.

Examples:

    sum([1,2,3]);  // returns 6.
    sum([[1,2,3], [3,4,5], [5,6,7]]);  //returns [9, 12, 15]



## sum\_of\_squares(v)
Returns the sum of the square of each element of a vector.



## point3d(p)
Returns a 3D vector/point from a 2D or 3D vector.



## path3d(points)
Returns an array of 3D vectors/points from a 2D or 3D vector array.



## distance(p1, p2)
Returns the distance between a pair of 2D or 3D points.



## ident(n)
Create an identity matrix, for a given number of axes.



## mat3\_to\_mat4(m)
Takes a 3x3 matrix and returns its 4x4 transform matrix equivalent.



## matrix3\_xrot(ang)
Returns the 3x3 matrix to perform a rotation of ang degrees around the X axis.



## matrix4\_xrot(ang)
Returns the 4x4 matrix to perform a rotation of ang degrees around the X axis.



## matrix3\_yrot(ang)
Returns the 3x3 matrix to perform a rotation of ang degrees around the Y axis.



## matrix4\_yrot(ang)
Returns the 4x4 matrix to perform a rotation of ang degrees around the Y axis.



## matrix3\_zrot(ang)
Returns the 3x3 matrix to perform a rotation of ang degrees around the Z axis.



## matrix4\_zrot(ang)
Returns the 4x4 matrix to perform a rotation of ang degrees around the Z axis.



## matrix3\_rot\_by\_axis(u, ang)
Returns the 3x3 matrix to perform a rotation of a vector around an axis.

Arg   | What it is
----- | ---------------------
u     | axis vector to rotate around.
ang   | number of degrees to rotate.



## matrix4\_rot\_by\_axis(u, ang)
Returns the 4x4 matrix to perform a rotation of a vector around an axis.

Arg   | What it is
----- | ---------------------
u     | axis vector to rotate around.
ang   | number of degrees to rotate.



## translate\_points(pts, v)
Translates each point in the array `pts` by the vector `v`.



## scale\_points(pts, v, cp)
Scales each point in the array `pts` by the [X,Y,Z] scale
factors in vector `v`, around the centerpoint `cp`.



## rotate\_points2d(pts, ang, cp)
Rotates each 2D point in the array `pts` by the angle `ang`,
around the centerpoint `cp`.



## rotate\_points3d(pts, v, cp)
Rotates each 3D point in the array `pts` by the Euller angles
[X,Y,Z], around the centerpoint `cp`.



## rotate\_points3d\_around\_axis(pts, ang, u, cp)
Rotates each 3D point in the array `pts` by the angle `ang`,
around the centerpoint `cp` and the axis `u`.



## sum\_of\_sines(a,sines)
Gives the sum of a series of sines, at the angle `a`.

Arg   | What it is
----- | ---------------------
a     | angle to get the value for.
sines | array of [amplitude, frequency] pairs, where the frequency is the number of times the cycle repeats around the circle.



## constrain(v, minval, maxval)
Returns the value of `v`, constrained to the range [`minval`, `maxval`], so that `minval` <= `v` <= `maxval`.



## normalize(v)
Returns unit length normalized version of vector `v`.



## vector2d\_angle(v1,v2)
Returns angle in degrees between two 2D vectors.



## vector3d\_angle(v1,v2)
Returns angle in degrees between two 3D vectors.



## polar\_to\_xy(r, theta)

Convert polar coordinates to cartesian coordinates.
Returns [X,Y] cartesian coordinates.

Args  | What it does
----- | --------------------------------------
r     | Radius of polar coordinate.
theta | Angle in degrees, counter-clockwise of X+.

Examples:

    xy = polar_to_xy(20,30);
    xy = polar_to_xy([40,60]);



## xy\_to\_polar(x, y)

Convert cartesian coordinates to polar coordinates.
Returns [radius, theta] where theta is the angle
counter-clockwise of X+, and radius is the distance
from the origin.

Args  | What it does
----- | --------------------------------------
x     | X coordinate.
y     | Y coordinate.

Examples:

    plr = xy_to_polar(20,30);
    plr = xy_to_polar([40,60]);



## cylindrical\_to\_xyz(r, theta, z)

Convert cylindrical coordinates to cartesian coordinates.
Returns [X,Y,Z] cartesian coordinates.

Args  | What it does
----- | --------------------------------------
r     | Distance from the Z axis.
theta | Angle in degrees, counter-clockwise of X+ on the XY plane.
z     | Height above XY plane.

Examples:

    xyz = cylindrical_to_xyz(20,30,40);
    xyz = cylindrical_to_xyz([40,60,50]);



## xyz\_to\_cylindrical(x, y, z)

Convert cartesian coordinates to cylindrical coordinates.
Returns [radius,theta,Z]. Theta is the angle counter-clockwise
of X+ on the XY plane.  Z is height above the XY plane.

Args  | What it does
----- | --------------------------------------
x     | X coordinate.
y     | Y coordinate.
z     | Z coordinate.

Examples:

    cyl = xyz_to_cylindrical(20,30,40);
    cyl = xyz_to_cylindrical([40,50,70]);



## spherical\_to\_xyz(r, theta, phi)

Convert spherical coordinates to cartesian coordinates.
Returns [X,Y,Z] cartesian coordinates.

Args  | What it does
----- | --------------------------------------
r     | Distance from origin.
theta | Angle in degrees, counter-clockwise of X+ on the XY plane.
phi   | Angle in degrees from the vertical Z+ axis.

Examples:

    xyz = spherical_to_xyz(20,30,40);
    xyz = spherical_to_xyz([40,60,50]);



## xyz\_to\_spherical(x, y, z)

Convert cartesian coordinates to spherical coordinates.
Returns [r,theta,phi], where phi is the angle from the Z+ pole,
and theta is degrees counter-clockwise of X+ on the XY plane.

Args  | What it does
----- | --------------------------------------
x     | X coordinate.
y     | Y coordinate.
z     | Z coordinate.

Examples:

    sph = xyz_to_spherical(20,30,40);
    sph = xyz_to_spherical([40,50,70]);



## altaz\_to\_xyz(alt, az, r)

Convert altitude/azimuth/range coordinates to cartesian coordinates.
Returns [X,Y,Z] cartesian coordinates.

Args  | What it does
----- | --------------------------------------
alt   | Altitude angle in degrees above the XY plane.
az    | Azimuth angle in degrees clockwise of Y+ on the XY plane.
r     | Distance from origin.

Examples:

    xyz = altaz_to_xyz(20,30,40);
    xyz = altaz_to_xyz([40,60,50]);



## xyz\_to\_altaz(x, y, z)

Convert cartesian coordinates to altitude/azimuth/range coordinates.
Returns [altitude,azimuth,range], where altitude is angle above the
XY plane, azimuth is degrees clockwise of Y+ on the XY plane, and
range is the distance from the origin.

Args  | What it does
----- | --------------------------------------
x     | X coordinate.
y     | Y coordinate.
z     | Z coordinate.

Examples:

    aa = xyz_to_altaz(20,30,40);
    aa = xyz_to_altaz([40,50,70]);



## slice(arr,st,end)
Returns a slice of the array `arr` from index `st` to `end`.
An index of 0 is the array start, -1 is array end.



