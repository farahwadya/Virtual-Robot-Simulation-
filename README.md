# Virtual Robot Simulation

No AI libraries are used. All logic and algorithms are implemented from scratch.

Python-based project simulating an autonomous robot in a 2D environment with path planning, obstacle avoidance, FSM, and visualization.

---

## Project Description

This project implements a virtual autonomous robot in a 2D grid environment.  
The robot navigates toward a goal while avoiding obstacles and walls using:

- Breadth-First Search (BFS) for path planning  
- A Finite State Machine (FSM) for decision-making  

The simulation is visualized using Pygame, displaying the robot's movement, states, environment, and how it reaches its goal step by step.

---

## Libraries Used

- **Pygame** – for visualization  
- **collections (deque)** – to implement the BFS algorithm  

---

## System Structure

### Environment
Responsible for managing the grid, obstacles, goal detection, and boundary checking.

Functions:
- `is_within_bounds`
- `is_obstacle`
- `is_goal`
- `display` (used when running without visualization)

---

### Robot
Handles movement, sensing, decision-making, state transitions, and path planning.

Includes:
- 2 Enum classes (`Direction`, `RobotState`)
- Movement functions:
  - `turn_left`
  - `turn_right`
  - `next_position` (calculates next coordinates)
  - `move_forward` (moves robot if no obstacle or wall)

- Sensor functions:
  - `sense` (checks only in front of the robot)
  - `sense_with_info` (returns detailed sensor data for debugging)
  - `sense_all_directions` (360° sensing around the robot)

- `find_path_bfs`  
  Finds the shortest safe path from the robot’s current position to the goal.

- `decide`  
  The robot’s "brain". Analyzes sensor data and determines the next action based on the current state.

---

### Visualizer
Implements the visualization window using Pygame.

Functions:
- `draw_grid`: to draw all cells and bounds of the screen.
- `draw_robot_state`: to add a note about robot state (idle, avoiding, moving).
- `update`: to update screen after each movement

---

### Simulation
Manages execution of the robot inside the environment.

Functions:
- `step()` – Executes a single logical step
- `run()` – Runs the full simulation loop
- `display_robot_info()` – Prints debugging data

---

### Main
Entry point of the program. Initializes environment, robot, and simulation.

---

## Features

### Core Features
- 2D grid-based environment
- Robot with position, orientation, and internal states:
  - IDLE
  - MOVING
  - AVOIDING
  - FINISHED
- Movement system (forward, left, right)
- Collision prevention
- Sensor-based decision-making
- Step-by-step simulation loop

---

## Extension Tracks Implemented

- BFS Path Planning
- Reactive Obstacle Avoidance
- Finite State Machine (FSM)
- Pygame Visualization

---

## Algorithms & Logic

### 1. BFS Path Planning
- Finds the shortest path to the goal
- Recalculates if path becomes blocked
- Returns a list of directions:
  `[NORTH, EAST, EAST, SOUTH, ...]`

### 2. Finite State Machine (FSM)

States:
- IDLE
- MOVING
- AVOIDING
- FINISHED

Transitions depend on sensor input and environment conditions.

### 3. Obstacle Avoidance
- Uses 360° virtual sensing
- Direction priority:
  Right -> Left -> Forward -> Backward
- Switches state when obstacle detected

---

## Installation

### Requirements
- Python 3.x
- Pygame

Install Pygame:

```bash
pip install pygame
## Installation

### Requirements
- Python 3.x
- Pygame

### 1️- Clone the repository

```bash
git clone https://github.com/farahwadya/Virtual-Robot-Simulation.git
cd your-repository-name
2️- (Optional) Create a virtual environment
python -m venv venv

Activate it:

Windows

venv\Scripts\activate

Mac/Linux

source venv/bin/activate
3️- Install dependencies
pip install pygame
Running the Simulation
python main.py

The Pygame window will open showing the robot navigating the environment.
Close the window to stop the simulation.

