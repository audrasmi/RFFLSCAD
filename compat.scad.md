# Library File compat.scad

Backwards Compatability library
To use, include this line at the top of your file:
```
use <compat.scad>
```

---

# Table of Contents

1. [Functions](#functions)
    - [`default()`](#default)
    - [`is_def()`](#is_def)
    - [`is_str()`](#is_str)
    - [`is_boolean()`](#is_boolean)
    - [`is_scalar()`](#is_scalar)
    - [`is_array()`](#is_array)
    - [`get_radius()`](#get_radius)
    - [`Len()`](#len)
    - [`remove_undefs()`](#remove_undefs)
    - [`first_defined()`](#first_defined)
    - [`any_defined()`](#any_defined)
    - [`scalar_vec3()`](#scalar_vec3)

2. [Modules](#modules)
    - [`assert_in_list()`](#assert_in_list)
    - [`assertion()`](#assertion)
    - [`echo_error()`](#echo_error)
    - [`echo_warning()`](#echo_warning)
    - [`deprecate()`](#deprecate)
    - [`deprecate_argument()`](#deprecate_argument)

---

# 1. Functions

### default()

**Description**:
Returns the value given as `v` if it is not `undef`.
Otherwise, returns the value of `dflt`.

Argument        | What it does
--------------- | ------------------------------
`v`             | Value to pass through if not `undef`.
`dflt`          | Value to return if `v` *is* `undef`.

---

### is\_def()

**Description**:
Returns true if given value is not `undef`.

---

### is\_str()

**Description**:
Given a value, returns true if it is a string.

---

### is\_boolean()

**Description**:
Given a value, returns true if it is a boolean.

---

### is\_scalar()

**Description**:
Given a value, returns true if it is a scalar number.

---

### is\_array()

**Description**:
Given a value, returns true if it is an array/list/vector.

---

### get\_radius()

**Description**:
Given various radii and diameters, returns the most specific radius.
If a diameter is most specific, returns half its value, giving the radius.
If no radii or diameters are defined, returns the value of dflt.
Value specificity order is r1, d1, r, d, then dflt

Argument        | What it does
--------------- | ------------------------------
`r1`            | Most specific radius.
`d1`            | Most specific Diameter.
`r`             | Most general radius.
`d`             | Most general diameter.
`dflt`          | Value to return if all other values given are `undef`.

---

### Len()

**Description**:
Given an array, returns number of items in array.  Otherwise returns `undef`.

---

### remove\_undefs()

**Description**:
Removes all `undef`s from a list.

---

### first\_defined()

**Description**:
Returns the first item in the list that is not `undef`.
If all items are `undef`, or list is empty, returns `undef`.

---

### any\_defined()

**Description**:
Returns true if any item in the given array is not `undef`.

---

### scalar\_vec3()

**Usage**:
- scalar\_vec3(v, [dflt]);

**Description**:
If `v` is a scalar, and `dflt==undef`, returns `[v, v, v]`.
If `v` is a scalar, and `dflt!=undef`, returns `[v, dflt, dflt]`.
If `v` is a vector, returns the first 3 items, with any missing values replaced by `dflt`.
If `v` is `undef`, returns `undef`.

Argument        | What it does
--------------- | ------------------------------
`v`             | Value to return vector from.
`dflt`          | Default value to set empty vector parts from.

---

# 2. Modules

### assert\_in\_list()

**Usage**:
- assert\_in\_list(argname, val, l, [idx]);

**Description**:
Emulates the newer OpenSCAD `assert()` with an `in_list()` test.

Argument        | What it does
--------------- | ------------------------------
`argname`       | The name of the argument value being tested.
`val`           | The value to test if it exists in the list.
`l`             | The list to look for `val` in.
`idx`           | If given, and `l` is a list of lists, look for `val` in the given index of each sublist.

---

### assertion()

**Usage**:
- assertion(succ, msg);

**Description**:
Backwards compatible assert() semi-replacement.  If `succ` is false, then print an error with `msg`.

Argument        | What it does
--------------- | ------------------------------
`succ`          | If this is `false`, trigger the assertion.
`msg`           | The message to emit if `succ` is `false`.

---

### echo\_error()

**Usage**:
- echo\_error(msg, [pfx]);

**Description**:
Emulates printing of an error message.  The text will be shaded red.

Argument        | What it does
--------------- | ------------------------------
`msg`           | The message to print.
`pfx`           | The prefix to print before `msg`.  Default: `ERROR`

---

### echo\_warning()

**Usage**:
- echo\_warning(msg, [pfx]);

**Description**:
Emulates printing of a warning message.  The text will be shaded yellow.

Argument        | What it does
--------------- | ------------------------------
`msg`           | The message to print.
`pfx`           | The prefix to print before `msg`.  Default: `WARNING`

---

### deprecate()

**Usage**:
- deprecate(name, [suggest]);

**Description**:
Show module deprecation warnings.

Argument        | What it does
--------------- | ------------------------------
`name`          | The name of the module that is deprecated.
`suggest`       | If given, the module to recommend using instead.

---

### deprecate\_argument()

**Usage**:
- deprecate(name, arg, [suggest]);

**Description**:
Show module argument deprecation warnings.

Argument        | What it does
--------------- | ------------------------------
`name`          | The name of the module the deprecated argument is used in.
`arg`           | The name of the deprecated argument.
`suggest`       | If given, the argument to recommend using instead.

---

