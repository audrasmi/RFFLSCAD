Routines to triangulate `polyhedron()` faces that have more than 3 vertexes.
To use this, include the following line at the top of your file:

    use <BOSL/triangulation.scad>


# Table of Contents

## triangulate\_face(points, face)
Triangulates a face if it is bound by more than three vertices.
Returns a list of faces, where each face is a list of 3 vertex
indices.

Args     | What it does
-------- | ------------------------
points   | The vertex points for the polyhedron.
face     | A list of vertex indices for the given face.



## triangulate\_faces(points, faces)
Triangulates each given face if it is bound by more than
three vertices.  Returns a list of faces, where each face
is a list of 3 vertex indices.

Args     | What it does
-------- | ------------------------
points   | The vertex points for the polyhedron.
faces    | A list of faces, where each face is a list of vertex indices.


