---
title: "DonkeyCar RL Racing"
excerpt: "Simulator-to-device reinforcement learning workflow for autonomous driving experiments on DonkeyCar and Jetson platforms."
---

## One-line Summary

Deploying reinforcement learning policies to a DonkeyCar platform with a simulator-to-device workflow.

## Problem

Small autonomous vehicles are useful learning platforms, but the full loop from simulation to physical deployment can be hard to organize. This project focuses on making the reinforcement learning workflow concrete: training policies, managing track profiles, and preparing models for deployment on resource-constrained hardware.

## System Architecture

The project is organized around a simulator-to-device workflow:

- Simulation and training environment for reinforcement learning experiments
- Track profiles and configuration files for repeatable runs
- Model and module structure for policy training and evaluation
- Jetson-oriented deployment path for running experiments closer to the vehicle

## My Contribution

- Structured the project around reinforcement learning experiments for DonkeyCar
- Organized training, testing, and deployment-related code paths
- Worked with edge hardware constraints as part of the autonomous driving workflow
- Documented the workflow so experiments can be repeated and extended

## Technical Stack

`Python` `DonkeyCar` `Reinforcement Learning` `Jetson` `Computer Vision` `Edge AI`

## Results / Current Status

This is the strongest flagship project for the site because it combines autonomous systems, reinforcement learning, and edge deployment in one coherent engineering story.

## What I Learned

- How simulation workflows differ from physical vehicle deployment
- Why repeatable configuration and track profiles matter for RL experiments
- How hardware constraints shape model deployment decisions

## Links

- [GitHub Repository](https://github.com/Gonglz/DonkeyCar-RL-Racing)
- [Projects Overview](/projects/)
