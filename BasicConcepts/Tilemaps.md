# Tilemaps

A `Tilemap` is used to build 2D levels with a grid of cells, where each cell can contain a tile.

Instead of placing individual sprites manually, Tilemaps let you paint tiles onto a grid. This makes level creation faster, more consistent, and easier to maintain.

A Tilemap system is composed of:

- A `Grid`, which defines the cell layout.
- A `Tilemap`, which stores the tiles.
- `Tiles`, which are the individual sprites placed in each cell.

Tilemaps are common in grid-based games such as platformers and top-down games.

Official reference: <https://docs.unity3d.com/2022.3/Documentation/Manual/Tilemap.html>

## Tilemap Collider 2D

A `Tilemap Collider 2D` automatically generates collision shapes based on the tiles placed in a Tilemap.

Instead of adding individual colliders to each tile, Unity creates colliders for the whole Tilemap. This simplifies setup and can improve performance.

The collider updates dynamically when tiles are added or removed.

For better optimization, a Tilemap Collider 2D is often combined with a `Composite Collider 2D`, which merges multiple tile colliders into a single more efficient shape.
