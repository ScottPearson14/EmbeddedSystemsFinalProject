# Reaction Timer Game (AVR + OLED + RGB LED)


This is an interactive reaction-based game developed for the ATmega328P microcontroller using C. The game features a colorful UI on an SSD1306 OLED display, RGB LED feedback, difficulty selection, reaction timing, and EEPROM-stored high scores.


## 🕹️ Game Overview


The game challenges players to react to a green light as quickly as possible. Players go through **5 rounds**, with each round randomly starting after a delay. Pressing the button **too early** (while the light is red) ends the game immediately.


### 🎮 Game Flow


1. **Welcome Screen** – Rainbow LED animation; press button to start.

2. **Difficulty Selection** – Press to cycle through Easy, Medium, and Hard; hold button to confirm.

3. **Countdown Phase** – Wait for the red light to turn green.

4. **Reaction Phase** – Press the button as fast as possible once the LED turns green.

5. **Results Phase** – Shows your reaction time and a comment.

6. **Final Score** – Average time shown after 5 rounds + placeholder for top 3 scores.


## 📦 Features


- **Interrupt-driven button input**

- **Difficulty selector** (Easy: 5s, Medium: 2.5s, Hard: 1s reaction window)

- **OLED screen feedback** (round status, reaction time, progress bars)

- **RGB LED feedback** for visual indication (Red = wait, Green = go, Blue = results)

- **Buzzer alert** if button is pressed too early

- **Top 3 scores** (EEPROM placeholder shown; implementation pending)

- **Hold to Restart** functionality after game ends

- **EEPROM** read/write for saving top 3 reaction times


## 🔧 Hardware Requirements


- ATmega328P microcontroller (e.g., Arduino Uno)

- SSD1306 OLED display (I2C)

- RGB LED connected to PWM pins

- Push button connected to `PD2` (INT0)

- Buzzer connected to `PB0`


## 🗂️ File Structure


- `main.c` – Contains the full game logic and state machine

- `i2c.h / SSD1306.h` – OLED display driver code

- **Note**: EEPROM storage for top scores is referenced but not yet implemented in the given code


## 🔩 Pin Configuration


| Component     | Pin        | Notes                          |

|---------------|------------|--------------------------------|

| Button        | PD2 (INT0) | Active LOW with pull-up        |

| Buzzer        | PB0        | Activated during penalty        |

| RGB LED       | PB1, PB2, PB3 | PWM-controlled (OC1A, OC1B, OC2A) |

| OLED Display  | I2C (SCL/SDA) | SSD1306 display                |


## 🧠 Concepts Used


- Finite State Machine for game logic

- External Interrupts (`INT0`) for responsive button handling

- Software PWM for RGB LED

- Debouncing using interrupt logic

- Non-blocking delays using `_delay_ms()` to maintain responsiveness


## 📸 Screens (OLED Text Output)


- "Welcome! Press Button to Start"

- "Choose Difficulty: > EASY <"

- "Round X of 5. Wait for GREEN light"

- "GREEN! Press button!"

- "Too slow!" or "YOU LOSE!"

- "Average Time: XXX ms"


## 🚀 Getting Started


1. Clone the repository

2. Build using `avr-gcc` or upload via Arduino IDE with correct pin mappings

3. Connect OLED, button, buzzer, and RGB LED as per pin config

4. Power your board and start the game!


## 👨‍💻 Authors

Scott Pearson - [@scottpearson14](https://github.com/scottpearson14)
Braden Miller – [@bradenmiller22](https://github.com/bradenmiller22)
