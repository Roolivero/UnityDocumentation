# Cameras

A `Camera` renders the scene and displays it on the screen.

A camera defines:

- What is visible.
- From where the scene is viewed.
- How the scene is projected.

Every scene needs at least one active camera to render anything.

Official reference: <https://docs.unity3d.com/2022.3/Documentation/Manual/CamerasOverview.html>

## Camera Transform

Like any GameObject, a camera has a Transform component.

This defines:

- `Position`: where the camera is located.
- `Rotation`: the direction the camera is facing.

In 2D projects, the camera usually looks along the `Z` axis, while objects are placed in the `XY` plane.

## Orthographic Projection

In `Orthographic` mode, objects are rendered without perspective distortion.

Objects keep the same size regardless of distance from the camera. This is the standard projection for many 2D games.

## Perspective Projection

In `Perspective` mode, objects appear smaller as they move farther away from the camera.

This simulates real-world vision and includes depth perception. It is more common in 3D games.

## Rendering in 2D

In a typical 2D setup:

- Camera projection is set to `Orthographic`.
- The camera looks toward the scene along the `Z` axis.
- Sprites are rendered based on Sorting Layers, Order in Layer, and sometimes distance from the camera.

## Camera Key Properties

Some important camera properties are:

- `Size` or `Orthographic Size`: controls how much of the scene is visible.
- `Clipping Planes`: define the near and far limits of what the camera can see.
- `Clear Flags`: define how the background is rendered.
- `Culling Mask`: defines which layers the camera renders.
- `Viewport Rect`: defines which part of the screen the camera renders to.

## Culling Mask

The `Culling Mask` determines which objects a camera renders.

It works with Unity `Layers`, not Sorting Layers.

Each GameObject belongs to a Layer, and each camera can be configured to render only specific layers.

This is useful for:

- Separating UI from gameplay.
- Rendering different elements with different cameras.
- Optimizing performance.

## Viewport Rect

The `Viewport Rect` defines the portion of the screen that a camera renders to.

It uses normalized values:

- `(X, Y)`: starting position.
- `(Width, Height)`: viewport size.

Examples:

- Full screen: `(0, 0, 1, 1)`.
- Minimap: a smaller rectangle in a corner.

This makes split-screen views and picture-in-picture effects possible.

## Clear Flags

The `Clear Flags` property defines how a camera prepares the screen before rendering.

With `Skybox` or `Solid Color`, the camera clears the screen before rendering. Skybox fills the background with a sky or environment. Solid Color fills it with a flat color.

With `Depth Only`, the camera keeps the existing image and renders on top of it. This is useful when combining multiple cameras.

Clear Flags are important when several cameras render to the same screen area.

## Rendering with Multiple Cameras

Unity can use multiple cameras in a scene to render different views or combine outputs into one final image.

Each camera can render the whole scene or only specific objects.

Unity renders cameras in order using the `Depth` property:

- Cameras with lower depth render first.
- Cameras with higher depth render on top.

This allows layered rendering and composite visuals.

## Camera and Audio

The camera is often related to how sound is perceived in the game.

This is handled through the `Audio Listener` component, which is usually attached to the Main Camera by default.

The Audio Listener acts as the ears of the scene:

- It determines how audio is heard based on the camera position and orientation.
- It processes spatial sound, including volume, distance, and direction.

Only one Audio Listener should be active in a scene at a time.
