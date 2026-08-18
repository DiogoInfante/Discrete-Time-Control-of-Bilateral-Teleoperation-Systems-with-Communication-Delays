# Discrete-Time Control of Bilateral Teleoperation Systems with Communication Delays

MATLAB simulations for my undergraduate thesis (TCC) in Control & Automation Engineering at PUC-Rio. The project develops and validates discrete-time servo-bilateral control routines for teleoperated robotic manipulators subject to time-invariant communication delays.

📄 **Thesis:** [Read the full document](https://www.maxwell.vrac.puc-rio.br/projetosEspeciais/TFCs/consultas/conteudo.php?strSecao=resultado&nrSeq=59932@1)

## Overview

In a bilateral teleoperation setup, a *master* station is driven by a human operator, and a *slave* station reproduces the master's trajectory from its sensor data. Bilaterality is completed by reflecting the external forces acting on the slave back to the master, so the operator can feel the remote environment.

These simulations model both stations as identical quasi-serial 2-DOF manipulators and implement optimal control laws that hold up under external disturbances, actuator saturation, sensor quantization, measurement noise, and communication delay.

## Techniques

- **Modeling** — Euler-Lagrange dynamics, discrete-time state-space representation (ZOH discretization), controllability and observability checks.
- **LQR** — Linear Quadratic Regulator for optimal state-feedback control of the master and, in the ideal case, the slave.
- **Kalman filter** — Linear quadratic estimator on the slave for the noisy, delayed, and disturbed scenarios. Delay is handled by an augmented state vector, giving optimal compensation for a fixed communication ping.
- **Force feedback** — kinematic/static duality (τ = Jᵀf) used to reflect external forces on the slave back to the master.

## Simulations

Three task sets of increasing difficulty:

1. **Position control at uniform velocity** — move both manipulators from an initial to a desired configuration at constant speed. Achieved ~0.1° precision.
2. **Defined circular trajectory** — track a predefined circle; a harder task that surfaced ~2° precision and confirmed the delay and noise compensation were exact.
3. **Straight-line trajectory with force feedback** — follow a vertical line while an external horizontal force acts on the slave, validating the bilateral reflection of forces to the master.

Across these, five scenarios (A–E) layer in delay, transmission noise, and slave-side disturbances one at a time to isolate each effect.

## Implementation

Written in MATLAB following object-oriented programming under a Model-View-Controller architecture, so the manipulator model or control technique can be swapped without touching the rest of the codebase. Beyond the standard plots, a graphical interface animates the master and slave side by side with a trace of each end-effector's path.

## Author

Diogo de Freitas Infante Vieira
Advisor: Marco Antonio Meggiolaro · Co-advisor: Helon Vicente Hultmann Ayala
PUC-Rio · 2022
