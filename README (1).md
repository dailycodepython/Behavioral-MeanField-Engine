# Behavioral Mean-Field Engine (BMFE)

A computational framework for simulating and controlling multi-agent systems using **Behavioral Mean Field Games (MFG)** in Google Colab. This project explores how classical Nash Mean Field Equilibria (MFE) deform under the influence of bounded rationality, cognitive biases, and informational constraints.

## 🚀 Theoretical Core
The simulation is powered by a coupled system of partial differential equations (PDEs) solved via an iterative Picard scheme with Anderson relaxation:
1. **Hamilton-Jacobi-Bellman (HJB) Equation** (Solved backward in time) – Determines the optimal value function $V(t, x)$ and behavioral strategies $u^*(t, x)$ for an individual agent.
2. **Fokker-Planck-Kolmogorov (FPK) Equation** (Solved forward in time) – Governs the advection and diffusion of the total population density $m(t, x)$ driven by agent controls and environmental noise.

---

## 📊 Behavioral Anomaly Matrix

| Model Scenario | Mathematical Paradigm | Visual Effect on Population Density | Socio-Economic Intuition |
| :--- | :--- | :--- | :--- |
| **1. Rational Baseline (MFE)** | $H = -\frac{1}{2\nu} (\nabla V)^2$ | Smooth bell curve shifting effectively toward the objective center ($x=0.0$). Peak $\approx 1.3$. | Agents possess infinite computing power and zero reaction time. |
| **2. Bounded Rationality** | $D_{eff} = 0.5(\sigma^2 + \epsilon^2)$ | Sharp, anomalous local cluster with an elevated narrow peak $\approx 1.8$. | Cognitive noise $\epsilon$ creates execution entropy. Agents freeze in uncoordinated sub-optimal groups. |
| **3. Prospect Theory** | $m_{perceived} = m^{\alpha_{pt}}$ | Heavily flattened, highly dispersed distribution across the entire space. Peak $< 0.75$. | Hypertrophied crowd aversion ($\alpha_{pt} = 0.6$). Agents sacrifice final goals for personal psychological comfort. |
| **4. Informational Lag** | $m_{delayed} = m(t - \tau, x)$ | Phase-lagged, multi-modal distribution stuck at the initial position ($x=-1.2$). | Rational inattention. Agents react to "ghosts of the crowd" from past states, resulting in severe overshooting. |

---

## 🎛️ Feedback Regulatory Incentives (Step 6)
To correct irrational crowding behaviors, a feedback penalty field $\zeta \cdot (m - m_{target})$ was introduced into the HJB framework. The empirical results demonstrated a fundamental mathematical duality:
* **Geometric Correction:** The controller perfectly forces the disoriented population to align with the socially optimal path.
* **Economic Inefficiency:** Forcing irrational agents onto a rational trajectory induces an exponential spike in their control energy expenditure ($0.5 \nu u^2$). This validates the concept of **coordination cost overheads** in complex human-centric systems.

## 🛠️ Installation & Usage in Google Colab
1. Open Google Colab and run the initialization cell to establish the space-time grid ($N_t=200, N_x=60$).
2. Execute the `BehavioralMFGSolver` class and its derived behavioral extensions.
3. Run the evaluation dashboards to render comparative population dynamics plots.