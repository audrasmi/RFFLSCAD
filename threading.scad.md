Generic Threaded Screw Rods and Nuts.


# Generic Trapezoidal Threaded Rods And Nuts


## trapezoidal\_threaded\_rod()
Constructs a generic trapezoidal-profile threaded screw rod.  This method makes
much smoother threads than the naive `linear_extrude()` method.

- For metric trapezoidal threads, use `thread_angle=15` and `thread_depth=pitch/2`.
- For ACME trapezoidal threads, use `thread_angle=14.5` and `thread_depth=pitch/2`.
- For square threads, use `thread_angle=0` and `thread_depth=pitch/2`.
- For normal screw threads, use `thread_angle=30` and `thread_depth=pitch*3*sqrt(3)/8`.

Arg           | What it does
------------- | ------------------------------
d             | Outer diameter of threaded rod.
l             | Length of threaded rod.
pitch         | Thread pitch.
thread\_depth | Depth of threads.  Default = pitch/2
thread\_angle | Trapezoidal angle of threads.  Default = 15 degrees.
starts        | The number of lead starts.  Default = 1
left\_handed  | If true, create left-handed threads.  Default = false

Example:

	trapezoidal_threaded_rod(d=10, l=100, pitch=5, thread_depth=2, thread_angle=30);



## trapezoidal\_threaded\_nut()
Constructs a generic trapezoidal-profile threaded nut.

- For metric trapezoidal threads, use `thread_angle=15` and `thread_depth=pitch/2`.
- For ACME trapezoidal threads, use `thread_angle=14.5` and `thread_depth=pitch/2`.
- For square threads, use `thread_angle=0` and `thread_depth=pitch/2`.
- For normal screw threads, use `thread_angle=30` and `thread_depth=pitch*3*sqrt(3)/8`.

Arg           | What it does
------------- | ------------------------------
od            | Outer diameter of threaded nut.
id            | Diameter of threaded rod to make a nut for.
h             | Height/Thickness of the nut.
pitch         | Thread pitch.
thread\_depth | Depth of threads.  Default = pitch/2
thread\_angle | Trapezoidal angle of threads.  Default = 15 degrees.
starts        | The number of lead starts.  Default = 1
left\_handed  | If true, create left-handed threads.  Default = false
slop          | Slop to make the printed parts fit tightly.  Default = 0.2


Examples:

	acme_threaded_nut(od=17.4, id=10.5, h=10, pitch=3.175, thread_depth=1, slop=0.15);



# Metric and UTS (American) Triangular Threaded Rods And Nuts


## threaded\_rod()
Constructs an standard triangular threaded metric or UTS screw rod.
This method makes much smoother threads than the naive `linear_extrude` method.

Arg           | What it does
------------- | ------------------------------
d             | Outer diameter of threaded rod.
l             | Length of threaded rod.
pitch         | Thread pitch.
left\_handed  | If true, create left-handed threads.  Default = false

Example:

	threaded_rod(d=10, l=100, pitch=5, left_handed=true);



## threaded\_nut()
Constructs a standard metric or UTS (American) triangular threaded nut.

Arg           | What it does
------------- | ------------------------------
od            | Outer diameter of threaded nut.
id            | Diameter of threaded rod to make a nut for.
h             | Height/Thickness of the nut.
pitch         | Thread pitch.
left\_handed  | If true, create left-handed threads.  Default = false
slop          | Slop to make the printed parts fit tightly.  Default = 0.2


Examples:

	acme_threaded_nut(od=17.4, id=10.5, h=10, pitch=3.175, thread_depth=1, slop=0.15);



# ACME Threaded Rods And Nuts


## acme\_threaded\_rod()
Constructs an acme threaded screw rod.  This method makes much
smoother threads than the naive `linear_extrude` method.

Arg           | What it does
------------- | ------------------------------
d             | Outer diameter of threaded rod.
l             | Length of threaded rod.
pitch         | Thread pitch.
thread\_depth | Depth of threads.  Default = pitch/2
thread\_angle | Trapezoidal angle of threads.  Default = 14.5 degrees.
starts        | The number of lead starts.  Default = 1
left\_handed  | If true, create left-handed threads.  Default = false

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
thread\_depth | Depth of threads.  Default = pitch/2
thread\_angle | Trapezoidal angle of threads.  Default = 14.5 degrees.
starts        | The number of lead starts.  Default = 1
left\_handed  | If true, create left-handed threads.  Default = false
slop          | Slop to make the printed parts fit tightly.  Default = 0.2


Examples:

	acme_threaded_nut(od=17.4, id=10.5, h=10, pitch=3.175, thread_depth=1, slop=0.15);



# Standard Metric Trapezoidal Threaded Rods And Nuts


## metric\_trapezoidal\_threaded\_rod()
Constructs an standard metric trapezoidal threaded screw rod.  This method
makes much smoother threads than the naive `linear_extrude` method.

Arg           | What it does
------------- | ------------------------------
d             | Outer diameter of threaded rod.
l             | Length of threaded rod.
pitch         | Thread pitch.
left\_handed  | If true, create left-handed threads.  Default = false
starts        | The number of lead starts.  Default = 1

Example:

	metric\_trapezoidal\_threaded_rod(d=10, l=100, pitch=5, left_handed=true);



## metric\_trapezoidal\_threaded\_nut()
Constructs a standard metric trapezoidal threaded nut.

Arg           | What it does
------------- | ------------------------------
od            | Outer diameter of threaded nut.
id            | Diameter of threaded rod to make a nut for.
h             | Height/Thickness of the nut.
pitch         | Thread pitch.
left\_handed  | If true, create left-handed threads.  Default = false
starts        | The number of lead starts.  Default = 1
slop          | Slop to make the printed parts fit tightly.  Default = 0.2


Examples:

	metric_trapezoidal_threaded_nut(od=17.4, id=12, h=16, pitch=2, left_handed=true, starts=2, slop=0.15);



# Standard Square-Profile Threaded Rods And Nuts


## square\_threaded\_rod()
Constructs a standard square-profile threaded screw rod.  This method
makes much smoother threads than the naive `linear_extrude` method.

Arg           | What it does
------------- | ------------------------------
d             | Outer diameter of threaded rod.
l             | Length of threaded rod.
pitch         | Thread pitch.
left\_handed  | If true, create left-handed threads.  Default = false
starts        | The number of lead starts.  Default = 1

Example:

	square\_threaded_rod(d=10, l=100, pitch=5, left_handed=true, starts=3);



## square\_threaded\_nut()
Constructs a standard square-profile threaded nut.

Arg           | What it does
------------- | ------------------------------
od            | Outer diameter of threaded nut.
id            | Diameter of threaded rod to make a nut for.
h             | Height/Thickness of the nut.
pitch         | Thread pitch.
left\_handed  | If true, create left-handed threads.  Default = false
starts        | The number of lead starts.  Default = 1
slop          | Slop to make the printed parts fit tightly.  Default = 0.2


Examples:

	square_threaded_nut(od=17.4, id=12, h=16, pitch=2, left_handed=true, starts=2, slop=0.15);



