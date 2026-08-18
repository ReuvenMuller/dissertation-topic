# Extended paper pool by category

These are **second-tier candidates**, not an instruction to read everything. Promote a paper to your active queue when a core paper raises a question that the candidate can answer.

## 1. Foundations and enabling ideas

| Paper | Year | Role | Why read it |
|---|---:|---|---|
| [Attention Is All You Need](https://arxiv.org/abs/1706.03762) — Vaswani et al. | 2017 | Foundation | Transformer architecture underlying modern language models. |
| [Training Language Models to Follow Instructions with Human Feedback](https://arxiv.org/abs/2203.02155) — Ouyang et al. | 2022 | Foundation | Instruction following and RLHF; essential context for controllable agent behavior. |
| [Augmented Language Models: a Survey](https://arxiv.org/abs/2302.07842) — Mialon et al. | 2023 | Bridge survey | Connects reasoning, tools, retrieval, and acting as language-model augmentation. |
| [Language Models Don’t Always Say What They Think](https://proceedings.neurips.cc/paper_files/paper/2023/hash/ed3fea9033a80fea1376299fa7863f4a-Abstract-Conference.html) — Turpin et al. | 2023 | Critical | Warns that visible chains of thought can rationalize answers rather than faithfully expose causes. |

## 2. Reasoning, planning, and verification

| Paper | Year | Role | Why read it |
|---|---:|---|---|
| [Reasoning with Language Model is Planning with World Model](https://arxiv.org/abs/2305.14992) — Hao et al. | 2023 | Method | Frames reasoning as planning and uses an LM as a world model. |
| [Language Agent Tree Search Unifies Reasoning, Acting, and Planning](https://arxiv.org/abs/2310.04406) — Zhou et al. | 2024 | Method | Integrates search, action, reflection, and memory in one agent procedure. |
| [TravelPlanner: A Benchmark for Real-World Planning with Language Agents](https://openreview.net/forum?id=l5XQzNkAOe) — Xie et al. | 2024 | Critical benchmark | Tests tool use and multiple constraints in realistic travel planning. |
| [Reducing Belief Deviation in Reinforcement Learning for Active Reasoning of LLM Agents](https://openreview.net/forum?id=r8hzDA3pUY) — Zou et al. | 2026 | Recent frontier | ICLR oral on stabilizing agentic multi-turn RL under belief deviation. |

## 3. Tool use and computer interaction

| Paper | Year | Role | Why read it |
|---|---:|---|---|
| [API-Bank: A Comprehensive Benchmark for Tool-Augmented LLMs](https://arxiv.org/abs/2304.08244) — Li et al. | 2023 | Dataset/benchmark | Evaluates planning, retrieval, and API calling across a broad tool set. |
| [ToolLLM: Facilitating Large Language Models to Master 16000+ Real-world APIs](https://arxiv.org/abs/2307.16789) — Qin et al. | 2023 | Method/dataset | Studies tool-use data generation, retrieval, and multi-step API execution at scale. |
| [WebArena: A Realistic Web Environment for Building Autonomous Agents](https://arxiv.org/abs/2307.13854) — Zhou et al. | 2024 | Environment | Reproducible, functional websites and execution-based grading for long-horizon web tasks. |
| [OSWorld: Benchmarking Multimodal Agents for Open-Ended Tasks in Real Computer Environments](https://arxiv.org/abs/2404.07972) — Xie et al. | 2024 | Environment | Moves from websites to cross-application tasks in real operating systems. |

## 4. Memory, reflection, and learning from interaction

| Paper | Year | Role | Why read it |
|---|---:|---|---|
| [MemGPT: Towards LLMs as Operating Systems](https://arxiv.org/abs/2310.08560) — Packer et al. | 2023 | Architecture | Hierarchical context management as virtual memory for long-running agents. |
| [ExpeL: LLM Agents Are Experiential Learners](https://arxiv.org/abs/2308.10144) — Zhao et al. | 2024 | Adaptation | Distills experience from prior tasks into reusable natural-language knowledge. |
| [Lifelong Learning of Large Language Model based Agents: A Roadmap](https://arxiv.org/abs/2501.07278) — Zheng et al. | 2025 | Survey | Organizes perception, memory, and action around continual adaptation. |
| [Agent Lightning: Train ANY AI Agents with Reinforcement Learning](https://arxiv.org/abs/2508.03680) — Luo et al. | 2025 | Recent system | Decouples agent execution from RL training and addresses trajectory credit assignment. |
| [From Player to Master: Enhancing Test-Time Learning of LLM Agents via Reinforcement Learning over Memory](https://openreview.net/forum?id=gNWNtstp3r) — Cai et al. | 2026 | Recent frontier | Trains memory updates to improve downstream performance across interactions. |

## 5. Multi-agent coordination and debate

| Paper | Year | Role | Why read it |
|---|---:|---|---|
| [AutoGen: Enabling Next-Gen LLM Applications via Multi-Agent Conversation](https://arxiv.org/abs/2308.08155) — Wu et al. | 2023 | Framework | Flexible conversational orchestration across LMs, people, tools, and code. |
| [MetaGPT: Meta Programming for a Multi-Agent Collaborative Framework](https://arxiv.org/abs/2308.00352) — Hong et al. | 2024 | Workflow architecture | Encodes roles and standard operating procedures for software-production workflows. |
| [Improving Factuality and Reasoning in Language Models through Multiagent Debate](https://arxiv.org/abs/2305.14325) — Du et al. | 2023 | Method | Influential proposal for iterative debate among multiple LM instances. |
| [Rethinking the Bounds of LLM Reasoning: Are Multi-Agent Discussions the Key?](https://aclanthology.org/2024.acl-long.331/) — Wang et al. | 2024 | Critical | Finds strong single-agent prompting can approach the best discussion methods in many settings. |

## 6. Embodied and multimodal agents

| Paper | Year | Role | Why read it |
|---|---:|---|---|
| [Do As I Can, Not As I Say: Grounding Language in Robotic Affordances](https://arxiv.org/abs/2204.01691) — Ahn et al. | 2022 | Grounded planning | Combines language-model task knowledge with robot affordance/value functions. |
| [PaLM-E: An Embodied Multimodal Language Model](https://arxiv.org/abs/2303.03378) — Driess et al. | 2023 | Multimodal foundation | Integrates continuous sensor inputs with language for embodied tasks. |
| [RT-2: Vision-Language-Action Models Transfer Web Knowledge to Robotic Control](https://arxiv.org/abs/2307.15818) — Brohan et al. | 2023 | Vision-language-action | Treats actions as tokens and studies transfer from web-scale visual-language data to robotics. |
| [VisualWebArena: Evaluating Multimodal Agents on Realistic Visual Web Tasks](https://arxiv.org/abs/2401.13649) — Koh et al. | 2024 | Benchmark | Tests whether agents can use visual information in realistic web interaction. |

## 7. Evaluation, work, software, and scientific agents

| Paper | Year | Role | Why read it |
|---|---:|---|---|
| [SWE-bench: Can Language Models Resolve Real-World GitHub Issues?](https://arxiv.org/abs/2310.06770) — Jimenez et al. | 2024 | Software benchmark | Landmark executable evaluation of repository-level issue resolution. |
| [TheAgentCompany: Benchmarking LLM Agents on Consequential Real World Tasks](https://arxiv.org/abs/2412.14161) — Xu et al. | 2025 | Workplace benchmark | Combines browsing, coding, tools, and communication inside a simulated company. |
| [Measuring AI Ability to Complete Long Tasks](https://arxiv.org/abs/2503.14499) — Kwa et al. | 2025 | Measurement | Introduces human task-completion time horizon as an interpretable autonomy metric. |
| [PaperBench: Evaluating AI’s Ability to Replicate AI Research](https://openreview.net/forum?id=xF5PuTLPbn) — Starace et al. | 2025 | Research benchmark | Uses author-developed hierarchical rubrics to grade long research-replication attempts. |
| [MLR-Bench: Evaluating AI Agents on Open-Ended Machine Learning Research](https://proceedings.neurips.cc/paper_files/paper/2025/hash/ab8dd000d6f87f40061a73f8bca7fae4-Abstract-Datasets_and_Benchmarks_Track.html) — Chen et al. | 2025 | Research benchmark | Evaluates end-to-end ML research and highlights fabricated or invalid experiments. |

## 8. Reliability, safety, and security

| Paper | Year | Role | Why read it |
|---|---:|---|---|
| [Identifying the Risks of LM Agents with an LM-Emulated Sandbox](https://arxiv.org/abs/2309.15817) — Ruan et al. | 2024 | Safety method | Scales testing for high-stakes, long-tailed tool-use failures through emulation. |
| [Model Evaluation for Extreme Risks](https://arxiv.org/abs/2305.15324) — Shevlane et al. | 2023 | Evaluation framework | Connects dangerous capability and alignment evaluations to deployment decisions. |
| [Agent Security Bench: Formalizing and Benchmarking Attacks and Defenses in LLM-based Agents](https://arxiv.org/abs/2410.02644) — Zhang et al. | 2024 | Security benchmark | Maps attacks and defenses across prompts, tools, planning, and memory. |
| [AI Control: Improving Safety Despite Intentional Subversion](https://arxiv.org/abs/2312.06942) — Greenblatt et al. | 2024 | Control | Evaluates protocols using trusted and untrusted models under deliberate subversion. |

## 9. Human-agent interaction, ethics, and governance

| Paper | Year | Role | Why read it |
|---|---:|---|---|
| [Guidelines for Human-AI Interaction](https://doi.org/10.1145/3290605.3300233) — Amershi et al. | 2019 | HCI foundation | Empirically grounded guidance across initial use, interaction, failure, correction, and learning. |
| [The Off-Switch Game](https://www.ijcai.org/Proceedings/2017/32) — Hadfield-Menell et al. | 2017 | Formal oversight | Shows how objective uncertainty can create incentives to preserve human control. |
| [A Survey on Large Language Model based Human-Agent Systems](https://arxiv.org/abs/2505.00753) — Zou et al. | 2025 | Survey | Maps feedback, control, orchestration, communication, and applications of human-agent systems. |

## Promotion rule

Before moving an extended paper into the active queue, record:

1. the question it should answer;
2. the core paper that raised the question;
3. whether it is foundational, representative, critical, or recent-frontier evidence;
4. what you will drop or postpone to make room for it.
