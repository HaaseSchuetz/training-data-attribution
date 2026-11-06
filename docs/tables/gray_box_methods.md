---
title: Gray-Box and Limited-Access Training Data Attribution Methods
source: Analysis as of October 2026
---

## Gray-Box / Limited-Access Methods
   Method | Year | Mechanism | Black-Box Note | Links |
 |--------|------|-----------|----------------|-------|
 | **[LoRIF](https://arxiv.org/abs/2601.21929)** | 2026 | Low-rank influence functions with truncated SVD | Requires **gradient access** | [arXiv](https://arxiv.org/abs/2601.21929) |
 | **[Traceprop](https://arxiv.org/abs/2609.32380)** | 2026 | Single-pass: records projected gradients during training backward pass | Requires **gradient access** | [arXiv](https://arxiv.org/abs/2609.32380) |
 | **[STRIDE](https://arxiv.org/abs/2606.05165)** | 2026 | Steering-based: low-rank operators applied to frozen model activations | Requires **activation access** (not pure black-box) | [arXiv](https://arxiv.org/abs/2606.05165) |
 | **[MDA](https://arxiv.org/abs/2601.21996)** | 2026 | Influence functions to trace interpretable LLM units to training samples | Requires **parameter access** | [arXiv](https://arxiv.org/abs/2601.21996) |
 | **[LWPA](https://arxiv.org/abs/2506.05647)** | 2025/2026 | Learns parameter importance weights for gradient-based attribution | Requires **gradient access** | [arXiv](https://arxiv.org/abs/2506.05647) |
 | **[DataInf](https://proceedings.iclr.cc/paper_files/paper/2025/file/804dbf8d3b8eee1ef875c6857efc64eb-Paper-Conference.pdf)** | 2024 | Influence function approximation for LoRA-tuned LLMs via Hessian approximations (EKFAC) | Requires **LoRA parameter access** | [ICLR 2025](https://proceedings.iclr.cc/paper_files/paper/2025/file/804dbf8d3b8eee1ef875c6857efc64eb-Paper-Conference.pdf) |
 | **[RepT](https://arxiv.org/abs/2510.02334)** | 2025 | Analyzes representation gradients in activation space | Requires **activation/gradient access** | [arXiv](https://arxiv.org/abs/2510.02334) |
