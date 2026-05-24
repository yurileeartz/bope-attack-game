# 💀 Bope Attack - Special Edition

A 2D top-down tactical survival shooter developed entirely in Python. .

<br>

![Bope Attack Gameplay](bopeattackGIF.gif)

In this project, the player takes on the role of a tactical operator with the objective of clearing areas dominated by criminals. The game features level progression, boss fights, and dynamic difficulty mechanics.

> 🎮 **Want to play?** Go to the [Releases](../../releases) tab of this repository, download the `.zip` file, extract it, and run the game! 

*(Note: The source code for this project is kept private due to commercialization plans and image usage rights, but the architecture and technical solutions are documented below).*

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
