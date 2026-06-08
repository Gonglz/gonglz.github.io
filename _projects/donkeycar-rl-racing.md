---
title: "Sim-to-Real Autonomous Racing on Jetson Nano"
excerpt: "An engineering case study of a DonkeyCar / JetRacer reinforcement learning stack, from multi-scene PPO training to Jetson TensorRT deployment, safety gates, and reproducible shadow validation."
classes: wide
---

<div class="case-study-hero" markdown="1">
<div class="case-study-hero__copy" markdown="1">

## Reinforcement learning, multimodal perception, and edge deployment for a small autonomous racing platform

This project is an end-to-end autonomous racing system built around DonkeyCar, DonkeySim, Jetson Nano, and a Waveshare JetRacer-style vehicle. The goal was not just to train a reinforcement learning policy in simulation, but to carry that policy through the real deployment chain: sensors, model export, embedded inference, control adaptation, runtime logging, and safety validation.

I treated the project as a **sim-to-real systems engineering problem**. The final engineering stack connects camera input, 360-degree LiDAR, RP2040 telemetry, a multimodal recurrent PPO actor, action adaptation, Jetson-side monitoring, TensorRT inference, and shadow-mode validation.

</div>
<div class="case-study-hero__panel" markdown="1">

**Project type**  
Autonomous systems / Reinforcement learning / Edge AI

**Platform**  
Jetson Nano + DonkeyCar / Waveshare JetRacer

**Core stack**  
Python, DonkeyCar, Stable-Baselines3, PyTorch, ONNX, TensorRT, ROS LiDAR

**Status**  
V17 endpoint deployment chain completed and frozen in shadow mode. Active obstacle-avoidance performance remains a separate model-quality problem.

</div>
</div>

<div class="metric-grid" markdown="1">

<div class="metric-card" markdown="1">
<span class="metric-card__label">Model</span>
<strong>RecurrentPPO multimodal actor</strong>
<span>6-channel semantic image, state vector, LiDAR sectors, and LSTM state</span>
</div>

<div class="metric-card" markdown="1">
<span class="metric-card__label">Sensors</span>
<strong>Camera + 360° LiDAR + RP2040</strong>
<span>Vision, range sectors, telemetry, scan-age awareness, and runtime diagnostics</span>
</div>

<div class="metric-card" markdown="1">
<span class="metric-card__label">Deployment</span>
<strong>ONNX → TensorRT FP16</strong>
<span>Actor-only export, TensorRT engine, CUDA runtime wrapper, and Jetson shadow backend</span>
</div>

<div class="metric-card" markdown="1">
<span class="metric-card__label">Validation</span>
<strong>180s / 10min / 20min shadow runs</strong>
<span>Preflight checks, safety counters, CSV summaries, and non-takeover shadow mode</span>
</div>

</div>

## Engineering Problem

A simulator-trained racing policy cannot be dropped directly onto a physical Jetson-powered car. The failure modes are coupled:

- simulation and real vehicle dynamics do not match;
- camera, LiDAR, and telemetry streams arrive at different rates;
- Jetson Nano has tight compute, memory, and runtime constraints;
- DonkeyCar, Gym, Stable-Baselines3, TensorFlow/Keras, PyTorch, and Jetson Python versions create deployment friction;
- logging and telemetry can block the vehicle loop if implemented naively;
- a policy that looks stable in simulation can still be unsafe or unusable on real hardware.

The project therefore evolved from a reinforcement learning experiment into a full deployment-oriented autonomy stack.

## System Architecture

<div class="architecture-flow" markdown="1">

<div markdown="1">**DonkeyCar / DonkeySim**<br><span>multi-scene PPO training</span></div>
<div markdown="1">**Policy export**<br><span>Keras, PyTorch weights, ONNX</span></div>
<div markdown="1">**Jetson runtime**<br><span>camera, LiDAR, RP2040</span></div>
<div markdown="1">**V17 actor backend**<br><span>PyTorch / TensorRT FP16</span></div>
<div markdown="1">**Action + safety layer**<br><span>adapter, gates, shadow logs</span></div>

</div>

The final V17 runtime path is:

```text
CSI camera + 360° LiDAR /scan + RP2040 telemetry
        ↓
Semantic image preprocessing + LiDAR sectorization + state vector
        ↓
V17 RecurrentPPO actor backend
        ↓
Action adapter + deployment safety gate
        ↓
Shadow-mode logging or real actuator path
        ↓
CSV, summary JSON, telemetry, and reproducible reports
```

The deployed model is not a simple image-only CNN. It uses a dictionary observation with semantic image channels, ego-state features, LiDAR range/validity sectors, timing metadata, and persistent LSTM state.

## My Engineering Contribution

<div class="contribution-grid" markdown="1">

<div markdown="1">
### Training Infrastructure
Built PPO training loops, parallel simulation workflows, curriculum logic, reward shaping, checkpointing, monitoring, and multi-scene sampling.
</div>

<div markdown="1">
### Deployment Interface
Created practical model bridges from PPO to Jetson, including PPO-to-Keras distillation and direct PyTorch policy-weight inference.
</div>

<div markdown="1">
### Multimodal Perception
Integrated camera features, semantic image channels, LiDAR sectors, timing metadata, and vehicle telemetry into policy observations.
</div>

<div markdown="1">
### Sim-to-Real Alignment
Measured simulator-vs-real differences in steering, throttle, control frequency, LiDAR semantics, and vehicle response.
</div>

<div markdown="1">
### Runtime Optimization
Profiled the Jetson chain and moved bottlenecks out of the vehicle loop: LiDAR sectorization, async logging, and telemetry caching.
</div>

<div markdown="1">
### Safety and Validation
Added engine/metadata preflight checks, LiDAR/RP2040 gates, inference timeout counters, safety summaries, and shadow-mode validation.
</div>

</div>

## Project Timeline

This timeline compresses the raw weekly engineering logs into a public engineering story. It intentionally uses **large implementation milestones**, not weekly status updates.

<div class="project-timeline" markdown="1">

<article class="timeline-node timeline-node--major" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Jul 2025</span>
<img src="/assets/images/projects/smartcar-timeline/2025-07-parallel-sim.jpg" alt="Parallel DonkeySim training windows" class="timeline-thumb">

### 1. Stable PPO Training Foundation

Built the first usable reinforcement learning baseline and stabilized the simulator training loop.

<div class="timeline-detail" markdown="1">

- Fixed deadlocks, NumPy crashes, reconnect failures, and simulator recovery issues.
- Added monitoring for reward, speed, deviation, collisions, and efficiency.
- Implemented early safeguards against catastrophic forgetting and unstable CTE behavior.
- Moved from isolated experiments toward parallel training and reproducible runs.

</div>
</div>
</article>

<article class="timeline-node" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Jul–Aug 2025</span>
<img src="/assets/images/projects/smartcar-timeline/2025-08-yolo-coach.jpg" alt="YOLO perception overlay from follower car camera" class="timeline-thumb">

### 2. Multi-Agent and Multimodal Exploration

Expanded the project from single-car lane following to multi-car interaction, camera perception, LiDAR, and overtaking logic.

<div class="timeline-detail" markdown="1">

- Launched multi-car / multi-environment training experiments.
- Added camera detection modules and early overtaking decision logic.
- Integrated LiDAR as an additional observation channel.
- Built a dual-car YOLO + Coach prototype for collision risk, following distance, and overtaking advice.

</div>
</div>
</article>

<article class="timeline-node timeline-node--major" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Sep 2025</span>
<img src="/assets/images/projects/smartcar-timeline/2025-09-jetson-baseline.jpg" alt="Jetson camera and simulator validation view" class="timeline-thumb">

### 3. Real-Car Deployment Contract

Validated the full DonkeyCar deployment path on Jetson before forcing reinforcement learning models into the vehicle stack.

<div class="timeline-detail" markdown="1">

- Trained and deployed a compatible KerasLinear `.h5` baseline.
- Verified the CSICamera → model inference → Web Controller → real vehicle control path.
- Clarified deployment contracts for image size, RGB preprocessing, steering range, throttle range, and model output order.
- Used the baseline as the reference interface for later RL deployment.

</div>
</div>
</article>

<article class="timeline-node" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Sep–Oct 2025</span>
<img src="/assets/images/projects/smartcar-timeline/2025-10-distilled-model.jpg" alt="Distilled DonkeyCar model running in a simulated indoor track" class="timeline-thumb">

### 4. RL-to-Jetson Model Bridge

Created practical deployment routes for reinforcement learning policies under Jetson Nano compatibility constraints.

<div class="timeline-detail" markdown="1">

- Built a PPO-to-distilled-Keras `.h5` pipeline for DonkeyCar compatibility.
- Removed fragile TensorFlow Lambda dependencies for Jetson Nano deployment.
- Rebuilt the RL environment around compatible DonkeyCar, Gym, SB3, Python, and Jetson versions.
- Later adopted a direct `.pth` policy-weight inference route to avoid SB3/cloudpickle `.zip` deserialization problems.

</div>
</div>
</article>

<article class="timeline-node timeline-node--major" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Nov 2025</span>

### 5. Multimodal PPO and Curriculum Learning

Moved beyond image-only policies into camera + LiDAR early fusion and curriculum-driven control improvement.

<div class="timeline-detail" markdown="1">

- Built a 6-channel vision pipeline with RGB, yellow mask, Canny edges, and motion-related features.
- Added LiDAR sector features and CNN + MLP fusion for policy input.
- Introduced curriculum learning for speed, CTE tolerance, penalties, and safe-distance behavior.
- Deployed the multimodal policy path to Jetson Nano for early real-car testing.

</div>
</div>
</article>

<article class="timeline-node" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Feb–Mar 2026</span>
<img src="/assets/images/projects/smartcar-timeline/2026-03-multiscene-features.jpg" alt="Multi-scene semantic feature analysis across simulated tracks" class="timeline-thumb">

### 6. System-Level Sim-to-Real Architecture

Shifted from “train a model” to “align the whole autonomy system.”

<div class="timeline-detail" markdown="1">

- Added action safety layers: slew-rate limiting, low-pass filtering, smoothness penalties, and mismatch diagnostics.
- Replaced direct actuation with high-level action targets executed by a lower-level controller.
- Refactored reset/spawn logic to reduce invalid episodes and NPC-coupled failures.
- Built FiLM/LSTM-based semantic observation and action adapter components for multi-scene training.
- Validated dual-domain training across Waveshare and Generated Track domains before adding obstacle-oriented training.

</div>
</div>
</article>

<article class="timeline-node" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">Apr 2026</span>
<img src="/assets/images/projects/smartcar-timeline/2026-04-real-track.jpg" alt="Real taped track with Jetson-based smart cars and obstacle boxes" class="timeline-thumb">

### 7. Hardware Alignment and Edge Limits

Closed the loop back to the physical vehicle by measuring real hardware behavior and edge-device constraints.

<div class="timeline-detail" markdown="1">

- Compared simulator and real-car steering, throttle, control frequency, and sensor behavior.
- Debugged servo center, PWM frequency, motor response, and LiDAR representation issues.
- Measured LiDAR timing and identified camera/LiDAR/control-loop mismatch.
- Benchmarked an on-device LLM strategy sidecar and concluded it was not suitable for real-time racing control on Jetson Nano.

</div>
</div>
</article>

<article class="timeline-node timeline-node--major" tabindex="0" markdown="1">
<div class="timeline-card" markdown="1">
<span class="timeline-date">May 2026</span>

### 8. V17 Endpoint Deployment Freeze

Completed the Jetson-side engineering deployment chain and froze the endpoint validation scope.

<div class="timeline-detail" markdown="1">

- Exported the V17 actor through ONNX and built a TensorRT FP16 engine.
- Implemented CUDA runtime inference without adding PyCUDA as a deployment dependency.
- Moved LiDAR sectorization out of the main vehicle loop.
- Converted DataCollector to asynchronous logging and cached Jetson telemetry in a background thread.
- Added engine/metadata preflight, LiDAR/RP2040 freshness gates, inference timeout counters, and shadow non-takeover validation.
- Completed repeated TensorRT shadow validation, including 180-second, 10-minute, and 20-minute runs.

</div>
</div>
</article>

</div>

## Selected Engineering Results

| Area | Result |
|---|---|
| Model deployment | Actor-only ONNX export and TensorRT FP16 runtime on Jetson Nano |
| Runtime profiling | Separated actor inference from image preprocessing, LiDAR processing, logging, and telemetry overhead |
| TensorRT benefit | Actor residual roughly halved in optimized PyTorch vs TensorRT A/B comparisons |
| Logging | DataCollector moved from blocking synchronous writes to asynchronous queue-based logging |
| LiDAR processing | 360-degree LiDAR sectorization moved out of the main vehicle loop |
| Safety checks | Engine, metadata, LiDAR, RP2040, and inference-timeout gates added before or during runtime |
| Shadow validation | Final endpoint chain validated through repeated non-takeover TensorRT shadow runs |

<div class="limitation-box" markdown="1">

### Scope and Limitation

The V17 endpoint deployment milestone evaluates the **Jetson-side engineering chain**: model export, TensorRT inference, runtime stability, logging, safety gates, and shadow-mode reproducibility.

It does **not** claim that the model has solved real-car obstacle avoidance, full active closed-loop racing, or multi-vehicle overtaking. Those remain policy-quality and active-validation problems, not endpoint-deployment conclusions.

</div>

## What This Project Demonstrates

This project demonstrates my ability to work across the full stack of an autonomous system:

- reinforcement learning training and curriculum design;
- multimodal perception and sensor preprocessing;
- embedded AI deployment on Jetson Nano;
- real-time runtime profiling and bottleneck isolation;
- hardware debugging across camera, LiDAR, PWM, motor, and telemetry layers;
- sim-to-real alignment for dynamics and sensor timing;
- safety-oriented validation and reproducible experiment reporting.

The value of the project is not a single checkpoint. The value is the engineering process that turned a fragile research prototype into a measurable, debuggable, and deployable edge autonomy system.

## Recognition

- **05/28/2026**: Received the **2026 Outstanding Master's Student Award in Computer Engineering** as a master's student RA. The announcement was shared by [IntelliSys Lab](https://intellisys.haow.us/), with the SES community event [video timestamp](https://youtu.be/c1m_otsr8sM?si=woDszEBnCbNG9tgU&t=1057).

## Links

- [GitHub Repository](https://github.com/Gonglz/DonkeyCar-RL-Racing)
- [Projects Overview](/projects/)
