# Search notes and selection rationale

## Scope

- **Search completed:** 2026-08-18
- **Primary focus:** LLM-based agents, with selected pre-LLM agent theory and adjacent foundation-model work needed to understand the field
- **Time emphasis:** landmark work from 2022–2024 plus peer-reviewed or high-salience developments from 2025–2026
- **Output:** a 20-paper core and a category-organized extended pool

## Two-stage search process

### Stage 1 — Build categories

Recent broad surveys and evaluation surveys were used as maps, particularly:

- [A Survey on Large Language Model based Autonomous Agents](https://arxiv.org/abs/2308.11432)
- [Survey on Evaluation of LLM-based Agents](https://arxiv.org/abs/2503.16416)
- [A Survey on Large Language Model based Human-Agent Systems](https://arxiv.org/abs/2505.00753)
- [Lifelong Learning of Large Language Model based Agents: A Roadmap](https://arxiv.org/abs/2501.07278)

Their taxonomies were compared rather than adopted wholesale. The resulting map separates agent components, interaction structures, environments, evaluation, and sociotechnical consequences.

### Stage 2 — Search within categories

Within each category, candidates were sought in four roles:

1. **Foundational:** introduced a durable concept or architecture.
2. **Representative:** shows how a major research line is operationalized.
3. **Critical:** tests whether influential claims survive stronger baselines or more realistic conditions.
4. **Recent frontier:** captures a material shift in the field, such as agentic reinforcement learning or long-horizon evaluation.

## Source preference

1. Official conference or journal proceedings
2. OpenReview pages for peer-reviewed conference papers
3. ACL Anthology or PMLR
4. arXiv abstract pages, clearly distinguished from peer-reviewed publication

Project pages and leaderboards were useful for discovery but were not treated as independent evidence of scientific importance.

## Inclusion criteria

A core paper needed to satisfy several of these:

- introduced or rigorously tested a widely reused idea;
- represents a distinct category rather than duplicating another paper;
- offers evidence or evaluation that can be interrogated;
- helps connect modern LLM agents to earlier AI, HCI, security, or multi-agent work;
- changes how later papers frame the problem;
- exposes limitations, not only capabilities;
- remains useful even if the named model or leaderboard score becomes obsolete.

## Important caveats

- **Recency is not maturity.** Several 2025–2026 papers are promising but have limited independent validation.
- **Citation counts lag and reward age.** They were not used as a sole selection rule.
- **Benchmarks are constructs, not reality.** High task success may reflect scaffolding, evaluator design, contamination, retries, or cost.
- **“Agent” is inconsistently defined.** Some papers evaluate an LM, some a scaffold, and some a complete system.
- **Reported model scores age quickly.** Read benchmark papers for task design, failure modes, and measurement choices—not as permanent capability rankings.
- **Industry-authored work can be valuable and conflicted.** Record funding, model access, and whether the evaluated system is the authors’ own.
- **The pool is broad by design.** Once two or three topics develop, their pools should become more systematic and include forward/backward citation chasing.

## What was deliberately excluded from the core

- many framework papers whose primary contribution is software packaging;
- several near-duplicate benchmarks measuring similar short-horizon abilities;
- application papers without a transferable architectural or evaluation lesson;
- papers selected only because they announce a current state-of-the-art score;
- very recent preprints when a more mature paper teaches the same concept.

## Refresh rule

Revisit the core every four to six weeks during scoping. Replace a paper only when the replacement offers a genuinely new category, stronger evidence, or an important change in the research frontier.

