# Idea-branch paper pool: cost-aware heterogeneous agent harnesses

Research date: 2026-08-23

Related idea: [heterogeneous-agent-harnesses.md](../../../04-ideas/heterogeneous-agent-harnesses.md)

Parent topic: [agent harness engineering](../../../03-topics/agent-harness-engineering/README.md)

## Working question

> Given a task and a pool of models with different capabilities and costs, which role assignment and orchestration policy produces the best quality–cost–latency–reliability frontier?

The motivating architecture is a frontier architect or planner, a mid-tier decomposer, and a low-cost executor, with optional verification and escalation. The literature shows that this exact family of systems now exists, but does not yet offer a settled answer about when it is beneficial.

## State-of-the-art in one paragraph

The field has progressed from routing whole queries between cheap and expensive models, through adaptive cascades, to selecting different models for modules and agent roles. The current frontier consists of **role-aware team composition** (AgentCARD), **joint role-and-model routing** (GraphPlanner), **small/large planner–executor collaboration** (COPE), and **step-level trajectory routing** (AgentRouter). At the same time, TeamBench and a 2026 Nature Machine Intelligence study show that coordination and verification can hurt when roles are weak, tasks do not decompose cleanly, or a strong single agent already performs well. The dissertation opportunity is therefore not “do multiple models help?” but predicting and controlling **when, where, and at what total cost** heterogeneity helps.

## Must-read sequence

Read in this order. The sequence establishes the foundations before the newest, closest papers.

| Order | Paper | Category | Why it is essential | Maturity |
|---:|---|---|---|---|
| 1 | [FrugalGPT](https://arxiv.org/abs/2305.05176) | Cascades | Establishes cost-aware selection across heterogeneous LLM APIs | TMLR 2024 |
| 2 | [AutoMix](https://arxiv.org/abs/2310.12963) | Adaptive cascades | Uses self-verification and a POMDP router across model sizes | NeurIPS 2024 |
| 3 | [RouteLLM](https://openreview.net/forum?id=8sSqNntaMr) | Query routing | Strong learned-routing baseline and cost–quality methodology | ICLR 2025 |
| 4 | [A Unified Approach to Routing and Cascading for LLMs](https://proceedings.mlr.press/v267/dekoninck25a.html) | Routing theory | Formalizes routing, cascading, and their optimal combination | ICML 2025 |
| 5 | [Optimizing Model Selection for Compound AI Systems](https://arxiv.org/abs/2502.14815) | Module assignment | Directly asks which model should serve each call or module | 2025 preprint |
| 6 | [Efficient LLM Collaboration via Planning (COPE)](https://arxiv.org/abs/2506.11578) | Planner–executor | Closest foundation for large/small collaboration through plans | TMLR 2026 |
| 7 | [GraphPlanner](https://arxiv.org/abs/2604.23626) | Agentic routing | Jointly selects an LLM backbone and agent role during a workflow | ICLR 2026 |
| 8 | [Specialize Roles, Mix Deployments (AgentCARD)](https://arxiv.org/abs/2606.20629) | Role-aware teams | Closest direct empirical study of planner/executor/verifier model assignment and cost frontiers | 2026 preprint |
| 9 | [AgentRouter](https://openreview.net/forum?id=nu3GPfkyJV) | Step-level routing | Routes each trajectory step to the cheapest adequate model tier | ICML 2026 workshop paper |
| 10 | [TeamBench](https://arxiv.org/abs/2605.07073) | Evaluation | Enforces planner/executor/verifier separation and measures whether teamwork was real | 2026 preprint |
| 11 | [Capable Language Models Can Outgrow the Benefits of Collaboration](https://www.nature.com/articles/s42256-026-01268-y) | Critical evidence | Controlled evidence that collaboration is conditional and can add damaging overhead | Nature Machine Intelligence 2026 |
| 12 | [RouterBench](https://arxiv.org/abs/2403.12031) | Benchmarking | Supplies routing baselines, oracle comparison, and cost–performance evaluation structure | 2024 preprint |

## What to extract from every must-read

1. What is the unit of allocation: query, response attempt, module, step, subtask, or semantic role?
2. Is allocation fixed, learned offline, adapted online, or changed after failure?
3. What information crosses each handoff, and how is information loss measured?
4. Which costs are counted: API dollars, tokens, GPU time, latency, retries, verification, and coordination?
5. Are single-agent and homogeneous-team baselines compute-matched?
6. Can the study attribute failure separately to planning, handoff, execution, verification, or tools?
7. Does the result transfer across model families, task domains, and newer model generations?

## Extended pool by subcategory

### A. Query routing, cascades, and budget allocation

| Paper | Contribution to the branch | Priority |
|---|---|---|
| [Hybrid LLM](https://arxiv.org/abs/2404.14618) | Difficulty- and quality-aware strong/weak query routing | High context |
| [BEST-Route](https://proceedings.mlr.press/v267/ding25d.html) | Joint choice of model and test-time sample count | High context |
| [Adaptive LLM Routing under Budget Constraints](https://aclanthology.org/2025.findings-emnlp.1301/) | Online contextual-bandit routing with explicit budgets | High context |
| [RouterEval](https://arxiv.org/abs/2503.10657) | Very large model-routing evaluation corpus | Reference |
| [LLMRouterBench](https://arxiv.org/abs/2601.07206) | Unified 2026 re-evaluation; finds many routers fail to beat simple baselines | Critical reference |
| [Dynamic Model Routing and Cascading for Efficient LLM Inference](https://arxiv.org/abs/2603.04445) | Recent survey and routing taxonomy | Orientation |

These papers optimize model choice for a query or response. They are necessary foundations, but they do not by themselves answer which model should perform an architect, executor, or verifier role.

### B. Model selection inside compound and agentic systems

| Paper | Contribution to the branch | Priority |
|---|---|---|
| [BudgetMLAgent](https://arxiv.org/abs/2411.07464) | Cheap base agent with occasional GPT-4 planning and expert escalation on ML workflows | High |
| [SC-MAS](https://arxiv.org/abs/2601.09434) | Selects roles, LLM backbones, and pairwise collaboration strategies | High |
| [Self-Resource Allocation in Multi-Agent LLM Systems](https://openreview.net/forum?id=0ZnEzvSLNR) | Capability-aware allocation among unequal worker agents | High |
| [MALT](https://arxiv.org/abs/2412.01928) | Jointly trains heterogeneous generator, verifier, and refiner roles | Medium |

### C. Planner–executor and role-specialization foundations

| Paper | Contribution to the branch | Priority |
|---|---|---|
| [Plan-and-Act](https://arxiv.org/abs/2503.09572) | Separates high-level planning from environment-specific execution | High |
| [LLM-Blender](https://aclanthology.org/2023.acl-long.792/) | Pairwise ranking and generative fusion across heterogeneous model outputs | Medium |
| [Mixture-of-Agents](https://arxiv.org/abs/2406.04692) | Layered collaboration across multiple different LLMs | Medium |
| [MultiAgentBench](https://aclanthology.org/2025.acl-long.421/) | Compares collaboration topologies and milestone-based coordination | Medium |

These papers show useful role or topology patterns, but most do not make model cost and role–capability matching the central experimental variable.

### D. Evaluation environments already in the repository

Do not duplicate their inventory rows or notes. Reuse them as candidate evaluation environments:

- [τ-bench](https://arxiv.org/abs/2406.12045) — policy-constrained tool–agent–user workflows and repeated-trial reliability.
- [SWE-bench](https://arxiv.org/abs/2310.06770) — repository-level software tasks with executable grading.
- [GAIA](https://openreview.net/forum?id=fibxvahvs3) — general assistant tasks requiring tools and multimodal reasoning.
- [AgentBench](https://arxiv.org/abs/2308.03688) — diverse interactive agent environments.
- [WorkArena++](https://arxiv.org/abs/2407.05291) — realistic, compositional enterprise workflows.
- [TheAgentCompany](https://arxiv.org/abs/2412.14161) — consequential tasks in a simulated workplace.

## Frontier claims that require replication

- AgentCARD reports that heterogeneous role assignments occupy the cost–accuracy frontier across its evaluated domains, but it is a June 2026 preprint.
- AgentRouter reports large savings from step-level routing, but it is a workshop paper and relies on its task-tier labeling and fallback design.
- SC-MAS and Self-Resource Allocation offer promising allocation results but are very recent and not yet a mature consensus.
- Results tied to current API prices, named models, or benchmark versions can age quickly. Preserve raw tokens, calls, latency, and hardware assumptions so costs can be recomputed.

## Exit criterion for this pool

After the 12 must-reads, produce:

1. A role × model × task matrix showing exactly what has been tested.
2. A shared definition of total cost and compute-matched baselines.
3. A list of at least three findings that replicate across independent papers.
4. One precise gap that remains after AgentCARD, GraphPlanner, COPE, AgentRouter, TeamBench, and the Nature study are all taken seriously.

Do not select the topic merely because the architecture is appealing. Select it only if the gap survives these closest papers.
