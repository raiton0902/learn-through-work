# Installation and first use

Choose a native skill installation for Codex, or paste the compact prompt into a regular chat. You do not need both approaches in the same conversation.

## Codex: user-level local installation

Install the **inner** `learn-through-work` folder, the one containing `SKILL.md`. The outer folder contains the documentation.

The following PowerShell commands assume your terminal is in the outer package folder beside this `INSTALL.md`. They create a user-level skill directory and copy the inner folder. They stop if a copy is already installed so existing files are not silently overwritten.

```powershell
$skillSource = Join-Path (Get-Location) 'learn-through-work'
$skillRoot = Join-Path $HOME '.agents/skills'
$skillDestination = Join-Path $skillRoot 'learn-through-work'

if (-not (Test-Path -LiteralPath (Join-Path $skillSource 'SKILL.md'))) {
    throw 'Open PowerShell in the outer package folder containing INSTALL.md.'
}
if (Test-Path -LiteralPath $skillDestination) {
    throw 'A skill already exists at the destination. Review it before updating.'
}
New-Item -ItemType Directory -Path $skillRoot -Force | Out-Null
Copy-Item -LiteralPath $skillSource -Destination $skillDestination -Recurse
Get-Item -LiteralPath (Join-Path $skillDestination 'SKILL.md')
```

On macOS or Linux, run this from the same outer package folder:

```sh
if [ ! -f ./learn-through-work/SKILL.md ]; then
  printf '%s\n' 'Run this from the outer package folder containing INSTALL.md.'
elif [ -e "$HOME/.agents/skills/learn-through-work" ]; then
  printf '%s\n' 'A skill already exists. Review it before updating.'
else
  mkdir -p "$HOME/.agents/skills"
  cp -R ./learn-through-work "$HOME/.agents/skills/learn-through-work"
fi
```

Codex's documented user-level discovery location is `~/.agents/skills`. For a repository-only installation, copy the same inner folder into that repository's `.agents/skills/` instead. Choose one location to avoid duplicate skill names. Local installation does not itself distribute the skill to other devices or remote environments. See [official OpenAI documentation](https://learn.chatgpt.com/docs/build-skills), checked October 23, 2026.

## Verify and use

Look for `learn-through-work` in the skill selector. Codex documents automatic discovery of skill changes; restart it if the skill does not appear. The installed structure should be:

```text
~/.agents/skills/learn-through-work/
  SKILL.md
  agents/openai.yaml
  references/research.md
  references/evaluation.md
```

Start with:

```text
Use $learn-through-work to help me complete this assignment while learning
the concepts behind it. I know basic loops but struggle with arrays.
The assignment is attached and due tomorrow. Keep explanations short.
```

Expect useful progress, a relevant brief explanation, and occasional checks. It should not require approving a separate curriculum. Listing the skill verifies discovery; try a small real task to assess its behavior.

## Regular chat interfaces, including limited-message use

1. Open [COMPACT_PROMPT.md](COMPACT_PROMPT.md).
2. Paste only the text inside its code block into a new chat.
3. Add your task and the necessary rubric, data, or work so far.
4. Mention any deadline, knowledge gap, or limited message budget.

This is ordinary prompt use, not a claim of native installation or availability of a particular product feature. You can use it wherever the service accepts such instructions; compliance varies by model. No file-reading tools or subscription-specific features are assumed.

For more complete guidance, paste the body of the inner `SKILL.md` instead of the compact prompt. Do not paste the research bibliography unless you are discussing the design.

## Continue in a fresh chat

Ask: "Give me a compact continuation note with task state and learning evidence."

Bring the note, your chosen instruction version, and required files or excerpts into the new chat. A path on another device is insufficient. Confirm important constraints survived the handoff. Summaries can omit information and do not remove history from an existing chat.

## Updates

Review the new inner folder against your installed copy before replacing it. Preserve personal work separately. Recheck discovery afterward. No installer, configuration edit, publication, or automatic update service is included in this package.
