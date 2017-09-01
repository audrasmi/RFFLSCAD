Quaternion math and modules.

Quaternions are stored internally as a 4-value vector:

	[X, Y, Z, W]  =  W + Xi + Yj + Zk


# Functions and math


## Quat(ax, ang)
Returns a Quaternion created from a given axis `ax` and angle `ang` (in degrees).



## Q\_Ident()
Returns an identity quaternion.



## Q\_Add\_S(q, s)
Returns the quaternion resulting from adding a scalar to a quaternion.



## Q\_Sub\_S(q, s)
Returns the quaternion resulting from subtracting a scalar from a quaternion.



## Q\_Mul\_S(q, s)
Returns the quaternion resulting from multiplying a quaternion by a scalar.



## Q\_Div\_S(q, s)
Returns the quaternion resulting from dividing a quaternion by a scalar.



## Q\_Add(a, b)
Returns the quaternion resulting from adding two quaternions together.



## Q\_Sub(a, b)
Returns the quaternion resulting from subtracting one quaternion from another.



## Q\_Mul(a, b)
Returns the quaternion resulting from multiplying two quaternions together.



## Q\_Dot(a, b)
Returns the quaternion resulting from the dot product of two quaternions.



## Q\_Neg(q)
Returns the negative of a quaternion.



## Q\_Conj(q)
Returns the conjugate of a quaternion.



## Q\_Norm(q)
Returns the length of a quaternion.



## Q\_Normalize(q)
Returns the unit length equivalent of the given quaternion.



## Q\_Dist(q1, q2)
Returns the distance between two quaternions.



## Q\_Matrix3(q)
Returns the 3x3 rotation matrix for the given normalized quaternion q.



## Q\_Matrix4(q) = [
// Returns the 4x4 rotation matrix for the given normalized quaternion q.



## Q\_Rot\_Vector(v,q)
Returns the vector v after rotating it by the quaternion q.



# Modules


## Qrot(q) { ... }
Rotates all children by the given quaternion q.

Example:

	q1 = Quat([1,0,0], 30);
	q2 = Quat([0,0,1], 15);
	q = Q_Mul(q1, q2);
    Qrot(q) cylinder(d=10, h=100, center=false);



