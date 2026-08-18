# Candidate research questions: agent harness engineering

These are deliberately framed as testable question families. They should become narrower after the first reading pass.

## A. Component contribution and interaction

**Question:** Which harness components improve reliable task completion, and which combinations create interaction effects?

- Compare context management, memory, verification, checkpointing, recovery, and permission policies.
- Hold the model and task set fixed; then repeat across model families.
- Measure task success, policy compliance, cost, latency, intervention rate, and failure severity.
- Main threat: components are difficult to isolate because they change the effective information and action space.

## B. Failure attribution from execution traces

**Question:** Can a diagnostic system distinguish model, context, tool, memory, orchestration, permission, and environment failures?

- Create or annotate a failure taxonomy using traces from several agent benchmarks.
- Compare human diagnosis, rule-based diagnosis, and model-assisted diagnosis.
- Evaluate inter-rater agreement, attribution accuracy, actionability, and time to repair.
- Main threat: many failures have multiple interacting causes rather than one label.

## C. Adaptive recovery and escalation

**Question:** What policy should decide whether an agent retries, replans, changes tools, asks a human, rolls back, or stops?

- Treat recovery as a sequential decision under uncertainty and asymmetric error costs.
- Compare fixed rules, confidence thresholds, learned policies, and model-generated reflection.
- Evaluate recovered-task success, repeated failure, unnecessary escalation, damage avoided, and added cost.
- Main threat: confidence signals may be poorly calibrated or easy to game.

## D. Portable harness evaluation

**Question:** Which harness benefits transfer across models, task families, and changing tools?

- Define a portable harness interface and a shared evaluation protocol.
- Test whether component rankings remain stable after model or environment changes.
- Measure absolute performance, relative gains, rank stability, and maintenance effort.
- Main threat: apparent portability may come from choosing tasks that omit domain-specific constraints.

## E. Harness complexity budget

**Question:** When does additional scaffolding stop being worth its operational cost?

- Construct a harness complexity measure using components, calls, state, branching, and maintenance burden.
- Estimate reliability–cost–latency frontiers rather than optimizing success alone.
- Include developer and operator effort if it can be measured credibly.
- Main threat: maintainability and human effort are hard to compare across systems.

## First-choice comparison

| Question family | Novelty potential | Evaluation access | Likely dissertation depth | Immediate next evidence |
|---|---|---|---|---|
| Component contribution | High | High | High | Harness/component matrix and pilot ablation |
| Failure attribution | High | Medium–high | High | Trace availability and labeling study |
| Recovery and escalation | High | Medium | High | Failure corpus and cost model |
| Portability | Medium–high | High | High | Cross-model replication design |
| Complexity budget | Medium | Medium | Medium–high | Operational metrics literature |

No winner is selected yet. Component contribution and failure attribution currently appear to offer the cleanest entry points.
