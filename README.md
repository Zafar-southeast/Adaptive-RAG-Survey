# Closing the Loop in Retrieval-Augmented Generation

## Overview

This repository accompanies the systematic survey **“Closing the Loop in Retrieval-Augmented Generation: A Systematic Survey of Adaptive Retrieval, Reasoning, and Resource-Aware Intelligence.”**

RAG is often implemented as a fixed retrieve-then-generate pipeline, although queries differ in difficulty, evidence requirements, modality, and computational demands. This survey examines adaptive RAG through a **closed-loop control perspective**: retrieval, evidence use, reasoning, and termination can change in response to the current inference state.

The PRISMA 2020-guided review covers **131 analytical studies published from January 2023 through 5 November 2026**. One publication cutoff and consistent eligibility criteria apply across all discovery routes. Included studies have a qualifying inference-time control decision, a verified peer-reviewed conference or journal publication, and publicly accessible full text. Contextual references are distinguished from the analytical corpus.

## Key Contributions

1. **Four-Phase Control Taxonomy:** Organizes adaptive decisions into pre-retrieval, retrieval-time, post-retrieval evidence control, and reasoning/termination. The phases can recur within a trajectory.
2. **Cross-Cutting Design Dimensions:** Compares systems by their control signals, controller mechanisms, evidence spaces, and resource objectives.
3. **Five-Layer Evaluation Framework:** Separates answer quality, retrieval quality, decision quality, retrieval utility, and realized resource efficiency.
4. **Evidence Synthesis and Research Agenda:** Applies the same ten reporting-appraisal criteria to all 131 studies and connects documented limitations to research questions on calibration, evidence use, controller overhead, stopping, and reproducibility.

## The Four-Phase Control Taxonomy

The phases describe where a control decision occurs, rather than prescribing a fixed execution order. A system may operate across several phases or make only a single query-conditioned decision.

- **Phase I: Pre-Retrieval Control**  
  Decides whether, when, and where to retrieve. Includes retrieval necessity, retrieval timing, query adaptation and decomposition, and source, retriever, and modality routing.

- **Phase II: Retrieval-Time Control**  
  Decides how to acquire evidence. Includes iterative retrieval, search breadth and depth, evidence granularity, and graph-guided expansion.

- **Phase III: Post-Retrieval Evidence Control**  
  Decides which evidence to retain and how to use it. Includes reranking, set selection and coverage, context budgeting and compression, and internal–external knowledge balance and conflict.

- **Phase IV: Reasoning, Verification, and Termination**  
  Assesses evidence sufficiency, identifies gaps, revises plans, verifies support, and decides whether to continue, answer, or abstain. A fixed round limit constrains cost but does not establish evidence sufficiency.

## Five-Layer Evaluation Framework

1. **Answer Quality:** Task accuracy, exact match/F1, factuality, answer relevance, and citation quality.
2. **Retrieval Quality:** Recall@k, Precision@k, MRR/NDCG, path recall, and supporting-evidence coverage.
3. **Decision Quality:** Retrieval activation, routing, sufficiency, stopping, and abstention assessed against a declared reference condition.
4. **Retrieval Utility:** Benefits and harms of evidence acquisition, including matched retrieval/no-retrieval comparisons and the marginal utility of continuing a search.
5. **Realized Resource Efficiency:** End-to-end retrieval calls, context tokens, search depth, LLM/tool calls, latency, and monetary or compute costs, including signal acquisition and controller overhead.

Robustness and calibration apply across all five layers. Cross-paper scores should be interpreted in their original settings: differences in datasets, readers, retrievers, evidence access, and cost definitions prevent a simple performance ranking.

## Open Issues and Future Directions

- **Retrieval Need and Retrieval Benefit:** Uncertainty or query complexity does not directly establish that retrieval will improve an answer.
- **Controller Overhead:** Preliminary generation, uncertainty estimation, reranking, and verification can consume the savings from reduced retrieval.
- **Stopping under Incomplete Evidence:** A controller must distinguish sufficient support from unsuccessful exploration, budget exhaustion, and fallback.
- **Evidence Conflict and Provenance:** Correction and compression should preserve claim–source links and distinguish successful corrections from harmful ones.
- **Retriever–Controller Mismatch:** Routing thresholds and confidence signals may not transfer reliably across retrievers, readers, or corpora.
- **Reproducible Evaluation:** Matched fixed-policy baselines, uncertainty reporting, and controller traces are needed to assess quality–cost improvements.

## Supplementary Material and Data

The supplementary material provides selection counts by discovery route, the complete analytical inventory and appraisal codes, and detailed method comparisons. The accompanying CSVs and selection audit support inspection of study membership, publication decisions, and count reconciliation.

Each study receives one **primary control emphasis** for descriptive counting. These labels do not measure every phase in which a method operates and should not be interpreted as phase co-occurrence statistics.

## Citation

If you use this survey, its taxonomy, or its evaluation framework, please cite the manuscript:

```bibtex
@unpublished{ali2026closingloop,
  title  = {Closing the Loop in {Retrieval-Augmented Generation}: A Systematic Survey of Adaptive Retrieval, Reasoning, and Resource-Aware Intelligence},
  author = {Ali, Zafar and Muhammad, Khan and Mohammed, Adam A. Q. and Qi, Guilin and Paulheim, Heiko and Kefalas, Pavlos},
  year   = {2026},
  note   = {Manuscript}
}
```
