# Bee Population Evolution Simulation

This project is a visual and mathematical simulation of a bee-pollen ecosystem. It models evolutionary dynamics governed by specific behavioral rules, tracking how a population of bees adapts, reproduces, and survives based on the quality of food sources they interact with. 

The simulation uses **Pygame** for real-time visual representation and **Matplotlib** for post-simulation data analysis and graphing.

---

## Ecosystem Mechanics

The simulation is built around two primary entities: **Bees** and **Pollen Sources**.

### Pollen Sources
Pollen spawns randomly across the screen and is assigned one of three quality levels (Quality Index / QI). The quality determines the color of the pollen and impacts the survival rate of the bees that consume it:
* **Red (Quality 1):** Low nutritional value.
* **Blue (Quality 5):** Medium nutritional value.
* **White (Quality 10):** High nutritional value.

When a pollen source runs out of nectar (after being collided with multiple times), it respawns at a new random location with a new randomized quality.

### Bee Behavior
Bees start with random positions and navigate the ecosystem based on the following rules:
* **Movement & Preference:** Bees have an 80% chance to actively seek out and move toward their "preferred" pollen quality. If they have no preference yet, or if the 20% randomness triggers, they move randomly.
* **Foraging (Collision):** When a bee gets close enough to a pollen source, it collects a reward, decreases the pollen's nectar, and updates its preference to match that pollen's quality.
* **Reproduction & Mutation:** Fitness is determined by collected rewards. Bees have a maximum of one offspring. The probability of reproduction scales logarithmically with fitness. When a bee reproduces, there is a **1% mutation chance** where the offspring will randomly prefer a different pollen quality than its parent.
* **Survival (Death):** The probability of a bee dying increases with age but is heavily mitigated by the Quality Index (QI) of their preferred pollen. A hard age cap of 720 ticks also exists.

---

## Installation & Setup

It is highly recommended to run this simulation inside a Python Virtual Environment to prevent dependency conflicts. 

**1. Create and activate a virtual environment:**

```
python -m venv venv
.\venv\Scripts\activate
```

**2. Install the required dependencies:**

```
pip install pygame-ce matplotlib numpy
```
**3. Run the Notebook:**

Open engine.py in your IDE and ensure you select the virtual environment's kernel before executing the cells.

### Usage Guide

For Windows:
```
python engine.py
```

For Linux/MacOS:
```
python3 engine.py
```

A Pygame window will open, displaying the live simulation. You will see:
* Colored circles representing Pollen.
* Yellow dots representing Bees.

* Live counters for the current number of bees and elapsed time in the bottom right corner.
* Pollen sources will blink yellow when a bee successfully forages from them.

To finish the simulation, click the red "X" to close the Pygame window.
Once the window closes, the final cell will execute and display the data plots inline.

### Data Outputs
After the simulation concludes, Matplotlib generates three distinct graphs to help analyze the evolutionary run:

1. Average Reward per Bee: Tracks the general fitness and foraging success of the hive over time.
   
2. Number of Bees over Time: Shows population fluctuations based on environmental constraints and food quality.
   
3. Bee Preferences over Time: A multi-line chart showing the distribution of the population's dietary preferences (Quality 1 vs. 5 vs. 10). This visualizes natural selection as the population adapts to prefer higher-quality food sources.

For a more detailed report refer to this doc: [Report.docx](https://github.com/user-attachments/files/27755810/Report.docx)
