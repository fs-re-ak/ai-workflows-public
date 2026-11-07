---
name: reak-analysis
description: >-
  Runs a RE-AK data project through five steps: organize sessions into
  dataset, process with re-akcas or Nucleus-Kit, annotate in time and in
  space, explore, and write the report. Keeps journal/analysis.md in the
  data project. Use when starting or continuing that work, or when the user
  asks to follow the RE-AK analysis method. A plan already stated by the
  user, or already written in the project's resources, takes priority.
---

# RE-AK data analysis

Read these files in the ai-workflows-public repository and follow them. Resolve the paths from this skill file's own directory, including through a symlink or junction, rather than from the data project's root.

- `../../../workflows/analysis-steps.md` — organize, process, annotate, explore, report, and the analysis journal
- `../../../workflows/project-layout.md` — where each kind of file goes

## Priority

1. Follow the question, protocol, or plan the user has stated, and the one already written in the data project's `resources/`.
2. Use the steps and the layout below when the user is starting or continuing a data project, or when a step or a file's place was left unspecified.
3. When a file is placed by this default, say so in one sentence.

## Steps

1. Organize. Put each session in `dataset/`, processed or not.
2. Process. Use re-akcas or Nucleus-Kit. Do not invent missing pipeline tables.
3. Annotate. Temporal marks go on the session clock (dashboard rows in `features/events/annotations.csv`, source `human`). Spatial marks name a place. A time interval is not a place.
4. Explore. Write tables to `results/data/` and exploratory figures to `results/`.
5. Report. Write `report/` and put cited figures in `report/figures/`.

After each step, append an entry to `journal/analysis.md` in the data project.

## Layout

| Path | What belongs there |
|---|---|
| `dataset/` | Source sessions and exports. Read them. Leave them unchanged unless the user asks for a correction. |
| `resources/` | Brief, protocol, maps, codebook, questionnaires, references. |
| `journal/analysis.md` | The analysis journal. One entry per step. |
| `results/` | Working analysis output, including exploratory figures. |
| `results/data/` | Tables the analysis writes. |
| `report/` | The written deliverable. |
| `report/figures/` | Figures the deliverable cites. |

A RE-AK session folder, including its own pipeline `results/` tables, lives under the project's `dataset/`. The project's `results/` is the analysis built on those sessions.

Scripts and notebooks stay at the project root unless the project already has a directory for code.

This skill's repository holds instructions only. Leave recordings, exports, identifiers, and deliverables in the data project.
