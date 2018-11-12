# Debugging modules

## debug\_vertices(vertices, size, disabled)
Draws all the vertices in an array, at their 3D position, numbered by their
position in the vertex array.  Also draws any children of this module with
transparency.

Arg         | What it is
----------- | --------------------------------
vertices    | Array of point vertices.
size        | The size of the text used to label the vertexes.
disabled    | If true, don't draw numbers, and draw children without transparency.  Default = false.


## debug\_faces(vertices, faces, size, disabled)
Draws all the vertices at their 3D position, numbered in blue by their
position in the vertex array.  Each face will have their face number drawn
in red, aligned with the center of face.  All children of this module are
drawn with transparency.  Works best with Thrown-Together preview mode, to
see reversed faces.

Arg         | What it is
----------- | --------------------------------
vertices    | Array of point vertices.
faces       | Array of faces by vertex numbers.
size        | The size of the text used to label the faces and vertexes.
disabled    | If true, don't draw numbers, and draw children without transparency.  Default = false.


## debug\_polyhedron(points, faces, txtsize, disabled)
A drop-in module to replace `polyhedron()` and help debug vertices and faces.
Draws all the vertices at their 3D position, numbered in blue by their
position in the vertex array.  Each face will have their face number drawn
in red, aligned with the center of face.  All given faces are drawn with
transparency. All children of this module are drawn with transparency.
Works best with Thrown-Together preview mode, to see reversed faces.

Arg         | What it is
----------- | --------------------------------
vertices    | Array of point vertices.
faces       | Array of faces by vertex numbers.
txtsize     | The size of the text used to label the faces and vertexes.
disabled    | If true, act exactly like `polyhedron()`.  Default = false.

Example:
    pts = [[-5,0,-5], [5,0,-5], [0,-5,5], [0,5,5]];
    fcs = [[0,2,1], [1,2,3], [1,3,0], [0,2,3]];  // Last face reversed
    debug_polyhedron(points=pts, faces=fcs, txtsize=1);

