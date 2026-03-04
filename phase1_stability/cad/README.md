
# Phase 1 — Stability Control

Phase 1 focuses on building the **core balancing system** of the robot.

The robot behaves as an **inverted pendulum**, where the wheel axle acts as the pivot and gravity continuously tries to rotate the robot downward.

The control system compensates for this instability by moving the wheels to keep the **center of mass aligned above the wheel axis**.

## Objectives

- Read tilt angle from the IMU
- Implement PID balance control
- Control motors through the motor driver
- Achieve stable two-wheel balancing

## Components

ESP32  
MPU6050 IMU  
TB6612 Motor Driver  
Two DC Gear Motors  
Battery  
3D Printed Chassis

## Subsystems

- `firmware/` → control code running on ESP32  
- `hardware/` → wiring diagrams and electrical setup  
- `cad/` → 3D printed mechanical design  
- `docs/` → physics model and control theory notes
