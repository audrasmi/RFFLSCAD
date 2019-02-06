Quaternion math and modules.

Quaternions are stored internally as a 4-value vector:

	[X, Y, Z, W]  =  W + Xi + Yj + Zk


# Table of Contents

- [Functions and math](#functions-and-math)
    - [`Quat(ax, ang)`](#quatax-ang)
    - [`Q_Ident()`](#q_ident)
    - [`Q_Add_S(q, s)`](#q_add_sq-s)
    - [`Q_Sub_S(q, s)`](#q_sub_sq-s)
    - [`Q_Mul_S(q, s)`](#q_mul_sq-s)
    - [`Q_Div_S(q, s)`](#q_div_sq-s)
    - [`Q_Add(a, b)`](#q_adda-b)
    - [`Q_Sub(a, b)`](#q_suba-b)
    - [`Q_Mul(a, b)`](#q_mula-b)
    - [`Q_Dot(a, b)`](#q_dota-b)
    - [`Q_Neg(q)`](#q_negq)
    - [`Q_Conj(q)`](#q_conjq)
    - [`Q_Norm(q)`](#q_normq)
    - [`Q_Normalize(q)`](#q_normalizeq)
    - [`Q_Dist(q1, q2)`](#q_distq1-q2)
    - [`Q_Slerp(q1, q2, t)`](#q_slerpq1-q2-t)
    - [`Q_Matrix3(q)`](#q_matrix3q)
    - [`Q_Matrix4(q)`](#q_matrix4q)
    - [`Q_Rot_Vector(v, q)`](#q_rot_vectorv-q)
- [Modules](#modules)
    - [`Qrot(q) { ... }`](#qrotq---)



# Functions and math


## Quat(ax, ang)
Returns a Quaternion created from a given axis vector `ax` and angle `ang` (in degrees).



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
This is geometrically equivalent to applying the rotation in quaternion `a` to the rotation in quaternion `b`.

Example:

    q1 = Quat([0,0,1], 30);
    q2 = Quat([1,0,0],-45);
    q3 = Q_Mul(q2, q1);
    // Result is a quaternion equivalent to the rotation
    // in q1 followed by the rotation in q2.


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



## Q\_Slerp(q1, q2, t)
Returns the spherical interpolation between two quaternions.



## Q\_Matrix3(q)
Returns the 3x3 rotation matrix for the given normalized quaternion q.



## Q\_Matrix4(q)
Returns the 4x4 rotation matrix for the given normalized quaternion q.



## Q\_Rot\_Vector(v, q)
Returns the vector v after rotating it by the quaternion q.



# Modules


## Qrot(q) { ... }
Rotates all children by the given quaternion q.

Example:

    q1 = Quat([1,0,0], 30);
    q2 = Quat([0,0,1], 15);
    q = Q_Mul(q1, q2);
    Qrot(q) cylinder(d=10, h=100, center=false);



