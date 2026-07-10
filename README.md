# Biologically Parameterized Drift Diffusion Model (BioDDM)
### A Computational Neuroscience Framework for Linking Brain Circuits to Decision-Making Behavior

---

## Overview
This project implements a biologically inspired extension of the classical Drift Diffusion Model (DDM), one of the most widely used computational models of perceptual decision making. Unlike a traditional DDM, where parameters such as drift rate or decision threshold are chosen directly, this implementation introduces an intermediate biological layer. Functional properties of cortical and subcortical brain regions are first represented as abstract neural variables, which are then mapped onto the latent parameters of the diffusion model.

This creates a multi-level computational framework that links:
> **Neural Circuit State** → **Cognitive Computation** → **Observable Behavior**

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
1. **Brain State**
2. **Biological Mapper**
3. **Drift Diffusion Parameters** ($v$, $\sigma$, $a$, $T_{er}$)
