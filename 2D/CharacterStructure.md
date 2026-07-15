# 2D Character Structure

A 2D character in Unity is usually built as a root GameObject with several child GameObjects that separate responsibilities.

This is not a mandatory Unity structure, but it is a common way to keep the character easier to modify and extend.

Example:

```text
Player
├── Visual
├── GroundCheck
├── WallCheck
├── Feet
├── AttackPoint
└── Effects
```

## Root Object

The root object represents the character as a whole.

It usually contains the main gameplay components, such as:

- `Rigidbody2D`
- Movement scripts
- Jump scripts
- State scripts
- Health or damage scripts

In Unity, a `Rigidbody2D` lets a GameObject be controlled by the 2D physics system. Collider 2D components on the same GameObject, or on child GameObjects, are implicitly attached to that Rigidbody2D and move with it.

This means a character can have one Rigidbody2D on the root object and several Collider2D components on children.

Official reference: <https://docs.unity3d.com/Manual/class-Rigidbody2D.html>

## Visual Object

The visual child contains the component that displays the character, usually a `Sprite Renderer`.

Separating the visual object from the root object is useful because the sprite can be changed without changing the physical body.

For example, the visual object can be used to:

- Flip the character when it changes direction.
- Change animations.
- Hide or show the character.
- Apply visual effects.
- Replace the character sprite without modifying colliders or physics.

The visual object should not necessarily define the physical shape of the character. The collider should match the playable body, not every detail of the drawing.

## Physical Colliders

Physical colliders define the solid body of the character.

When `Is Trigger` is disabled, a Collider2D participates in physical collision response. This means it can block or be blocked by other colliders.

Examples:

- Character body
- Walls
- Floors
- Platforms
- Obstacles

Official reference: <https://docs.unity3d.com/Manual/class-BoxCollider2D.html>

## Triggers and Sensors

When `Is Trigger` is enabled, the collider is used for detection instead of solid physical collision.

A trigger can detect overlaps, but it does not block movement.

Triggers are useful for:

- Ground detection
- Wall detection
- Attack areas
- Hurtboxes
- Interaction zones
- Collectable detection

## GroundCheck

`GroundCheck` is usually a small sensor placed near the bottom of the character.

Its purpose is to detect whether the character is touching ground.

This information can be used to decide:

- If the character can jump.
- If the character is falling.
- If a landing effect should play.
- Which animation state should be active.

Ground detection often uses a `LayerMask` so the script checks only objects that belong to a ground-related Layer.

For example:

```text
GroundCheck + Ground Layer = detect only floor/platform objects
```

## Feet

`Feet` is usually a small trigger placed near the bottom of the character.

While `GroundCheck` is often used by the character to know its own state, `Feet` can be used so other objects know they were touched by the character's feet.

For example:

- An enemy can detect that the player landed on it.
- A spring platform can detect that the player stepped on it.
- A breakable object can detect impact from above.

In short:

```text
GroundCheck = the character checks if it is grounded
Feet = other objects can identify foot contact
```

This is a project convention, not a special Unity component. The exact behavior depends on the scripts attached to the character and the other objects.

## WallCheck or WallSlide

A `WallCheck` or `WallSlide` child can be used to detect or manage contact with walls.

Depending on the project, it might be:

- A trigger used only to detect nearby walls.
- A physical collider used as part of the character body.
- A helper object referenced by wall slide or wall jump scripts.

The name alone does not define the behavior. The actual behavior depends on its components and scripts.

## AttackPoint

An `AttackPoint` is usually an empty child object that marks where an attack begins.

For example, a script can use this point as the center of an attack range, the origin of a projectile, or the position where an effect appears.

## Effects

An `Effects` child can group particles, sounds, or visual effects related to the character.

Examples:

- Landing dust
- Jump effect
- Damage effect
- Footstep particles

## Tags and Layers

`Tags` are used to identify GameObjects from scripts.

For example, objects can be tagged as:

- `Player`
- `Enemy`
- `Ground`
- `Collectable`
- `Feet`

Official reference: <https://docs.unity3d.com/Manual/Tags.html>

`Layers` are used to classify GameObjects for systems such as physics, cameras, raycasts, and filtering.

For example, a GroundCheck script can use a LayerMask to detect only objects on the `Ground` layer.

Official reference: <https://docs.unity3d.com/Manual/Layers.html>

For the difference between Layers and Sorting Layers, see [Layers and Sorting Layers](../BasicConcepts/LayersAndSortingLayers.md).

## Practical Rule

A clean 2D character structure usually separates:

- Root object: movement, physics, and main logic.
- Visual object: sprite and animation.
- Physical colliders: solid body.
- Triggers: sensors and detection areas.
- Helper points: attack origins, interaction points, and effect positions.

This keeps the character easier to debug, reuse, and turn into a [Prefab](../BasicConcepts/Prefabs.md).
