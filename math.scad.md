Math helper functions.


# Functions


## Cpi()
Returns the value of pi, 3.1415926535897932.  **Deprecated.  Use the variable `PI` instead.**



## quant(x,y)
Quantize a value x to an integer multiple of y, rounding to the nearest multiple.



## quantdn(x,y)
Quantize a value x to an integer multiple of y, rounding down to the previous multiple.



## quantup(x,y)
Quantize a value x to an integer multiple of y, rounding up to the next multiple.



## segs(r)
Calculate OpenSCAD standard number of segments for a circle of radius r, based on $fn, $fa, and $fs.



## hypot(x,y)
Calculate hypotenuse length of 2D triangle.



## hypot3(x,y,z)
Calculate hypotenuse length of 3D triangle.



## cdr(list)
Returns all but the first item of a given array.



## reverse(list)
Reverses a list/array.



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



## sum\_of\_sines(a,sines)
Gives the sum of a series of sines, at a given angle.

Arg   | What it is
----- | ---------------------
a     | angle to get the value for.
sines | array of [amplitude, frequency] pairs, where the frequency is the number of times the cycle repeats around the circle.



## normalize(v)
Returns unit length normalized version of vector v.



## vector2d\_angle(v1,v2)
Returns angle in degrees between two 2D vectors.



## vector3d\_angle(v1,v2)
Returns angle in degrees between two 3D vectors.



## slice(arr,st,end)
Returns a slice of an array.  An index of 0 is the array start, -1 is array end



