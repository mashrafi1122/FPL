# 🚀 FPL Test: Frame Per Layer Performance Benchmark

**FPL Test** is a sleek, browser-based performance and stress testing tool designed to measure the **rendering capability and stability** of any device's browser by dynamically spawning and animating a growing number of objects (balls) until the frame rate drops to a critically low level.

Created and Maintained by **Sliz®**.



---

## ✨ Features

* **Dynamic Stress Testing:** Continuously spawns physics-simulated objects upon user input (click-and-hold/touch-and-hold).
* **Real-time FPS Tracking:** Displays current, maximum (Max), and minimum (Min) Frame Per Second metrics in a clean overlay.
* **Automatic Test Termination:** The test automatically concludes when the FPS drops to **1 FPS or lower for 5 consecutive seconds**, indicating the device's maximum rendering load.
* **Detailed Results Modal:** Presents the final performance metrics, including the crucial **Total Balls** rendered and **Average FPS**.
* **Device Comparison:** Offers insights into similar-performing devices and a global **Leaderboard** based on successful `Total Balls` count.
* **Responsive Design:** Optimized for both desktop (mouse input) and mobile (touch input) devices.
* **Minimalist & Modern UI:** Utilizes a gradient background, glassmorphism in UI panels, and subtle glow effects for the animated objects.

---

## 💻 Technical Overview

The FPL Test is a single-file application built entirely with **HTML, CSS, and vanilla JavaScript**.

### Core Technologies

| Technology | Purpose |
| :--- | :--- |
| **HTML5** | Structure and UI element scaffolding. |
| **CSS3** | Modern styling, gradients, glassmorphism effects, and responsiveness. |
| **Vanilla JavaScript** | Core logic, animation loop, physics simulation, and DOM manipulation. |
| **Canvas API** | High-performance rendering of the animated balls and their trails. |

### Key Logic

1.  **`Ball` Class:** Defines each object with properties for position (`x`, `y`), velocity (`vx`, `vy`), radius, and a `trail` array for visual effects.
2.  **Physics Simulation:** In the `Ball.update()` method, basic physics are applied:
    * Velocity is added to position: `this.x += this.vx; this.y += this.vy;`
    * Boundary collision detection reverses and dampens velocity: `this.vx *= -0.95;`
    * Friction/Damping is applied: `this.vx *= 0.99; this.vy *= 0.99;`
3.  **Animation Loop:** The `animate()` function uses `requestAnimationFrame` for optimal, browser-managed frame pacing.
    * It calculates the **current FPS** using `performance.now()` (`const currentFps = Math.round(1000 / delta);`).
    * It updates the FPS statistics (`minFps`, `maxFps`, `fpsSum`).
4.  **Stress Trigger:** The `startHolding()` function is activated on mouse-down or touch-start. It uses `setInterval` to continuously call `spawnBalls()`, increasing the batch size as `totalSpawned` grows to accelerate the stress test.
5.  **Termination Condition:** The `animate()` function monitors for `fps <= 1` for a duration of **5000 milliseconds (5 seconds)**. If this condition is met, the `endTest()` function is called, locking the current `balls.length` as the final performance score.

---

## 🛠️ Usage

This is a closed source project but it is useful for using and testing your device.

You can also try it out and **check your device on the website**:

- [**Frames Per Layer**](https://fpl.pp.ua)

## Running the Test

1.  **Initial State:** The test starts with a clean canvas and the UI displaying default values (`-- FPS`).
2.  **Start the Test:**
    * **Desktop:** **Hold down the Left Mouse Button (LMB)** on the blue/purple area.
    * **Mobile:** **Hold down your finger** on the screen.
    * *(Hint: After 3 clicks without holding, a hint message will appear.)*
3.  **Observation:** Watch the `FPS Display` and the `White: [Ball Count]` increase. The `Min FPS` is a key indicator of rendering strain.
4.  **Test Completion:** The test will automatically stop when the device can no longer maintain a reasonable frame rate (1 FPS for 5s). A modal with the **Test Complete** results will appear.
5.  **Analyze & Compare:** Review your results, especially the **Total Balls** score, and compare your device's performance against others in the **Devices** section.

### Warning!

To get the **results**, **just wait**. On your **computer or phone**, hold down the screen and **don't let go until the statistics appear**.

---

## ⚙️ Project Structure

This project consists of a single file:

└── index.html


* **`index.html`:** Contains all the HTML structure, CSS styling, and JavaScript logic for the FPL Test.

---

## 🛡️ License

This project is licensed under a **Custom Proprietary License** by **Sliz®**.

This software is the proprietary and confidential property of **Sliz®** ("the Company"). No part of this project, including but not limited to the source code, design, and accompanying documentation, may be used, reproduced, distributed, or modified without the express written permission of the Company.

**Copyright (c) 2025 Sliz®**

---

## 📧 Contact

For support, partnership inquiries, or licensing questions, please contact the creators:

**Sliz®** - *Innovating at the intersection of performance and visual stress testing.*
