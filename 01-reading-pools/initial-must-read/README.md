# Initial must-read pool

This is a **20-paper orientation sequence**, curated on 2026-08-18. It is designed to build a defensible map of AI-agent research without mistaking popularity, benchmark scores, or recent hype for settled knowledge.

Read the [category map](category-map.md) first. Use the [extended pool](extended-pool.md) when a category catches your attention, and see [search notes](search-notes.md) for the selection method and caveats.

## Why these 20

The core balances:

- classic and modern definitions of agency;
- the main architecture patterns: reasoning, acting, tools, memory, reflection, learning, and coordination;
- embodied, digital, and human-facing agents;
- realistic evaluation rather than benchmark scores alone;
- papers proposing influential methods and papers testing their limits;
- peer-reviewed work plus a small amount of clearly marked recent work.

## Suggested sequence

### Phase 1 — Establish the map

| # | Paper | Year | Type | Why it belongs | Status |
|---:|---|---:|---|---|---|
| 1 | [Intelligent Agents: Theory and Practice](https://doi.org/10.1017/S0269888900008122) — Wooldridge & Jennings | 1995 | Foundations | Anchors “agent” in autonomy, reactivity, proactivity, social ability, theory, and architecture—well before LLM wrappers. | queued |
| 2 | [A Survey on Large Language Model based Autonomous Agents](https://arxiv.org/abs/2308.11432) — Wang et al. | 2024 | Survey | A broad construction–application–evaluation map and a common vocabulary for LLM agents. | queued |
| 3 | [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models](https://proceedings.neurips.cc/paper_files/paper/2022/hash/9d5609613524ecf4f15af0f7b31abca4-Abstract-Conference.html) — Wei et al. | 2022 | Method | Establishes the intermediate-reasoning pattern underlying many later agent loops. | queued |

### Phase 2 — Learn the principal architecture patterns

| # | Paper | Year | Type | Why it belongs | Status |
|---:|---|---:|---|---|---|
| 4 | [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629) — Yao et al. | 2023 | Architecture | The canonical interleaving of reasoning, environment observation, and action. | queued |
| 5 | [Tree of Thoughts: Deliberate Problem Solving with Large Language Models](https://arxiv.org/abs/2305.10601) — Yao et al. | 2023 | Planning/search | Shows explicit search, evaluation, and backtracking over reasoning paths. | queued |
| 6 | [Reflexion: Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366) — Shinn et al. | 2023 | Reflection/memory | Introduces learning across trials through linguistic feedback and episodic memory without weight updates. | queued |
| 7 | [On the Planning Abilities of Large Language Models: A Critical Investigation](https://proceedings.neurips.cc/paper_files/paper/2023/hash/efb2072a358cefb75886a315a6fcf880-Abstract-Conference.html) — Valmeekam et al. | 2023 | Critical evaluation | Separates plausible plan text from executable planning and demonstrates the value of sound external planners/verifiers. | queued |
| 8 | [Toolformer: Language Models Can Teach Themselves to Use Tools](https://proceedings.neurips.cc/paper/2023/hash/d842425e4bf79ba039352da0f658a906-Abstract-Conference.html) — Schick et al. | 2023 | Tool learning | A landmark self-supervised approach to deciding when and how to call APIs. | queued |
| 9 | [Gorilla: Large Language Model Connected with Massive APIs](https://proceedings.neurips.cc/paper_files/paper/2024/hash/e4c61f578ff07830f5c37378dd3ecb0d-Abstract-Conference.html) — Patil et al. | 2024 | Tool retrieval | Connects tool use to retrieval, changing documentation, API scale, and hallucination. | queued |
| 10 | [Generative Agents: Interactive Simulacra of Human Behavior](https://arxiv.org/abs/2304.03442) — Park et al. | 2023 | Memory/HCI | Influential memory–reflection–planning architecture with both individual and emergent social behavior. | queued |
| 11 | [Voyager: An Open-Ended Embodied Agent with Large Language Models](https://arxiv.org/abs/2305.16291) — Wang et al. | 2024 | Embodied learning | Combines automatic curriculum, executable skill memory, feedback, and lifelong open-ended exploration. | queued |
| 12 | [SimpleTIR: End-to-End Reinforcement Learning for Multi-Turn Tool-Integrated Reasoning](https://openreview.net/forum?id=hCZsutMyEF) — Xue et al. | 2026 | Agentic RL | Represents the shift from hand-built prompting loops toward learned multi-turn tool policies. | queued |
| 13 | [CAMEL: Communicative Agents for “Mind” Exploration of Large Scale Language Model Society](https://arxiv.org/abs/2303.17760) — Li et al. | 2023 | Multi-agent | A foundational role-playing and communication pattern for LLM multi-agent systems. | queued |
| 14 | [Should We Be Going MAD? A Look at Multi-Agent Debate Strategies for LLMs](https://arxiv.org/abs/2311.17371) — Smit et al. | 2024 | Critical multi-agent study | Tests whether debate beats strong single-agent alternatives and exposes sensitivity to protocol and tuning. | queued |

### Phase 3 — Understand what evaluation actually measures

| # | Paper | Year | Type | Why it belongs | Status |
|---:|---|---:|---|---|---|
| 15 | [AgentBench: Evaluating LLMs as Agents](https://arxiv.org/abs/2308.03688) — Liu et al. | 2024 | General benchmark | Evaluates reasoning and decision-making across eight interactive environments. | queued |
| 16 | [GAIA: A Benchmark for General AI Assistants](https://openreview.net/forum?id=fibxvahvs3) — Mialon et al. | 2024 | Generalist benchmark | Uses human-simple but agent-difficult questions requiring reasoning, browsing, multimodality, and tools. | queued |
| 17 | [τ-bench: A Benchmark for Tool-Agent-User Interaction in Real-World Domains](https://arxiv.org/abs/2406.12045) — Yao et al. | 2024 | Interaction benchmark | Adds users, policy constraints, database-state grading, and repeated-trial reliability. | queued |
| 18 | [Survey on Evaluation of LLM-based Agents](https://arxiv.org/abs/2503.16416) — Yehudai et al. | 2025 | Evaluation survey | Maps capability, application, generalist, benchmark-dimension, and developer-framework evaluation; revised in 2026. | queued |

### Phase 4 — Treat autonomy as a safety and governance problem

| # | Paper | Year | Type | Why it belongs | Status |
|---:|---|---:|---|---|---|
| 19 | [AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses for LLM Agents](https://proceedings.neurips.cc/paper_files/paper/2024/hash/97091a5177d8dc64b1da8bf3e1f6fb54-Abstract-Datasets_and_Benchmarks_Track.html) — Debenedetti et al. | 2024 | Security benchmark | Makes untrusted tool data and prompt injection central to realistic agent security evaluation. | queued |
| 20 | [The Ethics of Advanced AI Assistants](https://arxiv.org/abs/2404.16244) — Gabriel et al. | 2024 | Ethics/governance | Connects technical agency to alignment, trust, manipulation, privacy, social effects, access, and governance. | queued |

## How to work through the core

- Read papers 1–3 before specializing; they establish the conceptual and technical vocabulary.
- For papers 4–14, pair every claimed capability with the evidence and evaluation setting that supports it.
- For papers 15–19, ask what construct is actually being measured, what the environment omits, and whether the result survives repeated trials.
- After every five papers, write a short synthesis rather than continuing immediately.
- Promote an extended paper only when it answers a question raised by a core paper.

## Checkpoints

- **After paper 3:** write your working definition of an AI agent.
- **After paper 7:** distinguish reasoning, planning, search, verification, and acting.
- **After paper 14:** compare single-agent scaffolding with multi-agent coordination.
- **After paper 18:** draft your own agent-evaluation dimensions.
- **After paper 20:** identify three research directions that combine technical importance with personal pull.

