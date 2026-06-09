---
title: "Resume"
permalink: /resume/
---

# Longzhao Gong

**Edge AI / Robotics / ML Systems**  
Hoboken, NJ · [gonglz@hotmail.com](mailto:gonglz@hotmail.com) · [+1 551-376-8192](tel:+15513768192) · [LinkedIn](https://linkedin.com/in/gonglz) · [GitHub](https://github.com/Gonglz)

[Download English PDF](/resume_edge.pdf){: .btn .btn--primary}
[下载中文简历 PDF](/%E5%BC%93%E9%BE%99%E6%98%AD%E7%AE%80%E5%8E%86.pdf){: .btn .btn--primary}

M.S. Computer Engineering candidate specializing in edge inference, GPU acceleration, robotics/IoT deployment, and performance-critical ML systems. Built and validated systems across the stack, from C/CUDA/OpenMP compression kernels and distributed GNN training to Jetson TensorRT edge deployment, with reproducible benchmarks, correctness gates, and quantified latency/speedup results.

## Education

**Stevens Institute of Technology**, Hoboken, NJ  
M.S. in Computer Engineering, GPA: 3.94/4.00 · Sep 2024 - May 2026  
Relevant Coursework: Embedded Systems, Machine Learning, CUDA Programming, Computer Architecture, Internet of Things

**Chang'an University**, Xi'an, China  
B.E. in Automation · Aug 2016 - Jun 2020  
Relevant Coursework: Automatic Control Theory, Digital Electronics, Analog Electronics

## Technical Skills

**Programming:** Python, C/C++, SQL, CUDA

**Machine Learning / Deep Learning:** PyTorch, Stable-Baselines3, RecurrentPPO, GNN, RL, Transformers, LSTM

**Edge AI / Model Deployment:** ONNX, TensorRT FP16, model conversion, low-latency inference

**Robotics / Perception / IoT:** DonkeyCar, LiDAR sectorization, camera, STM32, embedded control, sensor integration, IoT systems

**GPU / Systems Optimization:** CUDA kernels, shared memory, warp-level parallelism, OpenMP, SIMD

**Tools & Cloud:** Linux, Git, Docker, Azure, Azure Blob Storage, Azure Pipelines, Azure OpenAI, RAG, OpenAI fine-tuning

## Projects

**Jetson Nano Edge TensorRT Deployment for DonkeyCar Robot, IntelliSys Lab**  
Jul 2025 - Apr 2026

- Led sim-to-real deployment for a DonkeyCar RL robot by unifying simulator and Jetson sensor/action interfaces, enabling consistent camera-LiDAR policy inference from training to edge execution.
- Engineered a semantic vision encoder that converted raw camera frames into task-relevant lane, edge, obstacle, and motion features for more stable DonkeyCar RL observations.
- Hardened the real-time Jetson runtime by deploying ONNX/TensorRT FP16 inference and decoupling blocking LiDAR preprocessing, cutting actor-stage p95 latency by 58.4% vs. PyTorch and shrinking DataCollector latency from 537 ms to 5.67 ms.

**PeMS Spatiotemporal Traffic Forecasting with Graph Neural Networks**  
Mar 2025 - May 2025

- Built a reproducible PeMS GNN forecasting pipeline with anomaly-aware imputation, station graph construction, weather-aware features, and PyG GraphSAGE/NeighborSampler training.
- Scaled GraphSAGE with 2-GPU DDP workload sharding, achieving 1.43x speedup and validating a full-scale run over 33,177 timestamps, 4,883 stations, and 162M timestamp-station pairs.

**Azure OpenAI Academic & Career Guidance Platform, Stevens IT Quackathon**  
Apr 2025 - May 2025

- Built a team Azure AI prototype that collected student interests, academic goals, and career goals through Microsoft online forms, then stored user inputs and generated artifacts in Azure Blob Storage.
- Implemented a curriculum-grounded RAG workflow over Stevens course schedules, course descriptions, and syllabus materials to support personalized course recommendation and academic planning responses.
- Generated structured JSON training data with GPT and fine-tuned a GPT-3.5 Turbo model for academic route and career-path guidance; connected intake, storage, retrieval, model inference, and response generation through Azure pipeline-style workflows.
- Selected as a Top 25% Finalist at the Stevens IT Quackathon.

## Professional Experience

**APECS Lab, Stevens Institute of Technology**, Hoboken, NJ  
Research Assistant · Aug 2025 - Dec 2025

- Owned the FalCom/APPFL model-update compression acceleration path across Python/C ABI integration, native C codec implementation, OpenMP/SIMD CPU optimization, and guarded CUDA q8 experimental codec.
- Reduced ResNet50 CPU compression latency from 797.62 ms to 211.36 ms on 8 threads, a 3.77x speedup, by optimizing the native C codec with safe grouped OpenMP/SIMD.
- Achieved 9.37x CUDA compress-only / 10.8x closed-loop compress-decompress speedup under consistent profiling and correctness gates.

**Project Engineer, Foshan Guanggong Renewable Resources Recycling Co., Ltd.**  
Dec 2022 - Mar 2024

- Supported factory-area energy storage deployment planning by translating site constraints, capacity requirements, and equipment interfaces into implementation inputs for system design review.

**Research Assistant, School of Microelectronics, Xidian University**  
Aug 2020 - Oct 2022

- Integrated sensors and circuit-level embedded controls for high-speed train pneumatic test systems, supporting reliability-oriented data collection, actuator response testing, and control-loop validation.

## Honors & Awards

- Outstanding Master Student Award in Computer Engineering, Top 10% · May 2026
- Finalist Award, Top 25%, Stevens IT Quackathon Competition · Apr 2025
- Bronze Award, College Student Innovation & Entrepreneurship Competition · May 2020
- First Prize, Top 10%, RoboMaster China Robot Contest · Sep 2019

## Languages

Mandarin Chinese (native), English (fluent)
