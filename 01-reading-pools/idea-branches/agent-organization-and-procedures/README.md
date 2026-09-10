# Idea-branch paper pool: agent organization and work procedures

Research and selection date: 2026-09-07

Related idea: [Organizational and procedural design for AI agent teams](../../../04-ideas/agent-organization-and-procedures.md)

Parent topic: [Agent harness engineering](../../../03-topics/agent-harness-engineering/README.md)

Companion: [Discussion notes and provisional assessment](discussion-notes.md)

## Purpose

This ten-paper sequence is selected to help decide whether, and in which direction, to pursue the area. It is not a citation-count ranking. It combines foundations, concrete systems, critical evidence, synergy measurement, and close conceptual competitors. Inclusion does not mean a paper has been read or its conclusions independently validated.

## Reading sequence

| Order | Paper | Publication context | Why read it / question to carry |
|---:|---|---|---|
| 1 | [A Survey of Multi-Agent Organizational Paradigms](https://mas.cs.umass.edu/Documents/bhorling/horling-paradigms.pdf) — Horling & Lesser | Knowledge Engineering Review, volume dated 2004; linked author version and online publication 2005 | Map hierarchies, markets, coalitions, federations, and alternatives. Which forms interest you beyond a simulated company? Skim the taxonomy before selected sections. |
| 2 | [MOISE+: Towards a Structural, Functional, and Deontic Model for MAS Organization](https://doi.org/10.1145/544741.544858) — Hübner, Sichman & Boissier | AAMAS 2002 | Direct predecessor to separating organization and procedure, connected through permissions and obligations. Which assumptions need reconsideration for LLMs? |
| 3 | [MetaGPT: Meta Programming for a Multi-Agent Collaborative Framework](https://arxiv.org/abs/2308.00352) — Hong et al. | ICLR 2024 | Concrete software-company roles and SOPs. What is enforced versus prompted? Can roles be separated from artifacts and workflow effects? |
| 4 | [Towards a Science of Scaling Agent Systems](https://arxiv.org/abs/2512.08296) — Kim et al. | 2025 preprint; use April 2026 v3 | Architecture/task alignment under controlled conditions. When is a team justified, and how convincing are its predictors? |
| 5 | [Why Do Multi-Agent LLM Systems Fail?](https://arxiv.org/abs/2503.13657) — Cemri et al. | 2025; use latest revision | MAST failure taxonomy and annotated traces. Which failures invite controlled experiments? A category is not a causal explanation. |
| 6 | [Debate or Vote: Which Yields Better Decisions in Multi-Agent Large Language Models?](https://arxiv.org/abs/2508.17536) — Choi, Zhu & Li | NeurIPS 2025 | Separates debate from voting. Which baseline distinguishes interaction benefits from sampling and aggregation? |
| 7 | [Emergent Coordination in Multi-Agent Language Models](https://arxiv.org/abs/2510.05174) — Riedl | ICLR 2026 | Information-theoretic collective structure in a controlled game. Distinguish emergence from useful performance and narrow evidence from general claims. |
| 8 | [Multi-Agent Design: Optimizing Agents with Better Prompts and Topologies](https://arxiv.org/abs/2502.02533) — Zhou et al. | ICLR 2026 | MASS analyzes the design space and optimizes prompts/topologies. Essential overlap check for designing a better harness from analysis. |
| 9 | [Evaluating Classical Software Process Models as Coordination Mechanisms for LLM-Based Software Generation](https://arxiv.org/abs/2509.13942) — Ha et al. | September 2025 preprint | Direct Waterfall/V-Model/Agile comparison. Are process effects isolated? Included for overlap, not established influence. |
| 10 | [Toward an Organizational Science of Multi-Agent LLM Systems: Decoupling Who, How, and Which Algorithm](https://arxiv.org/abs/2607.25446) — Chen et al. | July 2026 preprint | Closest recent conceptual competitor. What remains after separating organization, coordination, and protocols? Treat findings as preliminary. |

## Early decision checkpoint

Read **1, 4, 5, and 8** first: organizational breadth, evidence about usefulness, failure analysis, and competing automatic-design work. The remaining papers deepen formal foundations, software processes, synergy, and immediate novelty overlap.

## Initial extraction questions

1. What design decision does this paper actually study?
2. What does its evidence establish, under what assumptions and baselines?
3. What remains unresolved in this paper, and is that also unresolved in the wider literature?
4. Do I want to investigate that issue myself?

For empirical comparisons, additionally note model/tool access, agent definition, total budget, aggregation method, held-out evaluation, repetition, and whether roles are enforced. Do not compare headline results across incompatible protocols as if they isolate organization.

## Reading status and inventory

All ten are unprocessed for this branch at creation. Canonical status lives in [paper-inventory.csv](../../paper-inventory.csv); existing status is preserved when a paper is reused. MetaGPT already has an inventory row and is referenced here without duplication. Discussion notes are not completed paper notes, and no paper is marked read by creating this pool.

## Exit reflection

After the sequence, write a short synthesis comparing interest in organizational theory, empirical failure analysis, synergy measurement, and adaptive harness design. A decision to park the area is valid. A proposed gap must survive the closest papers; a new architecture is not a required conclusion.
