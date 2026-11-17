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
- 📖 **Full paper (read online):** <https://mtheus.github.io/bounded-delegation/article.html>
- 📄 **LaTeX source / PDF:** [`paper/main.tex`](./paper/main.tex) · [`paper/main.pdf`](./paper/main.pdf)
- 🗄️ **HAL:** <!-- TODO(hal): add the HAL deposit URL here --> *(link coming soon)*
- 📝 **Short summary:** [`article.md`](./article.md)
- 💼 **Author:** [linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/)

## Repository layout

```
.
├── article.md          short blog-style summary, for the website/socials
├── article.html         the FULL paper, converted to HTML for free online reading
├── index.html            landing page (abstract, findings, links) for GitHub Pages
├── .nojekyll             disables Jekyll processing — this is a hand-written static site
├── paper/
│   ├── main.tex           the FULL article in LaTeX — the canonical source
│   ├── main.pdf           compiled PDF (pdflatex, builds cleanly, 36 pages)
│   └── README.md          build instructions
└── LICENSE                CC0 1.0 (public domain)
```

**`paper/main.tex` is the canonical, complete article.** `article.html` is a full HTML
conversion of it (via pandoc, hand-finished) meant to be read freely in a browser, with no
paywall or submission gate; `article.md` stays a short summary for social sharing. If you
revise the argument, edit `paper/main.tex` first, then regenerate `article.html` and
`paper/main.pdf`, and update `article.md`'s summary only if the headline claims changed.

## License

[CC0 1.0](./LICENSE) — public domain.
