# Lighting

Lighting changes how objects are rendered by affecting brightness, shading, shadows, color, and visibility.

Unity provides different light types, mainly used in 3D scenes:

- `Directional Light`: simulates light from a distant source. Rays are parallel and affect the whole scene.
- `Point Light`: emits light in all directions from a point.
- `Spot Light`: emits light in a cone.

In most 2D projects, lighting is either not used, or it is handled through 2D lighting systems such as URP 2D Lights.

By default, sprites use simple shaders that do not react to lighting.

Official 2D lighting reference: <https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@10.0/manual/Lights-2D-intro.html>

## Lighting and Materials

Lighting affects objects only if their material uses a shader that supports lighting.

Not all objects react to lights by default. Their appearance depends on the shader assigned to the material.

For more detail, see [Materials and Shaders](MaterialsAndShaders.md).

## Sprites and 2D Lighting

In 2D projects, sprites can either react to lighting or remain unaffected depending on the shader used by their material.

By default, sprites use an unlit shader, so they are not affected by lights.

To enable 2D lighting, sprites must use a lit shader such as `Sprite-Lit-Default` and a compatible rendering pipeline, usually URP with 2D Lights.

Existing sprites or materials may need to be upgraded when switching to a 2D lighting workflow.

## Shadows

Shadows are created when objects block light.

Unity allows shadows to be enabled or disabled per light and adjusted in quality and distance.

Shadows can improve depth perception and realism.
