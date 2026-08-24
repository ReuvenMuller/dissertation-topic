---
idea: "Cost-aware heterogeneous agent harnesses"
created: 2026-08-23
status: literature-review
related_topics: [agent-harness-engineering, enterprise-agent-workflows]
source_notes: []
---

# Cost-aware heterogeneous agent harnesses

## Observation

A single model does not need to perform every part of a complex task. A harness could assign a frontier model to architecture or difficult planning, a mid-tier model to detailed decomposition, and a cheaper model to execution, then escalate or verify selectively.

## Why it may matter

Agent systems face a multi-objective deployment problem: performance, reliability, cost, and latency. Uniformly using the strongest model may waste resources, while uniformly using a cheap model may fail on the few decisions that determine the entire trajectory. Role-aware allocation could spend capability where its marginal value is highest.

## Researchable form

Primary question:

> Under what task and workflow conditions does role-aware heterogeneous model allocation improve the quality–cost–latency–reliability frontier over compute-matched single-agent and homogeneous-team baselines?

Candidate subquestions:

1. Which role is capability-critical for which task properties?
2. Should assignment be fixed before execution or adapt after uncertainty and failure signals?
3. How does handoff representation affect error propagation from planner to executor?
4. When does a verifier create value, and when does it add cost or false confidence?
5. Does an allocation policy transfer across model families, providers, and model generations?

## Existing evidence

- **Evidence for:** routing and cascade work repeatedly shows cost–quality gains; COPE, GraphPlanner, AgentRouter, SC-MAS, and AgentCARD extend selection into compound or agentic workflows.
- **Evidence against a general claim:** TeamBench exposes role and verifier failures; a 2026 Nature Machine Intelligence study finds that collaboration can degrade performance and that heterogeneous centralized teams did not consistently beat strong homogeneous baselines.
- **Unknowns:** robust task-to-architecture prediction, three-tier role hierarchies, realistic handoff losses, full operational cost, and generalization to industry workflows.

## Possible investigation

- **Method:** controlled factorial experiments plus a learned or rule-based allocation policy.
- **Data or environment:** TeamBench, τ-bench, SWE-bench, WorkArena++, and one lower-cost static benchmark for calibration.
- **Baselines:** strong and cheap single agents; homogeneous strong and cheap teams; fixed heterogeneous assignments in both directions; adaptive routing; oracle assignment.
- **Evaluation:** success, partial progress, repeated-trial reliability, plan quality, conditional execution success, verifier precision/recall, failure origin, tokens, monetary cost, latency, retries, and Pareto frontiers.

## Novelty check

The initial search found substantial direct overlap:

- AgentCARD evaluates role-aware planner/executor/verifier team composition and deployment cost.
- GraphPlanner jointly selects model backbones and agent roles.
- COPE studies small/large collaboration through planning.
- AgentRouter selects model tiers per trajectory step.

Therefore, a fixed demonstration of “large planner + small executor” is unlikely to be novel enough. Novelty must come from a surviving gap documented in the [state-of-the-art landscape](../01-reading-pools/idea-branches/heterogeneous-agent-harnesses/landscape.md).

## Next action

Read the [12-paper must-read sequence](../01-reading-pools/idea-branches/heterogeneous-agent-harnesses/README.md), then build a role × model × task matrix before refining the research question.
