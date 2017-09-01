Masks and models for NEMA stepper motors and mounts.


# Functions

## nema\_motor\_width(size)
Returns the width of the given NEMA motor size.



## nema\_motor\_plinth\_height(size)
Returns the face plinth height for the given NEMA motor size.



## nema\_motor\_plinth\_diam(size)
Returns the face plinth diameter for the given NEMA motor size.



## nema\_motor\_screw\_spacing(size)
Returns the spacing between screws for the given NEMA motor size.



## nema\_motor\_screw\_size(size)
Returns the screw size for the given NEMA motor size.



## nema\_motor\_screw\_depth(size)
Returns the width of the given NEMA motor size.



# Modules


## nema11\_stepper()
Creates a model for rendering a NEMA 11 stepper motor.

Arg        | What it is
---------- | ---------------------------
h          | height (length) of the stepper motor.
shaft      | Diameter of the shaft.
shaft\_len | Length of the shaft that protrudes from the motor.



## nema14\_stepper()
Creates a model for rendering a NEMA 14 stepper motor.

Arg        | What it is
---------- | ---------------------------
h          | height (length) of the stepper motor.
shaft      | Diameter of the shaft.
shaft\_len | Length of the shaft that protrudes from the motor.



## nema17\_stepper()
Creates a model for rendering a NEMA 17 stepper motor.

Arg        | What it is
---------- | ---------------------------
h          | height (length) of the stepper motor.
shaft      | Diameter of the shaft.
shaft\_len | Length of the shaft that protrudes from the motor.



## nema23\_stepper()
Creates a model for rendering a NEMA 23 stepper motor.

Arg        | What it is
---------- | ---------------------------
h          | height (length) of the stepper motor.
shaft      | Diameter of the shaft.
shaft\_len | Length of the shaft that protrudes from the motor.



## nema34\_stepper()
Creates a model for rendering a NEMA 34 stepper motor.

Arg        | What it is
---------- | ---------------------------
h          | height (length) of the stepper motor.
shaft      | Diameter of the shaft.
shaft\_len | Length of the shaft that protrudes from the motor.




## nema17\_mount\_holes(depth=5, l=5, slop=printer_slop)
Creates a mask shape for mounting a NEMA 17 motor.

Arg        | What it is
---------- | ---------------------------
depth      | Depth of hole to make.
l          | Length of adjustable screw slots.
slop       | Slight adjustment value to make motors fit in holes.



