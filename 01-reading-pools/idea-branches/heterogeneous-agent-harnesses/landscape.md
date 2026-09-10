# State-of-the-art landscape: heterogeneous agent harnesses

Cutoff: 2026-08-23

## Scope and terminology

The idea belongs at the intersection of several fields. No single name yet captures the entire space.

| Term | Typical allocation decision | Relationship to this idea |
|---|---|---|
| LLM routing | Choose one model for a query | Foundation, but usually no sequential roles |
| LLM cascade | Try a cheap model, then escalate | Adds sequential decisions, but usually solves one response |
| Compound AI model selection | Choose a model for each system module | Direct bridge to role-based harnesses |
| Heterogeneous multi-agent system | Different models or capabilities collaborate | Broad parent area; may omit cost and hierarchy |
| Planner–executor architecture | Separate strategic planning from actions | Direct architectural foundation |
| Agentic routing | Select models, roles, or workflows during a trajectory | Closest dynamic formulation |
| Role-aware team composition | Assign models to planner, executor, verifier, and other roles | Closest fixed-composition formulation |

The branch uses **cost-aware heterogeneous agent harnesses** as a working label because it includes model assignment, communication, verification, escalation, state, and cost accounting—not just the existence of several agents.

## Evolution of the field

```text
Whole-query selection
FrugalGPT / Hybrid LLM / RouteLLM
             ↓
Adaptive escalation and compute allocation
AutoMix / Unified Routing+Cascading / BEST-Route
             ↓
Model choice inside compound systems
LLMSelector / BudgetMLAgent
             ↓
Joint model, role, step, and workflow allocation
COPE / GraphPlanner / AgentRouter / SC-MAS / AgentCARD
             ↓
Controlled evaluation of whether teams help at all
TeamBench / Nature Machine Intelligence 2026
```

## Current frontier

### 1. Fixed role-aware composition

AgentCARD is the closest direct match to the proposed study. It evaluates planner–executor and planner–verifier–executor configurations, compares API, self-hosted, and hybrid deployment, and uses Pareto and role-criticality analyses. Its core implication is that “strongest model everywhere” is not always the cost-optimal team, and that the bottleneck role may vary by domain.

**Remaining issue:** it is a very recent preprint, its domain and model grid cannot establish a general law, and it does not settle dynamic adaptation or handoff design.

### 2. Dynamic role-and-model selection

GraphPlanner selects an agent role and model backbone during workflow construction. AgentRouter makes a finer step-level decision about the cheapest adequate tier. SC-MAS jointly constructs roles, backbones, and communication edges.

**Remaining issue:** these systems entangle several design choices. When they improve, it can be difficult to isolate whether the gain came from task decomposition, model selection, memory, topology, more inference, or the router itself.

### 3. Planning as the interface between strong and weak models

COPE directly studies small and large models exchanging plans in a cascade. Plan-and-Act provides an important planner–executor foundation, while BudgetMLAgent uses occasional expensive planning and expert calls around cheaper execution.

**Remaining issue:** a correct plan may still be unexecutable by a weak worker, and plan text can lose state, constraints, or tacit environment knowledge. Few studies measure execution success conditional on plan quality.

### 4. Cost-aware optimization

FrugalGPT, RouteLLM, AutoMix, Hybrid LLM, the unified routing/cascading framework, and BEST-Route establish quality–cost methods and oracle comparisons.

**Remaining issue:** their unit of allocation is commonly a standalone query. Agent workflows add delayed rewards, dependency between steps, repeated context, tool latency, recovery, and irreversible actions.

### 5. Critical and negative evidence

TeamBench shows that nominal role prompts can hide role collapse, and that a verifier can approve incorrect work. The 2026 Nature Machine Intelligence study finds that multi-agent benefit is strongly task-dependent, that coordination can amplify error, and that strong single-agent baselines can erase the value of collaboration. LLMRouterBench similarly reports that sophisticated routers often fail to reliably beat simple routing baselines under unified evaluation.

**Implication:** strong single-agent and simple-router baselines are not optional. A successful dissertation should explain negative results rather than filtering them out.

## What is established versus unsettled

| Proposition | Current assessment | Reason |
|---|---|---|
| Different models have meaningfully different cost–quality profiles | Established | Replicated across routing and cascade work |
| Learned routing can reduce cost on static query benchmarks | Established, conditional | Multiple peer-reviewed systems; sensitive to quality estimators and distribution shift |
| Planner–executor separation can improve some long-horizon tasks | Supported, conditional | Several systems, but both roles can remain bottlenecks |
| A frontier planner plus cheap executor is generally optimal | Not established | Role criticality is domain-dependent; worker quality can dominate |
| Heterogeneous teams generally beat one strong agent | Contradicted as a general claim | Benefits vary sharply by task and architecture |
| Dynamic role/model routing beats fixed teams | Promising, not settled | Closest evidence is recent and systems differ substantially |
| Current cost savings transfer across providers and model generations | Not established | Prices, throughput, context behavior, and capabilities change |
| Final task accuracy is enough to evaluate a team | Clearly inadequate | Role collapse, handoff failure, verifier error, and coordination overhead remain hidden |

## The most defensible research gaps

### Gap A: conditional architecture selection

Predict when a single agent, homogeneous team, fixed heterogeneous hierarchy, or adaptive heterogeneous harness should be used based on measurable task properties and pilot trajectories.

### Gap B: role-aware dynamic escalation

Allocate capability during the workflow rather than fixing a frontier planner and cheap executor in advance. Escalation could respond to uncertainty, plan quality, failed verification, environmental novelty, or action risk.

### Gap C: architecture, review, handoff fidelity, and failure propagation

Treat the workflow structure as an experimental variable rather than assuming a fixed hierarchy. Measure what information is lost when an architect's high-level plan is translated by a mid-tier model into detailed instructions for a low-tier executor. Vary whether roles are present, combined, repeated, or reordered, and assign the reviewer role to low-, mid-, and frontier-tier models. Determine whether instruction specificity and fidelity improve execution, whether review corrects more errors than it introduces, and when a more expensive upstream model merely creates an authoritative bad plan.

### Gap D: realistic total-cost frontiers

Include repeated context, coordination messages, router overhead, tool latency, retries, verification, parallel critical path, local GPU amortization, and human intervention—not only output-token price.

### Gap E: model- and domain-robust allocation

Test whether a learned role policy survives model replacement, pricing changes, new task distributions, and industry workflows with policy and state constraints.

## Recommended initial research formulation

> Under what task and workflow conditions does role-aware heterogeneous model allocation improve the quality–cost–latency–reliability frontier over compute-matched single-agent and homogeneous-team baselines?

This is stronger than assuming a capability hierarchy. It allows the experiment to discover that the frontier model belongs in planning, execution, verification, several roles, or nowhere for a given task class.

## Minimum experimental design implied by the literature

| Dimension | Minimum levels |
|---|---|
| Team architecture | Single agent; plan–execute; plan–execute–review; architect–instruction writer–executor; role-combined and role-ablated variants |
| Role assignment | All frontier; all mid-tier; all low-cost; frontier→mid→low; alternative and reversed assignments; adaptive; oracle |
| Review | No reviewer; reviewer before execution; reviewer after execution; low-, mid-, and frontier-tier reviewer |
| Task type | Static reasoning; decomposable parallel work; sequential tool work; policy-constrained workflow |
| Budget control | Equal dollar budget and equal inference-compute sensitivity analysis |
| Outcome | Success, partial progress, reliability across repeats, policy compliance |
| Process | Plan quality, handoff fidelity, execution conditional on plan, verifier precision/recall |
| Economics | Tokens by role, calls, retries, latency, local/API cost, critical path |

## Risks to the idea

- AgentCARD already covers a substantial portion of the fixed role-assignment question.
- Fast model turnover may make a model-specific result obsolete before publication.
- Large factorial experiments can become prohibitively expensive.
- Benchmarks may reward decomposition patterns that do not transfer to real workflows.
- A router can cost more to train or calibrate than it saves at realistic traffic volumes.
- “Model size” is an unreliable proxy for capability; role-specific measured competence should replace tier labels whenever possible.
