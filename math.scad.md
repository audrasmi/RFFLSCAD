# Library File math.scad

Math helper functions.
To use, add the following lines to the beginning of your file:
```
use <BOSL/math.scad>
```

---

# Table of Contents

1. [Simple Calculations](#1-simple-calculations)
    - [`quant()`](#quant)
    - [`quantdn()`](#quantdn)
    - [`quantup()`](#quantup)
    - [`constrain()`](#constrain)
    - [`posmod()`](#posmod)
    - [`modrange()`](#modrange)
    - [`segs()`](#segs)
    - [`lerp()`](#lerp)
    - [`hypot()`](#hypot)
    - [`sinh()`](#sinh)
    - [`cosh()`](#cosh)
    - [`tanh()`](#tanh)
    - [`asinh()`](#asinh)
    - [`acosh()`](#acosh)
    - [`atanh()`](#atanh)
    - [`sum()`](#sum)
    - [`sum_of_squares()`](#sum_of_squares)
    - [`sum_of_sines()`](#sum_of_sines)
    - [`mean()`](#mean)

2. [Comparisons and Logic](#2-comparisons-and-logic)
    - [`compare_vals()`](#compare_vals)
    - [`compare_lists()`](#compare_lists)
    - [`any()`](#any)
    - [`all()`](#all)
    - [`count_true()`](#count_true)

3. [List/Array Operations](#3-listarray-operations)
    - [`replist()`](#replist)
    - [`in_list()`](#in_list)
    - [`slice()`](#slice)
    - [`select()`](#select)
    - [`reverse()`](#reverse)
    - [`array_subindex()`](#array_subindex)
    - [`list_range()`](#list_range)
    - [`array_shortest()`](#array_shortest)
    - [`array_longest()`](#array_longest)
    - [`array_pad()`](#array_pad)
    - [`array_trim()`](#array_trim)
    - [`array_fit()`](#array_fit)
    - [`array_zip()`](#array_zip)
    - [`array_group()`](#array_group)
    - [`flatten()`](#flatten)
    - [`sort()`](#sort)
    - [`unique()`](#unique)
    - [`array_dim()`](#array_dim)

4. [Vector Manipulation](#4-vector-manipulation)
    - [`vmul()`](#vmul)
    - [`vdiv()`](#vdiv)
    - [`vabs()`](#vabs)
    - [`normalize()`](#normalize)
    - [`vector_angle()`](#vector_angle)
    - [`vector_axis()`](#vector_axis)

5. [Coordinates Manipulation](#5-coordinates-manipulation)
    - [`point2d()`](#point2d)
    - [`path2d()`](#path2d)
    - [`point3d()`](#point3d)
    - [`path3d()`](#path3d)
    - [`translate_points()`](#translate_points)
    - [`scale_points()`](#scale_points)
    - [`rotate_points2d()`](#rotate_points2d)
    - [`rotate_points3d()`](#rotate_points3d)

6. [Coordinate Systems](#6-coordinate-systems)
    - [`polar_to_xy()`](#polar_to_xy)
    - [`xy_to_polar()`](#xy_to_polar)
    - [`cylindrical_to_xyz()`](#cylindrical_to_xyz)
    - [`xyz_to_cylindrical()`](#xyz_to_cylindrical)
    - [`spherical_to_xyz()`](#spherical_to_xyz)
    - [`xyz_to_spherical()`](#xyz_to_spherical)
    - [`altaz_to_xyz()`](#altaz_to_xyz)
    - [`xyz_to_altaz()`](#xyz_to_altaz)

7. [Matrix Manipulation](#7-matrix-manipulation)
    - [`ident()`](#ident)
    - [`matrix_transpose()`](#matrix_transpose)
    - [`mat3_to_mat4()`](#mat3_to_mat4)
    - [`matrix3_translate()`](#matrix3_translate)
    - [`matrix4_translate()`](#matrix4_translate)
    - [`matrix3_scale()`](#matrix3_scale)
    - [`matrix4_scale()`](#matrix4_scale)
    - [`matrix3_zrot()`](#matrix3_zrot)
    - [`matrix4_xrot()`](#matrix4_xrot)
    - [`matrix4_yrot()`](#matrix4_yrot)
    - [`matrix4_zrot()`](#matrix4_zrot)
    - [`matrix4_rot_by_axis()`](#matrix4_rot_by_axis)
    - [`matrix3_skew()`](#matrix3_skew)
    - [`matrix4_skew_xy()`](#matrix4_skew_xy)
    - [`matrix4_skew_xz()`](#matrix4_skew_xz)
    - [`matrix4_skew_yz()`](#matrix4_skew_yz)
    - [`matrix3_mult()`](#matrix3_mult)
    - [`matrix4_mult()`](#matrix4_mult)
    - [`matrix3_apply()`](#matrix3_apply)
    - [`matrix4_apply()`](#matrix4_apply)

8. [Geometry](#8-geometry)
    - [`point_on_segment()`](#point_on_segment)
    - [`point_left_of_segment()`](#point_left_of_segment)
    - [`point_in_polygon()`](#point_in_polygon)
    - [`pointlist_bounds()`](#pointlist_bounds)

9. [Deprecations](#9-deprecations)
    - [`Cpi()`](#cpi)
    - [`hypot3()`](#hypot3)
    - [`distance()`](#distance)
    - [`cdr()`](#cdr)
    - [`wrap_range()`](#wrap_range)
    - [`vector2d_angle()`](#vector2d_angle)
    - [`vector3d_angle()`](#vector3d_angle)
    - [`rotate_points3d_around_axis()`](#rotate_points3d_around_axis)

---

# 1. Simple Calculations

### quant()

**Description**:
Quantize a value `x` to an integer multiple of `y`, rounding to the nearest multiple.

Argument        | What it does
--------------- | ------------------------------
`x`             | The value to quantize.
`y`             | The multiple to quantize to.

---

### quantdn()

**Description**:
Quantize a value `x` to an integer multiple of `y`, rounding down to the previous multiple.

Argument        | What it does
--------------- | ------------------------------
`x`             | The value to quantize.
`y`             | The multiple to quantize to.

---

### quantup()

**Description**:
Quantize a value `x` to an integer multiple of `y`, rounding up to the next multiple.

Argument        | What it does
--------------- | ------------------------------
`x`             | The value to quantize.
`y`             | The multiple to quantize to.

---

### constrain()

**Usage**:
- constrain(v, minval, maxval);

**Description**:
Constrains value to a range of values between minval and maxval, inclusive.

Argument        | What it does
--------------- | ------------------------------
`v`             | value to constrain.
`minval`        | minimum value to return, if out of range.
`maxval`        | maximum value to return, if out of range.

---

### posmod()

**Usage**:
- posmod(x,m)

**Description**:
Returns the positive modulo `m` of `x`.  Value returned will be in the range 0 ... `m`-1.
This if useful for normalizing angles to 0 ... 360.

Argument        | What it does
--------------- | ------------------------------
`x`             | The value to constrain.
`m`             | Modulo value.

---

### modrange()

**Usage**:
- modrange(x, y, m, [step])

**Description**:
Returns a normalized list of values from `x` to `y`, by `step`, modulo `m`.  Wraps if `x` > `y`.

Argument        | What it does
--------------- | ------------------------------
`x`             | The start value to constrain.
`y`             | The end value to constrain.
`m`             | Modulo value.
`step`          | Step by this amount.

**Example 1**:

    echo(modrange(90,270,360, step=45));  // Outputs [90,135,180,225,270]

**Example 2**:

    echo(modrange(270,90,360, step=45));  // Outputs [270,315,0,45,90]

**Example 3**:

    echo(modrange(90,270,360, step=-45));  // Outputs [90,45,0,315,270]

**Example 4**:

    echo(modrange(270,90,360, step=-45));  // Outputs [270,225,180,135,90]

---

### segs()

**Description**:
Calculate the standard number of sides OpenSCAD would give a circle based on `$fn`, `$fa`, and `$fs`.

Argument        | What it does
--------------- | ------------------------------
`r`             | Radius of circle to get the number of segments for.

---

### lerp()

**Description**:
Interpolate between two values or vectors.

Argument        | What it does
--------------- | ------------------------------
`a`             | First value.
`b`             | Second value.
`u`             | The proportion from `a` to `b` to calculate.  Valid range is 0.0 to 1.0, inclusive.

---

### hypot()

**Description**:
Calculate hypotenuse length of a 2D or 3D triangle.

Argument        | What it does
--------------- | ------------------------------
`x`             | Length on the X axis.
`y`             | Length on the Y axis.
`z`             | Length on the Z axis.

---

### sinh()

**Description**:
Takes a value `x`, and returns the hyperbolic sine of it.

---

### cosh()

**Description**:
Takes a value `x`, and returns the hyperbolic cosine of it.

---

### tanh()

**Description**:
Takes a value `x`, and returns the hyperbolic tangent of it.

---

### asinh()

**Description**:
Takes a value `x`, and returns the inverse hyperbolic sine of it.

---

### acosh()

**Description**:
Takes a value `x`, and returns the inverse hyperbolic cosine of it.

---

### atanh()

**Description**:
Takes a value `x`, and returns the inverse hyperbolic tangent of it.

---

### sum()

**Description**:
Returns the sum of all entries in the given array.
If passed an array of vectors, returns a vector of sums of each part.

Argument        | What it does
--------------- | ------------------------------
`v`             | The vector to get the sum of.

**Example**:

    sum([1,2,3]);  // returns 6.
    sum([[1,2,3], [3,4,5], [5,6,7]]);  // returns [9, 12, 15]

---

### sum\_of\_squares()

**Description**:
Returns the sum of the square of each element of a vector.

Argument        | What it does
--------------- | ------------------------------
`v`             | The vector to get the sum of.

**Example**:

    sum_of_squares([1,2,3]);  // returns 14.

---

### sum\_of\_sines()

**Usage**:
- sum\_of\_sines(a,sines)

**Description**:
Gives the sum of a series of sines, at a given angle.

Argument        | What it does
--------------- | ------------------------------
`a`             | Angle to get the value for.
`sines`         | List of [amplitude, frequency, offset] items, where the frequency is the number of times the cycle repeats around the circle.

---

### mean()

**Description**:
Returns the mean of all entries in the given array.
If passed an array of vectors, returns a vector of mean of each part.

Argument        | What it does
--------------- | ------------------------------
`v`             | The list of values to get the mean of.

**Example**:

    mean([2,3,4]);  // returns 4.5.
    mean([[1,2,3], [3,4,5], [5,6,7]]);  // returns [4.5, 6, 7.5]

---

# 2. Comparisons and Logic

### compare\_vals()

**Usage**:
- compare\_vals(a, b);

**Description**:
Compares two values.  Lists are compared recursively.
Results are undefined if the two values are not of similar types.

Argument        | What it does
--------------- | ------------------------------
`a`             | First value to compare.
`b`             | Second value to compare.

---

### compare\_lists()

**Usage**:
- compare\_lists(a, b)

**Description**:
Compare contents of two lists.
Returns <0 if `a`<`b`.
Returns 0 if `a`==`b`.
Returns >0 if `a`>`b`.
Results are undefined if elements are not of similar types.

Argument        | What it does
--------------- | ------------------------------
`a`             | First list to compare.
`b`             | Second list to compare.

---

### any()

**Description**:
Returns true if any item in list `l` evaluates as true.
If `l` is a lists of lists, `any()` is applied recursively to each sublist.

Argument        | What it does
--------------- | ------------------------------
`l`             | The list to test for true items.

**Example**:

    any([0,false,undef]);  // Returns false.
    any([1,false,undef]);  // Returns true.
    any([1,5,true]);       // Returns true.
    any([[0,0], [0,0]]);   // Returns false.
    any([[0,0], [1,0]]);   // Returns true.

---

### all()

**Description**:
Returns true if all items in list `l` evaluate as true.
If `l` is a lists of lists, `all()` is applied recursively to each sublist.

Argument        | What it does
--------------- | ------------------------------
`l`             | The list to test for true items.

**Example**:

    all([0,false,undef]);  // Returns false.
    all([1,false,undef]);  // Returns false.
    all([1,5,true]);       // Returns true.
    all([[0,0], [0,0]]);   // Returns false.
    all([[0,0], [1,0]]);   // Returns false.
    all([[1,1], [1,1]]);   // Returns true.

---

### count\_true()

**Usage**:
- count\_true(l)

**Description**:
Returns the number of items in `l` that evaluate as true.
If `l` is a lists of lists, this is applied recursively to each
sublist.  Returns the total count of items that evaluate as true
in all recursive sublists.

Argument        | What it does
--------------- | ------------------------------
`l`             | The list to test for true items.
`nmax`          | If given, stop counting if `nmax` items evaluate as true.

**Example**:

    count_true([0,false,undef]);  // Returns 0.
    count_true([1,false,undef]);  // Returns 1.
    count_true([1,5,false]);      // Returns 2.
    count_true([1,5,true]);       // Returns 3.
    count_true([[0,0], [0,0]]);   // Returns 0.
    count_true([[0,0], [1,0]]);   // Returns 1.
    count_true([[1,1], [1,1]]);   // Returns 4.
    count_true([[1,1], [1,1]], nmax=3);  // Returns 3.

---

# 3. List/Array Operations

### replist()

**Usage**:
- replist(val, n)

**Description**:
Generates a list or array of `n` copies of the given `list`.
If the count `n` is given as a list of counts, then this creates a
multi-dimensional array, filled with `val`.

Argument        | What it does
--------------- | ------------------------------
`val`           | The value to repeat to make the list or array.
`n`             | The number of copies to make of `val`.

**Example**:

    replist(1, 4);        // Returns [1,1,1,1]
    replist(8, [2,3]);    // Returns [[8,8,8], [8,8,8]]
    replist(0, [2,2,3]);  // Returns [[[0,0,0],[0,0,0]], [[0,0,0],[0,0,0]]]
    replist([1,2,3],3);   // Returns [[1,2,3], [1,2,3], [1,2,3]]

---

### in\_list()

**Description**:
Returns true if value `x` is in list `l`.

Argument        | What it does
--------------- | ------------------------------
`x`             | The value to search for.
`l`             | The list to search.
`idx`           | If given, searches the given subindexes for matches for `x`.

**Example**:

    in_list("bar", ["foo", "bar", "baz"]);  // Returns true.
    in_list("bee", ["foo", "bar", "baz"]);  // Returns false.
    in_list("bar", [[2,"foo"], [4,"bar"], [3,"baz"]], idx=1);  // Returns true.

---

### slice()

**Description**:
Returns a slice of a list.  The first item is index 0.
Negative indexes are counted back from the end.  The last item is -1.

Argument        | What it does
--------------- | ------------------------------
`arr`           | The array/list to get the slice of.
`st`            | The index of the first item to return.
`end`           | The index after the last item to return, unless negative, in which case the last item to return.

**Example**:

    slice([3,4,5,6,7,8,9], 3, 5);   // Returns [6,7]
    slice([3,4,5,6,7,8,9], 2, -1);  // Returns [5,6,7,8,9]
    slice([3,4,5,6,7,8,9], 1, 1);   // Returns []
    slice([3,4,5,6,7,8,9], 6, -1);  // Returns [9]
    slice([3,4,5,6,7,8,9], 2, -2);  // Returns [5,6,7,8]

---

### select()

**Usage**:
- select(list,start)
- select(list,start,end)

**Description**:
Returns a portion of a list, wrapping around past the beginning, if end<start.
The first item is index 0. Negative indexes are counted back from the end.
The last item is -1.  If only the `start` index is given, returns just the value
at that position.

Argument        | What it does
--------------- | ------------------------------
`list`          | The list to get the portion of.
`start`         | The index of the first item.
`end`           | The index of the last item.

**Example**:

    l = [3,4,5,6,7,8,9];
    select(l, 5, 6);   // Returns [8,9]
    select(l, 5, 8);   // Returns [8,9,3,4]
    select(l, 5, 2);   // Returns [8,9,3,4,5]
    select(l, -3, -1); // Returns [7,8,9]
    select(l, 3, 3);   // Returns [6]
    select(l, 4);      // Returns 7
    select(l, -2);     // Returns 8
    select(l, [1:3]);  // Returns [4,5,6]
    select(l, [1,3]);  // Returns [4,6]

---

### reverse()

**Description**:
Reverses a list/array.

Argument        | What it does
--------------- | ------------------------------
`list`          | The list to reverse.

**Example**:

    reverse([3,4,5,6]);  // Returns [6,5,4,3]

---

### array\_subindex()

**Description**:
For each array item, return the indexed subitem.
Returns a list of the values of each vector at the specfied
index list or range.  If the index list or range has
only one entry the output list is flattened.

Argument        | What it does
--------------- | ------------------------------
`v`             | The given list of lists.
`idx`           | The index, list of indices, or range of indices to fetch.

**Example**:

    v = [[[1,2,3,4],[5,6,7,8],[9,10,11,12],[13,14,15,16]];
    array_subindex(v,2);      // Returns [3, 7, 11, 15]
    array_subindex(v,[2,1]);  // Returns [[3, 2], [7, 6], [11, 10], [15, 14]]
    array_subindex(v,[1:3]);  // Returns [[2, 3, 4], [6, 7, 8], [10, 11, 12], [14, 15, 16]]

---

### list\_range()

**Usage**:
- list\_range(n, [s], [e], [step])
- list\_range(e, [step])
- list\_range(s, e, [step])

**Description**:
Returns a list, counting up from starting value `s`, by `step` increments,
until either `n` values are in the list, or it reaches the end value `e`.

Argument        | What it does
--------------- | ------------------------------
`n`             | Desired number of values in returned list, if given.
`s`             | Starting value.  Default: 0
`e`             | Ending value to stop at, if given.
`step`          | Amount to increment each value.  Default: 1

**Example**:

    list_range(4);                  // Returns [0,1,2,3]
    list_range(n=4, step=2);        // Returns [0,2,4,6]
    list_range(n=4, s=3, step=3);   // Returns [3,6,9,12]
    list_range(n=4, s=3, e=9, step=3);  // Returns [3,6,9]
    list_range(e=3);                // Returns [0,1,2,3]
    list_range(e=6, step=2);        // Returns [0,2,4,6]
    list_range(s=3, e=5);           // Returns [3,4,5]
    list_range(s=3, e=8, step=2);   // Returns [3,5,7]
    list_range(s=4, e=8, step=2);   // Returns [4,6,8]
    list_range(n=4, s=[3,4], step=[2,3]);  // Returns [[3,4], [5,7], [7,10], [9,13]]

---

### array\_shortest()

**Description**:
Returns the length of the shortest sublist in a list of lists.

Argument        | What it does
--------------- | ------------------------------
`vecs`          | A list of lists.

---

### array\_longest()

**Description**:
Returns the length of the longest sublist in a list of lists.

Argument        | What it does
--------------- | ------------------------------
`vecs`          | A list of lists.

---

### array\_pad()

**Description**:
If the list `v` is shorter than `minlen` length, pad it to length with the value given in `fill`.

Argument        | What it does
--------------- | ------------------------------
`v`             | A list.
`minlen`        | The minimum length to pad the list to.
`fill`          | The value to pad the list with.

---

### array\_trim()

**Description**:
If the list `v` is longer than `maxlen` length, truncates it to be `maxlen` items long.

Argument        | What it does
--------------- | ------------------------------
`v`             | A list.
`minlen`        | The minimum length to pad the list to.

---

### array\_fit()

**Description**:
If the list `v` is longer than `length` items long, truncates it to be exactly `length` items long.
If the list `v` is shorter than `length` items long, pad it to length with the value given in `fill`.

Argument        | What it does
--------------- | ------------------------------
`v`             | A list.
`minlen`        | The minimum length to pad the list to.
`fill`          | The value to pad the list with.

---

### array\_zip()

**Usage**:
- array\_zip(v1, v2, v3, [fit], [fill]);
- array\_zip(vecs, [fit], [fill]);

**Description**:
Zips together corresponding items from two or more lists.
Returns a list of lists, where each sublist contains corresponding
items from each of the input lists.  `[[A1, B1, C1], [A2, B2, C2], ...]`

Argument        | What it does
--------------- | ------------------------------
`vecs`          | A list of two or more lists to zipper together.
`fit`           | If `fit=="short"`, the zips together up to the length of the shortest list in vecs.  If `fit=="long"`, then pads all lists to the length of the longest, using the value in `fill`.  If `fit==false`, then requires all lists to be the same length.  Default: false.
`fill`          | The default value to fill in with if one or more lists if short.  Default: undef

**Example 1**:

    v1 = [1,2,3,4];
    v2 = [5,6,7];
    v3 = [8,9,10,11];
    array_zip(v1,v3);                       // returns [[1,8], [2,9], [3,10], [4,11]]
    array_zip([v1,v3]);                     // returns [[1,8], [2,9], [3,10], [4,11]]
    array_zip([v1,v2], fit="short");        // returns [[1,5], [2,6], [3,7]]
    array_zip([v1,v2], fit="long");         // returns [[1,5], [2,6], [3,7], [4,undef]]
    array_zip([v1,v2], fit="long, fill=0);  // returns [[1,5], [2,6], [3,7], [4,0]]
    array_zip([v1,v2,v3], fit="long");      // returns [[1,5,8], [2,6,9], [3,7,10], [4,undef,11]]

**Example 2**:

    v1 = [[1,2,3], [4,5,6], [7,8,9]];
    v2 = [[20,19,18], [17,16,15], [14,13,12]];
    array_zip(v1,v2);    // Returns [[1,2,3,20,19,18], [4,5,6,17,16,15], [7,8,9,14,13,12]]

---

### array\_group()

**Description**:
Takes a flat array of values, and groups items in sets of `cnt` length.
The opposite of this is `flatten()`.

Argument        | What it does
--------------- | ------------------------------
`v`             | The list of items to group.
`cnt`           | The number of items to put in each grouping.
`dflt`          | The default value to fill in with is the list is not a multiple of `cnt` items long.

**Example**:

    v = [1,2,3,4,5,6];
    array_group(v,2) returns [[1,2], [3,4], [5,6]]
    array_group(v,3) returns [[1,2,3], [4,5,6]]
    array_group(v,4,0) returns [[1,2,3,4], [5,6,0,0]]

---

### flatten()

**Description**:
Takes a list of lists and flattens it by one level.

Argument        | What it does
--------------- | ------------------------------
`l`             | List to flatten.

**Example**:

    flatten([[1,2,3], [4,5,[6,7,8]]]) returns [1,2,3,4,5,[6,7,8]]

---

### sort()

**Usage**:
- sort(arr, [idx])

**Description**:
Sorts the given list using `compare_vals()`.  Results are undefined if list elements are not of similar type.

Argument        | What it does
--------------- | ------------------------------
`arr`           | The list to sort.
`idx`           | If given, the index, range, or list of indices of sublist items to compare.

**Example**:

    l = [45,2,16,37,8,3,9,23,89,12,34];
    sorted = sort(l);  // Returns [2,3,8,9,12,16,23,34,37,45,89]

---

### unique()

**Usage**:
- unique(arr);

**Description**:
Returns a sorted list with all repeated items removed.

Argument        | What it does
--------------- | ------------------------------
`arr`           | The list to uniquify.

---

### array\_dim()

**Usage**:
- array\_dim(v, [depth])

**Description**:
Returns the size of a multi-dimensional array.  Returns a list of
dimension lengths.  The length of `v` is the dimension `0`.  The
length of the items in `v` is dimension `1`.  The length of the
items in the items in `v` is dimension `2`, etc.  For each dimension,
if the length of items at that depth is inconsistent, `undef` will
be returned.  If no items of that dimension depth exist, `0` is
returned.  Otherwise, the consistent length of items in that
dimensional depth is returned.

Argument        | What it does
--------------- | ------------------------------
`v`             | Array to get dimensions of.
`depth`         | Dimension to get size of.  If not given, returns a list of dimension lengths.

**Example 1**:

    array_dim([[[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]]]);     // Returns [2,2,3]

**Example 2**:

    array_dim([[[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]]], 0);  // Returns 2

**Example 3**:

    array_dim([[[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]]], 2);  // Returns 3

**Example 4**:

    array_dim([[[1,2,3],[4,5,6]],[[7,8,9]]]);                // Returns [2,undef,3]

---

# 4. Vector Manipulation

### vmul()

**Description**:
Element-wise vector multiplication.  Multiplies each element of vector `v1` by
the corresponding element of vector `v2`.  Returns a vector of the products.

Argument        | What it does
--------------- | ------------------------------
`v1`            | The first vector.
`v2`            | The second vector.

**Example**:

    vmul([3,4,5], [8,7,6]);  // Returns [24, 28, 30]

---

### vdiv()

**Description**:
Element-wise vector division.  Divides each element of vector `v1` by
the corresponding element of vector `v2`.  Returns a vector of the quotients.

Argument        | What it does
--------------- | ------------------------------
`v1`            | The first vector.
`v2`            | The second vector.

**Example**:

    vdiv([24,28,30], [8,7,6]);  // Returns [3, 4, 5]

---

### vabs()

**Description**:
Returns a vector of the absolute value of each element of vector `v`.

Argument        | What it does
--------------- | ------------------------------
`v`             | The vector to get the absolute values of.

---

### normalize()

**Description**:
Returns unit length normalized version of vector v.

Argument        | What it does
--------------- | ------------------------------
`v`             | The vector to normalize.

---

### vector\_angle()

**Usage**:
- vector\_angle(v1,v2);

**Description**:
Returns angle in degrees between two vectors of similar dimensions.

Argument        | What it does
--------------- | ------------------------------
`v1`            | First vector.
`v2`            | Second vector.

---

### vector\_axis()

**Usage**:
- vector\_xis(v1,v2);

**Description**:
Returns the vector perpendicular to both of the given vectors.

Argument        | What it does
--------------- | ------------------------------
`v1`            | First vector.
`v2`            | Second vector.

---

# 5. Coordinates Manipulation

### point2d()

**Description**:
Returns a 2D vector/point from a 2D or 3D vector.
If given a 3D point, removes the Z coordinate.

Argument        | What it does
--------------- | ------------------------------
`p`             | The coordinates to force into a 2D vector/point.

---

### path2d()

**Description**:
Returns a list of 2D vectors/points from a list of 2D or 3D vectors/points.
If given a 3D point list, removes the Z coordinates from each point.

Argument        | What it does
--------------- | ------------------------------
`points`        | A list of 2D or 3D points/vectors.

---

### point3d()

**Description**:
Returns a 3D vector/point from a 2D or 3D vector.

Argument        | What it does
--------------- | ------------------------------
`p`             | The coordinates to force into a 3D vector/point.

---

### path3d()

**Description**:
Returns a list of 3D vectors/points from a list of 2D or 3D vectors/points.

Argument        | What it does
--------------- | ------------------------------
`points`        | A list of 2D or 3D points/vectors.

---

### translate\_points()

**Usage**:
- translate\_points(pts, v);

**Description**:
Moves each point in an array by a given amount.

Argument        | What it does
--------------- | ------------------------------
`pts`           | List of points to translate.
`v`             | Amount to translate points by.

---

### scale\_points()

**Usage**:
- scale\_points(pts, v, [cp]);

**Description**:
Scales each point in an array by a given amount, around a given centerpoint.

Argument        | What it does
--------------- | ------------------------------
`pts`           | List of points to scale.
`v`             | A vector with a scaling factor for each axis.
`cp`            | Centerpoint to scale around.

---

### rotate\_points2d()

**Usage**:
- rotate\_points2d(pts, ang, [cp]);

**Description**:
Rotates each 2D point in an array by a given amount, around an optional centerpoint.

Argument        | What it does
--------------- | ------------------------------
`pts`           | List of 3D points to rotate.
`ang`           | Angle to rotate by.
`cp`            | 2D Centerpoint to rotate around.  Default: `[0,0]`

---

### rotate\_points3d()

**Usage**:
- rotate\_points3d(pts, v, [cp], [reverse]);
- rotate\_points3d(pts, v, axis, [cp], [reverse]);
- rotate\_points3d(pts, from, to, v, [cp], [reverse]);

**Description**:
Rotates each 3D point in an array by a given amount, around a given centerpoint.

Argument        | What it does
--------------- | ------------------------------
`pts`           | List of points to rotate.
`v`             | Rotation angle(s) in degrees.
`axis`          | If given, axis vector to rotate around.
`cp`            | Centerpoint to rotate around.
`from`          | If given, the vector to rotate something from.  Used with `to`.
`to`            | If given, the vector to rotate something to.  Used with `from`.
`reverse`       | If true, performs an exactly reversed rotation.

---

# 6. Coordinate Systems

### polar\_to\_xy()

**Usage**:
- polar\_to\_xy(r, theta);
- polar\_to\_xy([r, theta]);

**Description**:
Convert polar coordinates to 2D cartesian coordinates.
Returns [X,Y] cartesian coordinates.

Argument        | What it does
--------------- | ------------------------------
`r`             | distance from the origin.
`theta`         | angle in degrees, counter-clockwise of X+.

**Example 1**:

    xy = polar_to_xy(20,30);

**Example 2**:

    xy = polar_to_xy([40,60]);

---

### xy\_to\_polar()

**Usage**:
- xy\_to\_polar(x,y);
- xy\_to\_polar([X,Y]);

**Description**:
Convert 2D cartesian coordinates to polar coordinates.
Returns [radius, theta] where theta is the angle counter-clockwise of X+.

Argument        | What it does
--------------- | ------------------------------
`x`             | X coordinate.
`y`             | Y coordinate.

**Example 1**:

    plr = xy_to_polar(20,30);

**Example 2**:

    plr = xy_to_polar([40,60]);

---

### cylindrical\_to\_xyz()

**Usage**:
- cylindrical\_to\_xyz(r, theta, z)
- cylindrical\_to\_xyz([r, theta, z])

**Description**:
Convert cylindrical coordinates to 3D cartesian coordinates.  Returns [X,Y,Z] cartesian coordinates.

Argument        | What it does
--------------- | ------------------------------
`r`             | distance from the Z axis.
`theta`         | angle in degrees, counter-clockwise of X+ on the XY plane.
`z`             | Height above XY plane.

**Example 1**:

    xyz = cylindrical_to_xyz(20,30,40);

**Example 2**:

    xyz = cylindrical_to_xyz([40,60,50]);

---

### xyz\_to\_cylindrical()

**Usage**:
- xyz\_to\_cylindrical(x,y,z)
- xyz\_to\_cylindrical([X,Y,Z])

**Description**:
Convert 3D cartesian coordinates to cylindrical coordinates.
Returns [radius,theta,Z]. Theta is the angle counter-clockwise
of X+ on the XY plane.  Z is height above the XY plane.

Argument        | What it does
--------------- | ------------------------------
`x`             | X coordinate.
`y`             | Y coordinate.
`z`             | Z coordinate.

**Example 1**:

    cyl = xyz_to_cylindrical(20,30,40);

**Example 2**:

    cyl = xyz_to_cylindrical([40,50,70]);

---

### spherical\_to\_xyz()

**Usage**:
- spherical\_to\_xyz(r, theta, phi);
- spherical\_to\_xyz([r, theta, phi]);

**Description**:
Convert spherical coordinates to 3D cartesian coordinates.
Returns [X,Y,Z] cartesian coordinates.

Argument        | What it does
--------------- | ------------------------------
`r`             | distance from origin.
`theta`         | angle in degrees, counter-clockwise of X+ on the XY plane.
`phi`           | angle in degrees from the vertical Z+ axis.

**Example 1**:

    xyz = spherical_to_xyz(20,30,40);

**Example 2**:

    xyz = spherical_to_xyz([40,60,50]);

---

### xyz\_to\_spherical()

**Usage**:
- xyz\_to\_spherical(x,y,z)
- xyz\_to\_spherical([X,Y,Z])

**Description**:
Convert 3D cartesian coordinates to spherical coordinates.
Returns [r,theta,phi], where phi is the angle from the Z+ pole,
and theta is degrees counter-clockwise of X+ on the XY plane.

Argument        | What it does
--------------- | ------------------------------
`x`             | X coordinate.
`y`             | Y coordinate.
`z`             | Z coordinate.

**Example 1**:

    sph = xyz_to_spherical(20,30,40);

**Example 2**:

    sph = xyz_to_spherical([40,50,70]);

---

### altaz\_to\_xyz()

**Usage**:
- altaz\_to\_xyz(alt, az, r);
- altaz\_to\_xyz([alt, az, r]);

**Description**:
Convert altitude/azimuth/range coordinates to 3D cartesian coordinates.
Returns [X,Y,Z] cartesian coordinates.

Argument        | What it does
--------------- | ------------------------------
`alt`           | altitude angle in degrees above the XY plane.
`az`            | azimuth angle in degrees clockwise of Y+ on the XY plane.
`r`             | distance from origin.

**Example 1**:

    xyz = altaz_to_xyz(20,30,40);

**Example 2**:

    xyz = altaz_to_xyz([40,60,50]);

---

### xyz\_to\_altaz()

**Usage**:
- xyz\_to\_altaz(x,y,z);
- xyz\_to\_altaz([X,Y,Z]);

**Description**:
Convert 3D cartesian coordinates to altitude/azimuth/range coordinates.
Returns [altitude,azimuth,range], where altitude is angle above the
XY plane, azimuth is degrees clockwise of Y+ on the XY plane, and
range is the distance from the origin.

Argument        | What it does
--------------- | ------------------------------
`x`             | X coordinate.
`y`             | Y coordinate.
`z`             | Z coordinate.

**Example 1**:

    aa = xyz_to_altaz(20,30,40);

**Example 2**:

    aa = xyz_to_altaz([40,50,70]);

---

# 7. Matrix Manipulation

### ident()

**Description**:
Create an `n` by `n` identity matrix.

Argument        | What it does
--------------- | ------------------------------
`n`             | The size of the identity matrix square, `n` by `n`.

---

### matrix\_transpose()

**Description**:
Returns the transposition of the given matrix.

**Example**:

    m = [
        [11,12,13,14],
        [21,22,23,24],
        [31,32,33,34],
        [41,42,43,44]
    ];
    tm = matrix_transpose(m);
    // Returns:
    // [
    //     [11,21,31,41],
    //     [12,22,32,42],
    //     [13,23,33,43],
    //     [14,24,34,44]
    // ]

---

### mat3\_to\_mat4()

**Description**:
Takes a 3x3 matrix and returns its 4x4 equivalent.

---

### matrix3\_translate()

**Description**:
Returns the 3x3 matrix to perform a 2D translation.

Argument        | What it does
--------------- | ------------------------------
`v`             | 2D Offset to translate by.  [X,Y]

---

### matrix4\_translate()

**Description**:
Returns the 4x4 matrix to perform a 3D translation.

Argument        | What it does
--------------- | ------------------------------
`v`             | 3D offset to translate by.  [X,Y,Z]

---

### matrix3\_scale()

**Description**:
Returns the 3x3 matrix to perform a 2D scaling transformation.

Argument        | What it does
--------------- | ------------------------------
`v`             | 2D vector of scaling factors.  [X,Y]

---

### matrix4\_scale()

**Description**:
Returns the 4x4 matrix to perform a 3D scaling transformation.

Argument        | What it does
--------------- | ------------------------------
`v`             | 3D vector of scaling factors.  [X,Y,Z]

---

### matrix3\_zrot()

**Description**:
Returns the 3x3 matrix to perform a rotation of a 2D vector around the Z axis.

Argument        | What it does
--------------- | ------------------------------
`ang`           | Number of degrees to rotate.

---

### matrix4\_xrot()

**Description**:
Returns the 4x4 matrix to perform a rotation of a 3D vector around the X axis.

Argument        | What it does
--------------- | ------------------------------
`ang`           | number of degrees to rotate.

---

### matrix4\_yrot()

**Description**:
Returns the 4x4 matrix to perform a rotation of a 3D vector around the Y axis.

Argument        | What it does
--------------- | ------------------------------
`ang`           | Number of degrees to rotate.

---

### matrix4\_zrot()

**Usage**:
- matrix4\_zrot(ang)

**Description**:
Returns the 4x4 matrix to perform a rotation of a 3D vector around the Z axis.

Argument        | What it does
--------------- | ------------------------------
`ang`           | number of degrees to rotate.

---

### matrix4\_rot\_by\_axis()

**Usage**:
- matrix4\_rot\_by\_axis(u, ang);

**Description**:
Returns the 4x4 matrix to perform a rotation of a 3D vector around an axis.

Argument        | What it does
--------------- | ------------------------------
`u`             | 3D axis vector to rotate around.
`ang`           | number of degrees to rotate.

---

### matrix3\_skew()

**Usage**:
- matrix3\_skew(xa, ya)

**Description**:
Returns the 3x3 matrix to skew a 2D vector along the XY plane.

Argument        | What it does
--------------- | ------------------------------
`xa`            | Skew angle, in degrees, in the direction of the X axis.
`ya`            | Skew angle, in degrees, in the direction of the Y axis.

---

### matrix4\_skew\_xy()

**Usage**:
- matrix4\_skew\_xy(xa, ya)

**Description**:
Returns the 4x4 matrix to perform a skew transformation along the XY plane..

Argument        | What it does
--------------- | ------------------------------
`xa`            | Skew angle, in degrees, in the direction of the X axis.
`ya`            | Skew angle, in degrees, in the direction of the Y axis.

---

### matrix4\_skew\_xz()

**Usage**:
- matrix4\_skew\_xz(xa, za)

**Description**:
Returns the 4x4 matrix to perform a skew transformation along the XZ plane.

Argument        | What it does
--------------- | ------------------------------
`xa`            | Skew angle, in degrees, in the direction of the X axis.
`za`            | Skew angle, in degrees, in the direction of the Z axis.

---

### matrix4\_skew\_yz()

**Usage**:
- matrix4\_skew\_yz(ya, za)

**Description**:
Returns the 4x4 matrix to perform a skew transformation along the YZ plane.

Argument        | What it does
--------------- | ------------------------------
`ya`            | Skew angle, in degrees, in the direction of the Y axis.
`za`            | Skew angle, in degrees, in the direction of the Z axis.

---

### matrix3\_mult()

**Usage**:
- matrix3\_mult(matrices)

**Description**:
Returns a 3x3 transformation matrix which results from applying each matrix in `matrices` in order.

Argument        | What it does
--------------- | ------------------------------
`matrices`      | A list of 3x3 matrices.
`m`             | Optional starting matrix to apply everything to.

---

### matrix4\_mult()

**Usage**:
- matrix4\_mult(matrices)

**Description**:
Returns a 4x4 transformation matrix which results from applying each matrix in `matrices` in order.

Argument        | What it does
--------------- | ------------------------------
`matrices`      | A list of 4x4 matrices.
`m`             | Optional starting matrix to apply everything to.

---

### matrix3\_apply()

**Usage**:
- matrix3\_apply(pts, matrices)

**Description**:
Given a list of transformation matrices, applies them in order to the points in the point list.

Argument        | What it does
--------------- | ------------------------------
`pts`           | A list of 2D points to transform.
`matrices`      | A list of 3x3 matrices to apply, in order.

**Example**:

    npts = matrix3_apply(
        pts = [for (x=[0:3]) [5*x,0]],
        matrices =[
            matrix3_scale([3,1]),
            matrix3_rot(90),
            matrix3_translate([5,5])
        ]
    );  // Returns [[5,5], [5,20], [5,35], [5,50]]

---

### matrix4\_apply()

**Usage**:
- matrix4\_apply(pts, matrices)

**Description**:
Given a list of transformation matrices, applies them in order to the points in the point list.

Argument        | What it does
--------------- | ------------------------------
`pts`           | A list of 3D points to transform.
`matrices`      | A list of 4x4 matrices to apply, in order.

**Example**:

    npts = matrix4_apply(
      pts = [for (x=[0:3]) [5*x,0,0]],
      matrices =[
        matrix4_scale([2,1,1]),
        matrix4_zrot(90),
        matrix4_translate([5,5,10])
      ]
    );  // Returns [[5,5,10], [5,15,10], [5,25,10], [5,35,10]]

---

# 8. Geometry

### point\_on\_segment()

**Usage**:
- point\_on\_segment(point, edge);

**Description**:
Determine if the point is on the line segment between two points.
Returns true if yes, and false if not.

Argument        | What it does
--------------- | ------------------------------
`point`         | The point to check colinearity of.
`edge`          | Array of two points forming the line segment to test against.

---

### point\_left\_of\_segment()

**Usage**:
- point\_left\_of\_segment(point, edge);

**Description**:
Return >0 if point is left of the line defined by edge.
Return =0 if point is on the line.
Return <0 if point is right of the line.

Argument        | What it does
--------------- | ------------------------------
`point`         | The point to check position of.
`edge`          | Array of two points forming the line segment to test against.

---

### point\_in\_polygon()

**Usage**:
- point\_in\_polygon(point, path)

**Description**:
This function tests whether the given point is inside, outside or on the boundary of
the specified polygon using the Winding Number method.  (http://geomalgorithms.com/a03-\_inclusion.html)
The polygon is given as a list of points, not including the repeated end point.
Returns -1 if the point is outside the polyon.
Returns 0 if the point is on the boundary.
Returns 1 if the point lies in the interior.
The polygon does not need to be simple: it can have self-intersections.
But the polygon cannot have holes (it must be simply connected).
Rounding error may give mixed results for points on or near the boundary.

Argument        | What it does
--------------- | ------------------------------
`point`         | The point to check position of.
`path`          | The list of 2D path points forming the perimeter of the polygon.

---

### pointlist\_bounds()

**Usage**:
- pointlist\_bounds(pts);

**Description**:
Finds the bounds containing all the points in pts.
Returns [[minx, miny, minz], [maxx, maxy, maxz]]

Argument        | What it does
--------------- | ------------------------------
`pts`           | List of points.

---

# 9. Deprecations

### Cpi()

**DEPRECATED, use `PI` instead.**

**Description**:
Returns the value of pi.

---

### hypot3()

**DEPRECATED, use `norm([x,y,z])` instead.**

**Description**:
Calculate hypotenuse length of 3D triangle.

Argument        | What it does
--------------- | ------------------------------
`x`             | Length on the X axis.
`y`             | Length on the Y axis.
`z`             | Length on the Z axis.

---

### distance()

**DEPRECATED, use `norm(p2-p1)` instead.  It's shorter.**

**Description**:
Returns the distance between a pair of 2D or 3D points.

---

### cdr()

**DEPRECATED, use `slice(list,1,-1)` instead.**

**Description**:
Returns all but the first item of a given array.

Argument        | What it does
--------------- | ------------------------------
`list`          | The list to get the tail of.

---

### wrap\_range()

**DEPRECATED, use `select()` instead.**

**Usage**:
- wrap\_range(list,start)
- wrap\_range(list,start,end)

**Description**:
Returns a portion of a list, wrapping around past the beginning, if end<start.
The first item is index 0. Negative indexes are counted back from the end.
The last item is -1.  If only the `start` index is given, returns just the value
at that position.

Argument        | What it does
--------------- | ------------------------------
`list`          | The list to get the portion of.
`start`         | The index of the first item.
`end`           | The index of the last item.

---

### vector2d\_angle()

**DEPRECATED, use `vector_angle()` instead.**

**Usage**:
- vector2d\_angle(v1,v2);

**Description**:
Returns angle in degrees between two 2D vectors.

Argument        | What it does
--------------- | ------------------------------
`v1`            | First 2D vector.
`v2`            | Second 2D vector.

---

### vector3d\_angle()

**DEPRECATED, use `vector_angle()` instead.**

**Usage**:
- vector3d\_angle(v1,v2);

**Description**:
Returns angle in degrees between two 3D vectors.

Argument        | What it does
--------------- | ------------------------------
`v1`            | First 3D vector.
`v2`            | Second 3D vector.

---

### rotate\_points3d\_around\_axis()

**DEPRECATED, use `rotate_points3d(pts, v=ang, axis=u, cp=cp)` instead.**

**Usage**:
- rotate\_points3d\_around\_axis(pts, ang, u, [cp])

**Description**:
Rotates each 3D point in an array by a given amount, around a given centerpoint and axis.

Argument        | What it does
--------------- | ------------------------------
`pts`           | List of 3D points to rotate.
`ang`           | Angle to rotate by.
`u`             | Vector of the axis to rotate around.
`cp`            | 3D Centerpoint to rotate around.

---

