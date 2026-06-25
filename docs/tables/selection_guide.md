---
title: Practical Selection Guide for TDA Methods
source: Analysis as of June 2026
---

## Practical Selection Guide
   Scenario | Recommended Method | Rationale | Links |
 |----------|-------------------|-----------|-------|
 | **Proprietary LLM (API-only)** | **[Daunce](https://arxiv.org/abs/2505.23223)** | Only validated method for OpenAI GPT, etc. | [ICML 2025](https://icml.cc/virtual/2025/48688) |
 | **Large-scale, open-source LLM** | **[AirRep](https://arxiv.org/abs/2505.18513)** | Fastest inference, no gradient/parameter access needed | [NeurIPS 2025](https://neurips.cc/virtual/2025/poster/119133) |
 | **Activation access available** | **[STRIDE](https://arxiv.org/abs/2606.05165)** | Highest accuracy, but not pure black-box | [arXiv](https://arxiv.org/abs/2606.05165) |
 | **LoRA-tuned models** | **[DataInf](https://proceedings.iclr.cc/paper_files/paper/2025/file/804dbf8d3b8eee1ef875c6857efc64eb-Paper-Conference.pdf)** | Optimized for LoRA parameter access | [ICLR 2025](https://proceedings.iclr.cc/paper_files/paper/2025/file/804dbf8d3b8eee1ef875c6857efc64eb-Paper-Conference.pdf) |
