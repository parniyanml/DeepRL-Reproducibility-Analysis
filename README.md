# Reproducibility Analysis in Deep Reinforcement Learning

This repository contains the comprehensive report and presentation slides for a research project on **Deep Reinforcement Learning (Deep RL)**. The project focuses on the critical issue of reproducibility in continuous control tasks.

**Author:** Parniyan Malekzadeh  
**Supervisor:** Prof. Mohammad Hossein Manshaei  
**Institution:** Isfahan University of Technology (IUT)

##  Project Overview
Reproducing state-of-the-art Deep RL results is often challenging due to non-determinism in standard benchmarks and intrinsic variance in algorithms. This project investigates these challenges by conducting a comparative analysis of policy gradient methods.

We examine the impact of:
- **Hyperparameters** (Network architecture, Activation functions like ReLU/Tanh)
- **Random Seeds** and statistical significance
- **Environment Dynamics** (MuJoCo environments: HalfCheetah, Hopper, Swimmer)

##  Algorithms Implemented & Analyzed
The study evaluates the performance and stability of the following algorithms:
- **TRPO** (Trust Region Policy Optimization)
- **DDPG** (Deep Deterministic Policy Gradient)
- **PPO** (Proximal Policy Optimization)
- **ACKTR** (Actor-Critic using Kronecker-Factored Trust Region)

##  Key Results
- **Sensitivity:** The analysis highlights how minor changes in codebases or hyperparameters can lead to drastically different results.
- **Reporting Standards:** We propose guidelines for more robust experimental reporting, emphasizing the necessity of confidence intervals over simple average returns.
- **Performance:** Comparative plots demonstrate the variance of algorithms like DDPG versus more stable methods like PPO across different random seeds.

##  Contents
- `report/`: The detailed project report (PDF), including mathematical formulations and experimental results.
- `slides/`: Presentation slides summarizing the methodology and findings.

---
*This project was conducted under the supervision of the Department of Electrical and Computer Engineering at IUT.*
