# Bounded Delegation

**Why AI Coding Agents Are Breaking Software Engineering (And What to Do About It)**

Matheus Bastos Neves · Independent Researcher · [linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/)

A position paper arguing that code generation is no longer the bottleneck in AI-assisted
software engineering — verification is. It introduces the **Bounded Delegation Hypothesis
(H₀)**: delegating implementation to coding agents is sustainable if, and only if, delegation
is bounded on one side by human-owned **Intent** (problem statement, domain language,
architectural decisions) and on the other side by human-readable **Evidence** (executable
scenarios and test results).

- 🌐 **Landing page:** <https://mtheus.github.io/bounded-delegation/>
- 📖 **Full article:** [`article.md`](./article.md) (source) · [rendered page](https://mtheus.github.io/bounded-delegation/article.html)
- 📄 **arXiv preprint:** not yet submitted — LaTeX source is ready in [`paper/`](./paper). <!-- TODO(arxiv): replace with https://arxiv.org/abs/XXXX.XXXXX once published -->
- 🎓 **Future target venue:** [JSERD — Journal of Software Engineering Research and Development](https://journals-sol.sbc.org.br/index.php/jserd/) (SBC)
- 💼 **Author:** [linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/)

## Repository layout

```
.
├── article.md        canonical Markdown draft (source of truth)
├── article.html       rendered, styled version of the article for GitHub Pages
├── index.html          landing page (abstract, takeaways, links) for GitHub Pages
├── .nojekyll           disables Jekyll processing — this is a hand-written static site
├── paper/
│   ├── main.tex         LaTeX source for the arXiv submission
│   ├── references.bib   bibliography (see paper/README.md — some entries need verification)
│   └── README.md        build instructions + arXiv/JSERD submission checklist
└── LICENSE              CC0 1.0 (public domain)
```

`article.md` is the single source of truth. `index.html`/`article.html` and `paper/main.tex`
are hand-derived from it for their respective publishing targets (web, arXiv). If you revise
the content, update `article.md` first, then propagate the change to the other two.

## Publishing checklist

- [x] Draft written (`article.md`)
- [x] Landing page + styled article page for GitHub Pages (`index.html`, `article.html`)
- [x] LaTeX source for arXiv (`paper/main.tex`, `paper/references.bib`)
- [ ] **Enable GitHub Pages**: repo Settings → Pages → Source: "Deploy from a branch" → `main` / `/ (root)`. Once enabled, the site is served at <https://mtheus.github.io/bounded-delegation/>.
- [ ] **Fix references**: several bibliography entries in `paper/references.bib` are marked `VERIFY` — confirm exact titles/venues/URLs before submitting anywhere. See [`paper/README.md`](./paper/README.md).
- [ ] **Submit to arXiv**: build `main.pdf`/`main.bbl` and upload per [`paper/README.md`](./paper/README.md). After acceptance, update the two `TODO(arxiv)` markers (here and in `index.html`) with the real arXiv link.
- [ ] **Submit to JSERD** (later): adapt `article.md` to JSERD's author template once you're ready; see notes in [`paper/README.md`](./paper/README.md).

## License

[CC0 1.0](./LICENSE) — public domain.
