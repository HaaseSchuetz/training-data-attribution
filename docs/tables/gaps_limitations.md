---
title: Critical Gaps and Limitations in TDA
source: Analysis as of June 2026
---

## Critical Gaps & Limitations
   Gap/Limitation | Description | Impact | Reference |
 |----------------|-------------|--------|-----------|
 | **No pure black-box for fully frozen models** | STRIDE requires activation access; Daunce/AirRep need model interaction | Limits applicability to truly black-box APIs | [STRIDE](https://arxiv.org/abs/2606.05165) |
 | **Computational cost (Daunce)** | Requires training multiple perturbed models | Expensive for large LLMs | [Daunce](https://arxiv.org/abs/2505.23223) |
 | **Generalization (AirRep)** | Encoder must be trained per task/model | Limits transferability across domains | [AirRep](https://arxiv.org/abs/2505.18513) |
 | **Scalability tradeoffs** | AirRep/LoGRA fail at 1.38B scale due to runtime | Benchmarking challenges for large models | [STRIDE](https://arxiv.org/abs/2606.05165) |
 | **Query-only black-box remains unsolved** | No methods support fully query-only access | Open research challenge | [Survey](https://arxiv.org/html/2509.12581v1) |
