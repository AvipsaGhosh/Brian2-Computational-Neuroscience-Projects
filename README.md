# Biologically Parameterized Drift Diffusion Model (BioDDM)
### A Computational Neuroscience Framework for Linking Brain Circuits to Decision-Making Behavior

---

## Overview
This project implements a biologically inspired extension of the classical Drift Diffusion Model (DDM), one of the most widely used computational models of perceptual decision making. Unlike a traditional DDM, where parameters such as drift rate or decision threshold are chosen directly, this implementation introduces an intermediate biological layer. Functional properties of cortical and subcortical brain regions are first represented as abstract neural variables, which are then mapped onto the latent parameters of the diffusion model.

This creates a multi-level computational framework that links:
Neural Circuit State → Cognitive Computation → Observable Behavior

The repository also includes an ADHD-inspired parameter set demonstrating how alterations in attention, cognitive effort, response caution, and motor preparation may influence reaction time distributions.

---

## Motivation
Behavioral measurements such as reaction time provide only indirect information about the neural processes responsible for decision making. Computational psychiatry attempts to bridge this gap by combining mathematical models of cognition with biologically motivated hypotheses regarding brain function.

The Drift Diffusion Model is particularly useful because it separates decision making into interpretable latent variables:
* **Evidence accumulation (drift rate):** The rate at which information is processed.
* **Internal uncertainty (noise):** Stochastic variation in the sampling process.
* **Decision threshold:** The amount of evidence required to commit to a choice.
* **Non-decision processes:** Time for sensory encoding and motor execution.

This project extends the classical model by assigning biological interpretations to these latent variables.

---

## Model Architecture
The framework is intentionally modular and consists of three independent layers:
1. Brain State
2. Biological Mapper
3. Drift Diffusion Parameters ($v$, $\sigma$, $a$, $T_{er}$)

### Layer 1 — Brain State
The first layer represents the functional state of several brain regions that contribute to perceptual decision making. These variables represent abstract functional quantities describing the effectiveness of different neural systems rather than literal firing rates.

| Brain Region | Functional Interpretation |
| :--- | :--- |
| **dlPFC** | Quality of sensory evidence and executive processing |
| **dmPFC** | Cognitive effort and conflict evaluation |
| **Superior Colliculus** | Precision of attentional and oculomotor processing |
| **pre-SMA** | Response caution and decision threshold regulation |
| **Frontal Eye Fields** | Motor preparation and execution delay |

### Layer 2 — Biological Mapper
The Biological Mapper converts neural circuit variables into the latent parameters required by the Drift Diffusion Model.
* **Drift Rate ($v$):** Evidence accumulation is modeled as a function where stronger dlPFC processing increases drift, while greater cognitive effort (dmPFC) may reduce effective evidence accumulation.
* **Noise ($\sigma$):** Internal stochastic variability is inversely related to attentional precision; greater Superior Colliculus precision produces lower internal noise.
* **Decision Threshold ($a$):** Response caution is associated with pre-SMA and basal ganglia circuitry. Higher thresholds require more evidence before committing.
* **Non-Decision Time ($T_{er}$):** Represents processes occurring outside evidence accumulation, including sensory encoding and motor execution. Frontal Eye Field conflict contributes to increased delays.

### Layer 3 — Drift Diffusion Model
The final layer performs evidence accumulation using the standard stochastic diffusion process. At each simulation step:
1. Evidence increases according to the drift rate.
2. Random fluctuations are introduced through Gaussian noise.
3. Accumulation continues until the positive or negative decision boundary is reached.

The simulation returns reaction time and decision outcome, with numerical integration performed using the Euler-Maruyama method.

---

## Experimental Conditions
The repository includes two example conditions for comparison.

### Healthy Control
* Strong executive evidence generation.
* Low cognitive effort and high attentional precision.
* Standard response threshold and minimal motor conflict.
* **Expected behavior:** Relatively fast reaction times and narrow distributions.

### ADHD-Inspired Compensatory Condition
* Reduced executive signal quality and increased cognitive effort.
* Reduced attentional precision and slightly elevated response caution.
* Increased motor preparation delay.
* **Expected behavior:** Slower evidence accumulation, broader distributions, and increased behavioral variability.

---

## Simulation Output
The primary output is a histogram showing reaction time distributions across repeated simulated trials.
* **Healthy condition:** Faster responses and tighter distributions.
* **ADHD-inspired condition:** Slower responses, greater variability, and a wider distribution of reaction times.

---

## Computational Neuroscience Concepts Demonstrated
* Drift Diffusion Models and evidence accumulation.
* Stochastic differential equations and Euler-Maruyama integration.
* Latent cognitive variables vs. observable behavior.
* Neural-to-cognitive parameter mapping.
* Computational phenotyping and modular model design.

---

## Design Philosophy
A key objective is the separation of biological hypotheses from mathematical computation. The Drift Diffusion Model itself contains no neuroscience-specific assumptions; biological interpretations are introduced through an independent mapping layer. This modularity allows testing alternative hypotheses, such as the effects of dopamine modulation, fatigue, Parkinson's disease, or schizophrenia, without modifying the underlying decision model.

---

## References
* Ratcliff, R. (1978). A theory of memory retrieval. *Psychological Review*, 85(2), 59–108.
* Ratcliff, R., & McKoon, G. (2008). The diffusion decision model: Theory and data for two-choice decision tasks. *Neural Computation*, 20(4), 873–922.
* Bogacz, R., Brown, E., Moehlis, J., Holmes, P., & Cohen, J. D. (2006). The physics of optimal decision making: A formal analysis of models of performance in two-alternative forced-choice tasks. *Psychological Review*, 113(4), 700–765.
* Forstmann, B. U., Ratcliff, R., & Wagenmakers, E.-J. (2016). Sequential Sampling Models in Cognitive Neuroscience. *Trends in Cognitive Sciences*, 20(10), 736–747.
