# learn-through-work

An AI skill for people who need to finish a task while learning what they are doing.

Bring an assignment, spreadsheet, report, coding problem, or workplace task. The AI helps move it forward, explains the relevant ideas in small pieces, and occasionally invites you to apply one yourself. You can start with little subject knowledge. You do not have to finish a separate course before getting help.

## Start here

Follow [INSTALL.md](INSTALL.md) to install the skill in Codex or use the [compact prompt](COMPACT_PROMPT.md) in a regular chat interface.

```text
Use $learn-through-work to help with my statistics assignment.
I need to compare two groups, but I don't understand how to choose a test.
Use the attached rubric. It is due tomorrow. Keep explanations short.
```

```text
Use $learn-through-work to help me build this sales report.
I can use basic spreadsheet formulas, but weighted averages confuse me.
Help finish the report and explain the important choices as we go.
```

Useful requests during work:

- "Show one complete example first."
- "Explain that more slowly using my own data."
- "I only have a few messages left. Batch the remaining steps."
- "The deadline is close. Give more direct help and defer extra practice."
- "Check whether I can apply this to another example."
- "Give me a continuation note for a fresh chat."

## How it works

The AI starts from your task and available materials. It helps produce a useful part of the deliverable, explains a concept behind that part, then adjusts support based on your response. At a meaningful point it may ask a short prediction, explanation, or application question.

If you are lost, it gives more support. If you demonstrate understanding, it reduces repeated explanations. Checks are occasional and can be skipped. A skipped check leaves understanding unverified; it does not block ordinary task help.

For example, when building a sales report, the AI might help calculate revenue per order and briefly explain why averaging branch averages could mislead. It can then ask which branch should receive more weight in a small example. You learn an idea that matters to the report you are making.

The skill distinguishes:

| Status | Meaning |
| --- | --- |
| Explained only | The AI presented the idea; understanding is unchecked. |
| Answered with help | You used hints or a demonstration to complete a step. |
| Demonstrated independently | You explained or applied it without the answer being supplied for that check. This is local evidence, not proof of lasting mastery. |

## Context and message efficiency

The core instructions are in [SKILL.md](learn-through-work/SKILL.md). Research and evaluation material are separate and loaded only when needed. The skill favors relevant excerpts, brief explanations, and compact continuation notes over repeated histories and lectures.

The compact prompt is a shorter alternative for chat interfaces without skill support. Use one version at a time. Copying the whole package into every message defeats its purpose.

Learning still requires attention. The skill cannot guarantee zero extra time, a particular token saving, extra free messages, or automatic memory between chats. Adding a summary to the same chat does not erase earlier messages. A fresh chat needs the instructions, continuation note, and any required artifact content again.

## Research basis

| Design choice | Source | Evidence boundary |
| --- | --- | --- |
| Check independent understanding separately from assisted output | Bastani et al. (2025), [PNAS](https://doi.org/10.1073/pnas.2422633122) | High-school mathematics experiment; the guarded tutor mitigated harm but did not show an unassisted exam benefit. |
| Model a method, coach its use, and reduce support | Collins, Brown, and Holum (1991), [Cognitive Apprenticeship](https://www.aft.org/ae/winter1991/collins_brown_holum) | Instructional framework, not a trial of this skill. |
| Combine worked steps with brief principle explanations | Atkinson, Renkl, and Merrill (2003), [study](https://doi.org/10.1037/0022-0663.95.4.774) | Two experiments; their time and transfer results do not guarantee deadline savings here. |
| Invite retrieval or application | Karpicke and Blunt (2011), [Science](https://doi.org/10.1126/science.1199327) | Science-text learning experiments; not validation of every task or check. |
| Investigate learning during productive work | Brynjolfsson, Li, and Raymond (2025), [QJE](https://doi.org/10.1093/qje/qjae044) | Customer-support field evidence; not proof for all occupations. |
| Keep relevant information accessible | Liu et al. (2024), [Lost in the Middle](https://aclanthology.org/2024.tacl-1.9/) | Position-sensitive retrieval in tested models and tasks. |
| Remove redundancy carefully | Pan et al. (2024), [LLMLingua-2](https://aclanthology.org/2024.findings-acl.57/) | Trained compression system; its benchmark savings do not transfer automatically to these instructions. |
| Use selective context and continuation notes | Anthropic (2025), [context engineering guidance](https://www.anthropic.com/research/effective-context-engineering-for-ai-agents) | Vendor engineering guidance, not an education experiment. |

The [research notes](learn-through-work/references/research.md) explain the evidence and limitations. [CITATION.cff](CITATION.cff) lists the underlying publications. This package is a prototype: its combined effect on learning, speed, and token use has not been established. The [evaluation guide](learn-through-work/references/evaluation.md) describes how to assess those outcomes.

## Package contents

```text
learn-through-work/                 Shareable package
  README.md
  INSTALL.md
  COMPACT_PROMPT.md
  CITATION.cff
  learn-through-work/               Install this inner folder
    SKILL.md
    agents/openai.yaml
    references/research.md
    references/evaluation.md
```

The skill needs no scripts, additional API keys, or paid services of its own. Your chosen AI service supplies the model and determines account limits and available tools. Native skill support and plain-chat instruction following vary by product. Keep personal task files and continuation notes outside this package when sharing it.
