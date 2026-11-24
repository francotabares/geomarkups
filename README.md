# Geographic Markups

Research paper by Santiago Franco (working title).

## Structure

| Folder | Contents |
|---|---|
| `paper/` | LaTeX manuscript (`main.tex`, `sections/`, `references.bib`) |
| `derivations/` | Working derivations |
| `notes/` | Research log and meeting notes |
| `literature/` | Notes on related papers |

## Build

```
cd paper
pdflatex main && bibtex main && pdflatex main && pdflatex main
```

## Data

The empirical analysis uses confidential U.S. Census Bureau data accessed through the Federal Statistical Research Data Center (FSRDC). No confidential data is stored in this repository.
