# Broad category map for AI-agent research

This map was developed before selecting individual papers. Categories overlap by design: a real agent system usually combines several of them.

| Category | Central question | Typical approaches | Recurring research gaps | Why it may support a dissertation |
|---|---|---|---|---|
| 1. Foundations and definitions | What makes a system an agent rather than a model, workflow, or program? | Rational-agent models, autonomy, BDI architectures, foundation models, augmented language models | Competing definitions; unclear autonomy boundaries; agency often inferred from surface behavior | Conceptual clarity affects evaluation, governance, and system claims |
| 2. Reasoning and planning | How can an agent choose coherent actions over multiple steps? | Chain-of-thought, ReAct loops, tree search, world models, external planners, verification, inference-time scaling | Plausibility versus executability; compounding errors; weak state tracking; cost | Rich overlap between classical planning, modern LMs, verification, and learning |
| 3. Tool use and computer interaction | How does an agent select tools, form valid calls, interpret results, and act in changing environments? | Function calling, API retrieval, code execution, web/GUI control, tool-integrated reasoning | Tool discovery, version drift, permissioning, error recovery, irreversible actions | Highly practical and measurable; strong links to security and systems research |
| 4. Memory, reflection, and adaptation | How should agents preserve and learn from experience across tasks and time? | Episodic/semantic/procedural memory, retrieval, summarization, skill libraries, verbal reflection, test-time and reinforcement learning | Memory quality, poisoning, forgetting, credit assignment, evaluation over long horizons | Many open questions with tractable experimental designs |
| 5. Multi-agent systems | When does adding agents improve outcomes, and how should they coordinate? | Debate, role specialization, centralized orchestration, peer-to-peer communication, markets and games | Correlated errors, groupthink, protocol sensitivity, communication cost, unclear gains over sampling | Connects new LLM systems to mature multi-agent and game-theoretic research |
| 6. Embodied and multimodal agents | How do agents perceive and act in physical or visually grounded environments? | Vision-language-action models, robotics, simulation, curricula, executable skills, GUI grounding | Sim-to-real transfer, safety, sample efficiency, spatial/temporal grounding | Offers concrete environments and strong connections to robotics and HCI |
| 7. Evaluation and real-world capability | What does successful agent behavior mean, and how can it be measured reliably? | Interactive benchmarks, execution-based graders, repeated trials, human baselines, time horizons, cost and robustness metrics | Contamination, fragile graders, non-determinism, construct validity, missing process diagnostics | Evaluation is immature, consequential, and unusually dissertation-rich |
| 8. Reliability, safety, and security | How can agents act usefully without violating user intent or enabling attacks and harmful outcomes? | Sandboxes, prompt-injection benchmarks, monitors, least privilege, policy enforcement, red teaming, control protocols | Adaptive attacks, hidden side effects, long-tailed failures, oversight scalability, trusted components | Autonomy makes failures consequential; the research surface spans ML and security |
| 9. Human-agent interaction, ethics, and governance | How should people delegate, supervise, contest, trust, and coexist with agents? | Human-in-the-loop systems, mixed-initiative interaction, uncertainty and deferral, value alignment, policy and institutional design | Automation bias, manipulation, responsibility gaps, unequal access, consent, labor effects | Supports technical, HCI, sociotechnical, and policy dissertation paths |

## Cross-cutting axes to record for every paper

| Axis | Useful distinctions |
|---|---|
| Agent boundary | model only / scaffold / model + tools / multi-agent system / human-agent system |
| Learning | fixed prompting / in-context adaptation / memory update / supervised training / reinforcement learning |
| Environment | static text / API / web / operating system / codebase / simulation / physical world |
| Horizon | single action / short episode / long task / repeated tasks / lifelong |
| Autonomy | advise / propose / act with confirmation / delegated action / open-ended operation |
| Evaluation | final answer / executable state / trajectory quality / repeated reliability / human utility / safety |
| Evidence maturity | demonstration / benchmark study / ablation / independent comparison / real deployment |

## Initial dissertation-fertile seams

These are hypotheses for exploration, not chosen topics:

- planning quality when LLMs are paired with sound verifiers or classical planners;
- memory systems evaluated for downstream usefulness, not retrieval accuracy alone;
- when multi-agent orchestration adds value beyond independent sampling or a stronger single agent;
- reliable agent evaluation under non-determinism, changing environments, and long horizons;
- least-privilege tool use and defenses against indirect prompt injection;
- human control, confirmation, and calibrated delegation for consequential actions;
- evaluation of scientific or software-engineering agents where outputs can be executed and audited;
- learning agent policies from interaction while preserving safety and interpretability.

