## Overview

This mod introduces a customizable **Global Damage Reduction** option to the game's battle system, giving players granular control over incoming damage levels directly through the mod manager settings menu. Whether you want to fine-tune combat difficulty, create a more forgiving experience, or set up high-survivability testing environments, this tool provides a simple and flexible way to adjust damage scaling without requiring manual code edits.

---

## Key Features

* **Flexible Configuration Settings:**
Includes a built-in options menu featuring 11 selectable damage reduction tiers:


* **0% (Vanilla Damage)** — Standard unmodified gameplay.


* **10% to 90% Reduction** — Step-by-step reduction options in 10% increments.


* **95% Reduction (Maximum)** — Extreme protection mode.




* **Seamless Battle Hook Integration:**
Wraps the engine's core `battle.damage` calculation pipeline dynamically. Incoming damage is modified by calculating the remaining damage multiplier and rounding the result down using standard floor functions.


* **Minimum Damage Failsafe:**
To maintain battle logic and prevent invincibility loops or broken combat triggers, the mod includes a built-in check: if an attack originally dealt non-zero damage, the final calculated damage will never drop below **1 point**.



---

## How It Works

1. **Option Selection:** The player selects their desired reduction percentage in the mod settings menu.


2. **Calculation:** When battle damage is evaluated, the mod fetches the selected ratio, computes `damage * (1 - reduction)`, and applies `math.floor`.


3. **Execution:** The modified damage value along with the original engine metadata is returned safely to the game runtime.
