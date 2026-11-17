# Paper source

This folder holds the LaTeX source for the paper. `main.tex` is the full, canonical article.
(`../article.html` is a full HTML conversion of it for free online reading; `../article.md` is
a separate, short blog-style summary for the project website.)

## Files

- `main.tex` — article-class LaTeX source (`cs.SE`-flavoured; no particular venue template).
- `main.pdf` — compiled output, checked into the repo so the paper is readable without building it.

References are set directly in `main.tex` as running author-year text plus a thematically
grouped, hyperlinked "References" section at the end — matching how the source article itself
cites things — rather than through a separate `.bib`/BibTeX pipeline. There is no `references.bib`
in this folder.

## Figures

The source article had two embedded charts that did not survive the hand-off to Markdown
(the `.md` draft only kept a bracketed placeholder for each). Their original rendered versions
were not recoverable from anything available in this session, so both are reconstructed as
native TikZ vector figures in `main.tex` — drawn from the qualitative positioning and the
step-by-step description already given in the article's own prose (Section 5's findings and
Table 2 for Figure 1; Section 7.4's 8-step list for Figure 2), not from the lost originals:

- **Figure 1** (`fig:positioning`, Section 5): a qualitative scatter plot positioning the
  eleven reviewed techniques and the proposed model on two axes (scope of knowledge organised;
  strength of verification).
- **Figure 2** (`fig:cycle`, Section 7.4): an 8-step ring diagram of one increment under
  Bounded Delegation (4 human steps, 4 agent steps), closed by the feedback-ring arrow from
  Section 7.7.

Both compile directly with `pdflatex` — no external image files or asset pipeline needed. If
you have the original charts, they can replace these: swap the `tikzpicture` block for
`\includegraphics` and drop the image file in this folder. (`../article.html` reconstructs the
same two figures again, independently, as inline SVG — if you replace the originals here,
update that file too.)

## Building locally

Verified with TeX Live 2023 (`pdflatex`). From this folder:

```bash
pdflatex -interaction=nonstopmode main.tex
pdflatex -interaction=nonstopmode main.tex   # second pass for cross-references
```

This was run during the authoring of this file: it compiles cleanly (no errors, no undefined
references) to a 36-page PDF, with only a handful of cosmetically negligible overfull/underfull
boxes from the narrow table columns.

## Regenerating article.html

`../article.html` was produced from this file with `pandoc`, then hand-finished (deduplicated
longtable header rows, inline SVGs for the two figures, site styling, table of contents). If
`main.tex` changes substantially, regenerate the base conversion with:

```bash
pandoc main.tex -f latex -t html5 --standalone -o /tmp/raw.html
```

and re-apply the same post-processing (see the project's own notes/commit history for the
exact steps) rather than hand-editing `article.html` out of sync with `main.tex`.
