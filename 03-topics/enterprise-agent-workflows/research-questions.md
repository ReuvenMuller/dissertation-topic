# Candidate research questions: enterprise agent workflows

## A. Workflow difficulty and failure prediction

**Question:** Which measurable workflow properties predict whether an agent will succeed, fail dangerously, or require human help?

- Candidate properties: length, branching, application count, statefulness, ambiguity, policy density, exception rate, reversibility, and information distribution.
- Fit a difficulty model across several enterprise benchmarks rather than one task suite.
- Evaluate predictive accuracy, cross-benchmark transfer, and usefulness for deployment decisions.
- Main threat: benchmark annotations may not capture the hidden organizational knowledge that determines real difficulty.

## B. Deterministic–agentic boundary

**Question:** Which workflow steps should be encoded as deterministic process logic and which should be delegated to an agent?

- Compare fully agentic, fully scripted, and hybrid systems on workflow variants and exceptions.
- Vary the amount and placement of model discretion.
- Measure success, robustness, authoring effort, change cost, latency, and error severity.
- Main threat: the best boundary may be domain-specific and shift with model capability.

## C. Human intervention placement

**Question:** Where should a workflow require approval, allow optional review, or run autonomously?

- Model decisions by uncertainty, action reversibility, information sensitivity, and downstream impact.
- Compare fixed checkpoints with adaptive escalation.
- Measure risk reduction, unnecessary interruption, human workload, delay, and trust calibration.
- Main threat: simulated users and simplified cost models may poorly represent organizational behavior.

## D. Process-aware evaluation

**Question:** What evaluation signals distinguish a correct result produced through a bad process from a genuinely reliable workflow execution?

- Score milestones, policy compliance, evidence use, state changes, recovery, and auditability.
- Test whether process metrics predict failures under task perturbations better than final success alone.
- Compare automatic graders with expert review.
- Main threat: process scoring can become overly prescriptive when several valid paths exist.

## E. Workflow transfer and change

**Question:** How robust are workflow agents to changed interfaces, policies, roles, and organizational variants?

- Create controlled perturbations to known workflows.
- Compare brittle replay, retrieval-based adaptation, replanning, and human-assisted updating.
- Measure zero-shot transfer, adaptation cost, regression risk, and undetected policy violations.
- Main threat: realistic changes are expensive to model and may expose benchmark-specific shortcuts.

## F. From task automation to workflow redesign

**Question:** When does adding an agent justify redesigning the workflow rather than substituting for a human step?

- Compare substitution, augmentation, and redesigned processes.
- Include system-level throughput, queueing, review burden, and exception handling.
- Best suited to a later field study or realistic organizational simulation.
- Main threat: causal evidence may require partner access and a long observation period.

## First-choice comparison

| Question family | Novelty potential | Evaluation access | Likely dissertation depth | Immediate next evidence |
|---|---|---|---|---|
| Difficulty and failure prediction | High | High | High | Harmonize public benchmark task attributes |
| Deterministic–agentic boundary | High | Medium–high | High | Select one replayable environment |
| Intervention placement | High | Medium | High | Oversight and HCI literature pass |
| Process-aware evaluation | High | High | High | Compare milestone/trace evaluators |
| Transfer and change | High | Medium | High | Environment perturbation feasibility |
| Workflow redesign | High | Low–medium | High | Industry access or simulation design |

Difficulty prediction and process-aware evaluation currently appear to be the fastest rigorous entry points. Workflow redesign may ultimately be more consequential but has greater access risk.
