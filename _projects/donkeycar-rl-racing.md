---
title: "DonkeyCar RL Racing"
excerpt: "Simulator-to-device reinforcement learning workflow for autonomous driving experiments on DonkeyCar and Jetson platforms."
classes: wide
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

## Recognition

- **05/28/2026**: Received the **2026 Outstanding Master's Student Award in Computer Engineering** as a master's student RA. The announcement was shared by [IntelliSys Lab](https://intellisys.haow.us/), with the SES community event [video timestamp](https://youtu.be/c1m_otsr8sM?si=woDszEBnCbNG9tgU&t=1057).

## Project Timeline

This timeline compresses the raw weekly engineering logs into a public project story. It keeps only the major inflection points: system stability, perception, sim-to-real deployment, multi-agent work, generalization, and hardware alignment.

<div class="project-timeline" markdown="1">

<article class="timeline-node" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Jul 2025</span>
<img src="/assets/images/projects/smartcar-timeline/2025-07-parallel-sim.jpg" alt="Parallel DonkeySim training windows" class="timeline-thumb">

### Stable PPO and Parallel Simulation

Built the first stable PPO training loop and moved from single-run experiments toward parallel simulator workflows.

<div class="timeline-detail" markdown="1">

- Fixed deadlocks, NumPy crashes, reconnect failures, and simulator recovery issues.
- Added reward, speed, deviation, collision, and efficiency monitoring.
- Identified CPU saturation during PPO updates as a key bottleneck for multi-simulator training.

</div>
</div>
</article>

<article class="timeline-node timeline-node--major" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Aug 2025</span>
<img src="/assets/images/projects/smartcar-timeline/2025-08-yolo-coach.jpg" alt="YOLO perception overlay from follower car camera" class="timeline-thumb">

### Perception and Coach Layer

Added a perception layer for dual-car experiments, connecting camera detections to higher-level driving advice.

<div class="timeline-detail" markdown="1">

- Integrated YOLO-style detection for vehicles, cones, signs, and lane cues.
- Built a Coach module that reasoned over following distance, collision risk, and overtaking opportunities.
- Started converting perception outputs into structured JSON for local model-assisted analysis.

</div>
</div>
</article>

<article class="timeline-node" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Sep 2025</span>
<img src="/assets/images/projects/smartcar-timeline/2025-09-jetson-baseline.jpg" alt="Jetson camera and simulator validation view" class="timeline-thumb">

### Jetson Baseline Deployment

Validated the full DonkeyCar deployment path on Jetson before forcing reinforcement learning models into the vehicle stack.

<div class="timeline-detail" markdown="1">

- Trained and deployed a compatible KerasLinear `.h5` baseline.
- Verified the pipeline from CSICamera to model inference, Web Controller, and real vehicle control.
- Clarified model contracts: image shape, RGB preprocessing, steering range, and throttle range.

</div>
</div>
</article>

<article class="timeline-node timeline-node--major" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Oct 2025</span>
<img src="/assets/images/projects/smartcar-timeline/2025-10-distilled-model.jpg" alt="Distilled DonkeyCar model running in a simulated indoor track" class="timeline-thumb">

### PPO to Vehicle-Ready Models

Created practical deployment routes for reinforcement learning policies on Jetson Nano.

<div class="timeline-detail" markdown="1">

- Built a PPO-to-distilled-Keras `.h5` pipeline that could run through DonkeyCar.
- Removed TensorFlow Lambda dependencies to improve Jetson Nano compatibility.
- Later adopted a direct PyTorch inference path by exporting policy weights to `.pth`, reducing model size and avoiding fragile `.zip` deserialization.

</div>
</div>
</article>

<article class="timeline-node" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Feb 2026</span>
<img src="/assets/images/projects/smartcar-timeline/2026-02-obstacle-training.jpg" alt="Generated track with static obstacles in DonkeySim" class="timeline-thumb">

### Safety-Aware Training and Obstacle Behavior

Moved from lane following toward safety-aware control, smoother actuation, and obstacle-aware behavior.

<div class="timeline-detail" markdown="1">

- Upgraded observations to include RGB differences, yellow masks, and edge channels.
- Added action safety logic: slew-rate limits, low-pass filtering, smoothness penalties, and mismatch diagnostics.
- Observed early obstacle-aware behavior such as slowing down and reversing as recovery.

</div>
</div>
</article>

<article class="timeline-node timeline-node--major" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Mar 2026</span>
<img src="/assets/images/projects/smartcar-timeline/2026-03-multiscene-features.jpg" alt="Multi-scene semantic feature analysis across simulated tracks" class="timeline-thumb">

### Multi-Scene Generalization

Reworked the training stack around cross-map generalization, semantic observations, and a more stable action hierarchy.

<div class="timeline-detail" markdown="1">

- Introduced multi-scene sampling across Waveshare, generated, mini-monaco, and racing-league-style tracks.
- Replaced raw action output with high-level steering and throttle targets executed by a lower-level controller.
- Added semantic observation channels and feature analysis to make map transfer less brittle.

</div>
</div>
</article>

<article class="timeline-node" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Apr 2026</span>
<img src="/assets/images/projects/smartcar-timeline/2026-04-real-track.jpg" alt="Real taped track with Jetson-based smart cars and obstacle boxes" class="timeline-thumb">

### Real-Car Alignment and Edge Limits

Closed the loop back to hardware by comparing simulator behavior with real vehicle dynamics and testing edge-device limits.

<div class="timeline-detail" markdown="1">

- Measured simulator-vs-real differences in steering, throttle, control frequency, sensors, and LiDAR semantics.
- Debugged servo center, PWM behavior, motor issues, and LiDAR data representation.
- Benchmarked an on-device LLM strategy sidecar and concluded it was better suited for offline or training-time assistance than real-time racing control.

</div>
</div>
</article>

</div>

## What I Learned

- How simulation workflows differ from physical vehicle deployment
- Why repeatable configuration and track profiles matter for RL experiments
- How hardware constraints shape model deployment decisions

## Links

- [GitHub Repository](https://github.com/Gonglz/DonkeyCar-RL-Racing)
- [Projects Overview](/projects/)
