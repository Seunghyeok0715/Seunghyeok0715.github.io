---
title: "FAST-DIPS: Adjoint-Free Analytic Steps and Hard-Constrained Likelihood Correction for Diffusion-Prior Inverse Problems"
collection: publications
category: conferences
permalink: /publication/FAST-DIPS
excerpt: >
  FAST-DIPS is a training-free diffusion-prior inverse-problem solver that enforces a hard measurement-space feasibility constraint via an adjoint-free ADMM correction with an analytic (or forward-difference) step size, plus decoupled re-annealing. It supports linear/nonlinear forward operators without hand-coded adjoints and includes pixel, latent, and hybrid pixel→latent variants for faster, stable reconstructions. [OpenReview](https://openreview.net/forum?id=voMeZVAkKL) · [PDF](https://openreview.net/pdf?id=voMeZVAkKL) · [Code](https://github.com/ququlza/FAST-DIPS)
authors:
  - Minwoo Kim *
  - Seunghyeok Shin *
  - Hongki Lim 
date: 2026-01-26
venue: 'International Conference on Learning Representations (ICLR) 2026'
paperurl: 'https://openreview.net/pdf?id=voMeZVAkKL'
# citation: 'Kim, Minwoo; Shin, Seunghyeok; Lim, Hongki. (2026). FAST-DIPS: Adjoint-Free Analytic Steps and Hard-Constrained Likelihood Correction for Diffusion-Prior Inverse Problems. In <i>Proceedings of the International Conference on Learning Representations (ICLR 2026)</i>.'
---

Recovering an unknown signal from noisy measurements is a core inverse-problems task, but many diffusion-prior solvers depend on costly inner optimization loops and careful step-size tuning, and they often require adjoint (transpose) operators that are tedious or infeasible to implement for complex or nonlinear measurement models. FAST-DIPS (Fast And STable Diffusion-prior Inverse Problem Solver) introduces a training-free correction step applied at each diffusion noise level that explicitly enforces measurement feasibility while minimizing operator-engineering overhead.

At each sampling step, a pretrained diffusion denoiser produces a clean estimate, and FAST-DIPS then performs a hard-constrained “likelihood correction” that pushes the estimate to satisfy the measurement constraint within a user-specified tolerance. The correction is solved using an adjoint-free ADMM procedure: the measurement-space update is a simple closed-form projection, and the signal update is computed with a few steepest-descent steps using an analytic, locally optimal step size derived from forward-mode information (or a forward-difference probe when needed), with lightweight backtracking for stability. After correction, FAST-DIPS applies decoupled re-annealing (re-injecting noise according to the diffusion schedule) to maintain stable progression across noise levels.

FAST-DIPS also supports latent diffusion by composing the measurement operator with the decoder, and provides pixel-space, latent-space, and a hybrid pixel→latent strategy that reduces early overhead while preserving manifold-faithful refinement later in sampling. Across a range of linear and nonlinear inverse problems, FAST-DIPS reports competitive or improved reconstruction quality while significantly reducing runtime compared to prior diffusion-prior baselines.

