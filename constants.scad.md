Miscellaneous useful constants

## Vectors Constants

Useful for `mirror()`, `offsetcube()`, `rotate()`, etc.

- `V_LEFT`: A unit vector pointed to the left.
- `V_RIGHT`: A unit vector pointed to the right.
- `V_FWD`: A unit vector pointed to the front.
- `V_BACK`: A unit vector pointed to the back.
- `V_DOWN`: A unit vector pointed downwards.
- `V_UP`: A unit vector pointed upwards.

## Edge Constants

Constants for defining edges for [`chamfer()`](shapes.scad#chamfer--), etc.

#### Individual edges:

- `EDGE_BOT_LF`: Bottom left (X-Z-) edge.
- `EDGE_BOT_RT`: Bottom right (X+Z-) edge.
- `EDGE_BOT_FR`: Bottom front (Y-Z-) edge.
- `EDGE_BOT_BK`: Bottom back (Y+Z-) edge.
- `EDGE_TOP_LF`: Top left (X-Z+) edge.
- `EDGE_TOP_RT`: Top right (X+Z+) edge.
- `EDGE_TOP_FR`: Top front (Y-Z+) edge.
- `EDGE_TOP_BK`: Top back (Y+Z+) edge.
- `EDGE_FR_LF`: Front right (X-Y-) edge.
- `EDGE_FR_RT`: Front right (X+Y-) edge.
- `EDGE_BK_LF`: Back right (X-Y+) edge.
- `EDGE_BK_RT`: Back right (X+Y+) edge.

#### X-axis aligned edges.

- `EDGES_X_FR`: X-aligned edges of front face.
- `EDGES_X_BK`: X-aligned edges of back face.
- `EDGES_X_BOT`: X-aligned edges of bottom face.
- `EDGES_X_TOP`: X-aligned edges of top face.
- `EDGES_X_ALL`: All X-aligned edges.

#### Y-axis aligned edges.

- `EDGES_Y_LF`: Y-aligned edges of left face.
- `EDGES_Y_RT`: Y-aligned edges of right face.
- `EDGES_Y_BOT`: Y-aligned edges of bottom face.
- `EDGES_Y_TOP`: Y-aligned edges of top face.
- `EDGES_Y_ALL`: All Y-aligned edges.

#### Z-axis aligned edges.

- `EDGES_Z_LF`: Z-aligned edges of left face.
- `EDGES_Z_RT`: Z-aligned edges of right face.
- `EDGES_Z_FR`: Z-aligned edges of front face.
- `EDGES_Z_BK`: Z-aligned edges of back face.
- `EDGES_Z_ALL`: All Z-aligned edges.

#### Edges by face.

- `EDGES_LEFT`: All edges of left face.
- `EDGES_RIGHT`: All edges of right face.
- `EDGES_FRONT`: All edges of front face.
- `EDGES_BACK`: All edges of back face.
- `EDGES_BOTTOM`: All edges of bottom face.
- `EDGES_TOP`: All edges of top face.

#### Other edge sets.

- `EDGES_NONE`: No edges at all.
- `EDGES_ALL`: All edges.


