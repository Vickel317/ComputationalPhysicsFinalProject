# Final Project Requirements — SCIE6063001 Computational Physics

## Overview

Your final project models the **double pendulum**, a classic example of a chaotic dynamical system. The complete implementation lives in `DoublePendulum.ipynb`. Below is a summary of everything the project covers and what you should be prepared to discuss or demonstrate.

---

## What Was Completed (Previous Session)

The notebook built in the previous session addresses every major component of a computational-physics final project. Here is what is already implemented and ready to run:

### 1. Physical Description (Section 2)
- Definition of the double-pendulum system (two point masses on rigid, massless rods).
- Discussion of why the system is chaotic (coupled nonlinear ODEs, sensitivity to initial conditions, positive Lyapunov exponent).
- Table of simplifying assumptions (no friction, no air resistance, point masses, 2-D motion).

### 2. Mathematical Derivation (Section 3)
- Generalized coordinates ($\theta_1$, $\theta_2$).
- Kinetic and potential energy expressions.
- Lagrangian $\mathcal{L} = T - V$ and Euler–Lagrange equations.
- Full equations of motion for $\ddot\theta_1$ and $\ddot\theta_2$, rewritten as a first-order system of four ODEs.

### 3. Numerical Implementation (Section 4)
- **Parameters**: $m_1 = m_2 = 1\,\text{kg}$, $l_1 = l_2 = 1\,\text{m}$, $g = 9.81\,\text{m/s}^2$.
- **Initial conditions**: $\theta_1 = 120°$, $\theta_2 = 90°$, both starting from rest.
- **Two solvers**:
  - `scipy.integrate.solve_ivp` with adaptive RK45 (`rtol=1e-10`, `atol=1e-12`).
  - Hand-written 4th-order Runge–Kutta (fixed step `dt = 0.001`).
- Conversion to Cartesian coordinates for plotting.

### 4. 2-D Visualizations (Section 5)
- **Time series**: $\theta_1(t)$ and $\theta_2(t)$; $\omega_1(t)$ and $\omega_2(t)$.
- **Phase-space portraits**: $(\theta_i, \omega_i)$ for each pendulum.
- **Trajectory plot**: path of the second bob colored by time.
- **Energy vs time**: total mechanical energy from both solvers.

### 5. 3-D Visualization (Section 6)
- Parametric curve $(\theta_1, \theta_2, t)$ in 3-D space.

### 6. Animation (Section 7)
- Key-frame rendering of the pendulum (rods, bobs, trailing path).
- Full `FuncAnimation` saved as a GIF (`double_pendulum.gif`).

### 7. Error Analysis (Section 8)
- **Energy drift**: relative energy error $|E(t) - E_0|/|E_0|$ for both solvers.
- **Trajectory divergence**: $|\Delta\theta_1|$ and $|\Delta\theta_2|$ between RK45 and RK4.
- Discussion of why adaptive methods outperform fixed-step and why pointwise long-term accuracy is unattainable in chaotic systems.

### 8. Chaos Analysis (Section 9)
- Sensitivity to initial conditions: two runs with a $10^{-3}\,\text{rad}$ perturbation.
- Phase-space distance $d(t)$ showing exponential divergence.
- **Lyapunov exponent** estimation via $\lambda \approx (1/t)\ln(d(t)/d(0))$ and a linear fit to $\ln d$ vs $t$.

### 9. Boundary / Special Cases (Section 10)
- **Small-angle approximation**: linearized normal-mode solution vs full nonlinear numerical solution at $\theta = 5°$.
- Table of special cases (equal masses/lengths, zero velocity, one mass → 0, very large angles).

### 10. Conclusions (Section 11)
- Summary of findings: Lagrangian derivation, solver comparison, chaos confirmation, energy conservation as a diagnostic, and the small-angle limit.

---

## Checklist — What You Should Be Able To Do

Use this checklist to prepare for your project submission or presentation:

### Understanding the Physics
- [ ] Explain the setup of a double pendulum and the degrees of freedom ($\theta_1$, $\theta_2$).
- [ ] State the simplifying assumptions and their justification.
- [ ] Describe why the double pendulum is chaotic (nonlinear coupling, sensitive dependence).

### Understanding the Math
- [ ] Walk through the Lagrangian derivation: $T$, $V$, $\mathcal{L}$, Euler–Lagrange equations.
- [ ] Explain how the two second-order ODEs are rewritten as four first-order ODEs for numerical integration.
- [ ] Describe the small-angle linearization and normal-mode analysis.

### Understanding the Numerical Methods
- [ ] Explain the 4th-order Runge–Kutta algorithm (the four slopes $k_1$–$k_4$ and the weighted average).
- [ ] Explain how `scipy.integrate.solve_ivp` (adaptive RK45) differs from fixed-step RK4 (adaptive step sizing, error control via `rtol`/`atol`).
- [ ] Discuss why the adaptive solver conserves energy better.

### Running and Interpreting Results
- [ ] Run the notebook end-to-end: `jupyter notebook DoublePendulum.ipynb` (or use `jupyter nbconvert --execute`).
- [ ] Interpret the time-series plots (irregular oscillations indicate chaos).
- [ ] Interpret the phase-space portraits (dense, non-repeating orbits).
- [ ] Interpret the trajectory plot (complex, space-filling path of the second bob).
- [ ] Interpret the energy-drift plot (quantifies numerical accuracy).

### Chaos and Error Analysis
- [ ] Explain the sensitivity experiment (two nearly identical initial conditions diverge).
- [ ] Interpret the Lyapunov exponent: $\lambda > 0 \Rightarrow$ chaos.
- [ ] Discuss the error-analysis results: why both solvers eventually diverge from each other even with the same equations.

### Boundary Cases
- [ ] Explain how the small-angle (linearized) solution is derived and why it matches the numerical result at $5°$.
- [ ] Discuss at least two special cases from the table (e.g., one mass → 0 reduces to a simple pendulum).

### Presentation / Report Tips
- [ ] Open with a brief motivation: simple setup, complex behavior, real-world relevance.
- [ ] Show the animation or key frames to give an intuitive feel for the motion.
- [ ] Highlight the Lyapunov exponent as the quantitative proof of chaos.
- [ ] Use the energy-conservation plot to argue for solver reliability.
- [ ] Conclude with "deterministic ≠ predictable."

---

## How To Run

```bash
pip install numpy scipy matplotlib jupyter
jupyter notebook DoublePendulum.ipynb
```

Or execute non-interactively:

```bash
jupyter nbconvert --to notebook --execute DoublePendulum.ipynb
```

---

## Dependencies

| Package      | Purpose                                |
|--------------|----------------------------------------|
| `numpy`      | Array operations, linear algebra       |
| `scipy`      | ODE integration (`solve_ivp`), eigenvalue problems (`eigh`) |
| `matplotlib` | All plots, animations, 3-D figures     |
| `jupyter`    | Running the notebook interactively     |
