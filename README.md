# Maze Solver Robot (GEAR 2024)

Autonomous differential-drive robot designed to navigate and solve unknown maze environments using ultrasonic range sensing and a Wall-Follower navigation strategy. Developed for the [GEAR (Grupo de Estudos Aplicados à Robotica)](https://github.com/GEAR-EST/) 2024 selection process at UEA, placing 1st as the sole winning robot.

---

## Overview

The robot processes real-time distance measurements from three ultrasonic sensors (Front, Left, Right) to maintain course along corridor walls, avoid obstacles, and resolve intersections without external intervention.

## Hardware Architecture

| Component | Model / Specification | Function |
| :--- | :--- | :--- |
| **Microcontroller** | Arduino Uno (ATmega328P) | Core control logic and signal processing |
| **Motor Driver** | L298N Dual H-Bridge Module | Bidirectional motor PWM and direction control |
| **Actuators** | 2x TT DC Gearmotors (1:48) | Differential traction |
| **Sensors** | 3x HC-SR04 Ultrasonic Sensors | Spatial awareness (Front, Left, Right) |
| **Chassis** | Custom 3D Printed Structure | CAD design modeled in Autodesk Inventor |

## Control Logic

The firmware executes a deterministic **Wall-Follower** state machine:
* **Obstacle Avoidance:** When the front sensor detects an obstacle below the safety threshold, the controller compares lateral readings and pivots toward the open path.
* **Wall Alignment:** Dynamically corrects differential wheel speeds to maintain a constant distance from adjacent walls.
* **Dead-End Recovery:** Reverses and performs a 180-degree rotation when all forward and lateral paths are blocked.

## Repository Structure

```text
├── carrinho/
│   ├── circuito/             # Fritzing (.fzz) and wiring schematics
│   ├── programa/carrinho     # Platformio source code
│   ├── simulação/            # sBotics simulation files
│   └── modelo 3d/            # Autodesk Inventor CAD files (.iam) and renders
└── README.md
```

Simulation & Results
Validation: Simulated in sBotics to calibrate sensor thresholds, turning delays, and kinematics prior to physical prototyping.

Outcome: 1st place in the GEAR 2024 selective process maze-solving challenge.
