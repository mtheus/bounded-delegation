# Paper source (arXiv package)

This folder holds the LaTeX source for the preprint. It is built from
[`../article.md`](../article.md), the canonical Markdown draft.

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

### Submission checklist

- [ ] Replace every `VERIFY` note in `references.bib` with a real citation.
- [ ] Confirm the author line/affiliation in `main.tex` is how you want it to appear publicly on arXiv (currently "Independent Researcher").
- [ ] Decide on a license for the arXiv listing (arXiv offers CC BY 4.0, CC BY-SA 4.0, CC BY-NC-SA 4.0, or arXiv's default non-exclusive license — note this repo's code/text is CC0, which is *not* one of arXiv's own license options, so pick the closest arXiv license at submission time).
- [ ] Pick the primary category (`cs.SE` suggested) and any cross-lists (`cs.AI`, `cs.HC`).
- [ ] After acceptance, copy the arXiv ID back into `../index.html` and `../README.md` (there are `TODO(arxiv)` markers in both).

## Later: SBC JSERD submission

The [Journal of Software Engineering Research and Development (JSERD)](https://journals-sol.sbc.org.br/index.php/jserd/) has its own submission template and review process (SBC/Brazilian Computer Society). When you're ready to submit there:

1. Check JSERD's current author guidelines/template on the journal site (templates change between calls for papers).
2. Expand the related-work/validation sections — a journal submission typically expects more rigorous positioning against prior work than a position-paper preprint.
3. Reuse the content in `../article.md` as the source of truth; don't fork it — keep one canonical draft and regenerate both the arXiv and JSERD versions from it.
