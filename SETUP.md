# Link this repository to Claude Code or Cursor

Install the `reak-analysis` skill into the data project that should follow these workflows. The skill loads when the work is about that project's files, or when it is invoked as `/reak-analysis`. It does not replace a plan already written in the project's `resources/`, or a plan the user has stated.

Keep the clone of this repository as the copy you update with `git pull`. Link that clone. Do not install the skill into your personal skills folder (`~/.claude/skills/` or `~/.cursor/skills/`): those apply to every project on the machine.

## Claude Code

Claude Code loads project skills from `.claude/skills/` in the project where the session starts. Point a skill entry at this clone.

From the data project's root, with `WORKFLOWS` set to the clone (for example `D:\REAK\05-SoftwareDev\repos\RE-AK-CompleteStack-Cursor\ai-workflows-public`):

**Windows (PowerShell)**

```powershell
New-Item -ItemType Directory -Force -Path .claude\skills
New-Item -ItemType Junction -Path .claude\skills\reak-analysis -Target "$env:WORKFLOWS\.claude\skills\reak-analysis"
```

**macOS / Linux**

```bash
mkdir -p .claude/skills
ln -s "$WORKFLOWS/.claude/skills/reak-analysis" .claude/skills/reak-analysis
```

Start Claude Code in the data project. If it asks for approval to load a skill that points outside the project, approve it once for that project.

For a single session, without a link in the project:

```bash
claude --add-dir "$WORKFLOWS"
```

`--add-dir` loads `.claude/skills/` from the added directory for that session. File access granted by `permissions.additionalDirectories` does not load skills.

Check: in the data project, run `/reak-analysis` and ask where a new summary table belongs. The answer should be `results/data/`.

## Cursor

Cursor loads this skill when the repository is installed as a plugin. The manifest is `.cursor-plugin/plugin.json`, and it points at `.claude/skills/`, which is the same skill Claude Code uses.

1. Open the data project in Cursor.
2. In Customize, import the plugin from this Git repository.
3. Install it for that project. Leave the user-wide install off.

A project install follows `git pull` in the clone the next time the plugin updates. Opening this repository as a folder does not, by itself, load the skill into a different data project.

Check: in the data project's agent chat, invoke `reak-analysis`, or ask where a figure cited by the deliverable belongs. The answer should be `report/figures/`.

Leave the method out of a root `AGENTS.md`, a root `CLAUDE.md`, and any rule with `alwaysApply: true` in the data project. Those are included in every conversation there, including work that is not this analysis.

## After an update

Pull this repository. A junction, symlink, or project plugin install keeps pointing at the clone, so the next session sees the change. A copied skill folder does not: link the clone instead of copying the files.
