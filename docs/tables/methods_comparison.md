---
title: Comparative Analysis of TDA Methods
source: "Analysis as of June 2026"
---

## Comparative Analysis of Training Data Attribution Methods
   Method  | Access Level       | Mechanism                                      | Scalability | Accuracy | Use Case                          |
 |---------|--------------------|-----------------------------------------------|-------------|----------|-----------------------------------|
 | Daunce  | Pure black-box     | Covariance of per-example losses across perturbed models | High        | High     | Proprietary LLMs (OpenAI GPT)     |
 | AirRep  | Pure black-box     | Learned task-specific embeddings + attention pooling | ~100x faster | Parity   | Large-scale inference             |
 | STRIDE  | Gray-box (activation access) | Sparse steering operators on frozen activations | >10x more scalable | SOTA | Models with activation hooks      |

**Notes**:
- Pure black-box = API-only access.
- Gray-box = Requires activation/parameter access.
- Scalability: Relative to gradient-based baselines.
