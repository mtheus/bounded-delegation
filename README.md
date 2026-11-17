# Bounded Delegation

**Dividing Context and Decision Between Humans and Coding Agents**
*A comparative review of agent-oriented development techniques and a research agenda for 2027*

Matheus Bastos Neves · Independent Researcher · [linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/)

A multivocal review of eleven agent-oriented development techniques (specification kits,
multi-agent methods, knowledge-base formats, code-as-specification workflows), comparing how
each structures and verifies the knowledge a coding agent needs. It finds that no technique
keeps an explicit architecture model current, that cognitive debt is a market-wide blind spot,
and that verification splits between checking prose and checking behaviour. From there it
proposes the **Bounded Delegation hypothesis**: delegating implementation to coding agents is
sustainable when, and only when, the delegation is bounded on both sides by artifacts humans
own — intent before the work, human-readable executable evidence after it — with both bounds
kept current by feedback. The paper states this as six falsifiable sub-hypotheses, an
evaluation agenda, and a contrast with the software engineering canon (Brooks, Sommerville,
Parnas, Naur, the Agile Manifesto).

- 🌐 **Landing page:** <https://mtheus.github.io/bounded-delegation/>
- 📝 **Blog summary:** [`article.md`](./article.md) (source) · [rendered page](https://mtheus.github.io/bounded-delegation/article.html)
- 📄 **Full paper:** [PDF](./paper/main.pdf) · [LaTeX source](./paper/main.tex) — this is the complete article (the one meant for arXiv and, later, JSERD)
- 📄 **arXiv preprint:** not yet submitted — see [`paper/README.md`](./paper/README.md). <!-- TODO(arxiv): replace with https://arxiv.org/abs/XXXX.XXXXX once published -->
- 🎓 **Future target venue:** [JSERD — Journal of Software Engineering Research and Development](https://journals-sol.sbc.org.br/index.php/jserd/) (SBC)
- 💼 **Author:** [linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/)

## Repository layout

```
.
├── article.md          short blog-style SUMMARY of the paper, for the website/socials
├── article.html         rendered, styled version of that summary, for GitHub Pages
├── index.html            landing page (abstract, findings, links) for GitHub Pages
├── .nojekyll             disables Jekyll processing — this is a hand-written static site
├── paper/
│   ├── main.tex           the FULL article — the one submitted to arXiv/JSERD
│   ├── main.pdf           compiled PDF (pdflatex, builds cleanly, 35 pages)
│   └── README.md          build and arXiv/JSERD submission instructions
└── LICENSE                CC0 1.0 (public domain)
```

**`paper/main.tex` is the canonical, complete article** — the thing that gets submitted to
arXiv and, later, adapted for JSERD. `article.md`/`article.html` are a *short, separate*
blog-post summary used to drive traffic to the full paper; they are not meant to contain the
full text. If you revise the argument, edit `paper/main.tex` first, then update the summary in
`article.md`/`article.html` only if the headline claims changed, and recompile `paper/main.pdf`.

## License

[CC0 1.0](./LICENSE) — public domain.
