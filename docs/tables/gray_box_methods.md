---
title: Gray-Box and Limited-Access Training Data Attribution Methods
source: Analysis as of June 2026
---

## Gray-Box / Limited-Access Methods
   Method | Year | Mechanism | Black-Box Note | Links |
 |--------|------|-----------|----------------|-------|
 | **[STRIDE](https://arxiv.org/abs/2606.05165)** | 2026 | Steering-based: low-rank operators applied to frozen model activations | Requires **activation access** (not pure black-box) | [arXiv](https://arxiv.org/abs/2606.05165) |
 | **[DataInf](https://proceedings.iclr.cc/paper_files/paper/2025/file/804dbf8d3b8eee1ef875c6857efc64eb-Paper-Conference.pdf)** | 2024 | Influence function approximation for LoRA-tuned LLMs via Hessian approximations (EKFAC) | Requires **LoRA parameter access** | [ICLR 2025](https://proceedings.iclr.cc/paper_files/paper/2025/file/804dbf8d3b8eee1ef875c6857efc64eb-Paper-Conference.pdf) |
 | **[RepT](https://arxiv.org/abs/2510.02334)** | 2025 | Analyzes representation gradients in activation space | Requires **activation/gradient access** | [arXiv](https://arxiv.org/abs/2510.02334) |
