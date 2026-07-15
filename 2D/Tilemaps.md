# Tilemaps

A `Tilemap` is used to build 2D levels with a grid of cells, where each cell can contain a tile.

Instead of placing individual sprites manually, Tilemaps let you paint tiles onto a grid. This makes level creation faster, more consistent, and easier to maintain.

A Tilemap system is composed of:

- A `Grid`, which defines the cell layout.
- A `Tilemap`, which stores the tiles.
- `Tiles`, which are the individual sprites placed in each cell.

Tilemaps are common in grid-based games such as platformers and top-down games.

Official reference: <https://docs.unity3d.com/2022.3/Documentation/Manual/Tilemap.html>

## Rule Tile

A `Rule Tile` is a special type of tile that automatically chooses which sprite to display based on the tiles around it.

Instead of manually selecting a different tile for every edge, corner, or center piece, a Rule Tile uses rules to decide how it should look depending on its neighbors.

For example, when painting terrain:

- A tile surrounded by other ground tiles can use a center sprite.
- A tile with empty space above it can use a top edge sprite.
- A tile on a corner can use a corner sprite.

This makes Tilemap painting faster and keeps the level visually consistent.

Rule Tiles are especially useful for terrain, walls, paths, platforms, and any repeated environment where the sprite should adapt to nearby tiles.

## Rule Tile Neighbor Rules

Inside a Rule Tile, each rule has a small grid. The center represents the tile being evaluated, and the cells around it represent neighboring positions.

Each neighbor cell can have one of three states:

| State | Meaning |
| --- | --- |
| Green arrow | There must be a compatible tile in that position. |
| Red cross | There must not be a compatible tile in that position. |
| Empty cell | That position does not matter. |

In other words:

```text
green arrow = required neighbor tile
red cross = required empty space
empty = ignored condition
```

For example, if the cell above the center has a red cross, the rule means:

```text
use this sprite when there is no tile above the current tile
```

This is useful for a top edge sprite, because the Rule Tile can detect that the tile is at the top border of a terrain area.

Example pattern:

```text
[ ] [X] [ ]
[ ] [C] [ ]
[ ] [ ] [ ]
```

Where:

- `C` is the current tile.
- `X` means the position above must be empty.
- Empty cells mean those neighbors do not matter for this rule.

For terrain, common rules are:

- Center tile: several neighboring positions use green arrows.
- Top edge: the cell above uses a red cross.
- Corner: two directions use red crosses.
- Generic fallback: many cells are empty because their state does not matter.

## Animated Tile

An `Animated Tile` is a tile that cycles through multiple sprites over time.

Instead of displaying a single static sprite, it uses a sequence of sprites to create a simple animation directly inside the Tilemap.

Animated Tiles are useful for repeated environment elements such as:

- Water.
- Lava.
- Fire.
- Moving lights.
- Animated floor details.

For example, a water tile can use several water sprites that change one after another. When painted on the Tilemap, Unity plays that sprite sequence and the water appears animated.

Animated Tiles are useful when the animation belongs to the environment itself and does not need custom gameplay logic. If the object needs behavior, interaction, or complex animation control, a regular GameObject with an Animator may be a better option.

In short:

```text
tile = one reusable piece
tilemap = the grid where tiles are painted
rule tile = a smart tile that changes its sprite depending on neighboring tiles
animated tile = a tile that plays multiple sprites over time
```

## Tilemap Collider 2D

A `Tilemap Collider 2D` automatically generates collision shapes based on the tiles placed in a Tilemap.

Instead of adding individual colliders to each tile, Unity creates colliders for the whole Tilemap. This simplifies setup and can improve performance.

The collider updates dynamically when tiles are added or removed.

For better optimization, a Tilemap Collider 2D is often combined with a `Composite Collider 2D`, which merges multiple tile colliders into a single more efficient shape.
