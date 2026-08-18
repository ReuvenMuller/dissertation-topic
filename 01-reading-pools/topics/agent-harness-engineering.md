# Topic paper pool: agent harness engineering

This is a focused pool, not a claim that every paper uses the term “harness.” Read across older component research and the newer unifying frame.

## First pass: establish the construct

| Order | Paper | Role in the topic | Reading depth |
|---:|---|---|---|
| 1 | [AI Harness Engineering: A Runtime Substrate for Foundation-Model Software Agents](https://arxiv.org/abs/2605.13357) | Recent explicit formulation of the harness as a research object; test whether the framing is genuinely additive | Deep |
| 2 | [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629) | Canonical reasoning–action loop and a baseline for what the harness controls | Deep |
| 3 | [Benchmarking Agentic Workflow Generation](https://openreview.net/forum?id=vunPXOFmoi) | Evaluates generated workflow structure and exposes sequence-versus-graph planning gaps | Deep |
| 4 | [Agent Lightning: Train ANY AI Agents with Reinforcement Learning](https://arxiv.org/abs/2508.03680) | Separates agent execution from training and introduces credit assignment over traces | Medium |
| 5 | [Measuring AI Agent Autonomy: Towards a Scalable Approach With Code Inspection](https://openreview.net/forum?id=VulxpvCNoA) | Taxonomy of agent impact and oversight visible in code | Medium |

## Second pass: components and evaluation

| Paper | Harness dimension to extract |
|---|---|
| [Toolformer](https://arxiv.org/abs/2302.04761) | Tool selection and invocation |
| [Gorilla](https://arxiv.org/abs/2305.15334) | API grounding and changing tool interfaces |
| [Generative Agents](https://arxiv.org/abs/2304.03442) | Memory, reflection, and retrieval |
| [Reflexion](https://arxiv.org/abs/2303.11366) | Feedback and verbal learning |
| [SimpleTIR](https://openreview.net/forum?id=hCZsutMyEF) | Tool-integrated reasoning and reinforcement learning |
| [AgentBench](https://arxiv.org/abs/2308.03688) | Cross-environment agent evaluation |
| [τ-bench](https://arxiv.org/abs/2406.12045) | Tool–agent–user interaction and policy following |
| [AgentDojo](https://proceedings.neurips.cc/paper_files/paper/2024/hash/97091a5177d8dc64b1da8bf3e1f6fb54-Abstract-Datasets_and_Benchmarks_Track.html) | Prompt-injection threat model and defenses |
| [OSWorld](https://arxiv.org/abs/2404.07972) | Real computer interaction, state, and recoverability |

## Watch list

- [Agentic Harness Engineering: Observability-Driven Automatic Evolution of Coding-Agent Harnesses](https://arxiv.org/abs/2604.25850) — promising observability and automatic-evolution framing, but very recent and coding-specific.
- Agent harness surveys or terminology papers that survive peer review and distinguish the construct from agent architecture, workflow engines, and software middleware.

## Questions for this pool

1. What exactly belongs inside the harness?
2. Which components are model-independent?
3. Which papers perform true component ablations?
4. What trace or state is exposed for diagnosis?
5. How are permissions, verification, rollback, and escalation represented?
6. Does a method improve capability, reliability, or merely benchmark opportunity?

## Exit criterion

After the first five papers, write a one-page position: either the harness is a coherent research object with distinct questions, or the more precise home is agent architecture, evaluation, observability, or workflow systems.
