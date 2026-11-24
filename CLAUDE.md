# CLAUDE.md

Guidance for Claude Code when working in this repository.

## Project

Research paper, working title "Geographic Markups" (repo: `geomarkups`).
Author: Santiago Franco.
<!-- TODO: add 2-3 sentences on the research question, field, and main contribution. -->

Most of the work is **writing and theoretical derivations**. There is little code.
The empirical work uses **confidential U.S. Census Bureau microdata** that is accessed only inside the FSRDC and never enters this repository.

## Confidential data rules (strict)

- Census microdata, and any output that has not passed Census disclosure review, must never be added to this repo, committed, or pasted into a conversation.
- Never invent, guess, or "fill in" empirical numbers. Mark missing results with a placeholder such as `\todo{result: ...}` or `XX`.
- Any number in the paper must come from disclosure-approved output, and the author adds it by hand.
- Data file types (`*.dta`, `*.csv`, `*.sas7bdat`, etc.) and the `data/` and `confidential/` folders are gitignored. Do not override this with `git add -f`.

## Repository layout

- `paper/main.tex`: master file. Sections live in `paper/sections/*.tex` and are pulled in with `\input`.
- `paper/references.bib`: bibliography (natbib, `plainnat`). Cite with `\citet{}` / `\citep{}`.
- `paper/figures/`, `paper/tables/`: disclosure-approved figures and tables only.
- `derivations/`: long or rough derivations. Clean results move into `paper/sections/`.
- `notes/`: research log and meeting notes, named `YYYY-MM-DD-topic.md`.
- `literature/`: notes on papers, one file per paper (`authorYEAR.md`). PDFs are gitignored.

## Building the paper

From `paper/`:

```
pdflatex main && bibtex main && pdflatex main && pdflatex main
```

The TeX distribution is BasicTeX, so some packages may be missing. Install them with `sudo tlmgr install <pkg>`.

## Writing and math conventions

- Put each sentence on its own line in `.tex` files so git diffs stay readable.
- Number every displayed equation that is referenced and give it a `\label{eq:...}`. Section labels use `sec:` and propositions use `prop:`.
- Define notation the first time it appears and keep it consistent across sections. Record new symbols in `derivations/notation.md` (create it when first needed).
- When deriving, show the intermediate steps and state the assumptions used at each step. Flag any step that is not fully rigorous.
- Do not change the author's prose style or arguments unless asked. Suggest edits and explain them.
- Bibliography entries must be real, verifiable papers. Never fabricate citations. If a reference can't be verified, say so.

## Git workflow

- Default branch is `main`, remote is `git@github.com:francotabares/geomarkups.git` (SSH).
- Write short, descriptive commit messages ("Draft model section: demand system").
- Before committing, check `git status` to make sure no data or disclosure-sensitive files are staged.
