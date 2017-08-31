Trapezoidal-threaded (ACME) Screw Rods and Nuts.


# ACME Threaded Rods And Nuts

## acme\_threaded\_rod()
Constructs an acme threaded screw rod.  This method makes much
smoother threads than the naive `linear_extrude` method.

Arg           | What it does
------------- | ------------------------------
d             | Outer diameter of threaded rod.
l             | Length of threaded rod.
pitch         | Thread pitch.
thread\_depth | Depth of threads.
thread\_angle | Trapezoidal angle of threads.

Example:

	acme_threaded_rod(d=10, l=100, pitch=5, thread_depth=2, thread_angle=30);



## acme\_threaded\_nut()
Constructs an acme threaded nut.

Arg           | What it does
------------- | ------------------------------
od            | Outer diameter of threaded nut.
id            | Diameter of threaded rod to make a nut for.
h             | Height/Thickness of the nut.
pitch         | Thread pitch.
thread\_depth | Depth of threads.
thread\_angle | Trapezoidal angle of threads.
slop          | Slop to make parts fit tightly.


Examples:

	acme_threaded_nut(od=17.4, id=10.5, h=10, pitch=3.175, thread_depth=1, slop=printer_slop);



