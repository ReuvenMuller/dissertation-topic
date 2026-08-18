# Topic paper pool: enterprise agent workflows

This pool focuses on realistic, multi-step organizational work and the methods needed to generate, execute, evaluate, and improve it.

## First pass: benchmark the reality gap

| Order | Paper | What it contributes | Reading depth |
|---:|---|---|---|
| 1 | [WorkArena: How Capable Are Web Agents at Solving Common Knowledge Work Tasks?](https://arxiv.org/abs/2403.07718) | Reproducible ServiceNow environment and common enterprise tasks | Deep |
| 2 | [WorkArena++: Towards Compositional Planning and Reasoning-based Common Knowledge Work Tasks](https://arxiv.org/abs/2407.05291) | Hundreds of realistic compositional workflows and human baselines | Deep |
| 3 | [CRMArena-Pro](https://arxiv.org/abs/2505.18878) | Expert-validated CRM workflows, multi-turn work, and confidentiality constraints | Deep |
| 4 | [SCUBA: Salesforce Computer Use Benchmark](https://arxiv.org/abs/2509.26506) | Tasks grounded in user interviews, realistic sandboxes, and milestone evaluation | Deep |
| 5 | [WONDERBREAD: A Benchmark for Evaluating Multimodal Foundation Models on Business Process Management Tasks](https://arxiv.org/abs/2406.13264) | Extends beyond execution to documenting, validating, and improving workflows | Deep |
| 6 | [Benchmarking Agentic Workflow Generation](https://openreview.net/forum?id=vunPXOFmoi) | Tests whether models can generate executable sequence and graph workflows | Medium |

## Second pass: broaden domains and interaction models

| Paper | Why it belongs |
|---|---|
| [CRMArena](https://arxiv.org/abs/2411.02305) | Earlier CRM benchmark and baseline for the Pro extension |
| [TheAgentCompany](https://arxiv.org/abs/2412.14161) | Simulated software company with consequential professional tasks |
| [τ-bench](https://arxiv.org/abs/2406.12045) | Dynamic interaction among user, agent, tools, and policy |
| [A Survey on Agent Workflow — Status and Future](https://arxiv.org/abs/2508.01186) | Organizes workflow systems by functionality and architecture |
| [A Survey on Large Language Model based Human-Agent Systems](https://arxiv.org/abs/2505.00753) | Human feedback, control, communication, and orchestration |
| [Ethics of Advanced AI Assistants](https://arxiv.org/abs/2404.16244) | Welfare, autonomy, misuse, and broader effects of capable assistants |

## Comparison dimensions

Record these for every benchmark or system:

- Industry and user role
- Source of realism: logs, interviews, experts, demonstrations, or synthetic construction
- Workflow length, branching, and application count
- Persistent state and distributed information
- Policy, privacy, and permission constraints
- Exception handling and reversibility
- Human interaction and handoffs
- Outcome, milestone, trace, cost, time, and human-effort metrics
- Environment reproducibility and maintenance burden
- Robustness to changed interfaces, policies, and workflow variants

## Exit criterion

After the first six papers, produce a cross-benchmark matrix and identify one missing capability that is both measurable and shared across at least three environments. Do not choose an industry domain solely because it has a convenient benchmark.
