# Exploratory discussion notes: organization, procedure, and synergy

Recorded: 2026-09-07. Source: the advisor/topic exploration conversation in this task.

These notes preserve ideas and qualifications from the discussion. They are not full paper reviews, verified causal findings, or evidence of a settled novelty claim. The active reading assignment remains the ten papers in [README.md](README.md).

## Motivation and progression

The advisor questioned whether agent organization is promising or already explored. The discussion moved through software lifecycle strategies (Waterfall, Agile/sprints), company structures, joint organizational/procedural design, information distribution, other design factors, and whether collaboration creates synergy beyond independent contributions.

The user's preferred strategy is to reproduce existing approaches, identify their weaknesses, and let a new design emerge from evidence. The qualification is that universal superiority is unnecessary and unlikely: conditional improvements in reliability, cost, or task suitability may be more defensible.

## Design dimensions

| Dimension | Decisions to inspect |
|---|---|
| Organization | Roles, team membership, hierarchy, communication access, ownership, decision authority |
| Procedure | Decomposition, planning, execution order, iteration, testing, integration, review, recovery, termination |
| Information and memory | Shared/private context, selective retrieval, handoff contents, project state, stale assumptions |
| Capabilities and resources | Model assignment, tools, compute, coordination and verification budgets |
| Execution and enforcement | Shared versus isolated workspaces, conflict reconciliation, prompted versus enforced boundaries |
| Objectives and feedback | Local versus global success, independent evidence, executable checks, human judgment |
| Adaptation | Fixed design, within-task reorganization, learning across tasks, triggers and overhead |

These are useful lenses, not necessarily independent axes. Task dependencies, requirement uncertainty, change, and feedback availability are evaluation conditions. Human involvement and team diversity cut across the design. Define what an agent is: a model call is not necessarily a persistent worker with private state and tools.

## Agent-specific hypotheses

- No biological fatigue may permit frequent review, but review consumes compute and latency.
- On-demand instantiation may allow variable team size, but onboarding, duplicated context, and coordination have costs.
- Copyable/resettable context makes handoff and memory design explicit choices.
- Large context access does not imply reliable understanding of all dependencies.
- Different job titles do not establish different skills or independent errors.

These observations motivate experiments; they do not prove that human processes are unsuitable or that an agent-specific redesign is novel.

## Organizational alternatives

Company analogies include functional departments, product divisions, matrix authority, cross-functional teams, and networked teams; tall/flat describes hierarchy depth rather than a mutually exclusive category. Classical MAS adds markets, coalitions, holarchies (nested groups acting as units), federations/brokers, and normative organizations. Blackboard systems coordinate through shared evolving work. Distinguish common-goal teams under one owner from independently owned agents with conflicting interests.

## Synergy as an outcome

Do not add accuracy percentages to define the sum of independent contributions. Beating one ordinary run may reflect more compute. Independent voting/selection may yield gains without interaction. A practical interaction-gain comparison uses the same agents working independently with a defined aggregation procedure, comparable resources, and matching tool/information access where appropriate.

Stronger causal evidence comes from removing or altering exchanges and showing that gains disappear under controlled conditions. No agent initially possessing the answer is insufficient: additional independent attempts might find it. Information-theoretic emergence and useful task performance are distinct measurements. A narrow coordination game does not establish software-development synergy.

Working question: under what conditions does interaction create value beyond independent work, and which organizational/procedural choices enable it?

## Candidate experiments discussed

- Expertise-based versus feature-based grouping under varying component dependencies.
- Component ownership crossed with integration or verification timing.
- Identical roles/procedures with full history, assignment-specific context, or maintained shared state plus retrieval.
- Development under changing requirements, measuring regressions and rework as well as initial success.
- Temporary teams formed around a failure or dependency, with the cost and necessity of reorganization measured.
- Handoff sufficiency, verification placement, and recovery after partial failure.

All are candidate questions requiring novelty checks. Control models, tools, and budgets before attributing results to organization. Include strong single-agent, independent/aggregated, fixed-team, and relevant adaptive baselines; count search/design overhead separately from operating cost. Use held-out tasks, repeated runs, and multiple models when feasible.

## Prior-work cautions and wider context

The shortlist is deliberately bounded, but the discussion also identified direct overlap outside it:

- [AgileCoder](https://arxiv.org/abs/2406.11912): sprints plus dependency tracking; improvements cannot automatically be assigned to Agile alone.
- [MAS-ZERO](https://arxiv.org/abs/2505.14996): per-instance design/refinement, dynamic composition and decomposition, and simplification.
- [Meta-Team](https://arxiv.org/abs/2605.29790): experience-driven improvement of behavior, coordination, and organization.
- [OrgAgent](https://arxiv.org/abs/2604.01020): company-style hierarchy; reasoning-task results do not establish general software-development superiority.
- [TeamBench](https://arxiv.org/abs/2605.07073): enforced role separation, relevant to whether teamwork is actually exercised.
- [BenchAgent](https://arxiv.org/abs/2606.05670): normalized comparisons of single, fixed-team, and evolving workflows.
- [SWE-EVO](https://arxiv.org/abs/2512.18470) and [SWE-INTERACT](https://arxiv.org/abs/2606.30573): sustained development and interactive requirements already have dedicated evaluation work.
- [DyLAN](https://arxiv.org/abs/2310.02170), [Internet of Agents](https://arxiv.org/abs/2407.07061), and [LLM blackboard architecture](https://arxiv.org/abs/2507.01701): adaptive membership, heterogeneous integration, and shared-workspace coordination already exist.

These are context links, not additions to the ten-paper assignment. Neither a paper-specific limitation nor a new application automatically establishes a field-wide gap.

## Current assessment

The broad area is established and crowded. The two-dimensional framing has classical as well as recent predecessors. Initial encouragement concerned the exploration strategy; later searches required a more cautious novelty assessment. There may be room for a specific explanatory or methodological contribution, but that has not been demonstrated.

The purpose of reading is to decide whether organizational theory, failure analysis, synergy measurement, or adaptive design sustains interest and yields a precise question. Do not preselect a new architecture as the inevitable outcome of the review.
