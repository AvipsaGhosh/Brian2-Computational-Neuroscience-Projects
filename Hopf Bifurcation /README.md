# Supercritical Hopf Bifurcation: Emergence of Oscillatory Neural Dynamics
### A Computational Neuroscience Model in Python

---

## Overview
This project implements the canonical Supercritical Hopf Bifurcation using numerical simulation in Python. The model demonstrates how a stable equilibrium gradually loses stability as a control parameter crosses a critical threshold, giving rise to a stable limit cycle.

Although the equations represent the mathematical normal form of a Hopf bifurcation, the variables are interpreted as simplified excitatory and inhibitory neural population activities. This provides an intuitive connection between nonlinear dynamical systems and oscillatory neural behavior observed in computational neuroscience.

The project is intended as an educational implementation illustrating one of the most important bifurcations encountered in neural dynamics, neural mass models, and seizure modeling.

---

## Mathematical Background
The model is governed by the canonical Hopf normal form:

$$\frac{dE}{dt} = ZE - \omega I - E(E^2 + I^2)$$

$$\frac{dI}{dt} = \omega E + ZI - I(E^2 + I^2)$$

Where:
* **$E$** represents excitatory population activity.
* **$I$** represents inhibitory population activity.
* **$Z$** is the control (bifurcation) parameter.
* **$\omega$** determines the intrinsic oscillation frequency.

The nonlinear cubic terms $-E(E^2 + I^2)$ and $-I(E^2 + I^2)$ prevent unbounded growth and stabilize the oscillations after the bifurcation. Expressed in polar coordinates, the system simplifies elegantly to:

$$\dot r = Zr - r^3$$

$$\dot\theta = \omega$$

Which immediately predicts:
* A **stable equilibrium** at the origin for $Z < 0$.
* A **Hopf bifurcation** occurring exactly at $Z = 0$.
* A **stable limit cycle** with a steady-state radius of $r = \sqrt{Z}$ for $Z > 0$.

---

## Simulation Method
Rather than continuously varying the control parameter during a single simulation, this implementation performs a precise parameter sweep. For every value of $Z$:
1. The system is initialized near equilibrium.
2. The equations are integrated using the explicit Euler method.
3. Initial transient dynamics are discarded to ensure steady-state behaviors.
4. The steady-state oscillation amplitude is measured.
5. The measured amplitude is compared directly with the analytical prediction.

This systematic approach produces a true, calculated numerical bifurcation diagram.

---

## Visualizations
The simulation script generates four complementary figures:
* **1. Bifurcation Diagram:** Shows the numerical oscillation amplitude as a function of the control parameter $Z$. The measured amplitudes are directly compared with the theoretical prediction $r = \sqrt{Z}$, illustrating the characteristic square-root amplitude scaling of a Supercritical Hopf Bifurcation.
* **2. Phase Portrait (Stable Spiral):** For $Z < 0$, trajectories spiral tightly toward the origin. This represents a stable equilibrium where external perturbations gradually decay.
* **3. Phase Portrait (Stable Limit Cycle):** For $Z > 0$, trajectories rapidly converge onto a closed orbit. The equilibrium at the origin becomes unstable, and the persistent oscillation itself becomes the stable attractor.
* **4. Radius Evolution:** The oscillation radius $r = \sqrt{E^2 + I^2}$ is plotted over time and compared with the theoretical steady-state radius $r = \sqrt{Z}$, demonstrating the swift convergence of the numerical solution.

---

## Computational Neuroscience Interpretation


Although simplified, the model captures a fundamental mechanism underlying rhythmic neural activity. The variables may be interpreted as interacting excitatory and inhibitory neural populations:
* Excitatory activity increases inhibitory activity.
* Inhibitory activity suppresses excitatory activity.
* Their recurrent interaction produces natural oscillatory dynamics.

The bifurcation parameter determines whether these rhythmic oscillations decay back to baseline or become self-sustaining. Hopf bifurcations appear widely in advanced computational neuroscience frameworks, including neural mass models, cortical oscillation models, and theoretical studies of epileptic seizure onset.

---

## Learning Objectives
This project demonstrates:
* The canonical Supercritical Hopf Bifurcation mechanics.
* Stable fixed points vs. stable limit cycles.
* Spiral attractors in phase space.
* Nonlinear amplitude saturation.
* Parameter sweeps for numerical bifurcation analysis.
* Validation of numerical simulations against analytical equations.

---

## References
* **Bifurcation Theory Foundation:** Standard dynamical systems texts on Hopf normal forms.
* **Neural Oscillations:** References exploring the conversion of steady inputs into rhythmic neural patterns via bifurcation pathways.

---

## Repository Purpose
This project is part of a larger collection of computational neuroscience implementations developed to build an intuitive understanding of neural dynamics, bifurcation theory, and dynamical systems through progressively more realistic mathematical models.
