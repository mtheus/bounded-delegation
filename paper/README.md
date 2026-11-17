# Paper source (arXiv package)

This folder holds the LaTeX source for the preprint. `main.tex` is the full, canonical
article — the one meant for arXiv and, later, JSERD. (`../article.md` is a separate, short
blog-style summary for the project website — it does not contain the full text.)

## Files

- `main.tex` — article-class source, ready for arXiv (`cs.SE` primary category suggested; consider cross-listing `cs.AI`/`cs.HC`).
- `references.bib` — BibTeX bibliography. **Several entries are marked `VERIFY`** — see below.

## Before you submit: fix the references

The draft cites a number of very recent (2025–2026) industry reports and
public statements (Faros AI telemetry, Veracode's GenAI report, DORA's
report, Storey's "Triple Debt Model," Shaw & Nave, Borg et al., Tornhill,
Google's "Elephant-Goldfish Model" post, and remarks attributed to Karpathy,
Farley, and Cherny). I could not verify the exact venue/title/URL for these
against a primary source, so `references.bib` marks them `VERIFY` with
placeholder bibliographic data. **Replace those placeholders with the real
citation (title, outlet, date, URL/DOI) before submitting** — arXiv won't
reject incorrect references, but you are responsible for their accuracy,
and a reviewer at JSERD will check them closely.

Entries for Peng et al. (2023), Naur (1985), Brooks (1986), Parnas (1972),
Ousterhout (2021), and METR (2025) are real, well-known publications and
have been filled in with standard bibliographic data already.

## Building locally

You need a TeX distribution (TeX Live / MacTeX / MiKTeX) with `latexmk`,
or at least `pdflatex` + `bibtex`.

```bash
cd paper
latexmk -pdf main.tex
# or, manually:
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

This produces `main.pdf`.

## Packaging for arXiv

arXiv wants the LaTeX **source**, not just a PDF. From this folder:

```bash
# Generate main.bbl (arXiv does not reliably run bibtex for you)
pdflatex main.tex && bibtex main && pdflatex main.tex && pdflatex main.tex

# Package exactly what arXiv needs
tar -czvf bounded-delegation-arxiv.tar.gz main.tex main.bbl references.bib
```

Upload `bounded-delegation-arxiv.tar.gz` at <https://arxiv.org/submit>.

Note: arXiv's own license options (CC BY 4.0, CC BY-SA 4.0, CC BY-NC-SA 4.0, or arXiv's
default non-exclusive license) don't include CC0, which is what the rest of this repo uses —
pick the closest arXiv license at submission time.

## SBC JSERD

The [Journal of Software Engineering Research and Development (JSERD)](https://journals-sol.sbc.org.br/index.php/jserd/)
(SBC/Brazilian Computer Society) has its own submission template and review process, which
changes between calls for papers — check the journal site for the current author guidelines
when you're ready to submit there. Reuse `main.tex` as the source of truth rather than forking
it; regenerate the JSERD version from it.
