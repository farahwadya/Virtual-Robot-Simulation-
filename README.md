# Virtual-Robot-Simulation-
no AI libraries are used, all logic are written while programming
# Virtual Robot Simulation

Python-based project simulating an autonomous robot in a 2D environment with path planning, obstacle avoidance, FSM, and visualization.

---

## Project Description

This project implements a virtual autonomous robot in a 2D grid environment. 
The robot can navigate to a goal while avoiding obstacles and walls, using BFS for path planning 
and a finite state machine (FSM) for decision-making. The simulation is visualized 
using Pygame, showing the robot's movements, states, environment, and how exactly it's moving to reach it's goal.

---

## Libraries used

- Pygame: for visualization
- collections: to import deque. we use it to implement BFS algorithim

---
## Classes and Functions per class

- Environment:
  - is_within_bounds, is_obstacle, is_goal, display: this func are used in case there are no visual screen so it display the enviroment
- Robot:
  - 2 Enum classes (Direction, RoboteState)
  - Movment and assign coordinates Function (turn_left, turn_right, next position( assign the coordinates of next position), move_forward(move robot if no obstacles or wall)
  - Sensor Function( sense:check infront of robot only, sensewithinfo:print info that been sensed 'used for debugging', sense_all_direction:360 c sensor check all cells in all direction
---

## Features

### Core Features
- 2D grid-based environment with boundaries and obstacles
- Robot model with position, orientation, and internal states: IDLE, MOVING, AVOIDING, FINISHED
- Movement system: move forward, turn left/right
- Collision prevention and obstacle detection
- Decision-making based on virtual sensor inputs
- Simulation loop with step-by-step execution

### Extension Tracks Implemented
- Path Planning using BFS algorithm
- Obstacle Avoidance with reactive decision-making ( integrated with decide movement method in a special case when robot are in avoiding state).
- Finite State Machine (FSM) for state-based behavior
- Visualization using Pygame showing robot, obstacles, goal, and states

---

## Algorithms & Logic

### 1. BFS Path Planning
- Finds the shortest path from the robot's current position to the goal
- Recalculates path if blocked or path completed
- Represented as a list of directions: [NORTH, EAST, EAST, SOUTH, ...]

### 2. Finite State Machine (FSM)
- States:
  - IDLE: Robot waits before starting
  - MOVING: Follows BFS path toward goal
  - AVOIDING: Reacts to obstacles or walls dynamically
  - FINISHED: Goal reached
- Transitions occur based on sensor inputs or reaching path end

### 3. Obstacle Avoidance
- Uses 360-degree virtual sensors
- Priority directions: right → left → forward → backward
- Turns toward clear path if obstacle detected

---

## Installation

### Requirements
- Python 3.x
- Pygame library

Install Pygame using pip:
```bash
pip install pygame
Running the Simulation

Clone the repository

Run the main script:

python main.py

Observe the robot moving in the Pygame window

Press the close button to exit simulation
