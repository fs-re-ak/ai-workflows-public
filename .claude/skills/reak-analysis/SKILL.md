---
name: reak-analysis
description: >-
  Places files in a RE-AK data-analysis project: dataset (source sessions and
  exports), resources (brief, protocol, maps), results and results/data
  (analysis tables), report and report/figures (the deliverable). Use when
  starting such a project, deciding where to read or write an analysis file,
  or when the user asks to follow the RE-AK project layout. A plan already
  stated by the user, or already written in the project's resources, takes
  priority.
---

# RE-AK data project layout

Read `workflows/project-layout.md` in the ai-workflows-public repository and follow it. From this file, that path is `../../../workflows/project-layout.md`. Resolve it from this skill file's own directory, including through a symlink or junction, rather than from the data project's root.

## Priority

1. Follow the question, protocol, or plan the user has stated, and the one already written in the data project's `resources/`.
2. Use the layout below when the project uses these folders, when the user is starting a data project, or when a file's place was left unspecified.
3. When a file is placed by this default, say so in one sentence.

## Layout

| Path | What belongs there |
|---|---|
| `dataset/` | Source sessions and exports. Read them. Leave them unchanged unless the user asks for a correction. |
| `resources/` | Brief, protocol, maps, codebook, questionnaires, references. |
| `results/` | Working analysis output, including exploratory figures. |
| `results/data/` | Tables the analysis writes. |
| `report/` | The written deliverable. |
| `report/figures/` | Figures the deliverable cites. |

A RE-AK session folder, including its own pipeline `results/` tables, lives under the project's `dataset/`. The project's `results/` is the analysis built on those sessions.

Scripts and notebooks stay at the project root unless the project already has a directory for code.

This skill's repository holds instructions only. Leave recordings, exports, identifiers, and deliverables in the data project.
