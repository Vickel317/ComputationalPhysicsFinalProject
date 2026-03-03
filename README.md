# Computational Physics Final Project

## Double Pendulum: Chaos in Classical Mechanics

**Course:** SCIE6063001 — Computational Physics  

### Overview

This project models the **double pendulum**, a classic example of a chaotic dynamical system, using Python and numerical techniques. The system consists of two pendulums attached end-to-end, and despite being governed by deterministic equations, exhibits extreme sensitivity to initial conditions.

### Contents

- **`DoublePendulum.ipynb`** — Complete Jupyter Notebook containing all code, visualizations, and analysis.
- **`FINAL_PROJECT_REQUIREMENTS.md`** — Checklist of what the project covers and what you should be prepared to discuss.

### Topics Covered

- **Physical Process:** Lagrangian mechanics of a coupled two-body pendulum system.
- **Mathematical Background:** Derivation of equations of motion via Euler-Lagrange equations.
- **Numerical Methods:** 4th-order Runge-Kutta (RK4) and `scipy.integrate.solve_ivp` (RK45).
- **Visualizations:** Time series, phase space diagrams, trajectory plots, 3D parametric curves, and pendulum animation frames.
- **Error Analysis:** Energy conservation, method comparison (RK4 vs. RK45), and numerical stability.
- **Chaos Analysis:** Sensitivity to initial conditions and Lyapunov exponent estimation.
- **Boundary Cases:** Small-angle approximation comparison and special parameter cases.

### Requirements

```
numpy
scipy
matplotlib
jupyter
```

### Running the Notebook

```bash
pip install numpy scipy matplotlib jupyter
jupyter notebook DoublePendulum.ipynb
```