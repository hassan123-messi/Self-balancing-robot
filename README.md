# Self-Balancing Robot (Inverted Pendulum System)

A physics-driven self-balancing robot built using **ESP32**, **MPU6050 IMU**, and **dual DC gear motors**.

The robot is modeled as an **inverted pendulum system**, where the wheel axle acts as the pivot and the controller continuously moves the wheels to keep the **center of mass above the pivot point**.

This project focuses on **engineering the system from first principles**, emphasizing the physics and control theory behind dynamic balancing rather than simply assembling hardware.

---

# Project Goals

- Design a **two-wheeled inverted pendulum robot from scratch**
- Implement **real-time balance control using PID**
- Understand the **physics behind dynamic stabilization**
- Build a platform that can later integrate **ROS2, vision, and AI**

---

# System Overview

The robot behaves as an **unstable inverted pendulum**.

When the robot tilts, gravity generates torque that accelerates the fall.  
The controller compensates by driving the wheels so that the **ground contact point moves under the center of mass**, restoring balance.

Control loop:

IMU → Angle Estimation → PID Controller → Motor Driver → Wheels

This loop runs continuously to stabilize the robot.

---

# Physics Model

The robot can be approximated as a rigid inverted pendulum.

Gravity torque:

τ = mgh sin(θ)

Where:

- m = robot mass  
- g = gravitational acceleration  
- h = center of mass height above wheel axle  
- θ = tilt angle  

Rotational acceleration:

α = τ / I

Moment of inertia:

I ∝ mh²

Design implications:

- Higher center of mass increases **moment of inertia**
- Higher inertia slows rotational acceleration
- Slower fall gives the controller **more time to react**

However, excessive height increases gravity torque, so the design balances these effects.

---

# Hardware

## Microcontroller
ESP32

## Sensor
MPU6050 IMU (accelerometer + gyroscope)

## Motors
2× DC gear motors (~100–200 RPM recommended)

## Motor Driver
TB6612FNG dual H-bridge driver

## Power
7.4V LiPo battery

## Mechanical
Custom **3D printed chassis**

---

# Mechanical Design

The chassis is designed to satisfy several physical constraints:

- Center of mass located **above the wheel axis**
- Symmetrical mass distribution left/right
- Heavy components mounted **mid-upper height**
- High traction wheels for stable contact

The frame will be designed in **CAD (SolidWorks)** and exported as **STL files for 3D printing**.

---

# Software Architecture

The software is divided into three layers.

## Sensor Layer
Reads data from the MPU6050 and estimates the tilt angle.

## Control Layer
PID controller calculates the corrective motor torque.

## Actuation Layer
Motor driver receives PWM signals and drives the wheels.

Example control cycle:

1. Read IMU data  
2. Estimate robot angle  
3. Compute PID correction  
4. Drive motors

---

# Development Roadmap

## Phase 1 — Stability

Goal: Achieve stable balancing.

Tasks:

- IMU angle estimation
- PID controller implementation
- Motor response tuning
- Mechanical center of mass adjustment

---

## Phase 2 — Intelligence

Add a **Raspberry Pi** for higher-level computation.

Capabilities:

- Computer vision
- Object tracking
- Environment awareness

The ESP32 remains responsible for **low-level motor control**.

---

## Phase 3 — Robotics System Integration

Integrate the system with **ROS2**.

Goals:

- Modular robotics architecture
- Communication between sensors and controllers
- Simulation using **Gazebo or Webots**

---

# Future Improvements

- Kalman filter sensor fusion
- Wheel encoders for velocity feedback
- Advanced control (LQR / state-space)
- ROS2 autonomous navigation
- Computer vision tracking

---

# Repository Structure

self-balancing-robot

README.md  
cad/  
firmware/  
hardware/  
docs/

---

# Engineering Philosophy

Many robotics projects replicate existing designs.  
This project focuses on **understanding the physics and control theory behind balancing**, including:

- inverted pendulum dynamics  
- center of mass placement  
- gravity torque  
- moment of inertia effects  

The goal is to build a **robot designed through engineering reasoning rather than copying existing solutions**.
