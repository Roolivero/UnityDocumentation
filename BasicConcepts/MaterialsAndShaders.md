# Materials and Shaders

Materials and shaders define the appearance of surfaces in Unity.

A `shader` is a program that tells the GPU how to render an object, including lighting, color, transparency, and other visual effects.

A `material` is a container that uses a shader and defines its parameters, such as color, textures, and other visual properties.

A renderer, such as a Sprite Renderer or Mesh Renderer, uses a material. The material uses a shader to determine how the object is drawn on screen.

For most 2D games, Unity provides default materials and shaders. Custom shaders are usually only needed when a project needs custom visual effects.

Official reference: <https://docs.unity3d.com/Manual/Materials.html>

## Materials and Lighting

Lighting only affects objects if their material uses a shader that supports lighting.

Not all objects react to lights by default. Their appearance depends on the shader assigned to the material.

## Lit vs Unlit Materials

| Material type | Behavior |
| --- | --- |
| `Lit` | Reacts to light sources, shows shading, highlights, and shadows. Used mainly in 3D scenes or 2D projects with lighting. |
| `Unlit` | Does not react to light and keeps the same color and brightness. Common in simple 2D games. |

## Sprites and 2D Lighting

In 2D projects, sprites can either react to lighting or remain unaffected depending on the shader used by their material.

By default, sprites use an unlit shader, so they are not affected by lights.

To enable 2D lighting, sprites must use a lit shader such as `Sprite-Lit-Default` and a compatible rendering pipeline, usually URP with 2D Lights.

Existing sprites or materials may need to be upgraded when switching to a 2D lighting workflow.

Official 2D lighting reference: <https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@10.0/manual/Lights-2D-intro.html>
