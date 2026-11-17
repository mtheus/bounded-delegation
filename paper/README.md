# Paper source (arXiv package)

This folder holds the LaTeX source for the preprint. `main.tex` is the full, canonical
article — the one meant for arXiv and, later, JSERD. (`../article.md` is a separate, short
blog-style summary for the project website — it does not contain the full text.)

## Files

- `main.tex` — article-class source, ready for arXiv (`cs.SE` primary category suggested; consider cross-listing `cs.AI`/`cs.HC`).
- `main.pdf` — compiled output, checked into the repo so the paper is readable before arXiv is live.

References are set directly in `main.tex` as running author-year text plus a thematically
grouped, hyperlinked "References" section at the end — matching how the source article itself
cites things — rather than through a separate `.bib`/BibTeX pipeline. There is no `references.bib`
in this folder.

## Figures not reproduced

The source article had two embedded charts that did not survive the hand-off to this LaTeX
version:

- **Figure 1** (Section 5): a qualitative scatterplot positioning the eleven reviewed
  techniques and the proposed model on two axes (scope of knowledge organised; strength of
  verification).
- **Figure 2** (Section 7.4): an 8-step diagram of one increment under Bounded Delegation (4
  human steps, 4 agent steps).

Both are left as labelled placeholder quotes in `main.tex` (search for `[Figure`). If you have
the original charts, drop them in as `fig1.pdf`/`fig2.pdf` and replace the placeholders with
`\includegraphics`.

## Building locally

Verified with TeX Live 2023 (`pdflatex`). From this folder:

```bash
pdflatex -interaction=nonstopmode main.tex
pdflatex -interaction=nonstopmode main.tex   # second pass for cross-references
```

This was run during the authoring of this file: it compiles cleanly (no errors, no undefined
references) to a 35-page PDF, with only a handful of cosmetically negligible overfull/underfull
boxes from the narrow table columns.

## Packaging for arXiv

arXiv wants the LaTeX **source**, not just a PDF. From this folder:

```bash
tar -czvf bounded-delegation-arxiv.tar.gz main.tex
```

Upload `bounded-delegation-arxiv.tar.gz` at <https://arxiv.org/submit>. Note: arXiv's own
license options (CC BY 4.0, CC BY-SA 4.0, CC BY-NC-SA 4.0, or arXiv's default non-exclusive
license) don't include CC0, which is what the rest of this repo uses — pick the closest arXiv
license at submission time.

## SBC JSERD

The [Journal of Software Engineering Research and Development (JSERD)](https://journals-sol.sbc.org.br/index.php/jserd/)
(SBC/Brazilian Computer Society) has its own submission template and review process, which
changes between calls for papers — check the journal site for the current author guidelines
when you're ready to submit there. Reuse `main.tex` as the source of truth rather than forking
it; regenerate the JSERD version from it.
