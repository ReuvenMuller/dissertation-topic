# Search notes: heterogeneous agent harnesses

Search completed: 2026-08-23

## Search objective

Find the strongest literature relevant to assigning differently capable and differently priced language models to architect, planner, decomposer, executor, verifier, and related roles in a shared task harness.

## Sources prioritized

1. Peer-reviewed proceedings and journal pages: ICLR, ICML/PMLR, NeurIPS, ACL Anthology, TMLR, Nature Machine Intelligence.
2. arXiv and OpenReview for very recent work not yet represented in proceedings.
3. Author or project pages only to verify code, current acceptance status, or missing metadata.

Secondary summaries were used only to discover candidates. Claims in the pool were checked against primary paper pages or official proceedings wherever possible.

The Hugging Face Papers metadata path was attempted for structured lookup; direct API access was unavailable in this workspace, so arXiv, OpenReview, and proceedings metadata were used as the source of record.

## Query families

- heterogeneous LLM agents planner executor verifier cost
- role-aware model assignment agent teams
- large small model collaboration planning
- agentic model routing multi-step trajectories
- compound AI system model selection
- LLM routing cascades budget quality Pareto
- multi-agent coordination strong single-agent baseline
- benchmarks for planner executor verifier role separation
- collaboration failure cost latency agent systems

## Inclusion criteria

A paper was included if it contributed at least one of:

- A model-selection, routing, or cascade method with an explicit cost–quality objective.
- A hierarchical or role-separated agent architecture relevant to planning and execution.
- Heterogeneous model assignment at module, step, subtask, or role level.
- A benchmark capable of separating team structure from model capability.
- Controlled negative evidence about collaboration, coordination overhead, or verifier failure.
- A directly reusable evaluation environment already present in the repository.

## Exclusion and down-ranking criteria

- Internal mixture-of-experts routing inside a single neural network.
- Generic multi-agent frameworks with no relevant empirical allocation or evaluation result.
- Application demonstrations that did not isolate model assignment or team structure.
- Product benchmarks without reproducible methodology or primary paper support.
- Papers whose only connection was parallel sampling or voting, unless needed as an ensemble baseline.
- Withdrawn or workshop-only work was not excluded, but its maturity is labeled explicitly.

## Maturity policy

- Venue acceptance was verified from proceedings or official venue pages when available.
- A recent arXiv paper is labeled “preprint” even when its reported gains are impressive.
- OpenReview submissions are not described as accepted unless the venue decision or proceedings page confirms it.
- 2026 papers are treated as frontier signals rather than settled findings unless peer-reviewed and independently supported.

## Closest-paper novelty check

| Proposed element | Closest prior work | What appears to remain open |
|---|---|---|
| Strong planner + cheap executor | COPE; BudgetMLAgent; AgentCARD | General conditions, long-horizon handoffs, industry workflow transfer |
| Architect + decomposer + executor hierarchy | AgentCARD three-role pilot; GraphPlanner; MALT | Controlled three-tier factorial study and causal failure attribution |
| Cheapest adequate model per step | AgentRouter; GraphPlanner | Online uncertainty, irreversible actions, delayed reward, robust escalation |
| Role-specific model assignment | AgentCARD; LLMSelector; SC-MAS | Cross-domain and cross-generation generalization |
| Cost–performance frontier | AgentCARD; routing/cascade literature | Full operational cost, reliability, latency, recovery, and human intervention |
| When collaboration should be used | Nature 2026; TeamBench; OneFlow | Predictive selection tied specifically to heterogeneous role assignments |

## Search conclusion

The broad idea has definitely been studied, and AgentCARD overlaps it directly. The branch remains promising only if it moves beyond a fixed “largest plans, smallest executes” demonstration. The strongest surviving directions are conditional architecture selection, adaptive role-aware escalation, handoff/failure analysis, and realistic industry-workflow cost frontiers.

## Citation trails to follow during reading

- Forward citations to FrugalGPT, AutoMix, RouteLLM, LLMSelector, and Plan-and-Act.
- Work citing AgentCARD after June 2026, especially independent replications.
- New benchmarks adopting TeamBench role enforcement or AgentCARD role-criticality analysis.
- Work comparing AgentRouter or GraphPlanner with simple thresholds and oracle routing.
- Research on delayed credit assignment and constrained routing in tool-using agent trajectories.
