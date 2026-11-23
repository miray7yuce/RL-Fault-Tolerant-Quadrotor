# Reinforcement Learning Based Fault-Tolerant Control of a Quadrotor

> MathWorks Global Student Challenge 2026 · Project 235 (Drones)
> Video: _link will be added_ · #GlobalStudentChallenge2026

## Problem Statement

Quadrotors used in package delivery and urban air mobility can lose motor performance in flight because of wear, heat, wind, rain or dust. A fixed-gain PID controller tuned for a healthy vehicle degrades, and may fail, once a motor weakens. Model-based fault-tolerant control needs an accurate model of the faulty system, and that model is hard to keep accurate while the fault changes the vehicle's parameters.

## Solution Approach

- **Plant:** Simscape quadcopter model (airframe, battery, propulsion) with cascaded position and attitude PID control.
- **Fault model:** Increase in a motor's equivalent resistance (gradual degradation) and complete motor loss (abrupt failure).
- **Fault detection:** Kalman-filter-based estimator that tracks the fault-related parameters online and flags a fault.
- **Reinforcement learning:** An agent (TD3) observes the estimated fault parameters and the tracking error, then retunes the PID gains to compensate.
- **Baseline:** The same mission flown with fixed PID gains.

## How MATLAB, Simulink and Generative AI Were Used

| Tool | Used for |
| --- | --- |
| Simulink / Simscape | Quadcopter plant, controllers, fault injection |
| Reinforcement Learning Toolbox | Environment (`rlSimulinkEnv`), TD3 agent, training |
| MATLAB | Estimator, scripts, analysis, plots |
| Generative AI (Claude, chat) | _To be documented: model building, reward design, fault-scenario generation, code review_ |

Prompts, AI outputs and the corrections made to them are logged in [`genai/`](genai/).

## Repository Structure

```
models/      Simulink and Simscape models
src/
  estimator/ Kalman filter and fault detection
  rl/        Environment, agent, reward and training scripts
  faults/    Fault scenarios (gradual degradation, abrupt motor loss)
agents/      Trained agents (.mat)
results/     Figures and comparison tables
genai/       Generative AI usage log
docs/        Diagrams and video script
```

## Key Results

_To be added: RMS tracking error and recovery time, fixed PID vs RL-retuned PID, under each fault scenario._

## How to Run

_To be added._

Requirements: MATLAB R2026b, Simulink, Simscape, Simscape Electrical, Simscape Multibody, Reinforcement Learning Toolbox, Deep Learning Toolbox, Control System Toolbox, UAV Toolbox.

## References

- M. Blanke et al., *Diagnosis and Fault-Tolerant Control*, Springer, 2006.
- L. Bhan et al., "Fault Tolerant Control combining Reinforcement Learning and Model-based Control," SysTol 2021.
- M. Daigle et al., "A comparison of filter-based approaches for model-based prognostics," 2012.
- [MATLAB-Simulink Challenge Project Hub, Project 235](https://github.com/mathworks/MATLAB-Simulink-Challenge-Project-Hub/tree/main/projects/Reinforcement%20Learning%20Based%20Fault%20Tolerant%20Control%20of%20a%20Quadrotor)
