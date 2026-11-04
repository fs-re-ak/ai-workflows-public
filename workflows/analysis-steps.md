# Analysis steps

Default path for a RE-AK data project. A question, protocol, or plan already stated by the user, or already written in `resources/`, leads. These steps fill in what was left open. When a step is used as that default, say so in one sentence.

Keep an analysis journal in the data project for every step. The journal stays in that project. It is not copied into this repository.

## Journal

Create `journal/analysis.md` at the project root if it is not there. Append an entry each time a step is done or redone:

```markdown
## YYYY-MM-DD — Step N — short title

- Did: what was done
- Wrote: paths created or updated
- Found: what the step showed
- Open: what is still unresolved
```

Record decisions, paths, and conclusions. Leave raw biosignal samples out of the journal. Session folders already live under `dataset/`.

## Step 1 — Organize the data

Gather each recording into `dataset/`, one folder per session. A session may be unprocessed (raw streams only) or already processed (pipeline tables already present). Both belong here. Organizing does not require processing.

A project may keep its own download script to pull sessions from re-akcas into `dataset/`. That script and the files it writes stay in the data project.

Inside a session folder, `rawData/` holds the streams. `features/` holds intermediates. The session's own `results/` holds pipeline tables when processing has already been done. Those tables are inputs. They are distinct from the project-level `results/` directory, which Step 4 and Step 5 write.

Leave `dataset/` unchanged after this step. Record in the journal which sessions were gathered and whether pipeline results were already present.

## Step 2 — Process the data

Processing is done by re-akcas in the cloud, or locally by the Nucleus-Kit toolkit (the re-ak-core pipeline). This workflow does not reimplement those algorithms.

Use pipeline tables that are already in the session. When a table the analysis needs is missing, run re-akcas or Nucleus-Kit and keep the new outputs inside that session folder.

The shared result tables are the 2 Hz files for heart dynamics, arousal, cognition (engagement), and emotions. A missing file means that step has not been produced yet. Do not fill it with invented values.

Record in the journal which route was used (cloud results already present, re-akcas, or Nucleus-Kit) and which result files are present or still missing.

## Step 3 — Annotate the data

Annotations give the analysis its structure. Keep two kinds separate.

**Temporal** annotations mark *when* on the session clock.

- A point is one instant. A zone is a start and an end.
- Times are milliseconds from the start of the recording.
- Annotations made in the dashboard are temporal. Downloaded with the session, they are `dataset/<session>/features/events/annotations.csv`. Rows entered in the dashboard have `Source` `human`. The experiment's label list is the `annotation_labels.json` file beside that CSV.
- Analyze rows with `Active` true. Masked rows stay in the file with `Active` false.

**Spatial** annotations mark *where*.

- A spatial annotation is a place: a named zone on a site map, or a region tied to position (UWB or GPS) when the session has it.
- Maps and the list of places live in `resources/`.
- A temporal zone is a time interval. It is not a place. Use a spatial annotation when the question is about location.

When a claim needs both, restrict a time interval to the time spent in a place, and say that in the journal. Record which annotations were added, which file holds them, and whether each one is temporal or spatial.

## Step 4 — Analyze and explore the data

Read `resources/` and the journal before choosing a comparison. Follow the project's agenda. Use temporal annotations for periods and spatial annotations for places.

Work from the session pipeline tables. Write exploratory tables to `results/data/` and exploratory figures to `results/`. A figure that the deliverable will cite is copied or rewritten into `report/figures/` at Step 5.

Record each pass in the journal: the question, the files used, what turned up, and what was set aside.

## Step 5 — Finalize and produce the report

Write the deliverable in `report/`, in the form the project uses. Figures it cites go in `report/figures/`. Tables it cites stay in `results/data/`, and the text names them.

State which pipeline files and which annotations each claim rests on. The journal remains the working record of the steps. The report is the document the project hands on.

Record in the journal the report path and any claim that was dropped or narrowed while finalizing.
