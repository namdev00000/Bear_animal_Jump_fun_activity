# Bear Stair Jump 🐻🧗‍♂️

A fun, interactive, and physics-driven browser game where a cartoon bear climbs a staircase to reach a surprise at the top. Built entirely with Vanilla JavaScript, HTML, and CSS—no external libraries, images, or audio files required.

---

## 🎮 How to Play

Help the bear reach the 15th step to trigger the final celebration! Use your keyboard to control the bear's movements.

| Key | Action |
| :--- | :--- |
| **Spacebar / Right Arrow** | Jump up one stair |
| **Left Arrow** | Jump down one stair |
| **Up Arrow** | Jump up and land on the same stair |
| **Down Arrow** | Sit down to rest |
| **F** | *Ouch!* Collapse and fall back to the bottom |
| **Enter** | Restart the game (only works on the game-over screen) |

---

## ✨ Features

* **Custom Physics Engine:** The jumping arc is calculated using a mathematical sine wave within a `requestAnimationFrame` loop to create realistic gravity.
* **Dynamic Day/Night Cycle:** As the bear climbs higher, the background window transitions smoothly from a dark starry night to a bright sunny day.
* **Synthesized Audio:** All sound effects (jumping, falling, cat meows, fireworks, and celebration music) are generated in real-time using the browser's native Web Audio API. No `.mp3` files needed.
* **Interactive SVG Graphics:** The bear and cat are drawn completely with code (SVG). The bear's mouth, head angle, and arms react dynamically to jumping and sitting states.
* **Hidden Surprises:** * Keep an eye out for a mouse that scurries across the floor every 4 steps.
    * A cat pops out of the cardboard boxes at the end to congratulate you!
* **Dynamic Motivations:** Floating text encourages the player with a new phrase after every successful step upward.

---

## 🛠️ Code Patterns & Dependencies

If you want to look under the hood or modify the code, here is how the core systems connect:

* **The State Machine Pattern:** The entire game relies on the `currentStair` variable. Every function checks this number. 
    * *Dependency:* The Day/Night colors and the Sun/Moon positions calculate their CSS locations based on `currentStair / totalStairs` (progress percentage).
* **The Fall-Through Switch:** The keyboard event listener uses a `switch` statement. The `Space` and `ArrowRight` cases are stacked together.
    * *Dependency:* This tells the JavaScript engine to funnel both key presses into the exact same climbing function without duplicating code.
* **CSS Class Toggling:** Instead of animating the bear's body parts with heavy JavaScript, the JS simply adds a class like `.jumping` or `.sitting` to the main SVG wrapper.
    * *Dependency:* The CSS file watches for those specific classes and automatically applies transformations (like rotating the arms 130 degrees or squishing the body to sit).
* **Modulo Operator Trigger:** The mouse animation relies on the modulo mathematical operator (`currentStair % 4 === 0`). 
    * *Dependency:* Whenever the current stair divides evenly by 4 with zero remainder, the code forces the HTML to reload the mouse's CSS animation.

---

## 🚀 Installation & Usage

1. Download or copy the `index.html` file.
2. Double-click the file to open it in any modern web browser (Chrome, Firefox, Safari, Edge).
3. Make sure your browser allows audio to play, click the **Sound: ON** button if needed, and start jumping!
