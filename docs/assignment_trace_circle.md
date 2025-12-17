# Assignment 2: Controller Performance Feedback on a Circle Trajectory

## Objective
Track a kinematically generated circle trajectory with a 3‑link 3D arm using a controller constructed via MATLAB’s `place` command. Compare performance for two sets of pole placements:
- **Slow poles:** p = 0.1
- **Fast poles:** p = 10

## Approach
1. **Trajectory generation:** Joint‑angle trajectories for tracing a circle were computed and saved to a `.mat` file.
2. **Mass matrix computation:** At discrete times (t = 0, 1/8, 1/4, …, 1), the configuration‑dependent mass matrix was generated.
3. **Controller design:**  
   - State‑space matrices constructed as:  
     - A = [0 I; 0 0]  
     - B = [0; M⁻¹]  
   - Gains K computed at each configuration using `place`.
   - Saved as `K_matrices.mat`.
4. **Control policy:** At runtime, the current time was rounded to the nearest 1/8, and the corresponding K matrix was applied to the joint angle/velocity error vector.
5. **Simulation:** System motion was simulated under both pole choices.

## Results
- **p = 0.1 (slow poles):**  
  - End‑effector path tracked a portion of the circle with smoother, slower corrections.  
  - Lower control effort, but larger steady‑state deviations.
- **p = 10 (fast poles):**  
  - End‑effector path tracked more tightly to the desired circle.  
  - Higher control effort and more aggressive corrections.  
  - Increased sensitivity to modeling errors.

## Reflection on Controller Performance
The controller performance differed significantly across the tested pole values:

- **p = 1/100:**  
  The robot arm exhibited noticeable lag before converging toward a portion of the desired trajectory. Tracking was not achieved, and the response was slow and less smooth.

- **p = 1/10:**  
  The arm followed the trajectory more smoothly, with reduced lag compared to p = 1/100. However, the controller gains (K matrices) were still insufficient to fully compensate for joint friction and gravitational moments.

- **p = 1:**  
  Increasing the pole by a factor of 10 strengthened the controller gains. The system became more stable, and the arm was directed more effectively toward the desired path.

- **p = 10:**  
  With another tenfold increase, the controller gains produced a trajectory that closely resembled the desired path, with minimal lag. The higher pole placement improved responsiveness and reduced error, though at the cost of increased control effort.

### Key Insight
The experiment demonstrated the trade‑off between pole placement and controller performance:
- **Lower poles (p = 1/100, 1/10):** smoother but slower responses, insufficient to overcome system dynamics.  
- **Higher poles (p = 1, 10):** stronger stabilization and tighter trajectory tracking, but requiring greater control effort.

This highlights the importance of pole selection in balancing accuracy, stability, and physical limitations such as friction and gravity in robotic systems.
