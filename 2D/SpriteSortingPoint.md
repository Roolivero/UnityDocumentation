# Sprite Sort Point

The `Sprite Sort Point` determines which point of a sprite Unity uses to calculate its distance from the camera, and therefore its render order.

This property is available when the Sprite Renderer's `Draw Mode` is set to `Simple`.

In a 2D project, the Main Camera is usually set to `Orthographic` projection. In this mode, Unity renders sprites based on their distance to the camera along the camera viewing direction.

By default, the sort point is `Center`, meaning Unity measures distance from the camera to the center of the sprite.

The sort point can also be set to `Pivot`. In that case, Unity uses the sprite pivot as the reference point for distance calculation. This is useful when the visual base of an object, such as a character feet position, should determine render order instead of the center of the sprite.

## Related Rendering Concepts

Sorting Layers group sprites into rendering categories so Unity can decide which objects appear in front of others. Layers higher in the list are rendered above lower layers.

Within the same Sorting Layer, Unity uses `Order in Layer` to decide the order between sprites. Higher values are rendered in front of lower values.

In 2D projects, avoid relying only on object position, such as `Z` or `Y`, to control rendering order. Use Sorting Layers for broad groups and `Order in Layer` for precise ordering.

For more detail, see [Sorting Layers](SortingLayers.md).
