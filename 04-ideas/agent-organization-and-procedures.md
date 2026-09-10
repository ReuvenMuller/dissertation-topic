---
idea: "Organizational and procedural design for AI agent teams"
created: 2026-09-07
status: literature-review
related_topics: [agent-harness-engineering, enterprise-agent-workflows]
source_notes: []
---

# Organizational and procedural design for AI agent teams

## Observation

How should AI agents be organized, and what work procedures should they follow, to complete tasks reliably and efficiently? This exploratory idea grew from an advisor's concern that agent organization may already be heavily explored, followed by discussion of software lifecycle methods, company structures, information sharing, and synergy.

The proposed research strategy is to survey existing approaches, reproduce representative methods, identify and explain weaknesses, and develop a new design only if the evidence supports one. It is not a commitment to a particular architecture or dissertation topic.

## Why it may matter

Organization and procedure may interact: a division of work that succeeds with frequent integration may fail with delayed verification. Agent teams also differ from human teams: agents have no biological fatigue, can be instantiated or reset, and can receive copied context. However, inference and coordination still cost time and compute; a large context window does not guarantee accurate understanding; and differently named agents may make similar errors.

## Researchable form

Umbrella question:

> Under what task conditions do organization, work procedure, and information distribution enable reliable and cost-effective agent collaboration?

Candidate questions, not verified gaps:

1. Does the best procedure depend on organizational structure, and vice versa?
2. How does ownership of shared software components interact with integration and verification schedules?
3. When does interaction produce gains beyond independently working agents with comparable aggregation and total resources?
4. Are apparent organizational failures actually caused by missing information, delayed feedback, or unenforced responsibilities?
5. Which assumptions of classical multi-agent organization remain valid for LLM agents, and which require changes?

## Existing evidence

- **Foundations:** the organizational-paradigms survey and MOISE+ show that agent organization, and separating structure from function, have long histories.
- **Concrete systems:** MetaGPT implements roles and procedures inspired by software companies; existing research also compares classical development processes.
- **Critical evidence:** scaling studies and MAST show conditional benefits and recurring coordination/verification failures. Debate or Vote shows why improvement over one agent does not establish interaction-driven synergy.
- **Close overlap:** MASS analyzes and optimizes agent designs; the organizational-science preprint explicitly separates organization, coordination, and collaboration protocols.
- **Unknown:** a specific original contribution has not yet been established. See the [ten-paper reading sequence](../01-reading-pools/idea-branches/agent-organization-and-procedures/README.md) and [discussion notes](../01-reading-pools/idea-branches/agent-organization-and-procedures/discussion-notes.md).

## Possible investigation

- **Method:** literature mapping, selective reproduction, then controlled experiments that vary organization and procedure separately and test their interaction. Diagnose causes before introducing a new design.
- **Environment:** software engineering is a possible initial domain, particularly dependent components and evolving requirements; it is not yet fixed.
- **Baselines:** a strong single agent with comparable resources; independent agents with a defined selection/integration procedure; representative fixed teams; relevant adaptive or automatically designed systems.
- **Evaluation:** functional correctness, regressions, repeated-trial reliability, rework, integration failures, human effort, cost, and elapsed time. Count coordination, review, retries, aggregation, and design/search overhead.
- **Generalization:** held-out projects, repeated runs, and multiple models; distinguish design-time optimization from deployment-time cost.

## Novelty check

The broad framing is already explored. Surveying methods and proposing a better system is a research strategy, not a novelty claim. Dynamic teams, failure-driven improvement, and fair single-agent comparisons also have direct predecessors. Adding another taxonomy dimension does not establish originality.

Earlier conversational encouragement was subsequently qualified after finding closer literature. Current assessment: a narrower contribution is plausible, but no unfilled gap is confirmed. The searches were targeted primary-source checks, largely abstracts and publication records, not an exhaustive systematic review or full reproduction audit.

Before committing, establish a precise difference from the closest work, a reproducible consequential failure, and a testable explanation suggesting an intervention. A useful result may be conditional guidance or improved evaluation rather than universal superiority.

## Relationship to the existing idea

[Cost-aware heterogeneous agent harnesses](heterogeneous-agent-harnesses.md) studies role-aware model allocation. This branch emphasizes organization, procedure, information, and collaboration mechanisms. They overlap, but neither replaces the other; model capabilities and budgets could initially be controlled in this branch.

## Next action

Read papers 1, 4, 5, and 8 in the [reading sequence](../01-reading-pools/idea-branches/agent-organization-and-procedures/README.md) as an early checkpoint, then decide which of the remaining readings to study deeply. For each, record what is varied, what the evidence establishes, what remains unresolved, and whether the question sustains personal interest.
