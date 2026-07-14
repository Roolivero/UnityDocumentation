# Physics 2D

Unity has a physics system specifically designed for 2D games. It uses separate components from the 3D physics system.

Examples:

| 3D component | 2D component |
| --- | --- |
| `Rigidbody` | `Rigidbody2D` |
| `Box Collider` | `Box Collider 2D` |
| `Hinge Joint` | `Hinge Joint 2D` |

The 2D versions are simplified, flat versions of the 3D components. For example, `Box Collider 2D` represents a rectangle, while `Box Collider` in 3D represents a cube.

To give a sprite physical behavior, it is common to combine:

- A `Rigidbody2D`, to handle movement and the physics simulation.
- A `Collider 2D`, to define the collision shape.

Official reference: <https://docs.unity3d.com/2022.3/Documentation/Manual/Physics2DReference.html>

## Rigidbody2D

A `Rigidbody2D` allows a GameObject to be controlled by Unity's 2D physics system.

The `Transform` component defines the position, rotation, and scale of a GameObject. When a `Rigidbody2D` is attached, the physics system controls the object's movement.

This means:

- The `Rigidbody2D` updates the `Transform`.
- Movement is driven by physics, such as velocity, forces, and collisions.

When using a `Rigidbody2D`, the object should be treated as a physical body inside the physics simulation.

## Collider2D

A `Collider2D` defines the physical shape of an object for collision detection.

When a Collider2D is attached to the same GameObject as a Rigidbody2D, or to one of its children:

- It becomes part of that Rigidbody2D.
- It moves together with that Rigidbody2D.
- The collider should not be moved directly.
- The Rigidbody2D should be moved instead.

Multiple colliders attached to the same Rigidbody2D act as a single compound collider and do not collide with each other.

Collisions occur between Collider2D components, not between Rigidbody2D components by themselves.

A Rigidbody2D without a Collider2D will not collide with anything.

## Transform

Every GameObject has a `Transform` component. It defines:

- `Position`: where the object is located in the scene.
- `Rotation`: the object orientation.
- `Scale`: the object size.

The Transform is the main way to control objects that are not affected by physics.

## Rigidbody2D and Transform

When a GameObject has a `Rigidbody2D`, its movement should not be controlled directly through the Transform during gameplay.

Instead of doing this:

```csharp
transform.position += new Vector3(x, y, 0);
```

Use the Rigidbody2D API:

```csharp
rb.velocity = new Vector2(x, y);
rb.AddForce(force);
rb.MovePosition(newPosition);
```

These methods make movement interact correctly with collisions, forces, and other physical behavior.

Directly modifying the Transform of a GameObject with a Rigidbody2D can cause:

- Unpredictable movement.
- Incorrect collision detection.
- Objects passing through each other.
