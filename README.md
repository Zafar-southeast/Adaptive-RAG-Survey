## Overview
This repository accompanies the systematic review: **"Adaptive and resource-aware retrieval-augmented generation: A systematic review of closed-loop control, evidence allocation, and dynamic reasoning."**

Traditional RAG is often implemented as a fixed, linear retrieve-then-generate pipeline. This survey challenges that assumption by examining RAG through a **closed-loop control perspective**, where retrieval, evidence use, reasoning, and stopping dynamically adapt as inference unfolds. Based on a PRISMA 2020 selection process covering **107 studies (January 2023 – September 2026)**, we provide a comprehensive taxonomy and evaluation framework for adaptive RAG systems.

## Key Contributions
1. **Four-Phase Adaptive Taxonomy:** Organizes adaptive behavior sequentially across the inference lifecycle.
2. **Control Mechanisms & Signals:** Classifies how controllers trigger adaptation (e.g., rule-based, learned routers, reinforcement learning, agents) across various evidence spaces (text, graphs, multimodal).
3. **Five-Layer Evaluation Framework:** Separates final answer quality from intermediate decision quality, retrieval utility, and realized resource costs.
4. **Failure Modes & Open Issues:** Identifies systemic gaps in the field, such as unmeasured controller overhead, limited statistical robustness, and premature stopping.

## The Four-Phase Control Taxonomy
Adaptive RAG systems behave as stateful controllers rather than static pipelines. We categorize these dynamic decisions into four phases:

*   **Phase I: Pre-Retrieval Control**  
    Deciding *if, when, and where* to retrieve. Includes retrieval necessity (skip vs. retrieve), active retrieval timing, query rewriting/decomposition, and source/modality routing.
*   **Phase II: Retrieval-Time Control**  
    Deciding *how* to search. Involves iterative retrieval, adjusting search breadth and depth, changing evidence granularity, and structured/graph-guided expansion.
*   **Phase III: Post-Retrieval Evidence Control**  
    Deciding *what* to keep and how to use it. Covers adaptive reranking, set selection, context budgeting and compression, and resolving conflicts between internal parametric memory and external knowledge.
*   **Phase IV: Reasoning and Termination**  
    Deciding *when* to stop. Involves evidence sufficiency assessment, gap detection/replanning, explicit stopping, and abstention from answering when evidence is insufficient.

## Five-Layer Evaluation Framework
To accurately assess adaptive systems without conflating separate failure modes, we propose a multi-layered evaluation approach:
1.  **Answer Quality:** Task accuracy, EM/F1, factuality, citation quality, and answer relevance.
2.  **Retrieval Quality:** Recall@k, Precision@k, MRR/NDCG, path recall, and evidence coverage.
3.  **Decision Quality:** Retrieve/skip accuracy, router correctness, sufficiency classification, and abstention quality.
4.  **Retrieval Utility:** Accuracy gain over no retrieval, retrieval-harm rate, and marginal utility of additional search steps.
5.  **Resource Efficiency:** End-to-end tracking of retrieval calls, context tokens, search depth, LLM/tool calls, latency, and monetary/compute costs.

## Open Issues & Future Directions
The review highlights several critical frontiers for future research in adaptive RAG:
*   **Retrieval Need vs. Retrieval Benefit:** Signals triggering retrieval must align with expected answer improvement, not just model uncertainty.
*   **Hidden Controller Overhead:** The computational cost of the controller itself (e.g., generating preliminary answers or executing an LLM judge) can sometimes exceed the savings from skipping retrieval.
*   **Stopping vs. Triggering:** Knowing when to safely terminate a search based on evidence sufficiency is harder than deciding when to initiate retrieval.
*   **Evidence Conflict & Provenance:** Robust systems must handle contradictory evidence and preserve provenance without over-correcting valid internal memory.
*   **Retriever-Controller Mismatch:** Controllers calibrated to one retriever's score distribution may not transfer reliably to others.

## Citation
If you find this work or taxonomy useful, please cite our paper:
```bibtex
@article{adaptive_rag_review_2026,
  title={Adaptive and resource-aware retrieval-augmented generation: A systematic review of closed-loop control, evidence allocation, and dynamic reasoning},
  author={Anonymous},
  journal={Submission Version},
  year={2026}
}
