# Library File triangulation.scad

Functions to triangulate polyhedron faces.
To use, add the following lines to the beginning of your file:
```
use <BOSL/triangulation.scad>
```

---

# Table of Contents

1. [Functions](#1-functions)
    - [`face_normal()`](#face_normal)
    - [`find_convex_vertex()`](#find_convex_vertex)
    - [`point_in_ear()`](#point_in_ear)
    - [`normalize_vertex_perimeter()`](#normalize_vertex_perimeter)
    - [`is_only_noncolinear_vertex()`](#is_only_noncolinear_vertex)
    - [`triangulate_face()`](#triangulate_face)
    - [`triangulate_faces()`](#triangulate_faces)

---

# 1. Functions

### face\_normal()

**Description**:
Given an array of vertices (`points`), and a list of indexes into the
vertex array (`face`), returns the normal vector of the face.

Argument        | What it does
--------------- | ------------------------------
`points`        | Array of vertices for the polyhedron.
`face`          | The face, given as a list of indices into the vertex array `points`.

---

### find\_convex\_vertex()

**Description**:
Returns the index of a convex point on the given face.

Argument        | What it does
--------------- | ------------------------------
`points`        | Array of vertices for the polyhedron.
`face`          | The face, given as a list of indices into the vertex array `points`.
`facenorm`      | The normal vector of the face.

---

### point\_in\_ear()

**Description**:
Determine if a point is in a clipable convex ear.

Argument        | What it does
--------------- | ------------------------------
`points`        | Array of vertices for the polyhedron.
`face`          | The face, given as a list of indices into the vertex array `points`.

---

### normalize\_vertex\_perimeter()

**Description**:
Removes the last item in an array if it is the same as the first item.

Argument        | What it does
--------------- | ------------------------------
`v`             | The array to normalize.

---

### is\_only\_noncolinear\_vertex()

**Description**:
Given a face in a polyhedron, and a vertex in that face, returns true
if that vertex is the only non-colinear vertex in the face.

Argument        | What it does
--------------- | ------------------------------
`points`        | Array of vertices for the polyhedron.
`facelist`      | The face, given as a list of indices into the vertex array `points`.
`vertex`        | The index into `facelist`, of the vertex to test.

---

### triangulate\_face()

**Description**:
Given a face in a polyhedron, subdivides the face into triangular faces.
Returns an array of faces, where each face is a list of three vertex indices.

Argument        | What it does
--------------- | ------------------------------
`points`        | Array of vertices for the polyhedron.
`face`          | The face, given as a list of indices into the vertex array `points`.

---

### triangulate\_faces()

**Description**:
Subdivides all faces for the given polyhedron that have more than three vertices.
Returns an array of faces where each face is a list of three vertex array indices.

Argument        | What it does
--------------- | ------------------------------
`points`        | Array of vertices for the polyhedron.
`faces`         | Array of faces for the polyhedron. Each face is a list of 3 or more indices into the `points` array.

---

