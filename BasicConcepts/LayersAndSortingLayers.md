# Layers and Sorting Layers

Unity has two concepts with similar names but different responsibilities: `Layers` and `Sorting Layers`.

## Layers

`Layers` are general-purpose categories assigned to GameObjects.

They are used by several Unity systems, such as:

- Cameras.
- Physics.
- Raycasts.
- Collision filtering.
- Scene organization.

For example, a camera can use its `Culling Mask` to render only specific Layers. A raycast can also be configured to detect only objects in certain Layers.

In short:

```text
Layer = general GameObject category used by engine systems
```

## Sorting Layers

`Sorting Layers` are used by renderers, especially in 2D projects, to decide what appears in front of what.

They do not control physics, raycasts, or camera visibility in the same way regular Layers do.

In short:

```text
Sorting Layer = visual rendering order for sprites and 2D objects
```

## Main Difference

| Concept | Main use |
| --- | --- |
| `Layer` | Logic, physics, cameras, raycasts, filtering. |
| `Sorting Layer` | Visual order of sprites and 2D renderers. |

For 2D-specific rendering examples, see [Sorting Layers](../2D/SortingLayers.md).
