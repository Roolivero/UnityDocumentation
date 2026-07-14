# Audio

Unity's audio system is based on a simple model:

- `Audio Source` components emit sound.
- A single `Audio Listener` receives sound.

Audio can be processed as 2D or 3D sound.

Official reference: <https://docs.unity3d.com/2022.3/Documentation/Manual/AudioOverview.html>

## Audio Listener

The `Audio Listener` is usually attached to the Main Camera by default.

It acts as the ears of the scene:

- It determines how audio is heard based on position and orientation.
- It processes spatial sound, including volume, distance, and direction.

Only one Audio Listener should be active in a scene at a time.

## Audio Clip

An `Audio Clip` is the actual sound file used by an Audio Source, such as `.wav` or `.mp3`.

It defines the audio data that will be played.

## Audio Source

An `Audio Source` plays sound in a Unity scene.

It uses an Audio Clip and controls how and when that clip is played.

An Audio Source can be attached to any GameObject. Often, it is attached to the object that produces the sound, such as a player, spaceship, enemy, or temporary effect.

Unity supports:

- `2D audio`: not affected by position or distance.
- `3D audio`: changes based on distance and direction relative to the Audio Listener.

This behavior is controlled with the `Spatial Blend` property.

## Volume and Mixing

Audio Mixers can group sounds and control audio levels.

They can be used for:

- Music.
- Sound effects.
- UI sounds.
- Effects processing.
