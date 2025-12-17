# Robotic Arm Controller Showcase (MATLAB Documentation Only)

## Overview
This project demonstrates two controller designs applied to a simulated 2‑link planar robot arm:
1. **PD Control on a falling arm** – tuned to meet strict error, overshoot, and oscillation constraints.
2. **Scheduled state feedback via `place`** – applied to a trace circle trajectory with configuration‑dependent mass matrices.

The repo contains **plots, animations, and documentation only** (no source code) to highlight engineering skills while protecting academic integrity. Source code can be made available upon request. *This project was made as part of Oregon State University's ROB 417 Robots and Gyroscopes course.*

## Results
- **PD Controller:**  
  ![Joint Angles](plots/joint_angles_pd.jpg)  
  Animation: `media/falling_arm_pd.mp4`

- **Place Controller (p = 0.1 vs p = 10):**  
  ![End Effector Paths](plots/end_effector_paths_p_0.1.jpg)  
  ![End Effector Paths](plots/end_effector_paths_p_10.jpg)  
  Animations: `media/trace_circle_p_0.1.mp4`, `media/trace_circle_p_10.mp4`

## Documentation
- [Assignment 1: PD Falling Arm](docs/assignment_pd_falling_arm.md)  
- [Assignment 2: Place Controller Trace Circle](docs/assignment_trace_circle.md)

## Skills Demonstrated
- Control system design (PD tuning, state feedback via `place`)
- Dynamics modeling and trajectory generation
- MATLAB simulation, plotting, and animation
- Clear technical documentation
