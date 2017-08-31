Screws, Bolts, and Nuts.

# Functions

## get\_metric\_bolt\_head\_size(size)
Get the bolt head size for a given metric screw diameter.



## get\_metric\_nut\_size(size)
Get the nut diameter for a given metric screw diameter.



## get\_metric\_nut\_thickness(size)
Get the nut thickness for a given metric screw diameter.



# Modules

## screw()
Makes a simple threadless screw, useful for making screwholes.

Arg       | What it is
--------- | -----------------------------
screwsize | diameter of threaded part of screw.
screwlen  | length of threaded part of screw.
headsize  | diameter of the screw head.
headlen   | length of the screw head.

Example:

    screw(screwsize=3,screwlen=10,headsize=6,headlen=3);



## metric\_nut()
Makes an unthreaded model of a standard nut for a standard metric screw.

Arg       | What it is
--------- | -----------------------------
size      | standard metric screw size in mm. (Default: 3)
hole      | include an unthreaded hole in the nut.  (Default: true)
center    | If true, nut is centered, otherwise, sits on top of XY plane.

Example:

    metric_nut(size=8, hole=true);
    metric_nut(size=3, hole=false);




