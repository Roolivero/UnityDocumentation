# 2D Animations

2D animation in Unity usually uses the same general animation system described in [Animations](../BasicConcepts/Animations.md), but the animated visual elements are sprites.

There are two common 2D animation approaches:

- Sprite frame animation.
- Skeletal sprite animation with the 2D Animation package.

Official 2D overview: <https://docs.unity.cn/Manual/Unity2D.html>

## Sprite Frame Animation

Sprite frame animation uses multiple sprites shown one after another.

This is similar to traditional frame-by-frame animation.

For example, a walk animation might use several sprites:

```text
Walk_01 -> Walk_02 -> Walk_03 -> Walk_04
```

Unity stores that sequence in an `Animation Clip`, and the `Animator Controller` decides when that clip should play.

This approach is common for:

- Idle animations
- Walking
- Running
- Attacks
- Effects
- Enemies

## Sprite Sheets

A sprite sheet is a single image that contains multiple sprites.

After importing a sprite sheet, Unity can slice it into individual sprites. Those sprites can then be used to create Animation Clips.

This workflow is useful because many frames of animation can be kept inside one texture asset.

## Animator for 2D Characters

A 2D character usually has an `Animator` component on the character or on its visual child object.

The Animator Controller can contain states such as:

- Idle
- Run
- Jump
- Fall
- Attack
- Hurt

Gameplay scripts can update Animator parameters based on movement, grounded state, attack input, or damage state.

Example:

```text
speed > 0 = play Run
speed == 0 = play Idle
isGrounded == false = play Jump or Fall
attack trigger = play Attack
```

## Skeletal 2D Animation

Unity's `2D Animation` package supports skeletal animation for sprites.

Instead of swapping entire sprite frames, a sprite can be rigged with bones and deformed over time.

The package includes tools such as:

- Skinning Editor
- Bones
- Sprite geometry
- Weights
- Sprite Skin component

Official package reference: <https://docs.unity.cn/Packages/com.unity.2d.animation@latest/index.html>

## Skinning Editor

The `Skinning Editor` is available in the Sprite Editor when the 2D Animation package is installed.

It is used to:

- Create bones.
- Generate or edit sprite geometry.
- Assign weights.
- Define which bones influence each part of the sprite.

Official reference: <https://docs.unity.cn/Packages/com.unity.2d.animation@latest/index.html?subfolder=%2Fmanual%2FSkinningEditor.html>

## Sprite Skin Component

The `Sprite Skin` component is required when bones need to deform a sprite in the scene.

It works with a `Sprite Renderer` and uses GameObject Transforms as bones to deform the sprite mesh.

Official reference: <https://docs.unity.cn/Packages/com.unity.2d.animation@10.0/manual/SpriteSkin.html>

In short:

```text
Sprite Renderer = displays the sprite
Sprite Skin = deforms the sprite using bones
Animator = plays animation clips
Animator Controller = controls animation state transitions
```

## Choosing an Approach

Use sprite frame animation when the animation is based on separate drawn frames.

Use skeletal 2D animation when the character or object is built from parts that should bend, rotate, or deform through bones.

Frame animation is often simpler and works well for pixel art or hand-drawn frame sequences.

Skeletal animation can be useful when reusing the same artwork for many poses or when smoother deformation is needed.
