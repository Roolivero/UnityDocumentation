# Animations

Unity's current animation system is usually referred to as `Mecanim`.

It is built around a few main pieces:

- `Animation Clip`
- `Animator Controller`
- `Animator` component
- `Animator Window`
- `Animation Window`

Unity also has a Legacy Animation system, but Unity's current animation system is recommended in most situations, especially when animations need transitions, blending, state machines, or more complex behavior.

Official reference: <https://docs.unity.cn/Manual/AnimationOverview.html>

## Animation Clip

An `Animation Clip` contains animation data.

It describes how an object or one of its properties changes over time.

For example, an Animation Clip can represent:

- Idle
- Walk
- Run
- Jump
- Attack
- Door opening
- UI panel fade

An Animation Clip can be created inside Unity or imported from external tools.

In short:

```text
Animation Clip = one animation sequence
```

## Animator Controller

An `Animator Controller` is an asset that organizes Animation Clips and controls how the object changes from one animation to another.

It works like a state machine.

For example, a character Animator Controller might contain states such as:

- Idle
- Run
- Jump
- Fall
- Attack

Transitions define when the Animator can move from one state to another. 

Official reference: <https://docs.unity3d.com/Manual/class-AnimatorController.html>

In short:

```text
Animator Controller = state machine that controls animation flow
```

## Animator Component

The `Animator` component is added to the GameObject that should be animated.

It references an Animator Controller. At runtime, it uses that controller to decide which Animation Clip should play.

In short:

```text
Animator component = component on the GameObject
Animator Controller = asset that defines the animation logic
Animation Clip = actual animation data
```

## States and Transitions

Inside an Animator Controller, each animation is usually represented as a state.

A `Transition` connects one state to another.

For example:

```text
Idle -> Run
Run -> Jump
Jump -> Fall
Fall -> Idle
```

Transitions can be controlled by conditions, often through Animator parameters.

## Parameters

Animator parameters are values used by the Animator Controller to decide when transitions should happen.

Common parameter types include:

- `Float`
- `Int`
- `Bool`
- `Trigger`

For example:

```text
speed > 0 = transition from Idle to Run
isGrounded == false = transition from Run to Jump or Fall
attack trigger = transition to Attack
```

## Animation Window and Animator Window

The `Animation Window` is used to create and edit Animation Clips.

The `Animator Window` is used to edit the Animator Controller, states, transitions, and parameters.

In short:

```text
Animation Window = edit the clip
Animator Window = edit the state machine
```

## General Workflow

A common workflow is:

1. Create or import Animation Clips.
2. Create an Animator Controller.
3. Add the Animation Clips as states.
4. Add transitions between states.
5. Add an Animator component to the GameObject.
6. Assign the Animator Controller to the Animator component.
7. Control Animator parameters from scripts or gameplay events.

## 2D and 3D

The animation system is not only for 3D characters.

It can animate:

- 2D sprites
- 3D models
- UI elements
- Lights
- Cameras
- Any animatable GameObject property

For 2D-specific animation workflows, see [2D Animations](../2D/2DAnimations.md).
