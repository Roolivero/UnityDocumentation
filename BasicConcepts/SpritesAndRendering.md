# Sprites and Rendering

Graphic objects in 2D are known as sprites. A sprite is a texture that Unity renders in a scene through a `Sprite Renderer` component.

Unity provides a built-in Sprite Editor for working with sprite textures, especially when a single image contains multiple sprite elements.

Official reference: <https://docs.unity3d.com/2022.3/Documentation/Manual/Sprites.html>

## Sprite Editor

Before using the Sprite Editor, make sure the texture has `Texture Type` set to `Sprite (2D and UI)`.

If the texture contains multiple visual elements, set `Sprite Mode` to `Multiple` in the Inspector.

The Sprite Editor can identify sprite regions manually. Clicking on the image creates a rectangular selection area with handles in the corners. The `Trim` button resizes the selected sprite rectangle so that it fits tightly around the visible graphic, based on transparency.

Borders are supported for the UI system, but not for the 2D `Sprite Renderer` system.

## Sprite Renderer

The `Sprite Renderer` component renders a sprite and controls how it appears visually in the scene.

It is commonly used for 2D objects, but it can also be used in 3D projects when a flat sprite needs to be rendered in world space.

## Sorting Layers and Order in Layer

Sorting Layers group sprites into rendering categories so Unity can decide which objects appear in front of others. Layers higher in the list are rendered above lower layers.

Common Sorting Layers include:

- `Background`
- `Environment`
- `Player`
- `UI`

Within the same Sorting Layer, Unity uses `Order in Layer` to decide the order between sprites. Higher values are rendered in front of lower values.

In 2D projects, avoid relying only on object position, such as `Z` or `Y`, to control rendering order. Use Sorting Layers for broad groups and `Order in Layer` for precise ordering.

Incorrect Sorting Layer configuration can cause sprites to overlap incorrectly, objects to appear behind others, or UI elements to mix with game objects.

## Related Topic

For the difference between `Center` and `Pivot` when sorting sprites, see [Sprite Sort Point](SpriteSortingPoint.md).
