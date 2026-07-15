# Sorting Layers

Sorting Layers control the visual order of sprites and 2D renderers.

They are different from regular Unity `Layers`. Regular Layers are used by systems such as cameras, physics, raycasts, and filtering. Sorting Layers are used to decide which sprite appears in front of another.

For the general comparison, see [Layers and Sorting Layers](../BasicConcepts/LayersAndSortingLayers.md).

## Sorting Layers and Order in Layer

Sorting Layers group sprites into rendering categories. Layers higher in the list are rendered above lower layers.

Common Sorting Layers include:

- `Background`
- `Environment`
- `Player`
- `UI`

Within the same Sorting Layer, Unity uses `Order in Layer` to decide the rendering order between sprites.

Objects with higher `Order in Layer` values are rendered in front of objects with lower values.

## Why Not Use Position Only?

In 2D projects, avoid relying only on object position, such as `Z` or `Y`, to control rendering order.

Use Sorting Layers for broad visual groups and `Order in Layer` for precise ordering.

Incorrect configuration can cause:

- Sprites to overlap incorrectly.
- Objects to appear behind other objects.
- UI elements to mix visually with game objects.

## Example

```text
Background      Order in Layer: 0
Environment     Order in Layer: 0
Player          Order in Layer: 5
UI              Order in Layer: 10
```

This makes the background render behind the level, the player render above the environment, and the UI render above gameplay sprites.
