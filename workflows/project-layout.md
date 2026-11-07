# Data project layout

Standard folders for a RE-AK data-analysis project. Use them when a project is being started, when a file has no place yet, or when someone asks to follow this layout.

A question, protocol, or plan already written by the user, or already present in that project's `resources/`, leads. This page fills in where files go. When a file is placed by this default, say so in one sentence.

This repository holds the description only. Recordings, exports, identifiers, and deliverables stay in the data project.

## Tree

```text
<project>/
├── dataset/          # source material the analysis reads
├── resources/        # brief, protocol, maps, codebook, references
├── journal/          # analysis journal for every step
│   └── analysis.md
├── results/          # working analysis output
│   └── data/         # tables the analysis writes
└── report/           # the written deliverable
    └── figures/      # figures the deliverable cites
```

Analysis scripts and notebooks sit at the project root, beside these folders, unless the project already has a directory for code. They read `dataset/` and `resources/`. They write `results/` and `report/`.

## dataset/

Source material for the analysis: session folders, exported tables, and other files the study starts from.

A processed RE-AK session stays here as one folder. That folder has its own `rawData/`, `features/`, and `results/` (the pipeline's 2 Hz tables, such as `HeartDynamics.csv`, `Arousal.csv`, `Cognition.csv`, and `Emotions.csv`). Those pipeline tables are inputs. They are distinct from the project-level `results/` directory, which holds the analysis built on top of one or more sessions.

Leave `dataset/` unchanged. Correct a source file only when the user asks for that correction, and record what changed in `journal/analysis.md`.

## journal/

`journal/analysis.md` is the running record of the analysis steps: what was done, which files were written, what was found, and what is still open. One entry per step, appended when the step is done or redone. See [Analysis steps](analysis-steps.md).

The journal stays in the data project.

## resources/

Material that explains the study and is neither a recording nor a computed output: the brief, the protocol, zone or site maps, the codebook, questionnaires, and references.

Read `resources/` before choosing a comparison, an epoch, or a figure. The agenda for the analysis lives here when the project has one.

## results/

Working output of the analysis that is not the deliverable: joins, checks, intermediate tables, and exploratory figures.

`results/data/` holds the tables the analysis writes, such as per-session summaries and aggregates. A table that can be rebuilt from `dataset/` belongs here, so the deliverable can cite a stable file.

Exploratory plots stay in `results/`. A plot that the deliverable cites is written to `report/figures/`.

## report/

The written deliverable for the people the project is for: the narrative, in the form the project uses (Markdown, a document, or a PDF).

`report/figures/` holds the figures that deliverable cites, under names the text can refer to. A figure is produced from `results/data/` or from `dataset/`, and the text states which.

## What stays out of the workflows repository

`ai-workflows-public` contains instructions. It does not contain a data project's `dataset/`, `resources/`, `journal/`, `results/`, or `report/`. Those directories live only in the data project. Descriptions and examples in this repository use schematic names, such as `session-example`, and never a recording, an identifier, or a client deliverable.
