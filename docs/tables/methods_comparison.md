---
title: Comparative Analysis of TDA Methods
source: Analysis as of June 2026
---

## Comparative Analysis of Training Data Attribution Methods
   Method  | Access Level | Mechanism | Scalability | Accuracy | Use Case | Links |
 |---------|--------------|-----------|-------------|----------|----------|-------|
 | **[Daunce](https://arxiv.org/abs/2505.23223)** | Pure black-box | Covariance of per-example losses across perturbed models | High | High | Proprietary LLMs (OpenAI GPT) | [ICML 2025](https://icml.cc/virtual/2025/48688) |
 | **[AirRep](https://arxiv.org/abs/2505.18513)** | Pure black-box | Learned task-specific embeddings + attention pooling | ~100x faster | Parity with gradient-based | Large-scale inference | [NeurIPS 2025](https://neurips.cc/virtual/2025/poster/119133) • [GitHub](https://github.com/sunnweiwei/AirRep) |
 | **[STRIDE](https://arxiv.org/abs/2606.05165)** | Gray-box (activation access) | Sparse steering operators on frozen activations | >10x more scalable | SOTA | Models with activation hooks | [arXiv](https://arxiv.org/abs/2606.05165) |

**Notes**:
- Pure black-box = API-only access.
- Gray-box = Requires activation/parameter access.
- Scalability: Relative to gradient-based baselines.
