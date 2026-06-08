---
title: "FalCom / APPFL Compressor Acceleration"
excerpt: "Python/C ABI integration, native C codec work, OpenMP/SIMD CPU optimization, and guarded CUDA q8 experiments for model-update compression."
---

## One-line Summary

Accelerating a FalCom / APPFL model-update compression workflow across Python/C ABI integration, native C codec work, OpenMP/SIMD CPU optimization, and guarded CUDA q8 experiments.

## Problem

Gradient and model-update compression can reduce payload size in distributed and federated learning workflows, but the compressor implementation has to balance compression ratio, reconstruction quality, runtime, and integration overhead. This APECS Lab research-assistant project focused on making the compressor path fast while keeping correctness gates and profiling evidence intact.

## System Architecture

The project was organized around four implementation and reporting tracks:

- Python/C ABI integration for connecting FalCom with APPFL-side workflows
- Native C codec implementation with auditable baseline behavior
- CPU acceleration using safe grouped OpenMP/SIMD optimization
- Guarded CUDA q8 experimental codec work for GPU feasibility testing
- Reports, logs, CSVs, environment notes, and tests for reproducible comparison

## My Contribution

- Owned the FalCom / APPFL model-update compression acceleration path as an APECS Lab research assistant
- Integrated Python/C ABI boundaries and native C codec behavior for compressor workflows
- Optimized ResNet50 CPU compression from 797.62 ms to 211.36 ms on 8 threads using safe grouped OpenMP/SIMD, a 3.77x speedup
- Evaluated guarded CUDA q8 experiments with consistent profiling and correctness gates
- Preserved result evidence, reports, logs, and reproducibility notes for review and follow-up work

## Technical Stack

`Python` `C` `CUDA` `OpenMP` `SIMD` `APPFL` `Python/C ABI` `Compression` `Benchmarking`

## Results / Current Status

The resume version of this work reports a 3.77x CPU compression speedup for ResNet50 and 9.37x CUDA compress-only / 10.8x closed-loop compress-decompress speedups under consistent profiling and correctness gates. The public repository records a release snapshot with source, tests, reports, logs, CSVs, and environment notes.

## Research Context

This project was part of my research-assistant work at APECS Lab, Stevens Institute of Technology, and connects to my broader focus on performance-critical AI systems.

## What I Learned

- How to separate production-safe acceleration paths from experimental GPU feasibility work
- Why Python wrapper overhead, data movement, and C compression time need to be profiled separately
- How ABI, wire-format compatibility, and test contracts affect performance optimization work

## Links

- [GitHub Repository](https://github.com/Gonglz/Compressor)
- [APECS Lab Team Profile](https://apecs-lab.github.io/team.html)
- [Projects Overview](/projects/)
