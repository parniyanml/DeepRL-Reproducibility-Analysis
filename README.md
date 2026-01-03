# DeepRL-Reproducibility-Analysis

A comprehensive study on the reproducibility of Deep Reinforcement Learning algorithms (TRPO, PPO, DDPG, ACKTR) in continuous control tasks.

## Overview

Reproducing results for state-of-the-art Deep Reinforcement Learning (RL) methods is often challenging. Factors such as non-determinism in standard benchmark environments, intrinsic variance in algorithms, and differences in implementation details can make reported results difficult to interpret.

This project investigates the challenges posed by reproducibility, experimental techniques, and reporting procedures. It illustrates the variability in reported metrics and results when comparing against common baselines and suggests guidelines to make future results in Deep RL more reproducible.

## Algorithms Studied

The analysis focuses on the following model-free policy gradient methods:

* **TRPO** (Trust Region Policy Optimization)
* **PPO** (Proximal Policy Optimization)
* **DDPG** (Deep Deterministic Policy Gradient)
* **ACKTR** (Actor-Critic using Kronecker-Factored Trust Region)

## Environments

Experiments were conducted using continuous control tasks from the OpenAI Gym MuJoCo suite, selected for their varying dynamic properties:

* **HalfCheetah-v1:** Represents stable dynamics where agents generally learn to run forward effectively.
* **Hopper-v1:** Represents unstable dynamics where agents must balance; failure results in shortened trajectories.
* **Swimmer-v1:** A fluid-like environment where local optima (e.g., flailing without moving) are common.
* **Walker2d-v1:** A bipedal locomotion task requiring significant coordination.

## Key Factors Analyzed

This study isolates and analyzes specific factors affecting the reproducibility of the algorithms listed above:

### 1. Hyperparameters and Network Architecture
The project evaluates the impact of network structures and activation functions on performance.
* **Architectures:** Multi-Layer Perceptrons (MLP) with varying hidden layer sizes (e.g., 64x64, 400x300, 100x50x25).
* **Activation Functions:** ReLU, Tanh, Leaky ReLU, and ELU.
* **Finding:** Performance is highly sensitive to simple changes in activation functions or architecture size. For example, DDPG performance can vary significantly depending on whether ReLU or Tanh is used for the critic network.

### 2. Random Seeds and Trial Counts
We demonstrate that changing only the random seed can lead to statistically different distributions of results.
* **Observation:** Averaging a small number of trials (e.g., 5) can produce misleading learning curves.
* **Recommendation:** Reporting results based on a larger number of trials and utilizing bootstrap confidence intervals is essential for accuracy.

### 3. Environment Properties
The study highlights how algorithmic performance is tied to specific environment dynamics.
* **Dynamics:** DDPG outperforms others in stable environments like HalfCheetah but struggles in unstable environments like Hopper due to exploration noise causing early failures.
* **Local Optima:** In the Swimmer environment, TRPO significantly outperforms other methods, which often get stuck in local optima (flailing without swimming).

### 4. Codebase Variations
We compared different open-source implementations of the same algorithms (e.g., OpenAI Baselines vs. rllab implementations).
* **Finding:** Implementation details not always reflected in papers can lead to drastic differences in performance. A comparison of TRPO codebases showed significant divergence in average returns despite using identical hyperparameters.

## Evaluation Metrics

To ensure robust reporting, this project utilizes the following metrics:
* **Average Return:** The mean cumulative reward over the learning process.
* **Confidence Intervals:** 95% bootstrap confidence intervals to visualize the variance in performance.
* **Significance Testing:** Application of statistical tests (e.g., Kolmogorov-Smirnov, t-tests) to determine if improvements are statistically significant.

## Conclusion

The results indicate that sources of non-determinism—both internal (random seeds, environment dynamics) and external (hyperparameters, codebases)—contribute heavily to the difficulty of reproducing baselines. To sustain progress in the field, it is critical to report all experimental details, release codebases, and use proper statistical significance metrics rather than relying solely on maximum rewards or top-N trials.

## Author and Credits

**Author:** Parniyan Malekzadeh  
**Supervisor:** Dr. Manshaei  
**Institution:** Isfahan University of Technology  
