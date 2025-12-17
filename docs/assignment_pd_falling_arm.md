# Assignment 1: PD Control on a Falling 2‑Link Planar Arm

## Objective
Design and implement a PD controller for each joint of a 2‑link planar arm as it falls under gravity. The controller must:
- Reduce the mean error to ≤ 10% of the initial error over the interval [0, 5].
- Limit overshoot to ≤ 2% of the starting error.
- Use proportional gains slow enough to keep visible oscillations ≤ 5 cycles in the 5‑second window.

## Approach
- **Modeling:** The first two links of the planar arm were modeled with gravity acting on each joint.
- **Controller design:** A PD controller was applied independently to each joint. Gains were tuned iteratively:
  - **Proportional gain (P):** Adjusted to balance responsiveness with oscillation limits.
  - **Derivative gain (D):** Increased to dampen overshoot and stabilize the trajectory.
- **Validation:** Simulations were run to measure error envelopes, overshoot percentage, and cycle count.

## PD Gain Calculation Methodology

The proportional–derivative (PD) control gains were derived analytically from performance specifications:

- **Percent Overshoot Constraint:**  
  The system was required to limit overshoot to ±2% of the initial error. The damping ratio ζ was calculated using the standard relationship between overshoot and damping:

$$
\zeta = \frac{-\ln(\%OS/100)}{\sqrt{\pi^2 + \ln^2(\%OS/100)}}
$$

- **Natural Frequency:**  
  The desired settling behavior within 5 seconds defined the natural frequency:

$$
\omega_n = 2\pi f
$$

$$
f = \frac{1}{5 \ \text{seconds}}
$$

- **Controller Gains:**  
  With the mass of the system obtained from the robot dynamics function, the gains were set analogous to a spring–damper system:

$$
K_p = m \cdot \omega_n^2
$$

$$
K_d = 2 \zeta \cdot \omega_n
$$

## Results
- **Joint angle plots:** Both joints converged to their target angles within the 5‑second window.
- **Performance metrics:** Mean error < 10%, overshoot < 2%, oscillations ≤ 5 cycles.
- **Animation:** An MP4 video was generated using MATLAB’s `VideoWriter` to visualize the arm stabilizing as it falls.

## Reflection
The PD tuning process required balancing responsiveness with stability. Lower proportional gains reduced oscillations but slowed convergence, while derivative gains provided critical damping. The final gains achieved the specified performance targets and demonstrated the trade‑offs inherent in controller design.
