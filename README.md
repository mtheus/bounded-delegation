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
- 📝 **Blog summary:** [`article.md`](./article.md) (source) · [rendered page](https://mtheus.github.io/bounded-delegation/article.html)
- 📄 **Full paper:** [`paper/main.tex`](./paper/main.tex) — this is the complete article (the one meant for arXiv and, later, JSERD)
- 📄 **arXiv preprint:** not yet submitted — see [`paper/README.md`](./paper/README.md). <!-- TODO(arxiv): replace with https://arxiv.org/abs/XXXX.XXXXX once published -->
- 🎓 **Future target venue:** [JSERD — Journal of Software Engineering Research and Development](https://journals-sol.sbc.org.br/index.php/jserd/) (SBC)
- 💼 **Author:** [linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/)

## Repository layout

```
.
├── article.md          short blog-style SUMMARY of the paper, for the website/socials
├── article.html         rendered, styled version of that summary, for GitHub Pages
├── index.html            landing page (abstract, takeaways, links) for GitHub Pages
├── .nojekyll             disables Jekyll processing — this is a hand-written static site
├── paper/
│   ├── main.tex           the FULL original article — the one submitted to arXiv/JSERD
│   ├── references.bib     bibliography (see paper/README.md — some entries need verification)
│   └── README.md          build instructions + arXiv/JSERD submission checklist
└── LICENSE                CC0 1.0 (public domain)
```

**`paper/main.tex` is the canonical, complete article** — the thing that gets submitted to
arXiv and, later, adapted for JSERD. `article.md`/`article.html` are a *short, separate*
blog-post summary used to drive traffic to the full paper; they are not meant to contain the
full text. If you revise the argument, edit `paper/main.tex` first, then update the summary in
`article.md`/`article.html` only if the headline claims changed.

## Publishing checklist

- [x] Full paper written (`paper/main.tex`)
- [x] Blog summary + landing page for GitHub Pages (`article.md`/`article.html`, `index.html`)
- [ ] **Enable GitHub Pages**: repo Settings → Pages → Source: "Deploy from a branch" → `main` / `/ (root)`. Once enabled, the site is served at <https://mtheus.github.io/bounded-delegation/>.
- [ ] **Fix references**: several bibliography entries in `paper/references.bib` are marked `VERIFY` — confirm exact titles/venues/URLs before submitting anywhere. See [`paper/README.md`](./paper/README.md).
- [ ] **Submit to arXiv**: build `main.pdf`/`main.bbl` and upload per [`paper/README.md`](./paper/README.md). After acceptance, update the two `TODO(arxiv)` markers (here and in `index.html`) with the real arXiv link.
- [ ] **Submit to JSERD** (later): adapt `paper/main.tex` to JSERD's author template once you're ready; see notes in [`paper/README.md`](./paper/README.md).

## License

[CC0 1.0](./LICENSE) — public domain.
