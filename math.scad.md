Math helper functions.


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



## slice(arr,st,end)
Returns a slice of the array `arr` from index `st` to `end`.
An index of 0 is the array start, -1 is array end.



