# Interest map

Last updated: 2026-08-18

## The two anchor interests

### 1. AI harnesses

**Working interpretation:** the engineered runtime system around a model or agent that turns model capability into dependable behavior. It includes context selection, tool access, memory, task state, orchestration, permissions, observability, verification, recovery, and evaluation.

“AI harness engineering” is a useful but still-emerging label. The underlying components have longer research histories in agent architecture, software systems, human-computer interaction, security, and evaluation. Treat the label as a hypothesis about a coherent research area, not settled terminology.

### 2. AI in industry workflows

**Working interpretation:** agents performing or supporting consequential organizational work across enterprise software, people, documents, policies, and multi-step processes. The interesting unit is the workflow rather than an isolated prompt or task.

This includes both automation and collaboration: executing work, gathering information, making recommendations, requesting approval, handing off, documenting decisions, and recovering from exceptions.

## Strongest combined direction

> How should agent harnesses be designed and evaluated so that agents can execute real industry workflows reliably, observably, and under appropriate human control?

This seam is attractive because it joins a technical systems question with an applied organizational problem. It also creates measurable outcomes: task completion, process compliance, recovery quality, human effort, cost, latency, and trace quality.

## Adjacent areas worth testing

| Area | Connection to the anchors | Example research angle |
|---|---|---|
| Agent evaluation and observability | A harness must expose what happened and why | Trace-level failure attribution and process-aware evaluation |
| Human-agent workflow design | Industry work rarely becomes fully autonomous at once | Where approvals, escalation, and calibrated delegation belong |
| Security, permissions, and governance | Enterprise tools expose sensitive actions and data | Least-privilege tool use and policy-compliant execution |
| Process discovery and workflow mining | Organizations often lack clean machine-readable procedures | Learning executable workflows from demonstrations, logs, or SOPs |
| Multi-agent organizational systems | Real work is divided by role and expertise | When role-based agents help versus add coordination failure |
| Interoperability and portability | Harnesses must survive model, tool, and vendor changes | Portable agent specifications and cross-environment evaluation |
| Adaptation and organizational memory | Policies, software, and exceptions change over time | Safe updating of procedural memory without silent drift |
| Economics and job redesign | Technical success does not imply organizational value | Productivity, oversight cost, deskilling, and changed job boundaries |

## A useful decomposition

```text
Model capability
      ↓
Agent harness — context, tools, state, permissions, verification, recovery
      ↓
Workflow — tasks, dependencies, policies, people, enterprise software
      ↓
Organizational outcome — quality, time, cost, compliance, trust
```

This decomposition suggests that model quality, harness quality, workflow difficulty, and organizational outcome should be measured separately. Otherwise, a benchmark score cannot reveal where improvement came from or where failure occurred.

## Questions that cut across the map

1. Which failures belong to the model, harness, workflow specification, environment, or human handoff?
2. What is the right boundary between deterministic workflow logic and model-driven decisions?
3. Which forms of observability help developers, operators, auditors, and end users respectively?
4. How much reliability comes from a better model versus a better harness?
5. When should an agent act, ask, escalate, retry, roll back, or stop?
6. How do results transfer across models, organizations, software versions, and workflow variants?
7. What workflow properties predict whether agent deployment will create real value?

## Current priority

Deepen the two anchor topics first. Keep the adjacent areas as lenses, and promote one only when it repeatedly produces stronger questions or evidence than the anchors.
