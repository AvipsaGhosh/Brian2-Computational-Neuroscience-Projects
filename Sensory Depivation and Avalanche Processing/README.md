# Homeostatic Synaptic Scaling in a Recurrent Spiking Network
### A Computational Neuroscience Model in Python

---

## Overview
This project implements a recurrent Leaky Integrate-and-Fire (LIF) network that demonstrates homeostatic synaptic scaling following sensory deprivation. The model consists of excitatory and inhibitory neuronal populations connected through a recurrent weight matrix that obeys Dale's Law. 

During the simulation, external sensory input is reduced to mimic deprivation, after which neurons locally adjust the strength of their incoming excitatory synapses in an attempt to recover their target firing rate.

In addition to monitoring network activity and synaptic weight evolution, the project also analyzes neuronal avalanche statistics, allowing changes in collective network dynamics before and after deprivation to be compared.

---

## Biological Motivation
Neural circuits must maintain stable activity despite continual changes in sensory input, development, and learning. One important mechanism that supports this stability is **homeostatic synaptic scaling**, in which neurons multiplicatively adjust synaptic strengths to maintain an approximately constant firing rate.

This simulation demonstrates the basic principles of homeostatic regulation by showing how a recurrent spiking network responds to a sudden reduction in external input and gradually compensates through synaptic adaptation.

---

## Features
* Recurrent Leaky Integrate-and-Fire (LIF) network architecture
* Separate excitatory and inhibitory neuronal populations satisfying Dale's Law
* Multiplicative homeostatic scaling of excitatory synapses
* Sensory deprivation paradigm implementation
* Continuous firing-rate estimation using exponential averaging
* Neuronal avalanche detection, size, and duration analysis
* Complete visualization of network dynamics and synaptic adaptation

---

## Network Architecture
The network contains a total of 100 recurrently connected neurons:
* **80** Excitatory neurons
* **20** Inhibitory neurons

Each individual neuron receives:
1. External sensory input
2. Recurrent synaptic input from the network
3. Gaussian background noise

Neuron membrane potentials evolve according to a standard Leaky Integrate-and-Fire model with threshold-reset dynamics.

---

## Homeostatic Plasticity
Each neuron maintains a slowly varying estimate of its recent firing activity using an exponential moving average. 

When a neuron's firing rate falls below a predefined target, the strengths of its incoming excitatory synapses are increased. Conversely, if the firing rate exceeds the target, those synapses are weakened. This implements a simplified form of multiplicative homeostatic synaptic scaling, a mechanism observed experimentally in cortical circuits.

---

## Experimental Protocol
The simulation runtime is divided into three distinct functional phases:

| Phase | Description |
| :--- | :--- |
| **1. Baseline** | Normal external sensory input is provided. Network activity stabilizes reliably around the target firing rate. |
| **2. Sensory Deprivation** | External input is suddenly reduced, causing network activity levels to plummet. |
| **3. Homeostatic Recovery** | Synaptic scaling gradually compensates for the reduced input, pulling the collective activity back toward baseline. |

---

## Neuronal Avalanche Analysis
Following the simulation run, neuronal avalanches are identified as contiguous periods of non-zero population activity. For each detected avalanche, two distinct structural quantities are computed:
* **Avalanche size:** The total number of spikes recorded across the network during the event.
* **Avalanche duration:** The number of consecutive active time steps the event spans.

Probability distributions for both quantities are compared across the baseline, deprivation, and recovery phases to track the critical dynamics of the system.

---

## Output Visualizations
The simulation script automatically processes the data to generate four complementary figures:
* **Figure 1:** Network firing-rate dynamics across all experimental phases.
* **Figure 2:** Mean excitatory synaptic weight evolution over time.
* **Figure 3:** Probability distribution of avalanche sizes.
* **Figure 4:** Probability distribution of avalanche durations.

These visualizations cleanly summarize both the local homeostatic adaptation of individual neurons and the emergent collective dynamics of the whole network.

---

## References
Turrigiano, G. G. (2008). The Self-Tuning Neuron: Synaptic Scaling of Excitatory Synapses. Cell.

Dayan, P., & Abbott, L. F. (2001). Theoretical Neuroscience.

Gerstner, W., Kistler, W., Naud, R., & Paninski, L. Neuronal Dynamics
