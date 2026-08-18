# Synthesis: agent harness engineering

Status: initial scaffold; update after each cluster of papers.

## Provisional synthesis

The emerging harness view reframes an AI agent as a layered system rather than a model with a prompt. Earlier agent work provides the components—reasoning and acting, tools, memory, feedback, planning, evaluation, and control—while newer work asks whether the runtime substrate itself should be treated as an independent engineering and research object.

The central methodological opportunity is **separation of effects**. Current results often make it difficult to tell whether an improvement comes from a stronger model, better task specification, richer context, a new tool interface, additional retries, a verifier, or looser permissions. A dissertation contribution could make these components explicit and experimentally manipulable.

## Evidence table

| Claim or question | Supporting papers | Counterevidence or caveat | Confidence |
|---|---|---|---|
| Agent performance depends on the surrounding runtime | To add after reading | The label “harness engineering” is new and may repackage existing systems work | Low |
| Trace-level evaluation is necessary for diagnosis | To add after reading | More observability does not automatically yield correct causal attribution | Low |
| Harness components may transfer across models | To add after reading | Model-specific prompting and tool behavior may limit portability | Low |

## Concepts to reconcile

- Harness versus scaffold, runtime, middleware, agent architecture, workflow, and orchestration.
- State versus memory.
- Verification versus evaluation.
- Observability versus interpretability.
- Recovery versus replanning.
- Permissions versus human oversight.

## Reading synthesis prompts

For each paper, record:

1. What is inside the model, harness, environment, and workflow?
2. Which layer receives credit for improvement?
3. What state is maintained, and who can inspect it?
4. What can the agent do without confirmation?
5. How are failures detected, attributed, and recovered?
6. Which claims are likely to transfer to another model or domain?
