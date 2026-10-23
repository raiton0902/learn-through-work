# Research and design notes

Prepared October 23, 2026. These sources support individual design choices. They do not validate this complete skill or its compact prompt. No universal learning gain, time saving, or token reduction follows from combining them.

## Education and work

### 1. Assisted performance and independent learning

Bastani et al. (2025). *Generative AI without guardrails can harm learning: Evidence from high school mathematics*. PNAS, 122(26), e2422633122. [Publisher](https://doi.org/10.1073/pnas.2422633122).

In a randomized field experiment with nearly 1,000 high-school students in Turkey, GPT Base increased assisted practice grades by 48% relative to control, while subsequent unassisted exam grades were 17% lower. GPT Tutor increased assisted practice grades by 127% and largely removed the negative unassisted effect, but did not show a positive exam effect relative to control. These are relative changes, not percentage-point differences.

Design implication: track the quality of the assisted deliverable separately from independent learner performance. A friendly explanation or a finished artifact is insufficient evidence of learning. This experiment concerns mathematics practice in a particular setting; it does not show every use of AI reduces learning or that this skill prevents harm.

### 2. Cognitive apprenticeship

Collins, A., Brown, J. S., & Holum, A. (1991). *Cognitive apprenticeship: Making thinking visible*. American Educator. [Original publisher](https://www.aft.org/ae/winter1991/collins_brown_holum).

This framework connects authentic activity with modeling, coaching, scaffolding, articulation, reflection, and exploration. Support is reduced as competence develops.

Design implication: explain the method and its purpose in the user's actual task, then progressively invite participation. Adaptation here means concise observable rationale and feedback; it does not require an LLM to expose private internal reasoning. This is a framework, not a controlled trial of an AI skill.

### 3. Worked examples and fading support

Atkinson, R. K., Renkl, A., & Merrill, M. M. (2003). *Transitioning from studying examples to solving problems: Effects of self-explanation prompts and fading worked-out steps*. Journal of Educational Psychology, 95(4), 774-783. [DOI](https://doi.org/10.1037/0022-0663.95.4.774); [institutional abstract](https://experts.azregents.edu/en/publications/transitioning-from-studying-examples-to-solving-problems-effects-/).

Across two experiments, fading worked steps combined with prompts to identify underlying principles improved near and far transfer without additional time on task in those experiments. Fading alone had less reliable far-transfer benefits.

Design implication: show a novice a complete small example, then ask for a meaningful explanation or missing step. Do not assume unaided discovery is the best starting point. The skill's exact check frequency and deadline adjustments are prototype choices; these experiments do not establish that learning adds no time in ordinary work.

### 4. Retrieval and comprehension

Karpicke, J. D., & Blunt, J. R. (2011). *Retrieval practice produces more learning than elaborative studying with concept mapping*. Science, 331, 772-775. [DOI](https://doi.org/10.1126/science.1199327); [author-hosted paper](https://learninglab.psych.purdue.edu/downloads/2011/2011_Karpicke_Blunt_Science.pdf).

Experiments with science texts found advantages from retrieval practice, including on comprehension and inference questions.

Design implication: occasionally ask the person to retrieve or apply an idea before giving that check's answer. Provide corrective feedback. One correct answer demonstrates performance on that check, not durable mastery or broad transfer. Same-session questions alone cannot establish long-term retention.

### 5. Learning during productive work

Brynjolfsson, E., Li, D., & Raymond, L. (2025). *Generative AI at work*. Quarterly Journal of Economics, 140(2), 889-942. [Published paper](https://doi.org/10.1093/qje/qjae044).

The published study examined 5,172 customer-support agents and reported a 15% average productivity increase, with substantial differences across workers, alongside evidence consistent with learning. Earlier working-paper versions report different sample sizes and estimates; this package uses the published figures.

Design implication: work can be a setting for skill development, and assistance can be especially useful to less experienced workers. The study does not test these instructions, all occupations, or a particular teaching-to-work ratio.

## LLM context and efficiency

### 6. Access to relevant information in long contexts

Liu, N. F., et al. (2024). *Lost in the middle: How language models use long contexts*. Transactions of the Association for Computational Linguistics, 12, 157-173. [Paper and metadata](https://aclanthology.org/2024.tacl-1.9/). DOI: 10.1162/tacl_a_00638.

Multi-document question-answering and key-value retrieval tests showed sensitivity to the position of relevant information, often with worse performance in the middle of long inputs.

Design implication: keep the active objective, requirements, and relevant artifact details accessible and avoid redundant histories. This is evidence from tested models and tasks, not a claim that all current models fail at the same length or position. The skill cannot inspect context occupancy unless its host exposes that information.

### 7. Prompt compression

Pan, Z., et al. (2024). *LLMLingua-2: Data distillation for efficient and faithful task-agnostic prompt compression*. Findings of ACL 2024, 963-981. [Paper](https://aclanthology.org/2024.findings-acl.57/). DOI: 10.18653/v1/2024.findings-acl.57.

The paper describes a trained extractive compressor and benchmarked efficiency gains. Its method uses additional model infrastructure.

Design implication: removing redundancy while preserving necessary information is worth evaluating. This package does not implement LLMLingua-2; its results cannot justify a claimed compression ratio or latency gain for ordinary summaries. Do not remove negations, exact requirements, units, source pointers, or evidence distinctions merely to shorten a note.

### 8. Context engineering practice

Anthropic (2025). *Effective context engineering for AI agents*. [Engineering article](https://www.anthropic.com/research/effective-context-engineering-for-ai-agents).

The article describes selective retrieval, compaction, and external notes, and warns that aggressive compaction can discard important details. This is vendor engineering guidance rather than peer-reviewed educational evidence.

Design implication: keep the skill entrypoint short, load this research file only when relevant, and preserve a compact state note at handoff. In plain chat, a summary is text, not automatic history deletion. Reusing it in a new chat requires bringing essential source material too. Do not add multi-agent infrastructure just to use this skill.

## Prototype decisions and open questions

The following are design inferences, not established treatment effects:

- Occasional milestone checks can balance learner effort against workflow interruption.
- Deadline-aware support can preserve useful learning while keeping the task moving.
- A small combined task-and-learning note may help continuity without storing a transcript.
- A compact prompt may be practical for limited-message users, at the cost of less guidance.

Context capacity, input/output token usage, and product message quotas are different constraints. Shorter text can reduce overhead but does not necessarily increase message allowances. Exact token counts depend on the tokenizer and exact input; fewer words alone do not establish a measured token saving. Installation and product capabilities may change independently of these studies.

Evaluate task quality, time, independent application, delayed retention, exchanges, and tokens separately. Use [evaluation.md](evaluation.md). Avoid optimizing only for the shortest conversation or the most correct assisted artifact.
