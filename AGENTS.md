# Bounded Delegation — notes for agents

## What the study is for

The paper asks how humans and coding agents should divide reading and decision so that
delegating implementation stays sustainable. It reviews eleven agent-oriented techniques,
then proposes the **Bounded Delegation hypothesis** (H0): delegation is sustainable when it is
bounded by human-owned **intent** before the work and human-readable executable **evidence**
after it, both verified independently of their authors and kept current by feedback.
H0 splits into six falsifiable sub-hypotheses (H1–H6) with an evaluation agenda. The paper
reads the two bounds as **boundary objects** between people and agents, with agile
requirements engineering (user stories) as the nearest precedent.

Every claim beyond the review is a **conjecture to be tested**, not a finding. Keep that
framing in any text you write: hedge new claims, state the evidence type (peer-reviewed,
vendor, practitioner), and mark untested proposals as hypotheses.

## Source of truth

`paper/main.tex` is canonical. Every other copy is derived from it:

| Derived copy | How it follows `main.tex` |
|---|---|
| `paper/main.pdf` | `pdflatex` twice (see `paper/README.md`); expect zero errors and no undefined references |
| `article.html` | pandoc conversion plus the hand-finishing described in `paper/README.md` |
| `article.md` + `index.html` | the blog post: a short summary, mirrored between the two files |
| Claude Docs draft "Bounded Delegation: Dividing Context and Decision Between Humans and Coding Agents" | revision space for comments and suggestions; held by the author |

A change to the paper's argument lands in `main.tex` first, then propagates in the same commit
to the PDF, `article.html`, and — when the change alters the blog's message — both blog files.
Changes agreed in the Claude Docs draft are ported into `main.tex`; from that point the
`.tex` wins any disagreement.

## Gotchas

- Cite tables with `Table~\ref{...}`; table numbers in `main.tex` are automatic and differ from
  the lettered tables (A–F) in the Claude Docs draft.
- Section numbers are written literally in prose ("Section 7.4"); renumbering a section means
  searching for its literal references.
- `article.html` wraps paragraphs across lines, so match anchors with flexible whitespace and
  curly quotes.
