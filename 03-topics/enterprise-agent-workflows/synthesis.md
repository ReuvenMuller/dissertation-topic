# Synthesis: enterprise agent workflows

Status: initial scaffold; update after each cluster of papers.

## Provisional synthesis

Enterprise workflow research shifts the unit of analysis from an isolated task to a process. The agent must maintain state, gather distributed information, follow rules, use several capabilities, handle exceptions, and coordinate with people or other systems. Recent benchmarks make this work more measurable, but each captures a different slice of organizational reality.

The central opportunity is to develop **process-aware science of agent performance**: identify workflow properties that cause failure, design the right deterministic and agentic division of labor, and evaluate execution quality beyond the final answer.

## Benchmark comparison scaffold

| Benchmark | Domain | Workflow unit | Realism source | Human interaction | Policy/security | Process evaluation | Main limitation |
|---|---|---|---|---|---|---|---|
| WorkArena | ServiceNow | To fill after reading |  |  |  |  |  |
| WorkArena++ | Enterprise knowledge work |  |  |  |  |  |  |
| CRMArena / Pro | CRM |  |  |  |  |  |  |
| SCUBA | Salesforce computer use |  |  |  |  |  |  |
| WONDERBREAD | Business processes |  |  |  |  |  |  |
| WorfBench | Generated agent workflows |  |  |  |  |  |  |
| TheAgentCompany | Simulated software company |  |  |  |  |  |  |
| τ-bench | Tool-agent-user interaction |  |  |  |  |  |  |

## Evidence table

| Claim or question | Supporting papers | Counterevidence or caveat | Confidence |
|---|---|---|---|
| Realistic workflows remain difficult for leading agents | To add after reading | Results change quickly with models and scaffolds | Low |
| Workflow properties explain performance beyond task length | To add after reading | No shared cross-benchmark schema yet | Low |
| Process metrics reveal risks hidden by final success | To add after reading | Process grading may penalize valid alternative paths | Low |

## Reading synthesis prompts

For each paper, record:

1. What makes its tasks representative of industry work?
2. What workflow properties are present or absent?
3. Is the system executing, generating, documenting, monitoring, or improving a workflow?
4. Which actions are consequential or irreversible?
5. Where do people enter the process?
6. Does evaluation score outcomes, milestones, traces, policies, cost, or human effort?
7. What would break if the organization, interface, or policy changed?
