---
title: "FrugalGPT: How to Use Large Language Models While Reducing Cost and Improving Performance"
authors: ["Lingjiao Chen", "Matei Zaharia", "James Zou"]
year: 2024
venue: "Transactions on Machine Learning Research"
url: "https://openreview.net/forum?id=cSimKw5p6R"
paper_id: "arxiv-2305.05176"
status: read
priority: high
topics: [routing, cascades, cost, model-selection, heterogeneous-models]
date_added: 2026-08-23
date_read: 2026-08-24
---

# FrugalGPT: How to Use Large Language Models While Reducing Cost and Improving Performance

## Why I am reading this

This paper is a foundation for the cost-aware heterogeneous-agent idea. It should clarify what was already established about allocating queries among differently capable and differently priced models, and where a study of end-to-end task completion using three model tiers would need to go beyond query routing.

## Citation

Chen, L., Zaharia, M., & Zou, J. (2024). FrugalGPT: How to use large language models while reducing cost and improving performance. *Transactions on Machine Learning Research*. https://openreview.net/forum?id=cSimKw5p6R

The work first appeared as arXiv:2305.05176 in 2023 and was published by TMLR in December 2024.

## One-paragraph summary

FrugalGPT addresses the high and highly variable inference cost of using commercial LLM services. Its central observation is that no model is best on every query: inexpensive models often answer correctly, while a more expensive model is needed for only a subset of difficult cases and can itself be wrong where a cheaper model is right. The paper discusses three broad cost-saving strategies—prompt adaptation, LLM approximation, and LLM cascades—and implements the cascade strategy. The learned cascade calls models sequentially, scores the apparent quality of each generated answer, accepts an answer when its score passes a learned threshold, and otherwise escalates to another model. The model order and stopping thresholds are optimized under a budget constraint using labeled examples. Across classification and question-answering datasets, the authors report matching the strongest individual model at substantially lower API cost and, in some settings, improving accuracy at the same cost. The paper therefore establishes the continuing principle that capability should be allocated selectively instead of sending every query to the strongest model.

## Research problem and context

- **Problem:** How can an application answer natural-language queries accurately while respecting an inference-cost budget?
- **Setting:** A user can call multiple black-box LLM APIs with different prices and non-identical error patterns.
- **Motivation:** Prices differed by orders of magnitude, and the most expensive model was neither necessary nor correct for every query.
- **Broader strategies discussed:** Shorter or shared prompts, approximation through caching or fine-tuning cheaper models, and adaptive LLM cascades.
- **Empirical focus:** A supervised, query-level cascade that decides whether to accept the current answer or call another model.

## Contribution

1. Frames LLM use as constrained optimization over answer quality and inference cost rather than as a choice of one universal model.
2. Identifies prompt adaptation, LLM approximation, and LLM cascades as three families of cost-saving techniques.
3. Implements FrugalGPT as a learned cascade over heterogeneous LLM services.
4. Shows empirically that complementary model errors can produce both lower cost and, sometimes, higher accuracy than one strong model.
5. Provides an early cost–quality frontier for adaptive model allocation.

The main novel and evaluated contribution is methodological and empirical: learning the order and stopping rules of a query-level model cascade under a budget.

## Approach

- **Model or system:** A cascade of up to three LLM APIs. A query is sent to the first model; a generation-quality scorer evaluates the query–answer pair; the answer is returned if its score exceeds a threshold, otherwise the next model is called.
- **Router optimization:** Learns the model order and score thresholds subject to an average-cost budget. Search-space pruning makes the mixed-integer optimization tractable.
- **Quality estimation:** Uses a comparatively inexpensive supervised scorer, including a DistilBERT-based regression model in the reported case study, trained to predict whether a generated answer is correct.
- **Data:** HEADLINES, OVERRULING, COQA, AGNEWS, and SCIQ, covering classification, reading comprehension, and scientific question answering.
- **Models:** The published paper evaluates heterogeneous proprietary and hosted/open models. Core experimental generations and prices were collected in March 2023; the final paper also reports a later comparison using models such as Claude 3.5, Gemini 1.5, GPT-4o, GPT-4 Turbo, Jamba 1.5, and Llama 3.
- **Baselines:** Individual LLM APIs, including the best-performing individual model, and a simple self-confidence threshold cascade.
- **Unit of allocation:** A standalone user query and successive attempts to answer it—not roles or dependent steps in a long-running task.

## Evidence and results

| Claim | Evidence offered | Strength of support | Caveat |
|---|---|---|---|
| A cascade can match the best individual model at lower cost | Reported savings at matched accuracy were 98.3% on HEADLINES, 73.3% on OVERRULING, 59.2% on COQA, 75.4% on AGNEWS, and 52.3% on SCIQ | Strong within the evaluated datasets | Dollar results depend on model prices and generations from a particular period |
| A heterogeneous cascade can outperform one strong model | The abstract reports accuracy improvement of up to 4% at the same cost; case studies show cheaper models correctly answering some items missed by GPT-4 | Moderate | Gains depend on scorer quality and complementary model errors |
| Cheap models can handle many queries | Cascades frequently stop before calling the most expensive model; one case study sent only 16.6% of queries to GPT-4 | Strong for the studied distributions | Requires reliable prediction of answer quality |
| Learned quality scoring adds value | A supervised scorer supports selective stopping and is compared with a simple log-probability threshold | Moderate | The scorer itself requires labeled, distribution-relevant data and adds training and inference overhead |

## Evaluation quality

- The accuracy-versus-cost framing directly measures the paper's primary claim.
- Multiple datasets and model providers strengthen the evidence for the general cascade principle.
- Comparison with individual models and a simple threshold baseline is useful, although later routing work provides more demanding baselines and evaluations.
- The experiments mostly use bounded classification or short-answer tasks with immediate correctness labels; these do not represent long-horizon agent execution.
- Reported API-dollar savings age quickly because models, prices, tokenization, and serving arrangements change.
- The evaluation does not fully account for operational latency, repeated context, tool calls, retries, coordination, or irreversible actions.

## Limitations and threats to validity

### Stated by the authors

- Training the cascade requires labeled examples.
- Training examples should come from the same or a similar distribution as deployment queries.
- Learning the cascade has an upfront computational cost and makes the most sense when amortized over a larger deployment workload.
- The paper is not intended as a comprehensive or definitive treatment of efficient LLM use.

### Additional limitations I see

- The cascade evaluates successive answers to one query; it does not allocate models to distinct roles that jointly complete a task.
- The reward is immediate answer correctness. Agentic work has delayed outcomes, dependencies between steps, state changes, and error propagation.
- A scorer can confidently accept a plausible but harmful intermediate result, especially when correctness cannot be observed until much later.
- The method assumes that escalation remains possible. In tool-using workflows, an inexpensive model may already have taken an irreversible action.
- Cost is centered on API inference rather than the full cost of routing, handoffs, growing context, retries, verification, latency, and human recovery.
- The numerical findings are temporally fragile even though the allocation principle remains relevant.

## Relationship to the landscape

- **Topics:** LLM routing, model cascades, constrained inference, heterogeneous model selection, cost-aware agent harnesses.
- **Role in the literature:** Foundational query-level evidence. Later work moves from whole-query routing to modules, trajectory steps, and semantic roles.
- **Important concepts:** quality–cost frontier, generation-quality scorer, escalation threshold, complementary model errors, budget-constrained routing.
- **Current interpretation:** The paper is old relative to the fast-moving 2026 model ecosystem, but its central claim still holds: the strongest model need not process every input. Its model-specific prices and results should not be treated as current evidence.

## Gap relative to my three-tier task-completion idea

FrugalGPT asks: **Which model or sequence of models should answer this individual query?**

My proposed study asks: **How should three capability/cost tiers be assigned across the roles or stages needed to complete an end-to-end task?**

One motivating configuration is:

1. a frontier model for architecture, difficult planning, high-risk decisions, or recovery;
2. a mid-tier model that decomposes the high-level plan and writes detailed, context-rich instructions that the low-tier model can follow, while also handling coordination;
3. a low-cost model that executes those bounded instructions, with escalation when needed;
4. an optional reviewing or verification stage whose model tier is itself an experimental variable.

This is not yet a fixed architecture. Roles may be added, removed, combined, repeated, or reordered to support a valid comparison. Model tier should be varied independently for the architect, instruction writer, executor, and reviewer rather than assuming in advance that the frontier-to-mid-to-low ordering is optimal. This changes the unit of analysis from a single response to a task trajectory. The study would measure not just final-answer accuracy, but completion success, partial progress, repeated-trial reliability, plan and instruction quality, handoff fidelity, error propagation, reviewer accuracy, tool-use failures, recovery, latency, tokens, retries, and total monetary cost. It should compare candidate three-tier configurations with single agents at every tier, homogeneous multi-agent systems, role ablations, alternative and reversed tier assignments, reviewer tiers and no-review controls, adaptive escalation, and an oracle allocation.

However, **the mere use of three tiers is not by itself a sufficient research gap in 2026**. More recent work already studies role-aware model composition, planner–executor collaboration, and step-level model routing. The defensible gap is to determine **when and why** heterogeneous role allocation improves end-to-end task completion; which roles, reviewer tier, ordering, and handoffs are beneficial; which task properties predict the best architecture; and whether the resulting policy transfers across domains and model generations.

## Suggested positioning statement

FrugalGPT established that heterogeneous models can be selected adaptively at the query level to reduce inference cost without sacrificing answer quality. It uses a learned cascade that tries models sequentially and escalates when an answer-quality scorer is not sufficiently confident. Although the specific models and prices have aged, the underlying principle remains important: not every query requires the strongest model. My proposed work shifts this principle from individual query answering to end-to-end task completion. A motivating configuration uses a frontier model for high-level architecture or planning, a mid-tier model to convert that plan into detailed instructions, and a low-cost model to execute those instructions, possibly followed by a reviewer. However, the architecture and tier assignments are experimental variables rather than fixed assumptions: roles can be added, removed, combined, reordered, or assigned different model tiers, and the reviewer can also be low-, mid-, or frontier-tier. The study would determine which configurations improve completion, reliability, instruction fidelity, downstream execution, review accuracy, latency, and total cost. The research gap is therefore not simply the use of multiple model tiers, but identifying the task and workflow conditions under which particular role, tier, handoff, and review configurations improve the overall performance–cost frontier.

## Research ideas triggered

- Compare multiple role and tier configurations with query-level cascading, per-step routing, role-ablated systems, and single agents at every tier under matched budgets.
- Test whether task properties such as horizon, decomposability, action reversibility, and verification difficulty predict the best tier assignment.
- Measure execution success conditional on both high-level plan quality and detailed-instruction quality to separate architecture, instruction-writing, handoff, and executor failures.
- Vary reviewer presence, placement, and model tier; measure correction rate, false approval, unnecessary rejection, added latency, and net cost.
- Introduce escalation before high-risk actions rather than only after low answer confidence.
- Recompute dollar costs from raw token and call counts so results survive price changes.

## Key passages and figure locators

- **Section 1 and Figure 1:** Motivation, adaptive model selection, and the quality–cost framing.
- **Section 4:** Definition of the learned LLM cascade, generation-quality scorer, router, model order, and stopping thresholds.
- **Section 5, Table 2:** Matched-accuracy cost savings across the five evaluation datasets.
- **Section 5, Figure 3:** Accuracy–cost trade-offs and examples where a cheaper model is correct while GPT-4 is wrong.
- **Section 6:** Need for labeled, distribution-relevant training data and discussion of broader deployment criteria.

## My judgment

- **Importance:** high
- **Confidence in findings:** medium
- **Relevance to dissertation search:** high as a foundation; low as a statement of the 2026 frontier
- **Next action:** synthesize after reading AutoMix, RouteLLM, and the later agentic allocation papers
