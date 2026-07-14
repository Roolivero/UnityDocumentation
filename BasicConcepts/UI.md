# UI

The User Interface system is used to create elements the player interacts with or sees on screen, such as menus, buttons, scores, and health bars.

UI elements are usually not part of the game world. They are displayed on top of it.

## UI Systems in Unity

Unity provides three UI systems:

| System | Use |
| --- | --- |
| `UI Toolkit` | Modern UI system based on UXML and USS. Common for editor tools and newer runtime UI. |
| `Unity UI (uGUI)` | Standard GameObject-based UI system for in-game interfaces. Uses Canvas, Image, Button, and related components. |
| `IMGUI` | Older immediate-mode system mainly used for debugging and editor scripting. Not recommended for in-game UI. |

Official reference: <https://docs.unity3d.com/Packages/com.unity.ugui@2.5/manual/index.html>

## Canvas

All Unity UI elements must be placed inside a `Canvas`.

The Canvas is the container that controls how UI elements are rendered and displayed.

Without a Canvas, UI elements will not be visible.

## Canvas Render Modes

Unity provides different ways to render UI through the Canvas.

| Render mode | Behavior |
| --- | --- |
| `Screen Space - Overlay` | UI is rendered directly on the screen, does not depend on a camera, and appears on top. Common for menus and HUD. |
| `Screen Space - Camera` | UI is rendered through a specific camera. Useful when mixing UI with camera effects. |
| `World Space` | UI behaves like a regular object in the scene. Used for in-game UI such as labels above enemies. |

## UI Elements

Common UI components include:

- `Text` / `TextMeshPro`: displays text.
- `Image`: displays graphics.
- `Button`: creates an interactive element.
- `Slider`: adjusts values such as volume or health.

These elements are children of the Canvas.

## Interaction

UI elements can respond to player input such as clicks, touches, and keyboard input.

This is handled through Unity's event system.
