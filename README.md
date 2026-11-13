# Sprite Flight

A small 2D arcade game built in Unity: pilot a pirate ship across the ocean, steer with the mouse, and survive as long as you can while spinning obstacles drift through the arena. Your score is how long you last.

**▶ [Play it in your browser](https://play.unity.com/en/games/8d4b0741-8674-48bb-8dfe-07e3de2a197f/sprite-flight-scurvy-edition)** (Scurvy Edition on Unity Play)

![Unity](https://img.shields.io/badge/Unity-6000.3-000000?logo=unity&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?logo=csharp&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-2D_%7C_WebGL-blue)

## Gameplay

- **Hold the left mouse button** to rotate the ship towards the cursor and thrust in that direction.
- **Avoid the obstacles.** Each one spawns with a random size, speed, direction and spin. Smaller ones move faster.
- **Score** grows for every second you survive.
- **Any collision ends the run** with an explosion and a Restart button.

## Technical notes

| Area | Implementation |
|---|---|
| Engine | Unity 6 (`6000.3.22f1`), 2D URP template |
| Movement | `Rigidbody2D` physics: the player applies a force toward the mouse position each frame (`PlayerController.cs`) |
| Obstacles | Randomised scale, velocity and torque at start-up; speed is scaled inversely with size so small objects feel quicker (`Obstacle.cs`) |
| Input | Unity Input System (`Mouse.current`) |
| UI | UI Toolkit (`UIDocument`) for the score label and restart button, wired up in code |
| Feedback | Explosion prefab, bouncy `PhysicsMaterial2D`, background music and sound effects |

## Run it

**In the editor**

1. Install Unity **6000.3.22f1** (or a compatible Unity 6.3 version) through Unity Hub.
2. Open this folder as a project.
3. Open `Assets/Scenes/Game.unity` and press **Play**.

**WebGL build**

The easiest way to play is the [online version on Unity Play](https://play.unity.com/en/games/8d4b0741-8674-48bb-8dfe-07e3de2a197f/sprite-flight-scurvy-edition). A WebGL build is also included in [`Web Build/`](Web%20Build/) (zipped as `Web Build.zip`). It uses Brotli compression, so it has to be hosted by a server that sends `Content-Encoding: br`, such as itch.io or Unity Play. Opening `index.html` directly from disk won't work.

## Project structure

```
Assets/
├── Scenes/Game.unity        # the playable scene
├── Scripts/
│   ├── PlayerController.cs  # thrust, scoring, game-over and restart
│   └── Obstacle.cs          # randomised size, speed and spin
├── Prefabs/                 # Obstacle, ExplosionEffect
├── Materials/               # bouncy 2D physics material
├── Sprites/ Audio/
Web Build/                   # WebGL export
```
