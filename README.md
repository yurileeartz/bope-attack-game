# 💀 Bope Attack - Special Edition

A 2D top-down tactical survival shooter developed entirely in Python. .

<br>

![Bope Attack Gameplay](bopeattackGIF.gif)

In this project, the player takes on the role of a tactical operator with the objective of clearing areas dominated by criminals. The game features level progression, boss fights, and dynamic difficulty mechanics.

> 🎮 **Want to play?** Go to the [Releases](../../releases) tab of this repository, download the `.zip` file, extract it, and run the game! 

*(Note: The source code for this project is kept private due to commercialization plans and image usage rights, but the architecture and technical solutions are documented below).*

<br>

### 🖥️ Tech Stack & Tools
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pygame](https://img.shields.io/badge/pygame-ED2024?style=for-the-badge&logo=python&logoColor=white)
![Adobe Photoshop](https://img.shields.io/badge/adobe%20photoshop-%2331A8FF.svg?style=for-the-badge&logo=adobe%20photoshop&logoColor=white)
![CorelDraw](https://img.shields.io/badge/CorelDraw-00A859?style=for-the-badge&logo=Corel&logoColor=white)

<br>

## 🛠️ Technical Features & Architecture

* **Modular State Machine (AI):** Engineered a custom Finite State Machine (FSM) to control enemy AI behaviors, managing smooth transitions between patrolling, tracking, and engaging the player.
* **Sprite Sheet Animation Pipeline:** Developed an efficient sprite-cutting logic to parse and cache animation frames into Pygame surfaces, reducing runtime CPU overhead.
* **Collision Matrix Optimization:** Implemented strict box-collision layers to accurately detect bullet impacts, environmental boundaries, and player health damage grids without dropping frame rates.
* **Persistent Scoring & State:** Integrated local data management to store high scores, player progress, and custom session settings.

---

## ⚙️ Tech Stack

* **Python 3.x:** The core programming language of the project.
* **Pygame:** Graphic engine used for 2D rendering, FPS control, event handling (keyboard/mouse), collision detection (hitboxes), and the sound/music system.
* **OpenCV (cv2):** Integrated for decoding and displaying video intros and credits directly on the Pygame screen.
* **Vector Mathematics (math):** Trigonometry and hypotenuse calculations for projectile physics, allowing enemies and grenades to follow the X and Y axes of the mouse or player.

---

## 🧠 Architecture and Technical Solutions

The game was built using **Object-Oriented Programming (OOP)**, ensuring clean and scalable code. The main game entities operate independently:

* **State Machine:** A robust system that controls the application flow (Intro Video -> Menu -> Options -> Gameplay -> Game Over/Victory), rendering only what is necessary for each screen state.
* **Class System:** * `Player`: Manages health, movement (WASD or Arrows), finite ammunition (grenades), and animation cooldowns.
  * `Enemy` & `Boss`: Simple AI based on vector tracking (`math.hypot`) to chase the player, featuring specific shooting cooldowns.
  * `Bullet` & `Grenade`: Ballistic trajectory calculations. For grenades, an "Area of Effect" (AoE) damage system was implemented using collision rectangle inflation (`rect.inflate`).
* **Dynamic Difficulty (Hard Mode):** A state variable that scales entity spawning in the main loop, doubling the enemy load based on the current level.
* **Asset Management:** A custom `Fallback` system (Try/Except) for image loading. If an asset fails to load, the game doesn't crash; instead, it renders a "pink square" placeholder for visual debugging.

---

## 🎯 Game Features

* Customizable controls (WASD or Arrows).
* "Hard" Mode with double enemy spawn rates.
* 7 Progressive levels with dynamic changing backgrounds.
* 2 Boss Fights with health bars and custom AI mechanics.
* **Unlockable Content:** Secret characters and skins (Mascot) unlocked via state change after beating the main campaign.
