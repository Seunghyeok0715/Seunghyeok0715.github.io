---
title: "Geometry-Correct Diffusion Posterior Sampling with Denoiser-Pullback Curvature Guidance and Manifold-Aligned Damping"
collection: publications
category: conferences
permalink: /publication/CLAMP
excerpt: >
  CLAMP is a training-free diffusion posterior sampler for inverse problems that replaces hand-tuned scalar likelihood guidance with geometry-aware, per-noise-level damped Gauss–Newton corrections in diffusion-state coordinates. It pulls likelihood sensitivity back through the denoiser, uses a one-sided curvature model with manifold-aligned rank-one damping, solves each correction with matrix-free GMRES, and advances sampling via a variance-preserving Langevin transition. CLAMP supports pixel and latent diffusion priors for linear and nonlinear forward operators, achieving competitive or improved reconstruction quality with favorable runtime on FFHQ/ImageNet inverse problems and accelerated MRI. [OpenReview](https://openreview.net/forum?id=x9Cy1wydfo) · [PDF](https://openreview.net/pdf?id=x9Cy1wydfo)
authors:
  - Seunghyeok Shin *
  - Minwoo Kim *
  - Dabin Kim
  - Hongki Lim
date: 2026-05-01
venue: 'International Conference on Machine Learning (ICML) 2026'
paperurl: 'https://openreview.net/pdf?id=x9Cy1wydfo'
# citation: 'Shin, Seunghyeok; Kim, Minwoo; Kim, Dabin; Lim, Hongki. (2026). Geometry-Correct Diffusion Posterior Sampling with Denoiser-Pullback Curvature Guidance and Manifold-Aligned Damping. In <i>Proceedings of the 43rd International Conference on Machine Learning (ICML 2026)</i>. PMLR 306.'
---

Inverse problems aim to recover an unknown signal from indirect, noisy measurements, but diffusion posterior sampling methods often rely on hand-tuned scalar guidance weights for data consistency. This scalar correction can be brittle when the likelihood geometry is stiff, anisotropic, or operator-dependent, and it can become mis-scaled because measurements are evaluated on denoised clean predictions while the sampler updates noisy diffusion-state variables. CLAMP (Curvature-aware Langevin with Aligned Manifold Pullback) addresses these issues by replacing heuristic scalar guidance with a geometry-correct correction step at each diffusion noise level.

At each sampling step, a pretrained diffusion denoiser first produces a clean estimate, and CLAMP evaluates the measurement residual through the composed operator defined by the forward model and the denoiser. The likelihood correction is then computed in diffusion-state coordinates by pulling measurement sensitivity back through the denoiser. Instead of using a single scalar step size, CLAMP solves a damped Gauss–Newton-style system that scales the update according to local measurement curvature. For efficiency, it uses a one-sided curvature approximation that avoids forward denoiser-Jacobian products inside the curvature matvec while retaining the denoiser pullback needed for coordinate-correct update directions.

To stabilize the correction across noise levels, CLAMP introduces a prior-aligned anisotropic damping metric: a rank-one damping direction aligned with the denoiser residual, together with an automatically scaled regularization strength tied to the remaining diffusion noise. Each correction is solved with a fixed-budget matrix-free GMRES procedure using Jacobian-vector and vector-Jacobian products rather than explicitly forming large curvature matrices. After correction, CLAMP advances the sample with a variance-preserving Langevin transition whose drift/noise split is determined in closed form, avoiding an additional stochasticity hyperparameter.

The same framework applies to latent diffusion by composing the measurement operator with the decoder, enabling both pixel-space and latent-space variants. Across FFHQ and ImageNet inverse problems—including super-resolution, inpainting, deblurring, phase retrieval, nonlinear deblurring, and high dynamic range reconstruction—CLAMP reports competitive or improved PSNR/SSIM/LPIPS while reducing runtime relative to many diffusion-prior baselines. On accelerated MRI reconstruction, CLAMP achieves the best PSNR/SSIM among the compared diffusion-based methods, demonstrating that the geometry-aware correction remains effective beyond natural-image restoration.