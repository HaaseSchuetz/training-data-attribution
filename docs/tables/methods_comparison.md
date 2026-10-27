---
title: Comparative Analysis of TDA Methods
source: Analysis as of October 2026
---

## Comparative Analysis of Training Data Attribution Methods
   Method  | Access Level | Mechanism | Scalability | Accuracy | Use Case | Links |
 |---------|--------------|-----------|-------------|----------|----------|-------|
 | **[Daunce](https://arxiv.org/abs/2505.23223)** | Pure black-box | Covariance of per-example losses across perturbed models | High | High | Proprietary LLMs (OpenAI GPT) | [ICML 2025](https://icml.cc/virtual/2025/48688) |
 | **[AirRep](https://arxiv.org/abs/2505.18513)** | Pure black-box | Learned task-specific embeddings + attention pooling | ~100x faster | Parity with gradient-based | Large-scale inference | [NeurIPS 2025](https://neurips.cc/virtual/2025/poster/119133) \u2022 [GitHub](https://github.com/sunnweiwei/AirRep) |
 | **[LoRIF](https://arxiv.org/abs/2601.21929)** | Gray-box (gradient access) | Low-rank influence functions with truncated SVD | 20x storage reduction, query-time speedup | Matches/exceeds LoGRA | Models up to 70B parameters | [arXiv](https://arxiv.org/abs/2601.21929) |
 | **[Traceprop](https://arxiv.org/abs/2609.32380)** | Gray-box (gradient access) | Records projected gradients during training backward pass | Minimal overhead (2.6-11.3%) | Matches LogIX quality | Single-pass attribution | [arXiv](https://arxiv.org/abs/2609.32380) |
 | **[STRIDE](https://arxiv.org/abs/2606.05165)** | Gray-box (activation access) | Sparse steering operators on frozen activations | >10x more scalable | SOTA | Models with activation hooks | [arXiv](https://arxiv.org/abs/2606.05165) |
 | **[MDA](https://arxiv.org/abs/2601.21996)** | Gray-box (parameter access) | Influence functions tracing interpretable units | High | Causal validation | Mechanistic interpretability | [arXiv](https://arxiv.org/abs/2601.21996) |
 | **[LWPA](https://arxiv.org/abs/2506.05647)** | Gray-box (gradient access) | Learned parameter importance weights | High | Improved accuracy | Cross-task attribution | [arXiv](https://arxiv.org/abs/2506.05647) |

**Notes**:
- Pure black-box = API-only access.
- Gray-box = Requires activation/parameter/gradient access.
- Scalability: Relative to gradient-based baselines.
