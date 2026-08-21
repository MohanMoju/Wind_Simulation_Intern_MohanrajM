# Realistic Wind Simulation in Unity 6

## Overview

This project is a realistic outdoor environment created in Unity 6. The project includes a dynamic wind simulation system that affects environmental elements during gameplay.

The main feature is a runtime wind control system that allows the user to change wind speed, wind direction, and wind strength without restarting or reloading the scene.

---

## Features

### Realistic Environment

The environment includes:

* Terrain or ground surface
* Trees
* Grass and bushes
* Rocks and environmental props
* Skybox
* Directional sunlight
* Shadows
* Realistic lighting

---

### Dynamic Wind System

The wind system supports:

* Wind speed control
* Wind direction control
* Wind strength control
* Random wind variation
* Natural swaying movement
* Real-time environmental updates

The wind affects:

* Trees
* Leaves
* Grass
* Falling particles
* Lightweight physics objects

---

### Runtime Wind Controls

The project includes a runtime UI system.

Users can control:

* Wind Speed
* Wind Strength
* Wind Direction

Changes are applied immediately during gameplay.

The user does not need to restart the game or reload the scene.

---

## User Interface

The UI contains:

```text id="g9g6tc"
Canvas
├── SettingsButton
└── WindSettingsPanel
    ├── SpeedSlider
    ├── StrengthSlider
    ├── DirectionSlider
    └── CloseButton
```

### Controls

| Control              | Function                      |
| -------------------- | ----------------------------- |
| Wind Settings Button | Opens the wind settings panel |
| Speed Slider         | Changes wind speed            |
| Strength Slider      | Changes wind force            |
| Direction Slider     | Changes wind direction        |
| Close Button         | Closes the settings panel     |

---

## Wind System Workflow

```text id="dfxylp"
                 WIND SETTINGS UI
                         │
                         ▼
                   WIND MANAGER
                         │
        ┌────────────────┼────────────────┐
        │                │                │
        ▼                ▼                ▼
      Trees            Leaves         Physics
        │                │                │
        ▼                ▼                ▼
     Swaying       Particle Motion   Rigidbody Force
        │                │                │
        └────────────────┼────────────────┘
                         │
                         ▼
              REAL-TIME ENVIRONMENT
```

---

## Scripts

### `WindManager.cs`

Controls the main wind system.

Functions include:

* Wind speed
* Wind strength
* Wind direction
* Wind variation
* Current wind force

---

### `WindSettingsUI.cs`

Controls the runtime user interface.

Functions include:

* Opening the settings panel
* Closing the settings panel
* Changing wind speed
* Changing wind strength
* Changing wind direction

---

### `TreeSway.cs`

Controls tree movement based on the current wind.

Trees react to:

* Wind direction
* Wind strength
* Random movement variation

---

### `LeafWindController.cs`

Controls falling leaf movement.

Leaves:

* Fall using gravity
* Move according to wind direction
* React to wind strength
* Rotate while falling

---

### `WindAffectedObject.cs`

Applies wind force to lightweight Rigidbody objects.

The object requires:

* Rigidbody
* Collider

---

## Physics System

Lightweight objects are affected by the wind.

Examples:

* Small ball
* Lightweight box
* Paper object
* Physical leaves

When wind strength increases, the applied force becomes stronger.

When wind direction changes, the force direction also changes.

---

## Project Setup

### Unity Version

* Unity 6 or later

### Required Components

* Terrain
* Wind Zone
* Particle System
* Rigidbody
* Collider
* Canvas UI
* Directional Light

---

## Running the Project

1. Open the project in Unity 6.
2. Open the main scene.
3. Check the Console for errors.
4. Press the **Play** button.
5. Open the **Wind Settings** panel.
6. Adjust the wind values using the sliders.
7. Observe the changes in the environment.

---

## Problems Faced

### Settings Button Not Appearing

The Settings Button did not appear during Play Mode.

### Solution

The Canvas hierarchy and UI object activation were checked. The Settings Button and Wind Settings Panel were placed as separate children of the Canvas.

Correct structure:

```text id="7xnk8l"
Canvas
├── SettingsButton
└── WindSettingsPanel
```

The Canvas was also configured using:

```text id="dl6y1c"
Render Mode: Screen Space - Overlay
```

---

### Wind Settings Panel Hiding the Button

The following code was used:

```csharp id="69zsn1"
settingsPanel.SetActive(false);
```

If the Settings Button was placed inside the Wind Settings Panel, disabling the panel also hid the button.

### Solution

The Settings Button was placed outside the Wind Settings Panel.

---

### Incorrect Inspector Assignment

The wrong object could be assigned to the `settingsPanel` field.

Correct assignment:

```text id="3f4z1r"
Settings Panel = WindSettingsPanel
```

The Canvas and Settings Button should not be assigned to this field.

---

## Future Improvements

Possible improvements include:

* More advanced grass shaders
* Realistic tree shaders
* Cloth simulation
* Weather system
* Rain effects
* Storm simulation
* Dynamic time of day
* Improved wind gust effects
* Sound effects for wind
* Wind direction indicator

---

## Technologies Used

* Unity 6
* C#
* Unity Terrain
* Unity Wind Zone
* Unity Particle System
* Rigidbody Physics
* Unity Canvas UI

---

## Author

**Mohanraj M**

Unity Game Development Project

---
