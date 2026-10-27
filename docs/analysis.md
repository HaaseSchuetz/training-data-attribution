---
title: Training Data Attribution (TDA) Analysis - Black-Box and Limited-Access Methods
date: June 29, 2026
author: TDA Analysis Repository
version: 1.0
---

# Training Data Attribution (TDA) Analysis: Black-Box and Limited-Access Methods

**Last Updated**: October 2026
**Focus**: Pure black-box (API-only) and gray-box (limited-access) TDA methods for LLMs and other models.

---

## \ud83c\udfaf Executive Summary

Training Data Attribution (TDA) aims to identify which training examples most influence a model's predictions. For **proprietary LLMs** (e.g., OpenAI GPT, Anthropic) where only API access is available, **pure black-box methods** are required. As of October 2026, **only two methods**\u2014**[Daunce](https://arxiv.org/abs/2505.23223)** and **[AirRep](https://arxiv.org/abs/2505.18513)**\u2014are explicitly validated for pure black-box settings. For models with **activation access**, **[STRIDE](https://arxiv.org/abs/2606.05165)** (ICML 2026) is the most recent and highest-performing method. For **large-scale models (70B parameters)**, **[LoRIF](https://arxiv.org/abs/2601.21929)** enables scalable gradient-based attribution.

---

## \ud83c\udfaf Recent Additions (July-October 2026)

### New Impactful Papers
| Paper | Date | Access Level | Key Contribution | Impact |
|-------|------|--------------|------------------|--------|
| **[LoRIF](https://arxiv.org/abs/2601.21929)** | Jan 2026 (v2: May 2026) | Gray-box | Low-Rank Influence Functions - 20x storage reduction & query speedup vs LoGRA, scales to **70B parameters** | \u2605\u2605\u2605\u2605\u2605 **Major scalability breakthrough** |
| **[Traceprop](https://arxiv.org/abs/2609.32380)** | Sept 2026 | Gray-box | Single-pass: records projected gradients during training backward pass, 2.6-11.3% overhead vs 10.7-27% for LogIX | \u2605\u2605\u2605\u2605 **Systems innovation** |
| **[MDA](https://arxiv.org/abs/2601.21996)** | Jan 2026 (v2: Jun 2026) | Gray-box | Mechanistic Data Attribution - traces interpretable LLM units to training data, ICML 2026 Oral | \u2605\u2605\u2605\u2605 **Interpretability link** |
| **[LWPA](https://arxiv.org/abs/2506.05647)** | Jun 2025 (v4: Feb 2026) | Gray-box | Learning to Weight Parameters - improves attribution accuracy across tasks, ICLR 2026 | \u2605\u2605\u2605 |

**Note**: No new **pure black-box** methods have emerged since June 2026. The query-only black-box challenge remains open.

---

## \ud83d\udcca Comparative Analysis

### Pure Black-Box Methods (API-Only)
| Method | Year | Mechanism | Scalability | Accuracy | Use Case | Links |
|--------|------|-----------|-------------|----------|----------|-------|
| **[Daunce](https://arxiv.org/abs/2505.23223)** | 2025 | Generates perturbed models, computes covariance of per-example losses | High | High | Proprietary LLMs (OpenAI GPT) | [arXiv](https://arxiv.org/abs/2505.23223) \u2022 [ICML 2025 Talk](https://icml.cc/virtual/2025/48688) |
| **[AirRep](https://arxiv.org/abs/2505.18513)** | 2025 | Representation-based: task-specific embeddings optimized for TDA | ~100x faster | Parity with gradient-based | Large-scale inference | [arXiv](https://arxiv.org/abs/2505.18513) \u2022 [NeurIPS 2025 Talk](https://neurips.cc/virtual/2025/poster/119133) \u2022 [Slides (PDF)](https://neurips.cc/media/neurips-2025/Slides/119133.pdf) \u2022 [GitHub](https://github.com/sunnweiwei/AirRep) |

**Key Insight**: AirRep is the **only method achieving both black-box compatibility and near-gradient-based accuracy at scale**. Daunce is **unique in working on proprietary APIs** (e.g., OpenAI) but requires fine-tuning perturbed models, which may be costly.

---

### Gray-Box / Limited-Access Methods
| Method | Year | Mechanism | Black-Box Note | Links |
|--------|------|-----------|----------------|-------|
| **[LoRIF](https://arxiv.org/abs/2601.21929)** | 2026 | Low-rank influence functions with truncated SVD | Requires **gradient access** | [arXiv](https://arxiv.org/abs/2601.21929) |
| **[Traceprop](https://arxiv.org/abs/2609.32380)** | 2026 | Single-pass: records projected gradients during training backward pass | Requires **gradient access** | [arXiv](https://arxiv.org/abs/2609.32380) |
| **[STRIDE](https://arxiv.org/abs/2606.05165)** | 2026 | Steering-based: low-rank operators applied to frozen model activations | Requires **activation access** (not pure black-box) | [arXiv](https://arxiv.org/abs/2606.05165) |
| **[MDA](https://arxiv.org/abs/2601.21996)** | 2026 | Influence functions to trace interpretable LLM units to training samples | Requires **parameter access** | [arXiv](https://arxiv.org/abs/2601.21996) |
| **[LWPA](https://arxiv.org/abs/2506.05647)** | 2025/2026 | Learns parameter importance weights for gradient-based attribution | Requires **gradient access** | [arXiv](https://arxiv.org/abs/2506.05647) |
| **[DataInf](https://proceedings.iclr.cc/paper_files/paper/2025/file/804dbf8d3b8eee1ef875c6857efc64eb-Paper-Conference.pdf)** | 2024 | Influence function approximation for LoRA-tuned LLMs via Hessian approximations (EKFAC) | Requires **LoRA parameter access** | [ICLR 2025](https://proceedings.iclr.cc/paper_files/paper/2025/file/804dbf8d3b8eee1ef875c6857efc64eb-Paper-Conference.pdf) |
| **[RepT](https://arxiv.org/abs/2510.02334)** | 2025 | Analyzes representation gradients in activation space | Requires **activation/gradient access** | [arXiv](https://arxiv.org/abs/2510.02334) |

**Note**: LoRIF and STRIDE are the **most recent** methods (2026) addressing scalability and accuracy respectively. LoRIF achieves **20x storage reduction and query-time speedup** compared to LoGRA while matching or exceeding attribution quality. STRIDE achieves **SOTA accuracy** but is not pure black-box.

---

## \ud83c\udfaf Practical Selection Guide

| Scenario | Recommended Method | Rationale | Links |
|----------|-------------------|-----------|-------|
| **Proprietary LLM (API-only)** | **[Daunce](https://arxiv.org/abs/2505.23223)** | Only validated method for OpenAI GPT, etc. | [ICML 2025](https://icml.cc/virtual/2025/48688) |
| **Large-scale, open-source LLM** | **[AirRep](https://arxiv.org/abs/2505.18513)** | Fastest inference, no gradient/parameter access needed | [NeurIPS 2025](https://neurips.cc/virtual/2025/poster/119133) |
| **Activation access available** | **[STRIDE](https://arxiv.org/abs/2606.05165)** | Highest accuracy, but not pure black-box | [arXiv](https://arxiv.org/abs/2606.05165) |
| **LoRA-tuned models** | **[DataInf](https://proceedings.iclr.cc/paper_files/paper/2025/file/804dbf8d3b8eee1ef875c6857efc64eb-Paper-Conference.pdf)** | Optimized for LoRA parameter access | [ICLR 2025](https://proceedings.iclr.cc/paper_files/paper/2025/file/804dbf8d3b8eee1ef875c6857efc64eb-Paper-Conference.pdf) |
| **Large-scale models (70B parameters)** | **[LoRIF](https://arxiv.org/abs/2601.21929)** | Scalable gradient-based attribution with low-rank approximations | [arXiv](https://arxiv.org/abs/2601.21929) |

---

## \ud83d\udd0d Critical Gaps & Limitations

| Gap/Limitation | Description | Impact | Reference |
|----------------|-------------|--------|-----------|
| **No pure black-box for fully frozen models** | STRIDE requires activation access; Daunce/AirRep need model interaction | Limits applicability to truly black-box APIs | [STRIDE](https://arxiv.org/abs/2606.05165) |
| **Computational cost (Daunce)** | Requires training multiple perturbed models | Expensive for large LLMs | [Daunce](https://arxiv.org/abs/2505.23223) |
| **Generalization (AirRep)** | Encoder must be trained per task/model | Limits transferability across domains | [AirRep](https://arxiv.org/abs/2505.18513) |
| **Scalability tradeoffs** | AirRep/LoGRA fail at 1.38B scale due to runtime | Benchmarking challenges for large models | [STRIDE](https://arxiv.org/abs/2606.05165) |
| **Scalability resolved (LoRIF)** | LoRIF addresses storage/I/O bottlenecks with low-rank approximations | Enables 20x speedup at 70B scale | [LoRIF](https://arxiv.org/abs/2601.21929) |
| **Query-only black-box remains unsolved** | No methods support fully query-only access | Open research challenge | [Survey](https://arxiv.org/html/2509.12581v1) |

---

## \ud83d\udcc8 State of the Field (October 2026)

### Pure Black-Box
- **Daunce** and **AirRep** are the **only two production-ready options** for proprietary LLMs.
- **Daunce** is validated on **OpenAI GPT models** (first instance of TDA on proprietary LLMs).
- **AirRep** achieves **parity with gradient-based methods** while being **~100x faster** at inference.

### Gray-Box
- **LoRIF** (2026) is the **new scalability frontier** - makes gradient-based TDA practical at **70B parameters** with 20x storage/query speedup.
- **Traceprop** (2026) enables **single-pass attribution** during training with minimal overhead.
- **STRIDE** (ICML 2026) is the **new accuracy frontier** for high-accuracy attribution but requires **activation access**.
- **MDA** (ICML 2026 Oral) links **mechanistic interpretability** to training data attribution.
- **LWPA** (ICLR 2026) improves attribution accuracy by learning parameter importance weights.
- **DataInf** and **RepT** target specific architectures (LoRA, representation gradients).

### Emerging Needs
- The [2025 survey on limited-access TDA](https://arxiv.org/html/2509.12581v1) confirms that **fully black-box methods (query-only) remain an open challenge**.
- **STRIDE's benchmarking** shows that prior representation-based methods (e.g., AirRep, LoGRA) **fail to complete at 1.38B scale** due to runtime constraints.
- **LoRIF addresses scalability** with low-rank approximations enabling 20x speedup at 70B scale.
- **Traceprop demonstrates** that gradient attribution can be recorded during training with minimal overhead (2.6-11.3%).

---

## \ud83d\ude80 Recommendations

### For Practitioners
1. **Proprietary LLMs (e.g., OpenAI, Anthropic)**:
   - Use **Daunce** if you can afford perturbed model fine-tuning.
   - **Limitation**: Requires fine-tuning multiple models (costly for large LLMs).

2. **Open-Source LLMs**:
   - Use **AirRep** for **speed** (no gradient/parameter access needed).
   - Use **STRIDE** for **accuracy** (if activation access is possible).

3. **LoRA-Tuned Models**:
   - Use **DataInf** for optimized LoRA parameter access.

4. **Large-Scale Models (70B parameters)**:
   - Use **LoRIF** for scalable gradient-based attribution with low-rank approximations.

### For Researchers
- **Focus on query-only black-box methods**: This is the **next unsolved frontier** per [limited-access TDA analysis](https://arxiv.org/html/2509.12581v1).
- **Benchmark scalability**: STRIDE's [paper](https://arxiv.org/abs/2606.05165) highlights runtime bottlenecks in prior methods (e.g., AirRep, LoGRA). **LoRIF addresses this** with low-rank approximations enabling 20x speedup at 70B scale.
- **Single-pass attribution**: Traceprop demonstrates that gradient-based attribution can be recorded during training with minimal overhead (2.6-11.3%).

---

## \ud83c\udfa5 Conference Talks & Videos

| Method/Paper | Conference | Video/Slides Link | Notes |
|-------------|------------|-------------------|-------|
| **Daunce** | ICML 2025 | [ICML Virtual Page](https://icml.cc/virtual/2025/48688) | Pure black-box; first for proprietary LLMs |
| **AirRep** | NeurIPS 2025 | [NeurIPS Virtual Page](https://neurips.cc/virtual/2025/poster/119133) \u2022 [Slides (PDF)](https://neurips.cc/media/neurips-2025/Slides/119133.pdf) | Spotlight presentation |
| **Data Attribution at Scale** | ICML 2024 Tutorial | [ICML Tutorial Page](https://icml.cc/virtual/2024/tutorial/35228) | Comprehensive survey |
| **Training Data Attribution for Generative Models** | MIT 2024 | [YouTube (Zheng Dai)](https://www.youtube.com/watch?v=WzKuwIxlMtA) | Counterfactual framework |
| **Trustworthy ML Lecture** | Univ. of T\u00fcbingen (2023/2024) | [YouTube (Lecture 8)](https://www.youtube.com/watch?v=unDA9yPjG68) | Covers influence functions |
| **SOURCE Method** | Q&A Session | [YouTube (Q&A)](https://www.youtube.com/watch?v=grGNjU4SVWg) | Computationally efficient TDA |
| **Large-Scale TDA for Music** | ICML 2025 Workshop | [ICML Virtual Page](https://icml.cc/virtual/2025/52886) | Unlearning-based attribution |

**Note**: STRIDE (ICML 2026) and LoRIF/MDA (2026) talks will be available on their respective conference virtual sites after the conferences.

---

## \ud83d\udcda References

### Pure Black-Box Methods
- **Daunce**: Pan, X., Ye, C., Melkonian, J., Ma, J. W., & Zhang, T. (2025). *Daunce: Data Attribution through Uncertainty Estimation*. [arXiv:2505.23223](https://arxiv.org/abs/2505.23223). ICML 2025.
- **AirRep**: Sun, W., Liu, H., Kandpal, N., Raffel, C., & Yang, Y. (2025). *Enhancing Training Data Attribution with Representational Optimization*. [arXiv:2505.18513](https://arxiv.org/abs/2505.18513). NeurIPS 2025.

### Gray-Box Methods
- **LoRIF**: Li, S., Le, H., Xu, J., & Salzmann, M. (2026). *LoRIF: Low-Rank Influence Functions for Scalable Training Data Attribution*. [arXiv:2601.21929](https://arxiv.org/abs/2601.21929).
- **Traceprop**: Nautiyal, A. (2026). *Traceprop: Training Data Attribution in a Single Pass*. [arXiv:2609.32380](https://arxiv.org/abs/2609.32380).
- **MDA**: Chen, J., Luo, Y., & Pan, L. (2026). *Mechanistic Data Attribution: Tracing the Training Origins of Interpretable LLM Units*. [arXiv:2601.21996](https://arxiv.org/abs/2601.21996). ICML 2026.
- **LWPA**: Li, S., Le, H., Xu, J., & Salzmann, M. (2026). *Learning to Weight Parameters for Training Data Attribution*. [arXiv:2506.05647](https://arxiv.org/abs/2506.05647). ICLR 2026.
- **STRIDE**: Dagli, R., et al. (2026). *STRIDE: Training Data Attribution via Sparse Recovery from Subset Perturbations*. [arXiv:2606.05165](https://arxiv.org/abs/2606.05165). ICML 2026.
- **DataInf**: (2024). *DataInf: Efficient Influence Function Approximation for LoRA-Tuned LLMs*. [ICLR 2025](https://proceedings.iclr.cc/paper_files/paper/2025/file/804dbf8d3b8eee1ef875c6857efc64eb-Paper-Conference.pdf).
- **RepT**: (2025). *RepT: Representation Gradient Tracing*. [arXiv:2510.02334](https://arxiv.org/abs/2510.02334).

### Surveys & Analysis
- *Exploring Training Data Attribution under Limited Access Constraints*. [arXiv:2509.12581](https://arxiv.org/html/2509.12581v1).

---
**Maintained by**: [TDA Analysis Repository](https://github.com/)
**License**: CC BY 4.0 
