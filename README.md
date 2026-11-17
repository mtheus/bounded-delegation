# Bounded Delegation

**Why AI Coding Agents Are Breaking Software Engineering (And What to Do About It)**

Matheus Bastos Neves · Independent Researcher · [linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/)

AI coding agents write code fast, but team-level delivery is getting less stable: review
queues are growing, pull requests are bigger and less reviewed, bug rates are rising.
Verification, not generation, is the bottleneck now. This repo holds two things:

- A **blog post** making that case in plain language, and introducing the **Bounded Delegation
  Hypothesis**: delegating implementation to coding agents is sustainable only when the
  delegation is bounded on both sides by artifacts humans own — intent before the work, and
  human-readable executable evidence after it.
- The **full academic paper** behind it: a multivocal review of eleven agent-oriented
  development techniques, a formal model with six falsifiable sub-hypotheses, a reading of its two bounds as
  boundary objects (building on agile requirements engineering), an evaluation
  agenda, and a contrast with the software engineering canon (Brooks, Sommerville, Parnas,
  Naur, the Agile Manifesto).

- 🌐 **Read the blog post:** <https://mtheus.github.io/bounded-delegation/>
- 📖 **Read the full paper:** <https://mtheus.github.io/bounded-delegation/article.html> · [PDF](./paper/main.pdf)
- 💼 **Author:** [linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/)

## Repository layout

```
.
├── index.html            the blog post, for GitHub Pages (homepage)
├── article.md             the same blog post, in Markdown (for GitHub browsing/social sharing)
├── article.html            the FULL academic paper, converted to HTML for free online reading
├── .nojekyll               disables Jekyll processing — this is a hand-written static site
├── paper/
│   ├── main.tex             the full academic paper — the canonical source
│   ├── main.pdf             compiled PDF (builds cleanly, 41 pages)
│   └── README.md            build instructions
└── LICENSE                  CC0 1.0 (public domain)
```

`index.html` and `article.md` are the same blog post in two formats; edit one, then mirror the
change in the other. `article.html` is a separate, full HTML conversion of `paper/main.tex` —
the actual academic paper, not the blog post. If you revise the paper's argument, edit
`paper/main.tex` first, then regenerate `article.html` and `paper/main.pdf`.

## License

[CC0 1.0](./LICENSE) — public domain.
