---
idea: "Cost-aware heterogeneous agent harnesses"
created: 2026-08-23
status: literature-review
related_topics: [agent-harness-engineering, enterprise-agent-workflows]
source_notes: ["../02-paper-notes/2024-chen-frugalgpt.md", "../02-paper-notes/2025-chen-llmselector.md", "../02-paper-notes/2026-jiang-agentcard.md"]
---

# Cost-aware heterogeneous agent harnesses

## Observation

A single model does not need to perform every part of a complex task. One candidate harness could assign a frontier model to architecture or difficult planning, a mid-tier model to decompose that plan and write detailed instructions for a cheaper model, and the cheaper model to execute those bounded instructions. This is a hypothesis to test, not a fixed architecture: components may be added, removed, combined, or reordered, and an optional reviewer or verifier may itself use a low-, mid-, or frontier-tier model.

## Why it may matter

Agent systems face a multi-objective deployment problem: performance, reliability, cost, and latency. Uniformly using the strongest model may waste resources, while uniformly using a cheap model may fail on the few decisions that determine the entire trajectory. Role-aware allocation could spend capability where its marginal value is highest.

## Researchable form

Primary question:

> Under what task and workflow conditions does role-aware heterogeneous model allocation improve the quality–cost–latency–reliability frontier over compute-matched single-agent and homogeneous-team baselines?

Candidate subquestions:

1. Which role is capability-critical for which task properties?
2. Should assignment be fixed before execution or adapt after uncertainty and failure signals?
3. How faithfully can a mid-tier model translate a high-level plan into detailed instructions that a low-tier model can execute, and how do errors propagate across these handoffs?
4. When does a reviewer or verifier create value, which model tier should perform that role, and when does review add cost, latency, or false confidence?
5. Does an allocation policy transfer across model families, providers, and model generations?
6. Which components and handoffs are actually necessary, and when should roles be combined, omitted, repeated, or reordered?

## Existing evidence

- **Evidence for:** routing and cascade work repeatedly shows cost–quality gains; COPE, GraphPlanner, AgentRouter, SC-MAS, and AgentCARD extend selection into compound or agentic workflows.
- **Evidence against a general claim:** TeamBench exposes role and verifier failures; a 2026 Nature Machine Intelligence study finds that collaboration can degrade performance and that heterogeneous centralized teams did not consistently beat strong homogeneous baselines.
- **Unknowns:** robust task-to-architecture prediction, whether plan-to-instruction-to-execution separation is beneficial, instruction sufficiency, reviewer-tier effects, realistic handoff losses, full operational cost, and generalization to industry workflows.

## Possible investigation

- **Method:** controlled factorial and ablation experiments that vary included roles, role ordering, tier assignment, review placement, and escalation, followed by a learned or rule-based allocation policy.
- **Data or environment:** TeamBench, τ-bench, SWE-bench, WorkArena++, and one lower-cost static benchmark for calibration.
- **Baselines:** strong, mid-tier, and cheap single agents; homogeneous teams at each tier; architectures with roles removed or combined; fixed heterogeneous assignments in multiple directions; reviewers at each tier; no-review controls; adaptive routing; oracle assignment.
- **Evaluation:** success, partial progress, repeated-trial reliability, plan quality, instruction quality, conditional execution success, reviewer precision/recall by tier, failure origin, tokens, monetary cost, latency, retries, and Pareto frontiers.

## Novelty check

The initial search found substantial direct overlap:

- AgentCARD evaluates role-aware planner/executor/verifier team composition and deployment cost.
- GraphPlanner jointly selects model backbones and agent roles.
- COPE studies small/large collaboration through planning.
- AgentRouter selects model tiers per trajectory step.

Therefore, a fixed demonstration of “large planner + small executor” is unlikely to be novel enough. Novelty must come from a surviving gap documented in the [state-of-the-art landscape](../01-reading-pools/idea-branches/heterogeneous-agent-harnesses/landscape.md).

## Next action

Read the [12-paper must-read sequence](../01-reading-pools/idea-branches/heterogeneous-agent-harnesses/README.md), then build a role × model × task matrix before refining the research question.
