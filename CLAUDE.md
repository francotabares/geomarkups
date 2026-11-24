# CLAUDE.md

Guidance for Claude Code when working in this repository.

## Project

Research paper, working title "Geographic Markups" (repo: `geomarkups`).
Author: Santiago Franco.
The paper extends the empirical part of the author's job market paper, "Output Market Power and Spatial Misallocation", and studies how the markups of establishments in non-traded industries vary across space, over time, and across industries.
The field is industrial organization, spatial economics, and macroeconomics.
The approach combines a general homothetic demand system with establishment-level production function estimation, so that consumer demand and firm technology together deliver an estimating equation from which markups are recovered.
The empirical findings, and so the paper's substantive contribution, are not yet known: they depend on implementing the strategy with the Census data, and should not be assumed or anticipated in the writing.

Most of the work is **writing and theoretical derivations**. There is little code.
The empirical work uses **confidential U.S. Census Bureau microdata** that is accessed only inside the FSRDC and never enters this repository.

## Model and estimation strategy (starting point)

This is the current baseline, not the final model.
The goal is to generalize it as far as possible, toward general homothetic demand and general production functions.
Prefer derivations that hold in the general case, and say explicitly where a specific functional form or assumption is used.

- **Demand.** Preferences over non-traded varieties are in the HDIA class (homothetic with direct implicit additivity) of `Matsuyama&Ushev17`, i.e. Kimball preferences: $\int \Upsilon(y_j/Y)\,dG = 1$, with $\Upsilon$ strictly increasing and concave, $\Upsilon(0)=0$, and a finite choke price. CES is the special case $\Upsilon(q) = q^{(\sigma-1)/\sigma}$.
- **Production.** A general production function in principle. Because of data limits, the baseline is Cobb-Douglas with output elasticities constant within an industry. Labor is the flexible input.
- **Markets.** A market is a county or a commuting zone. Results use both.
- **Conduct.** The baseline is monopolistic competition: establishments take the local price indices as given. A planned extension is oligopolistic competition in the style of `Atkeson&Burstein08`, where establishments internalize their effect on the local price indices. This matters most in small markets, where single establishments can have large sales shares.
- **Estimating equation.** The ratio estimator $\mu_{jnct} = (\beta_n/\alpha^l_{jnct})\,e^{-\nu_{jnct}}$ is combined with the demand system. Markups then become a function of $s^y_{jnct}\,\mathbb{P}_{nct}/\mathbb{D}_{nct}$. A cubic sieve with no constant term (the choke price implies $\mu \to 1$ as $s^y \to 0$) gives the baseline

  ```latex
  \log \alpha_{jnct}^l = \log \beta_n + \varsigma_{1,nct} s^y_{jnct} + \varsigma_{2,nct} (s^y_{jnct})^2 + \varsigma_{3,nct} (s^y_{jnct})^3 + \upsilon_{jnct}
  ```

  Here $j$ is the establishment, $n$ the industry, $c$ the market and $t$ the year.
  $\alpha^l_{jnct}$ is the wage bill over sales.
  $\beta_n$ is the industry-specific labor output elasticity.
  $s^y_{jnct}$ is the establishment's sales share in its market-industry-year.
  The $\varsigma_{k,nct}$ are market-industry-year coefficients that absorb $\mathbb{P}_{nct}/\mathbb{D}_{nct}$, the ratio of the ideal price index to the competition price index.
  Markups are $\hat\mu_{jnct} = \exp(-\sum_k \hat\varsigma_{k,nct} (s^y_{jnct})^k)$.
  This is the multi-sector version in JMP Appendix `a:muext` with a time index added. The single-market JMP equation is the special case with one industry and one year.
  Whether $\beta_n$ should also vary over time ($\beta_{nt}$) is an open choice.
- Notation is listed in `derivations/notation.md`.

## Relation to the job market paper

- The JMP is `literature/OMPSM_Franco.tex` ("Output Market Power and Spatial Misallocation"). This paper extends its empirical part: Section "Empirical Analysis" (`s:empanal`) and the appendix "Markup Estimation".
- The JMP appendix already contains the derivation of the estimating equation (`a:muestderiv`), sieve consistency (`a:mucons`), the multi-sector version (`a:muext`), labor market power (`a:muestlmp`), and the general production function (`a:genprodfn`). Build on these rather than re-deriving from scratch.
- Keep notation consistent with the JMP. Flag any departure.
- The JMP and this paper share the same preamble and citation commands, so JMP text can be ported without converting citations. JMP labels use `s:` and `a:` prefixes; relabel to this paper's `sec:` convention when porting.
- Numbers in the JMP are JMP results. Do not carry them into this paper as its own results.

## Key literature

Bib keys in `paper/biblio.bib`:

- Markup estimation, production approach: `DeLoecker&Warzynski12`, `DeLoeckerEeckhout&Unger2019` (published QJE 2020), `DeRidderGrassi&Morzenti24` (published Econometrica 2026).
- Oligopolistic competition: `Atkeson&Burstein08`.
- Using demand structure to estimate markups or production functions: `DeLoecker11`, `blum2024abc`.
- Flexible homothetic demand systems: `Matsuyama&Ushev17`.
- Non-CES demand and price index estimation: `Errico&Lashkari25`.
- Geography of markups: `AndersonRebelo&Wong23`.

## Confidential data rules (strict)

- Census microdata, and any output that has not passed Census disclosure review, must never be added to this repo, committed, or pasted into a conversation.
- Never invent, guess, or "fill in" empirical numbers. Mark every missing result with `XX`. Do not use the preamble's `\todo` macro for results.
- Any number in the paper must come from disclosure-approved output, and the author adds it by hand.
- Data file types (`*.dta`, `*.csv`, `*.sas7bdat`, etc.) and the `data/` and `confidential/` folders are gitignored. Do not override this with `git add -f`.

## Repository layout

- `paper/Paper.tex`: the paper, as one single document (it is a short paper, so there are no separate section files). Its organization follows the JMP: introduction, model, empirical analysis, conclusion, references, appendix.
- `paper/preamble.tex`: the author's preamble, shared with the JMP. Do not edit it without asking. It defines shortcut macros (for example `\P` for $\mathbb{P}$, `\C` for $\mathbb{C}$, `\vs` for $\varsigma$) and the theorem environments `prop`, `assum`, `lemma`, `cor`, `defi`.
- `paper/Scratch.tex`: scratch paper for exploratory notes and derivations, using the same preamble and bibliography as `Paper.tex`. It need not be polished. One `\section` per topic, each entry started with a dated comment, open questions marked `\textbf{Open:}`. When a result is settled, move it to `Paper.tex` and leave a one-line note saying where it went.
- `paper/biblio.bib`: bibliography, processed with biblatex and biber (`authoryear` style). Cite with `\textcite{}` (in text) and `\parencite{}` (in parentheses).
- `paper/figures/`, `paper/tables/`: disclosure-approved figures and tables only.
- `derivations/`: standalone derivations that grow too long for `Scratch.tex`, plus `notation.md`.
- `notes/`: research log and meeting notes, named `YYYY-MM-DD-topic.md`.
- `literature/`: notes on papers, one file per paper (`authorYEAR.md`). PDFs are gitignored.

## Building the paper

From `paper/`:

```
pdflatex Paper && biber Paper && pdflatex Paper && pdflatex Paper
```

The same sequence builds `Scratch.tex`.

The TeX distribution is BasicTeX, so some packages may be missing. Install them with `sudo tlmgr install <pkg>`.

## Writing and math conventions

- Put each sentence on its own line in `.tex` files so git diffs stay readable.
- Number every displayed equation that is referenced and give it a `\label{eq:...}`. Section labels use `sec:` and propositions use `prop:`.
- Define notation the first time it appears and keep it consistent across sections. Record new symbols in `derivations/notation.md`.
- When deriving, show the intermediate steps and state the assumptions used at each step. Flag any step that is not fully rigorous.
- Do not change the author's prose style or arguments unless asked. Suggest edits and explain them.
- Bibliography entries must be real, verifiable papers. Never fabricate citations. If a reference can't be verified, say so.

## Git workflow

- Default branch is `main`, remote is `git@github.com:francotabares/geomarkups.git` (SSH).
- Write short, descriptive commit messages ("Draft model section: demand system").
- Before committing, check `git status` to make sure no data or disclosure-sensitive files are staged.
- The author edits the paper manually in Overleaf, which syncs with this GitHub repository. Edits can therefore arrive on GitHub from Overleaf at any time.
  - Run `git pull` before reading or editing any file, so work starts from the latest Overleaf version.
  - Commit and push finished edits promptly, so the author can pull them into Overleaf before editing the same lines.
  - If a pull produces a merge conflict, do not resolve it by discarding either side. Show the conflict to the author and ask.
- Everything in this repository is also visible in Overleaf, which is an external service. This is one more reason the confidential data rules above are strict.
