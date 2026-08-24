# Industry evidence: agent harnesses and heterogeneous model systems

Research date: 2026-08-23

Academic companion: [cost-aware heterogeneous agent harnesses](../idea-branches/heterogeneous-agent-harnesses/README.md)

Canonical report inventory: [industry-inventory.csv](industry-inventory.csv)

## Purpose and boundary

This collection captures evidence that is valuable but does not belong in the academic paper inventory:

- production system descriptions;
- engineering experiments and postmortems;
- architecture and deployment guidance based on customer work;
- product documentation that exposes a concrete routing mechanism; and
- original practitioner surveys.

These sources are useful for discovering real constraints, system patterns, operational costs, and research questions. They are not substitutes for peer review. Vendor benchmarks, internal evaluations, and product claims must be labelled as such and independently tested before they support a dissertation conclusion.

## The industry picture in one paragraph

Several independent organizations have converged on the same broad design: use a capable model for planning, ambiguity, synthesis, or final review; delegate bounded work to cheaper models or agents; and pay the coordination cost only when the task decomposes cleanly. Anthropic supplies the clearest production account and cost warning, Cognition describes the closest explicit frontier-model-plus-cheap-sidekick harness, and Microsoft now recommends per-step model tiering in its agent architecture guidance. At the same time, Anthropic, Cognition, Google Cloud, and AWS all warn—directly or through their design trade-offs—that multi-agent systems add context-transfer problems, latency, debugging difficulty, token use, and failure modes. The convergence is a strong motivation for controlled research, not proof that the architecture is generally optimal.

## Evidence labels

| Label | What it means | How much weight to give it |
|---|---|---|
| Measured production system | A deployed system with architecture details and quantitative internal results | Strong industry evidence, but metrics and data are controlled by the publisher |
| Engineering experiment | A concrete built system or artifact with costs or outcomes | Useful mechanism evidence; generalization and controls may be weak |
| Production case study | Lessons from a real internal or customer deployment | Strong for constraints and failure modes; often weak for causal comparison |
| Vendor benchmark | Quantitative comparison supplied by the product maker | Treat as a result to reproduce, not an established fact |
| Practice-based guide | Recommendations distilled from deployments or engineering experience | Good for hypotheses and baselines; not outcome evidence |
| Product documentation | A precise description of a currently implemented capability | Establishes that a mechanism exists, not that it is optimal |
| Reference architecture | A proposed production design and its trade-offs | Useful for realistic experimental requirements |
| Practitioner survey | Self-reported adoption, obstacles, and practices | Useful context; vulnerable to sampling and response bias |

## Must-read sequence

Read these first, in order.

| Order | Report | Organization | Why it matters | Evidence type |
|---:|---|---|---|---|
| 1 | [Building Effective Agents](https://www.anthropic.com/engineering/building-effective-agents) | Anthropic | Defines orchestrator–worker and evaluator–optimizer patterns, while recommending the simplest architecture that works | Practice-based guide |
| 2 | [A Practical Guide to Building AI Agents](https://openai.com/business/guides-and-resources/a-practical-guide-to-building-ai-agents/) | OpenAI | Gives an explicit workflow for starting with the strongest model, establishing evals, then replacing calls with cheaper models | Practice-based guide |
| 3 | [How We Built Our Multi-Agent Research System](https://www.anthropic.com/engineering/multi-agent-research-system) | Anthropic | Best production account of a strong lead model coordinating cheaper parallel workers, with quality and token-use measurements | Measured production system |
| 4 | [Devin Fusion](https://cognition.com/blog/devin-fusion) | Cognition | Closest industry implementation of the proposed idea: frontier main agent plus cheaper sidekick, with dynamic mid-session routing | Vendor benchmark |
| 5 | [Choice of Agent Host](https://learn.microsoft.com/en-us/agents/architecture/host-platform) | Microsoft | Explicitly recommends frontier models for hard steps and smaller models for extraction, formatting, and routing | Practice-based architecture guidance |
| 6 | [Use Model Router with Foundry Agents](https://learn.microsoft.com/en-us/azure/foundry/openai/how-to/model-router-agents) | Microsoft | Documents per-turn routing among cheap, mid-tier, and frontier models inside agent trajectories | Product documentation |
| 7 | [Harness Design for Long-Running Application Development](https://www.anthropic.com/engineering/harness-design-long-running-apps) | Anthropic | Tests planner–generator–evaluator separation and publishes phase-level time and token cost | Engineering experiment |
| 8 | [Building a C Compiler with a Team of Parallel Claudes](https://www.anthropic.com/engineering/building-c-compiler) | Anthropic | Large artifact-level experiment exposing specialization, shared-repository coordination, testing, and total cost | Engineering experiment |
| 9 | [Harness Engineering: Leveraging Codex in an Agent-First World](https://openai.com/index/harness-engineering/) | OpenAI | Real internal software system illustrating environment design, feedback loops, decomposition, and agent-first development | Production case study |
| 10 | [AgentOps: Operationalize Agentic AI at Scale](https://aws.amazon.com/blogs/machine-learning/agentops-operationalize-agentic-ai-at-scale-with-amazon-bedrock-agentcore/) | AWS | Adds the operational variables academic benchmarks often omit: traces, budgets, security, deployment, and system-level evaluation | Reference architecture and field guidance |

## Extended collection by category

### A. Multi-agent production systems and experiments

| Source | Contribution | Main limitation |
|---|---|---|
| [Effective Harnesses for Long-Running Agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) | Initializer/coder separation, structured handoffs, incremental progress, and context resets | Same model and tools; not a heterogeneous model comparison |
| [Multi-Agents: What’s Actually Working](https://cognition.com/blog/multi-agents-working) | Candid discussion of shared context, implicit decisions, write conflicts, and why read-only subagents are easier | Qualitative company experience rather than a controlled evaluation |
| [Inside OpenAI’s In-House Data Agent](https://openai.com/index/inside-our-in-house-data-agent/) | Production lessons on context, memory, permissions, clarification, and continuous evals across enterprise data | Does not compare role-specific model allocation |
| [Scaling Managed Agents: Decoupling the Brain from the Hands](https://www.anthropic.com/engineering/managed-agents) | Separates session, harness, and sandbox; reports latency improvements from infrastructure decoupling | Infrastructure architecture rather than model-team effectiveness |

### B. Heterogeneous models, routing, and cost

| Source | Contribution | Main limitation |
|---|---|---|
| [Effective Cost Optimization Strategies for Amazon Bedrock](https://aws.amazon.com/blogs/machine-learning/effective-cost-optimization-strategies-for-amazon-bedrock/) | Recommends specialized agents, task-matched models, parallelism, and a lightweight supervisor | Vendor guidance without a controlled comparison for the proposed hierarchy |
| [The Builder’s Guide to GPT-5.6](https://openai.com/index/builders-guide-to-gpt-5-6/) | Current examples of model selection, parallel decomposition, compaction, and moving deterministic work into code | Model-specific guide with selected customer claims |
| [Agentic AI: Multimodal GraphRAG Resource Orchestration](https://docs.cloud.google.com/architecture/agentic-ai-multimodal-graph-rag-resource-orchestration) | Explicitly recommends granular model scaling: smaller models for high-volume tasks and high-capacity models for complex reasoning | Reference design, not an evaluated comparative study |

### C. Architecture selection and enterprise operation

| Source | Contribution | Main limitation |
|---|---|---|
| [Choose a Design Pattern for Your Agentic AI System](https://docs.cloud.google.com/architecture/choose-design-pattern-agentic-ai-system) | Compares single-agent, sequential, coordinator, hierarchical, and collaborative patterns with latency and cost trade-offs | General architecture guidance |
| [Orchestrate Access to Disparate Enterprise Systems](https://docs.cloud.google.com/architecture/agenticai-orchestrate-access-disparate-systems) | Production-oriented orchestrator architecture with state, MCP tools, identity, observability, and human review | Describes a target architecture rather than measured outcomes |
| [How We Contain Claude Across Products](https://www.anthropic.com/engineering/how-we-contain-claude) | Shows a role-specific small model used to inspect tool results inside a safety harness | Safety mechanism, not general task allocation |
| [State of Agent Engineering](https://www.langchain.com/state-of-agent-engineering) | Original survey of what practitioners deploy, evaluate, and struggle with | Self-selected respondents from an agent-framework ecosystem |

## Quantitative claims worth reproducing

These are claims made by the publishers, not independent conclusions:

- Anthropic reports that its Opus-lead/Sonnet-worker research system improved its internal research evaluation by 90.2% over single-agent Opus, while multi-agent use consumed about 15 times the tokens of ordinary chats.
- Cognition reports that Devin Fusion’s frontier-agent-plus-sidekick architecture reached near-frontier coding performance at substantially lower task cost on its FrontierCode benchmark; the page’s figures were updated after publication as models changed.
- Anthropic’s planner–generator–evaluator application harness cost more than 20 times its short solo comparison in one early experiment, and a later run still cost roughly $125 for several hours of work.
- Anthropic’s parallel compiler experiment used 16 agents, nearly 2,000 sessions, and about $20,000 to produce a roughly 100,000-line compiler capable of building Linux for multiple architectures.
- Anthropic reports that decoupling managed-agent inference from execution containers reduced median time-to-first-token by roughly 60% and p95 by more than 90%.

Record the original benchmark, model version, price date, and denominator whenever citing one of these figures.

## What to extract from each source

1. Is this a deployed system, an experiment, a guide, or a product claim?
2. What is the allocation unit: role, subtask, turn, tool call, or whole session?
3. Which model handles planning, ambiguity, execution, verification, and safety?
4. What crosses the handoff, and what context stays private to a worker?
5. Which costs are reported: tokens, dollars, latency, infrastructure, retries, or people?
6. What is the comparison baseline, and is it compute-matched?
7. Which failures are admitted, and which claims cannot be audited from public material?
8. What concrete experiment or benchmark could independently test the claim?

## Reading discipline

- Never convert “used in production” into “shown to improve performance.”
- Never treat a vendor’s benchmark as independent validation of its architecture.
- Prefer architectural details, denominators, costs, failure cases, and negative results over headline percentages.
- Recalculate dollar costs when possible because model prices and routing pools change quickly.
- Use these reports to improve experimental realism and identify hypotheses; use papers and reproducible experiments to decide whether those hypotheses hold.

## Exit criterion

After the ten must-reads, produce:

1. an industry-pattern matrix mapping company × architecture × role allocation × cost measurement;
2. a list of claims independently supported by more than one organization;
3. a list of vendor claims that still lack independent replication; and
4. at least three operational variables that must be added to an academic benchmark.
