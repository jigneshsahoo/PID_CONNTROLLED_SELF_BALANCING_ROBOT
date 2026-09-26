# PID_CONNTROLLED_SELF_BALANCING_ROBOT
Modeling and PID control of a two-wheeled self-balancing robot in MATLAB/Simulink using Simscape Multibody and closed-loop feedback.
# PID-Controlled Two-Wheeled Self-Balancing Robot — MATLAB/Simulink

A simulation-based two-wheeled self-balancing robot developed using **MATLAB**, **Simulink**, and **Simscape Multibody**. The project investigates how a **PID feedback controller** stabilizes an inverted-pendulum-type system and maintains the robot near its upright equilibrium position after an external disturbance.

Robot Model<img width="1917" height="947" alt="Screenshot 2026-09-13 133522" src="https://github.com/user-attachments/assets/1b1bcf30-f54d-4f49-aa36-edf3b324b0b1" />


---


## Project Overview

A self-balancing robot behaves similarly to an **inverted pendulum**, which is naturally unstable. The objective of the controller is to continuously monitor the robot's tilt angle and generate corrective actions through wheel motion to maintain balance.
This project includes:

- Simscape Multibody model of a two-wheeled robot
- Closed-loop PID control
- Initial perturbation testing
- Simulation response analysis
- Basic PID validation model

---

## Control Objective

The controller performs the following tasks:

1. Detect robot tilt angle
2. Compare it with the desired upright position
3. Calculate the error
4. Generate a corrective control signal using PID control
5. Drive the robot back toward equilibrium

---

## System Architecture

Initial Perturbation
        │
        ▼
Desired Angle (0°)
        │
        ▼
Error Calculation
        │
        ▼
PID Controller
(Kp, Ki, Kd)
        │
        ▼
Robot Dynamics
(Simscape Model)
        │
        ▼
Measured Angle
        │
        └────────── Feedback ──────────┘


---

## Simulink Model

The robot model is developed using **Simscape Multibody** and includes:

- World Frame
- Mechanical Configuration
- Chassis
- Wheel/Joint System
- Revolute Joint
- Joint Sensor
- PID Controller
- Feedback Loop
- Initial Perturbation Input
- Scope for Response Analysis

---

## PID Controller

The controller is implemented using a continuous-time PID block in parallel form.

### Controller Parameters

| Parameter | Value |
|------------|--------|
| Kp | 2 |
| Ki | 1 |
| Kd | 0.01 |
| Filter Coefficient (N) | 100 |

The controller follows:

\[
u(t)=K_p e(t)+K_i\int e(t)dt+K_d\frac{de(t)}{dt}
\]

For the current gains:

\[
u(t)=2e(t)+\int e(t)dt+0.01\frac{de(t)}{dt}
\]

---

## Basic PID Validation Model

Before integrating the controller with the robot model, a simple closed-loop system was used for PID validation.

Plant:

\[
G(s)=\frac{1}{s+1}
\]

### Basic PID Model

Basic PID Model<img width="1919" height="1012" alt="Screenshot 2026-08-20 214543" src="https://github.com/user-attachments/assets/e37adfd1-b929-4e23-9ddc-3b92671693c0" />

---

## Initial Perturbation

An initial disturbance is applied to test the controller's ability to recover the upright position.

This allows observation of:

- Stability
- Oscillation behavior
- Convergence
- Controller effectiveness

Initial Perturbation<img width="568" height="567" alt="Screenshot 2026-09-13 133705" src="https://github.com/user-attachments/assets/4ba1a0ba-6181-4b53-8d69-c40cc2b1ada2" />


---

## Simulation Results

The system was tested by applying an initial perturbation.

### Observations

- Initial positive excursion: ~ +19°
- Maximum negative excursion: ~ -12°
- Oscillatory transient respo
- Oscillations decrease prognseressively
- System approaches equilibrium within approximately 1–1.5 seconds
- Stable behavior after transient response
on
The respse indicates that the PID controller successfully stabilizes the simulated robot after disturbance.

### Simulation Response

Simulation Response<img width="1917" height="1000" alt="Screenshot 2026-09-26 134505" src="https://github.com/user-attachments/assets/3d219410-3ff7-4689-a33e-e0afd75644e2" />
## Simulation Demo

The following video demonstrates the self-balancing robot simulation running in Simulink with the implemented PID controller.

---

## Performance Summary

| Metric | Observation |
|----------|-------------|
| Controller Type | PID |
| Simulation Time | 10 s |
| Response Type | Damped Oscillatory |
| Stability | Stable |
| Steady-State Error | Approximately Zero |
| Equilibrium Recovery | Successful |

---

## Project Files


self-balancing-robot-simulink/
│
├── README.md
│
├── Self_Balancing_Robot.slx
└── screenshots/
    ├── robot_model.png
    ├── basic_pid_model.png
    ├── pid_parameters.png
    ├── initial_perturbation.png
    └── simulation_response.png


---

## Tools & Technologies

- MATLAB
- Simulink
- Simscape Multibody
- PID Control
- Feedback Control Systems
- Dynamic System Modeling

---


## Limitations

Current implementation limitations:

- Simulation only
- No real IMU data
- No encoder feedback
- No motor saturation model
- No battery model
- No sensor noise model
- No hardware validation

Results represent simulated behavior and not physical robot performance.
