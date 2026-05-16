---
title: "Lightweight Human Activity Recognition with Model Distillation"
excerpt: "Teacher-student model distillation for wearable-sensor activity recognition, targeting efficient inference on edge devices."
---

## One-line Summary

Compressing wearable-sensor activity recognition models through teacher-student distillation for edge devices.

## Problem

Human activity recognition models often need to run on devices with limited compute and power. A large model may perform well during experimentation, but it can be too expensive for edge deployment. This project explores teacher-student knowledge distillation as a way to preserve useful accuracy while reducing computational cost.

## System Architecture

The workflow is organized around:

- Wearable sensor time-series data preprocessing
- Teacher model training for stronger baseline performance
- Student model training through distillation
- Evaluation on activity recognition datasets such as PAMAP2 and MHEALTH
- Edge-oriented model selection based on inference efficiency

## My Contribution

- Built the model distillation workflow for time-series activity recognition
- Worked with sensor data preprocessing and classification experiments
- Compared model behavior through the lens of edge-device deployment constraints
- Framed the project around practical lightweight inference rather than only raw model accuracy

## Technical Stack

`Python` `TensorFlow` `scikit-learn` `NumPy` `Pandas` `Time-Series ML` `Model Distillation`

## Results / Current Status

The project demonstrates a practical edge AI direction: start with a stronger teacher model, then train a smaller student model that is better suited to resource-constrained wearable or embedded devices.

## What I Learned

- How teacher-student distillation can transfer behavior from a larger model to a smaller one
- Why time-series preprocessing is central to wearable sensor intelligence
- How deployment constraints change the way model quality should be evaluated

## Links

- [GitHub Repository](https://github.com/Gonglz/Lightweight-Human-Activity-Recognition-with-Model-Distillation)
- [Projects Overview](/projects/)
