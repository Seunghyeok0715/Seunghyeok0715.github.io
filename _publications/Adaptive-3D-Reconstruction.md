---
title: "Adaptive 3D Reconstruction via Diffusion Priors and Forward Curvature-Matching Likelihood Updates"
collection: publications
category: conferences
permalink: /publication/Adaptive-3D-Reconstruction
excerpt: >
  FCM is a training-free, likelihood-guided diffusion update that auto-tunes step sizes via forward-mode autodiff and curvature probes, enabling fast, stable 3D point-cloud reconstruction from single/multi-view inputs. [OpenReview](https://openreview.net/pdf?id=IJLqUjtrls) · [Project page](https://fcm2025.github.io) · [Code](https://github.com/Seunghyeok0715/FCM)
authors:
  - Seunghyeok Shin
  - Dabin Kim
  - Hongki Lim
date: 2025-10-29
venue: 'The Thirty-Ninth Annual Conference on Neural Information Processing Systems(NeurIPS), Spotlight'
paperurl: 'https://openreview.net/pdf?id=IJLqUjtrls'
# citation: 'Shin, Seunghyeok; Kim, Dabin; Lim, Hongki. (2025). Adaptive 3D Reconstruction via Diffusion Priors and Forward Curvature-Matching Likelihood Updates. <i>Proceedings of the Thirty-Ninth Conference on Neural Information Processing Systems (NeurIPS 2025)</i>.'
---

Reconstructing high-quality point clouds from images remains challenging in computer vision. Existing generative models, particularly diffusion models, based approaches that directly learn the posterior may suffer from inflexibility—they require conditioning signals during training, support only a fixed number of input views, and need complete retraining for different measurements. Recent diffusion-based methods have attempted to address this by combining prior models with likelihood updates, but they rely on heuristic fixed step sizes for the likelihood update that lead to slow convergence and suboptimal reconstruction quality. We advance this line of approach by integrating our novel Forward Curvature-Matching (FCM) update method with diffusion sampling. Our method dynamically determines optimal step sizes using only forward automatic differentiation and finite-difference curvature estimates, enabling precise optimization of the likelihood update. This formulation enables high-fidelity reconstruction from both single-view and multi-view inputs, and supports various input modalities through simple operator substitution—all without retraining. Experiments on ShapeNet and CO3D datasets demonstrate that our method achieves superior reconstruction quality at matched or lower NFEs, yielding higher F-score and lower CD and EMD, validating its efficiency and adaptability for practical applications. [OpenReview](https://openreview.net/pdf?id=IJLqUjtrls) · [Project page](https://fcm2025.github.io) · [Code](https://github.com/Seunghyeok0715/FCM)
