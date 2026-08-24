# Search notes: industry evidence for heterogeneous agent harnesses

Search date: 2026-08-23

## Search objective

Find original, official industry material that can inform the question:

> When should a harness assign planning, execution, verification, routing, or safety work to models of different capability and cost?

The search deliberately excluded academic papers already handled by the paper inventory.

## Source classes searched

- Frontier AI laboratories: Anthropic and OpenAI.
- Cloud and enterprise AI platforms: Microsoft, Google Cloud, AWS, and Databricks.
- Agent-native engineering companies: Cognition and LangChain.
- Production case studies, engineering blogs, official architecture centers, product documentation, original surveys, and technical guides.

## Inclusion criteria

A source was included only when it met all of the following:

1. It came from the organization that built, operated, documented, or surveyed the system.
2. It described at least one concrete mechanism or observed constraint involving orchestration, delegation, model selection, context, evaluation, cost, latency, safety, or production operations.
3. It was specific enough to generate a baseline, variable, hypothesis, or reproducible question.
4. Its evidence type and limitations could be stated without pretending it was peer reviewed.

## Exclusion criteria

- Generic market forecasts and unsourced trend pieces.
- Product announcements with no reusable architecture or operational detail.
- Customer testimonials without sufficient system description.
- Tutorials that merely assemble a framework without extracting a design lesson.
- Consulting reports that summarize other sources without publishing an original method or dataset.
- Academic or workshop papers, which belong in `paper-inventory.csv`.

## Search result by organization

### Anthropic

Anthropic provides the deepest public set of harness accounts. The sequence from *Building Effective Agents* through the Research system, long-running-agent work, planner–generator–evaluator harness, compiler team, managed-agent infrastructure, and containment shows multiple layers of the same problem: orchestration pattern choice, context boundaries, handoff artifacts, evaluator independence, parallel write conflicts, infrastructure cost, and specialized small-model safety checks.

Most important direct result: the production Research system used Opus as lead and Sonnet as workers. It is the closest mature deployment evidence, but its benchmark is internal and the reported gain comes with much greater token use.

### Cognition

*Devin Fusion* is the closest industry match to the proposed dissertation idea. Its main agent retains planning, ambiguity resolution, monitoring, and final review, while a cheaper sidekick gathers context and executes delegated work. Cognition also publishes unusually candid discussion of multi-agent context fragmentation and conflicting write decisions.

The major caveat is independence: Cognition designed the system, product, and FrontierCode benchmark. Its claims should become replication targets.

### Microsoft

Microsoft's current agent-host architecture guidance independently articulates the same allocation heuristic: frontier reasoning for genuinely difficult steps, cheaper models for deterministic or bounded subtasks, and per-step model mixing where supported. Foundry's Model Router documentation establishes that per-turn heterogeneous routing is now a concrete platform capability rather than only an academic proposal.

The documentation does not establish that the router beats simple rules or an oracle across realistic long-horizon workflows.

### OpenAI

OpenAI's practical guide recommends a disciplined optimization process: establish a best-model baseline and evals, then replace individual tasks with smaller models where quality remains acceptable. Its internal data-agent and agent-first software reports add real constraints involving context, memory, environment design, continuous evals, and feedback loops.

These reports are stronger on harness engineering than on controlled heterogeneous-model comparison.

### AWS

AWS explicitly recommends small specialized agents, task-specific model choice, parallel processing, and a lightweight supervisor for Bedrock cost optimization. Its AgentOps material adds production concerns frequently missing from papers: per-interaction cost, traceability, token budgets, deployment versioning, security policies, session-level evaluation, and collaboration metrics.

These are reference practices rather than causal evidence that a particular team topology is optimal.

### Google Cloud

Google Cloud's architecture center offers a useful topology decision framework and production reference designs. It explicitly records that coordinator, hierarchical, and collaborative systems can have high latency and model-call cost. Its GraphRAG orchestration design recommends smaller models for high-volume well-defined work and larger models for complex reasoning.

The documents describe intended architectures, not controlled deployments with public outcome data.

### LangChain

The State of Agent Engineering survey provides ecosystem context on which agent use cases reach production and which evaluation and observability problems practitioners report. It is retained as contextual evidence only because the sample is self-selected and likely overrepresents organizations already engaged with agent tooling.

### Databricks

Databricks material strongly supports the shift from standalone models to compound AI systems and contains useful agent-system design guidance. It was not promoted into the active collection because the selected Anthropic, OpenAI, Microsoft, AWS, and Google sources cover the branch's specific model-allocation and orchestration questions more directly. Revisit Databricks if the research question broadens to compound AI systems or enterprise data agents.

## Cross-source convergence

The official sources independently converge on five propositions:

1. **Strong models should be spent selectively.** Planning, ambiguous reasoning, synthesis, and final review are recurring candidates.
2. **Cheap models need bounded work.** Extraction, formatting, classification, focused search, code implementation, and safety inspection recur as candidate roles.
3. **Parallelism is conditional.** It helps breadth-first or separable work and creates conflicts when agents share state or make coupled decisions.
4. **Context is an architectural resource.** Clean worker contexts can expand effective capacity, but handoffs lose information and shared state creates interference.
5. **Total cost is larger than API price.** Coordination turns, retries, evaluation, tool calls, infrastructure, latency, observability, and failure recovery matter.

These are well-supported industry hypotheses. None yet supplies a general policy for optimal role × model assignment.

## Research gaps revealed by industry material

- Independent replication of Cognition's sidekick architecture and Anthropic's lead-worker allocation on neutral benchmarks.
- Comparisons against strong single-agent, homogeneous-team, fixed heterogeneous, adaptive router, and oracle baselines under equal budgets.
- Causal measurement of handoff loss, context isolation benefit, parallel write conflict, and verifier value.
- Routing policies that account for irreversible tool actions, safety risk, uncertainty, and delayed downstream failure.
- Cost models that include engineering overhead, infrastructure, concurrency, retry storms, human intervention, and price changes.
- Evaluation across research, software, enterprise data, browser workflows, and policy-constrained business tasks.
- Longitudinal tests showing when harness assumptions become obsolete as base models improve.

## Monitoring list

- Independent evaluations of Devin Fusion or similar frontier-plus-sidekick systems.
- Public eval details or datasets for Anthropic's Research system and long-running harness experiments.
- Benchmarks of Microsoft Foundry Model Router within multi-step agents rather than isolated requests.
- Production postmortems that disclose negative results, failure rates, and full operating cost.
- Industry systems that dynamically change role topology, not only the model for a fixed call.
- Evidence that separates gains from extra token budget from gains due to role specialization.
