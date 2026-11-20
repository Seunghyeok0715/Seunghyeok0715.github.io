---
title: "Anchored Inertial Proposals with Objective Verification for Diffusion-Prior Inverse Problems"
collection: publications
category: conferences
permalink: /publication/PIVOT
excerpt: >
  PIVOT reconstructs images from measurements using a pretrained diffusion model.
  At each noise level, it accepts a proposed correction only if it improves an objective
  that balances measurement fit against distance from the denoiser prediction.
  [OpenReview](https://openreview.net/forum?id=8wurOw8o4D) · [arXiv](https://arxiv.org/abs/2611.25551) · [Project page](https://pivot-2026.github.io/) · [Code](https://github.com/Seunghyeok0715/PIVOT2026)
authors:
  - Minwoo Kim *
  - Seunghyeok Shin *
  - Dabin Kim
  - Hongki Lim †
date: 2026-11-19 # arXiv v1 submission
venue: 'Conference on Neural Information Processing Systems (NeurIPS)'
paperurl: 'https://arxiv.org/pdf/2611.25551'
---

\* Equal contribution. † Corresponding author.

At each noise level, PIVOT holds the denoiser prediction fixed as an anchor. It estimates local curvature to set the step size and momentum for a sequence of heavy-ball updates. A verifier then compares the proposed reconstruction with the anchor using the same objective. If the proposal fails to lower the objective, sampling continues from the anchor.

The correction works in pixel space and, through a decoder, in latent space. It uses a pretrained model without retraining or additional denoiser calls during the correction.

[OpenReview](https://openreview.net/forum?id=8wurOw8o4D) · [arXiv](https://arxiv.org/abs/2611.25551) · [Project page](https://pivot-2026.github.io/) · [Code](https://github.com/Seunghyeok0715/PIVOT2026)
