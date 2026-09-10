---
title: "Optimizing Model Selection for Compound AI Systems"
authors: ["Lingjiao Chen", "Jared Quincy Davis", "Boris Hanin", "Peter Bailis", "Matei Zaharia", "James Zou", "Ion Stoica"]
year: 2025
venue: "arXiv preprint"
url: "https://arxiv.org/abs/2502.14815"
paper_id: "arxiv-2502.14815"
status: read
priority: high
topics: [compound-ai, model-selection, heterogeneous-models, cost, routing]
date_added: 2026-08-23
date_read: 2026-08-24
---

# Optimizing Model Selection for Compound AI Systems

## Why I am reading this

This paper is closely related to my interest in using models with different capability and cost levels inside one AI system. It should help clarify what has already been studied about assigning different models to different parts of a workflow, and what remains open for agentic task completion, cost reduction, and model handoffs.

## Citation

Chen, L., Davis, J. Q., Hanin, B., Bailis, P., Zaharia, M., Zou, J., & Stoica, I. (2025). *Optimizing model selection for compound AI systems*. arXiv:2502.14815. https://arxiv.org/abs/2502.14815

## One-paragraph summary

This paper studies how to assign different LLMs to the modules of a compound AI system. A compound system makes several connected LLM calls, such as generating an answer, criticizing it, and refining it. The authors argue that using one model for every module is often not ideal because models have different strengths. They introduce LLMSelector, which tries candidate models one module at a time and uses another LLM as a diagnoser to estimate which model performs best in each role. It learns a mostly fixed model assignment from labeled training examples, then applies that assignment to held-out examples from the same dataset. Across self-refine, multi-agent debate, and locate-solve systems, the authors report accuracy gains over using the same model everywhere. The paper shows that module-level model choice matters, but it does not optimize the production cost of the final system or study dynamic handoffs during long-running agentic work.

## Research problem and context

- **Problem:** Given a fixed multi-stage AI pipeline and a pool of candidate LLMs, which model should be used for each module?
- **Motivation:** One model may be good at generation but weaker at criticism, refinement, debate, or another specialized role.
- **Challenge:** With ten models and three modules, there are 1,000 possible assignments. The search space grows exponentially as modules are added.
- **Setting:** The number of modules, their order, their prompts, and their connections are already defined. Only the model assigned to each module is optimized.
- **Related idea:** The paper moves beyond routing one query to one model. It studies model selection inside a system containing several connected calls.

## Contribution

1. Defines the model selection problem for static compound AI systems.
2. Introduces LLMSelector, which searches for a good model assignment one module at a time.
3. Uses an LLM diagnoser to estimate whether a particular module caused an error.
4. Shows that different models can be useful in different roles within the same system.
5. Provides experiments across three compound-system designs and six datasets.

The main contribution is methodological and empirical: an efficient way to choose models for the modules of an already designed compound system.

## Approach

- **Input:** A fixed pipeline, candidate LLMs, labeled question-answer examples, and a search budget.
- **Initialization:** Start with an initial model assignment.
- **Module selection:** Choose one module, such as the generator or critic.
- **Candidate testing:** Try each candidate model in that module while keeping the other modules fixed.
- **Diagnosis:** Give an LLM the question, known correct answer, intermediate module outputs, and final answer. Ask whether the chosen module contributed to the error.
- **Update:** Select the candidate with the best estimated module performance, aggregate decisions across training examples, and move to the next module.
- **Stopping:** Continue until the allocation stops changing or the search budget is exhausted.
- **Deployment:** Use the learned assignment on held-out examples. The system does not normally ask every candidate model to answer each new query.

The diagnoser matters because final-answer accuracy alone may hide an improvement. A critic may produce better feedback even when a later refiner still gives a wrong answer. The diagnoser can credit the critic separately and help the search move away from a poor local solution.

## Evidence and results

| Claim | Evidence offered | Strength of support | Caveat |
|---|---|---|---|
| Different modules benefit from different models | The selected systems often assign different models to generation, criticism, debate, refinement, location, and solving | Strong for the tested systems | The pipeline and prompts were fixed in advance |
| Mixed assignments can outperform one model used everywhere | LLMSelector reports gains of 5 to 70 percentage points over the best same-model assignment | Moderate | The largest gains came from synthetic table tasks |
| The diagnoser can improve search | The TableArithmetic case study shows it escaping a locally good but globally poor assignment | Moderate | The example is small, synthetic, and uses a powerful LLM judge |
| The search is more efficient than exhaustive testing | In the two-module, five-model case study it evaluates 10 alternatives rather than all 25 assignments | Strong for that search setup | This counts search evaluations, not full production cost |

## Evaluation quality

- The paper compares mixed assignments with using each candidate model for all modules.
- It evaluates three different pipeline types: self-refine, multi-agent debate, and locate-solve.
- It uses held-out examples, usually splitting each dataset 50% for training and 50% for evaluation.
- Final success is measured against known answers rather than only by the diagnoser's opinion.
- Several tasks use exact matching or simple binary metrics, which makes grading clear but does not capture complex work quality.
- The synthetic TableArithmetic and TableBias tasks make module failures easy to isolate but are less realistic than long-running agent tasks.

## Limitations and threats to validity

### Stated by the authors

- The theoretical result relies on strong assumptions about module improvements being consistent and not harming other modules.
- The authors acknowledge that these assumptions do not always hold in practice.
- The framework focuses on static systems with a bounded, fixed number of modules.

### Additional limitations I see

- LLMSelector does not design the pipeline, prompts, roles, or module connections.
- The learned assignment is mostly fixed for a dataset instead of adapting during each task.
- The objective emphasizes accuracy rather than model price, tokens, latency, or cost per successful completion.
- The LLM diagnoser needs labeled answers and may make incorrect error-attribution judgments.
- The experiments mainly produce answers or benchmark outputs rather than completing long-running work with tools, state, retries, and recovery.
- Results may change as models improve, prices change, and model strengths become less stable.

## Relationship to the landscape

- **Topics:** compound AI systems, heterogeneous model selection, LLM-as-a-judge, module assignment, multi-agent systems.
- **Connection to FrugalGPT:** FrugalGPT chooses which model or sequence of models should answer a query. LLMSelector assigns models to different modules inside a multi-stage system.
- **Important distinction:** It is an offline system configurator, not mainly a real-time router for each incoming query.
- **Landscape role:** It is a useful bridge between query-level routing and later work on role-aware or step-level agent routing.

## Gap relative to my research interests

The paper leaves several gaps connected to my interests:

1. **Production cost:** It reduces the cost of searching for an assignment, but does not directly optimize the operating cost of the selected system.
2. **Agentic work completion:** It focuses mostly on answer-producing pipelines rather than long-running work involving tools, changing state, retries, verification, and recovery.
3. **Dynamic handoffs:** It learns a mostly fixed assignment rather than deciding when to escalate or de-escalate between large, medium, and small models during a task.
4. **Handoff content:** It does not study what one model should communicate to the next model.
5. **Instruction detail:** It does not compare a short handoff with a detailed, context-rich instruction written specifically to help a lower-tier model execute the next stage.

A direction suggested by this paper is to study **cost-aware model handoffs during end-to-end agentic task completion**. For example, a large or mid-tier model could handle difficult planning or recovery and then give a lower-cost model either a minimal instruction or a detailed execution plan. The evaluation could measure whether extra handoff detail improves completion enough to offset its added token cost.

This is a gap relative to LLMSelector, not yet proof of a unique dissertation contribution. Later papers on planner-executor systems, agent routing, and heterogeneous teams still need to be considered.

## Research ideas triggered

- Compare fixed module assignments with dynamic step-level model selection.
- Measure total cost per successful task rather than only accuracy or search calls.
- Compare full history, short summaries, structured handoff state, and detailed downstream instructions.
- Study escalation and de-escalation between large, medium, and small models after progress or failure signals.
- Test whether conclusions hold on agentic benchmarks with executable task-completion grading.

## Key passages and figure locators

- **Abstract and Section 1:** Main problem, motivation, method, and reported gains.
- **Figure 3:** Overall LLMSelector workflow and required inputs.
- **Section 4.3 and Algorithm 1:** Module-by-module model selection and stopping process.
- **Section 4.3:** Definition and role of the LLM diagnoser.
- **Figure 4:** TableArithmetic example and comparison with exhaustive and greedy search.
- **Table 2:** Results across the six datasets.
- **Appendix B.4:** Exact prompt used for the LLM diagnoser.

## My judgment

- **Importance:** high
- **Confidence in findings:** medium
- **Relevance to dissertation search:** high
- **Next action:** compare with newer work on dynamic agent routing, planner-executor collaboration, role assignment, and full cost accounting

