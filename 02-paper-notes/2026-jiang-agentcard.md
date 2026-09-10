---
title: "Specialize Roles, Mix Deployments: Pushing the Cost-Accuracy Frontier of LLM Agent Teams"
authors: ["Yinsicheng Jiang", "Liang Cheng", "Yeqi Huang", "Yufan Zhao", "Zhan Lu", "Li Dong", "Wenda Li", "Edoardo Ponti", "Luo Mai"]
year: 2026
venue: "arXiv preprint"
url: "https://arxiv.org/abs/2606.20629"
paper_id: "arxiv-2606.20629"
status: read
priority: high
topics: [agent-teams, role-assignment, planner-executor, verifier, heterogeneous-models, cost, deployment, pareto]
date_added: 2026-08-23
date_read: 2026-08-24
---

# Specialize Roles, Mix Deployments: Pushing the Cost-Accuracy Frontier of LLM Agent Teams

## Why I am reading this

This is the closest paper found so far to the proposed research on cost-aware heterogeneous agent harnesses. It evaluates different models in different agent roles, compares API and self-hosted deployments, treats the whole team as the evaluated system, and asks which allocation lies on the cost-accuracy frontier. It therefore provides both a foundation and an important boundary for a proposed three-tier hierarchy in which a strong model creates the architecture or high-level plan, a medium model turns that plan into a detailed execution contract, and a cheaper model performs the work with bounded repair and escalation.

## Citation

Jiang, Y., Cheng, L., Huang, Y., Zhao, Y., Lu, Z., Dong, L., Li, W., Ponti, E., & Mai, L. (2026). *Specialize roles, mix deployments: Pushing the cost-accuracy frontier of LLM agent teams*. arXiv:2606.20629. https://arxiv.org/abs/2606.20629

## One-paragraph summary

AgentCARD is not merely a collection of existing benchmarks adapted to multi-agent tasks. It is a controlled evaluation framework for studying **Cost, Accuracy, Role assignment, and Deployment mode** at the level of the agent team. The authors place models into a common planner-executor harness across five existing task benchmarks, enumerate heterogeneous and homogeneous role assignments, and calculate per-task cost for API, self-hosted, and hybrid deployments. Their main finding is that the model assigned to each role matters: a heterogeneous team can outperform the corresponding homogeneous teams at lower cost, while reversing the same two models can sharply reduce performance. They add role-specific Shapley values to identify whether planning or execution is the bottleneck, a small planner-verifier-executor pilot, and a same-domain held-out selection experiment. The paper establishes that team configuration is a meaningful unit of evaluation, but it does not study a full strong-to-medium-to-cheap handoff cascade, systematic model-size or reasoning-effort scaling, detailed handoff fidelity, or dynamic exception-driven escalation.

## Research problem and context

Most model evaluations ask which individual model is best. Most multi-agent work holds the backbone model fixed and varies prompts, roles, or communication structure. Neither view directly answers a deployment question: given several models with different prices and deployment modes, which model should occupy each role in a compound agent system?

AgentCARD reframes evaluation around the **team configuration** rather than an isolated model. A configuration includes the model-role mapping and whether each role uses a hosted API or self-hosted open-weight model. This is especially important because roles consume different amounts and kinds of tokens. In the paper’s harness, executors read roughly 200 times more input than planners emit and have a median cost about 6.3 times the planner cost. A relatively expensive planner can therefore be economical if it enables a much cheaper executor to complete the long, token-heavy part of the task.

## Contribution

The paper makes three main contributions:

1. **Role-aware team evaluation.** It evaluates heterogeneous planner-executor assignments in both directions and shows that model identity and role are not interchangeable.
2. **Unified deployment economics.** It compares API, self-hosted, and hybrid teams using a common per-task cost model and reports cost-accuracy Pareto frontiers.
3. **Role-criticality diagnosis.** It uses role-specific Shapley values to estimate whether upgrading the planner or executor contributes more on a task family.

Two smaller extensions broaden the main study: a three-role planner-verifier-executor pilot and a held-out same-domain experiment testing whether a team selected on a calibration split remains strong on the other half.

## Approach

### Benchmarks and harness

The authors use a unified OpenCode-based planner-executor harness with common role prompts and tool interfaces. They vary models and deployment modes while keeping the surrounding scaffold fixed. The five task environments are:

- MCP-Atlas for open-domain tool use;
- MedAgentBench for clinical API interaction;
- FinanceBench for document-based financial question answering;
- IMO-AnswerBench for mathematical problem solving with Python; and
- SWE-bench Lite for software issue resolution.

These are existing benchmarks, but AgentCARD uses them as environments in a new factorial study of team configurations. The paper is therefore better understood as a deployment and allocation benchmark layered over existing task benchmarks than as a new task corpus.

### Models and assignments

The API pool contains GPT-5.4, Claude Opus 4.6, MiniMax M2.7, and GLM 5.1. The self-hosted pool contains Qwen3.5-4B, Qwen3.5-27B, GPT-OSS-20B, and GPT-OSS-120B. The main API experiment evaluates the full 4-by-4 matrix of planner-executor assignments, including homogeneous self-play and heterogeneous teams. Additional experiments cover open-weight and hybrid API/local teams.

This gives some within-family scale contrasts—4B versus 27B Qwen and 20B versus 120B GPT-OSS—but it is not a systematic small/medium/large scaling study. API parameter counts are unknown, and model identity, provider, training, serving mode, price, and capability change together.

### Cost accounting

API cost is computed from the input, cached-input, and output tokens consumed by each role. Self-hosted cost is based on GPU count, an H100 hourly price of $1.87, wall-clock time, and task count. Headline self-hosted estimates assume a 1,000-task parallel workload; the authors report that throughput saturates near 100 parallel tasks and that single-stream cost is about 1.9 times higher. Tool and orchestration costs are excluded because the authors estimate them at less than 5% of the measured total.

This is a useful reproducible serving-cost definition, but not a complete operational cost model. It does not fully price orchestration engineering, queueing, human intervention, failures, retries outside the harness, or latency-sensitive capacity.

### Synergy and Pareto analysis

The headline pairwise synergy measure compares a heterogeneous team with a cost-matched convex interpolation between the two corresponding homogeneous teams. A positive value means that assigning the two models to different roles performs above the line connecting their self-play configurations. An appendix also reports a stricter comparison against the upper envelope of all homogeneous teams. This distinction is essential: the paper’s largest reported pair-line synergy is 44 points, while the corresponding gain over the global homogeneous envelope is 8 points.

Pareto analysis then identifies configurations for which no other measured team is both cheaper and more accurate. The claim is empirical and conditional on the tested models, prices, harness, benchmarks, and concurrency assumptions; it is not evidence that one team is universally optimal.

### Role-criticality analysis

For a chosen weak and strong model in each role, the authors evaluate the four planner-executor combinations and compute the marginal value of upgrading each role using Shapley attribution. The result is a useful local bottleneck diagnostic. It should not be treated as an intrinsic property of a benchmark: the attribution is conditional on the selected weak-to-strong upgrade path and the fixed harness.

## Evidence and results

| Claim | Evidence | Strength | Caveat |
|---|---|---:|---|
| Heterogeneous role assignment can improve the cost-accuracy frontier. | Heterogeneous API, local, and hybrid teams occupy evaluated Pareto frontiers across the five domains. | Strong within the experiment. | Conditional on the model pool, snapshot prices, harness, and tasks. |
| Direction of assignment matters. | Reversing the same model pair can turn positive synergy negative; the paper describes swings approaching 80 points. | Strong. | Does not isolate whether the cause is planning ability, instruction style, tool competence, context handling, or another model-specific property. |
| A strong planner can enable a cheaper executor. | On SWE-bench, GPT-5.4 planning with MiniMax execution reaches 76.2%, compared with 68.2% for GPT-5.4 self-play, at about $0.021 per task in the appendix. | Strong headline example. | SWE-bench shows the clearest separation; several other top configurations have overlapping confidence intervals. |
| Hybrid deployment can preserve quality at much lower cost. | On IMO-AnswerBench, Claude planning with Qwen3.5-27B execution reaches 80.6%, versus 80.2% for Claude self-play, at roughly $0.108 versus $1.283. | Strong example. | Depends on the paper’s high-utilization local-serving assumptions. |
| All-local teams can be competitive. | On FinanceBench, Qwen3.5-4B planning with Qwen3.5-27B execution reaches 60.0% at about $0.009 per task, outperforming tested API teams and costing roughly 23 times less than Claude self-play. | Strong example. | One domain and one deployment snapshot; local costs may differ in practice. |
| Different tasks have different capability-critical roles. | Open-weight Shapley values identify planning as critical on MedAgentBench (29 versus 3) and execution as critical on FinanceBench, IMO, and MCP-Atlas. SWE-bench varies with model scale and deployment mode. | Useful diagnostic evidence. | Values are conditional on the selected model upgrade pair, not universal task constants. |
| A verifier can add value when assigned carefully. | In the MCP pilot, GLM planning, GPT verification, and MiniMax execution reaches 83.8% at $0.039, versus 80.4% at $0.070 for the strongest two-agent comparison. A Finance pilot improves from 53.3% to 62.7% with a Qwen-27B verifier. | Promising pilot. | Small, selectively explored three-role study; a weak or mismatched verifier can reduce performance. |
| Configuration selection has some held-out stability. | A random 50/50 calibration split selects the held-out top team in four of five domains and the second-ranked Finance team, 1.8 points below the top. | Encouraging. | This is same-domain random splitting, not transfer to new domains, providers, model generations, or task distributions. |

The confidence intervals matter. Several top teams are statistically tied under 95% bootstrap intervals, and small reported synergies of around two or three points should be interpreted cautiously. The most defensible conclusion is not that heterogeneous teams always win, but that role assignment can materially change outcomes and should be evaluated explicitly.

## Evaluation quality

The evaluation is unusually strong in its breadth of assignments, common harness, role-level cost logging, deployment comparison, and inclusion of homogeneous baselines. Enumerating both directions of each pair directly exposes asymmetry that a simple “large model plus small model” label would hide. Reporting configuration-level Pareto frontiers also matches the actual deployment decision better than reporting accuracy alone.

The analysis is strengthened by bootstrap confidence intervals, stricter appendix synergy metrics, held-out selection, scaling measurements for local inference, logged prompts and tool registries, and a versioned snapshot of models and prices. The paper also makes a valuable conceptual move: public claims about a model’s quality are insufficient for predicting its contribution inside a workflow.

At the same time, the experiment entangles model family, size, training, inference policy, provider, and deployment. It reveals which tested configuration works, but not a clean causal scaling law for model capability or reasoning effort. The fixed harness improves internal comparability while potentially favoring models that follow its planner and executor prompts particularly well.

## Limitations and threats to validity

- **Snapshot dependence.** Rankings and Pareto frontiers can change as providers update models and prices.
- **Limited task coverage.** Five benchmarks provide breadth, but do not establish generality across enterprise, browser, long-horizon, high-risk, or open-ended workflows.
- **Primarily two roles.** The main evidence concerns a fixed planner-executor topology; the three-role verifier study is a small pilot.
- **No systematic tier or reasoning-effort experiment.** The paper does not independently vary small, medium, and large models or low-to-high thinking budgets within the same family.
- **Static configuration selection.** Teams are selected offline at the domain level rather than adapting per task or escalating during execution.
- **Handoff quality is mostly latent.** The plan is the interface, but the paper does not compare minimal, detailed, structured, or validated execution contracts or directly measure information loss across handoffs.
- **No learned specialization.** “Specialize” means assigning existing general-purpose models to roles, not training models to become role specialists.
- **Conditional role attribution.** Shapley conclusions depend on which weak and strong models define the upgrade path.
- **Incomplete operational economics.** Serving cost is carefully measured, but latency, orchestration, intervention, and downstream failure costs are not jointly optimized.
- **Optimistic local utilization.** Batched self-hosting costs presume enough parallel work to utilize the GPUs efficiently.
- **Limited transfer evidence.** The held-out analysis uses random same-domain splits and does not test cross-family or cross-domain policy transfer.
- **Combinatorial scaling.** Exact two-level Shapley analysis requires 2^N configurations for N roles, and a full model-role grid grows as |M|^N. Large teams or swarms are not studied.

## Relationship to the landscape

AgentCARD moves beyond request-level routers such as FrugalGPT by allocating models to persistent functional roles inside an agent workflow. It is also more directly empirical than general compound-system optimizers because it measures actual planner-executor deployments across API and self-hosted models. It supports the broad premise that heterogeneous assignment can outperform homogeneous self-play on both quality and cost.

For the current idea, it closes off a weak novelty claim: **“use the strongest model to plan and a cheaper model to execute” is already demonstrated and is not enough by itself.** It also shows why a proposal should not assume that the strongest model always belongs upstream. Several tasks are executor-critical, and direction must be treated as an experimental factor.

The paper leaves a more specific and potentially valuable opening around **handoff engineering and conditional control**. It does not determine when a middle translation layer is useful, how detail and structure affect downstream execution, how failures propagate through the hierarchy, or when an executor should repair locally versus escalate upward. It also does not derive a transferable decision rule from task properties to architecture and allocation.

## Gap relative to my hierarchical handoff idea

The proposed system is better described as a **hierarchical capability cascade with detailed handoffs and exception-driven escalation**:

1. A high-capability model converts the original task into an architecture, intent, constraints, and high-level plan.
2. A medium-capability model converts that plan into a concrete, step-by-step execution contract, checking for ambiguity and missing prerequisites.
3. A lower-cost model executes the contract, repairs local problems within defined bounds, and escalates when the plan conflicts with the environment or exceeds its authority.
4. An optional reviewer may inspect plans, execution traces, or final outcomes; reviewer tier and placement are experimental variables rather than fixed assumptions.

The conceptual flow is **intent → specification → action**, with upward exception paths. This differs from a conventional cheap-to-expensive query cascade because it deliberately pays for high-tier planning first. The economic hypothesis must therefore be tested explicitly: a short expensive planning call plus medium-tier translation, cheap execution, and occasional recovery must cost less than frontier-model execution while preserving comparable task success and reliability.

The most defensible gap is not “three models instead of two.” It is the joint study of:

- whether an intermediate translator improves executable specificity or introduces distortion and overconstraint;
- handoff fidelity and causal error propagation across stages;
- exception-driven local repair, escalation, and replanning;
- task-conditional inclusion, removal, combination, or reordering of roles;
- model tier and reasoning-effort allocation within and across providers;
- repeated-run reliability, latency, intervention, and cost per successful task; and
- whether a learned decision map transfers across task families, model families, and model generations.

This is a conditional-pattern question rather than a yes-or-no hypothesis. The desired output is a map from task and environment properties to the architecture and allocation most likely to occupy the quality-cost-latency-reliability frontier.

## Candidate experimental direction prompted by the paper

### Research question

Under what task, model-family, reasoning-effort, and handoff conditions does hierarchical capability delegation improve the performance-cost-latency-reliability frontier relative to compute-matched single-model and homogeneous-agent baselines?

### Candidate explanatory factors

- task horizon, decomposability, reversibility, tool burden, and environmental uncertainty;
- proportion of work spent planning versus executing;
- plan quality, abstraction level, and execution-contract completeness;
- within-family versus cross-family allocation;
- model tier and reasoning effort at each stage;
- permission for local correction and the threshold for escalation; and
- reviewer competence, placement, and false-accept/false-reject behavior.

### Initial hypotheses to test rather than assume

- Decomposable tasks with long, routine execution phases will benefit most from expensive upstream reasoning and cheap downstream execution.
- Dynamic or poorly observed environments will require a stronger executor or frequent upward escalation, eroding savings.
- A medium translator will help when a sound high-level plan is too abstract for a cheaper executor, but will hurt when it removes useful flexibility, adds unsupported assumptions, or faithfully elaborates a flawed plan.
- Reasoning effort may be most valuable upstream for architecture-heavy tasks and downstream for tasks dominated by tool feedback and local decisions.
- Within-family teams may preserve intent and formatting more reliably, while cross-family teams may gain complementary strengths or lower prices.
- Short tasks may favor a single capable model because orchestration overhead dominates.
- High-risk or irreversible tasks may require stronger verification even when ordinary benchmark accuracy is unchanged.

Negative findings are informative. For example, discovering that the translator rarely adds value, that escalation eliminates the cost advantage, or that cross-family handoffs systematically distort intent would narrow the useful design space.

### Baselines and ablations

For an OpenAI example using Sol, Terra, and Luna, compare:

- each model acting alone;
- homogeneous three-stage teams at each tier;
- Sol → Terra → Luna;
- Sol → Luna, removing the translator;
- Terra → Luna, removing the frontier architect;
- Sol → Terra with Terra also executing;
- Luna direct versus Luna with a high-level plan versus Luna with a detailed execution contract;
- reversed and alternative assignments;
- no-review versus reviewers at different tiers and positions;
- fixed allocation versus adaptive escalation; and
- budget-matched, token-matched, latency-matched, and oracle configurations.

The same factorial logic should be repeated within other genuine model families and then across providers. Exact model IDs and snapshots must be frozen because vendor tier names and available versions change. Within-family results provide a cleaner test of capability tier and reasoning effort; cross-family results test complementarity, communication compatibility, provider effects, and transfer, but introduce more confounds.

Candidate family structures include OpenAI Sol/Terra/Luna; Anthropic Opus/Sonnet/Haiku; Google Pro/Flash/Flash-Lite where concurrent versions permit; DeepSeek Pro/Flash; Grok using reasoning-effort levels when distinct general-model tiers are unavailable; Kimi using reasoning-effort levels and clearly labeled specialist models; and open-weight Qwen sizes for more controlled scale experiments. These should be treated as experimental strata, not assumed equivalent tiers.

### Outcome and failure measures

The final benchmark score should remain the primary outcome, but it is insufficient for explaining the system. Also record:

- plan quality and unsupported assumptions;
- execution-contract completeness, ambiguity, and constraint preservation;
- handoff fidelity from user intent to plan to instructions to actions;
- executor compliance and conditional success given a valid plan;
- local repair success, false escalation, missed escalation, and replanning frequency;
- failure origin and downstream propagation;
- final success, partial progress, and repeated-trial reliability;
- tokens, monetary cost, and latency by stage;
- retries, human intervention, and total cost per successful task; and
- Pareto frontiers over quality, cost, latency, and reliability.

## Benchmark strategy

State-of-the-art individual-model benchmarks should be used largely **as they are** so that the three-model hierarchy can be evaluated as one agent system on the same task definition and primary metric. Preserve task instances, environments, tools, graders, time limits, and official scoring. Do not rewrite tasks to advertise the intended hierarchy; the harness should decide how to divide the original work.

However, public leaderboard results are usually outcomes of a **model plus agent scaffold**, not a naked model. A fair study therefore needs three reporting layers:

1. **Controlled same-harness comparison:** rerun single models, homogeneous teams, and heterogeneous teams under the same tools, context rules, stopping criteria, and infrastructure.
2. **Unchanged benchmark result:** report the official task metric so the system remains legible to the broader literature.
3. **External leaderboard context:** show public state-of-the-art results separately, clearly labeled as contextual rather than controlled comparisons.

Promising primary environments are Terminal-Bench for long-running terminal work, τ²-bench for tool-policy-user interaction and repeated-trial reliability, WorkArena++ for compositional enterprise workflows, and SWE-bench Verified or its standardized Bash-only setting for software work. Static knowledge and reasoning benchmarks can serve as calibration tasks, but they should not be the primary evidence because they do not exercise persistent handoffs, tool execution, repair, or escalation.

A small development subset can be used to debug prompts and instrumentation. The architecture, escalation policy, metrics, and analysis plan should then be frozen before running the full benchmark to reduce overfitting to public tasks.

## Research ideas triggered

1. **Handoff-fidelity benchmark.** Create controlled variants of the execution contract—minimal, detailed natural language, structured schema, checked contract, and deliberately corrupted handoff—to estimate how information quality changes downstream success.
2. **Error-propagation tracing.** Label whether each failure originates in architecture, translation, execution, verification, or escalation and measure which errors are amplified, caught, or repaired at later stages.
3. **Conditional architecture selector.** Learn a policy that predicts whether a task needs one model, two stages, three stages, a verifier, or a stronger executor from task and early-trajectory features.
4. **Reasoning-budget allocation.** Hold model identity fixed where possible and move thinking effort among roles to distinguish architectural value from simply buying more inference compute.
5. **Transfer study.** Train or tune the allocation rule within one provider family, test on other families, then evaluate whether role-criticality and escalation policies survive model updates.
6. **Operational frontier.** Extend AgentCARD-style monetary accounting with latency, capacity, retries, intervention, and failure costs to estimate the deployable rather than merely serving-cost frontier.

## Key passages and figure locators

- **Abstract and introduction, pp. 1–2:** motivation for treating model-role-deployment configuration as the unit of evaluation and summary of heterogeneous-team gains.
- **AgentCARD framework and cost definitions, pp. 3–5:** benchmark composition, unified planner-executor harness, model pools, deployment modes, and per-task cost accounting.
- **Main cost-accuracy results, pp. 6–8:** API, self-hosted, and hybrid Pareto frontiers; assignment direction and synergy results.
- **Role-criticality analysis, pp. 8–9:** role-specific Shapley construction and domain-dependent planner/executor bottlenecks.
- **Three-agent pilot and held-out analysis, pp. 9–10:** planner-verifier-executor results and calibration-to-held-out stability.
- **Limitations and discussion, pp. 10–11:** scaling, snapshot, task-coverage, and combinatorial caveats.
- **Appendix tables:** exact team accuracies, costs, pair-line versus upper-envelope synergy, confidence intervals, concurrency scaling, and prompts.

## My judgment

- **Importance:** high
- **Confidence in understanding:** high
- **Relevance to my work:** very high
- **Bottom line:** AgentCARD strongly validates evaluating heterogeneous agent teams as systems and makes fixed planner-executor role assignment a required baseline. It also prevents an overly broad novelty claim about using a strong planner with a cheap executor. The promising dissertation gap is narrower and richer: detailed multi-stage handoffs, reasoning-budget placement, error propagation, adaptive repair and escalation, and task-conditional architecture selection across model families.
- **Next action:** use AgentCARD’s full directional role matrix, homogeneous baselines, role-level cost accounting, and Pareto reporting as design requirements for the experimental protocol. Before implementation, operationalize handoff-fidelity labels and select one long-horizon benchmark plus one interactive reliability benchmark for the first controlled pilot.
