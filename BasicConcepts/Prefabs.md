# Prefabs

A `Prefab` is a reusable GameObject template.

Instead of creating the same GameObject configuration again and again, a Prefab lets you define it once and reuse it across scenes.

A Prefab can include:

- A GameObject hierarchy.
- Components.
- Component values.
- Child objects.
- References to assets such as sprites, materials, audio clips, or scripts.

For example, an enemy Prefab can contain its sprite or mesh, collider, Rigidbody, health script, movement script, and default values. Every time that Prefab is placed in a scene, Unity creates an instance of that predefined setup.

## Prefab Asset and Prefab Instance

The `Prefab Asset` is the original reusable template stored in the project.

A `Prefab Instance` is a copy of that Prefab placed in a scene.

In short:

```text
Prefab Asset = original template
Prefab Instance = scene object created from that template
```

If the Prefab Asset is updated, its instances can receive those changes. This makes Prefabs useful for keeping repeated objects consistent.

## Overrides

A Prefab Instance can have local changes called `overrides`.

An override means that one instance is different from the original Prefab Asset.

For example, several enemies can come from the same Prefab, but one instance can have a different speed, color, or starting position.

Overrides are useful when an object should mostly follow the Prefab, but still needs small scene-specific changes.

## Why Prefabs Are Useful

Prefabs are useful for objects that appear multiple times or need a consistent setup, such as:

- Enemies.
- Projectiles.
- Pickups.
- UI panels.
- Doors.
- Obstacles.
- Environment pieces.

They also make it easier to instantiate objects at runtime from scripts, such as spawning bullets, enemies, or effects.

## 2D and 3D

Prefabs are not specific to 2D or 3D.

They can be used for any reusable object in Unity, whether it is a 2D sprite, a 3D model, a UI element, or an invisible gameplay object.
