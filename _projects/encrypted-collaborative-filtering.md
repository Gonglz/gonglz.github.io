---
title: "Encrypted Collaborative Filtering"
excerpt: "Privacy-preserving recommendation system using encrypted identifiers, zero-knowledge validation, and matrix factorization."
---

## One-line Summary

A privacy-preserving recommendation system using encrypted IDs, zero-knowledge proof validation, and matrix factorization.

## Problem

Recommendation systems often rely on user-item interaction data, which can expose sensitive user behavior if handled carelessly. This project explores how collaborative filtering can be paired with privacy-preserving mechanisms while still producing useful recommendations.

## System Architecture

The system combines:

- MovieLens-style user-item rating data
- Encrypted identifiers for privacy protection
- Matrix factorization for collaborative filtering
- Zero-knowledge proof validation concepts
- Evaluation with recommendation metrics such as RMSE and MAE

## My Contribution

- Implemented the recommendation model workflow with PyTorch
- Integrated encryption-oriented handling for identifiers
- Studied how privacy mechanisms interact with recommendation quality
- Evaluated the system with standard collaborative filtering metrics

## Technical Stack

`Python` `PyTorch` `MovieLens` `AES` `Zero-Knowledge Proof` `Matrix Factorization`

## Results / Current Status

This project is a strong complement to the embedded AI work because it shows machine learning system design through a privacy and security lens.

## What I Learned

- How matrix factorization supports collaborative filtering
- Why privacy-preserving system design affects data modeling choices
- How recommendation metrics help evaluate model behavior beyond implementation correctness

## Links

- [GitHub Repository](https://github.com/Gonglz/Encrypted-Collaborative-Filtering-for-Privacy-Preserving-Recommendation)
- [Project Summary Report (PPTX)](/assets/files/projects/encrypted-collaborative-filtering/encrypted-collaborative-filtering-project-report.pptx)
- [Projects Overview](/projects/)
