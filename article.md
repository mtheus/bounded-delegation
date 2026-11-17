# Why AI Coding Agents Are Breaking Software Engineering (And What to Do About It)

**Matheus Bastos Neves** · Independent Researcher
[linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/) · November 2026

*This is a short summary of the full paper. Read the complete argument, data, and the formal Bounded Delegation framework in the [LaTeX source](./paper/main.tex) (soon on arXiv).*

---

AI coding agents are writing code with incredible fluency, boosting individual developer speed by over 50% on targeted tasks. Yet across engineering organizations, delivery is getting *less* stable: review queues are growing, pull requests are getting bigger and less reviewed, and bug rates are rising. The industry bet that generative AI would resolve software engineering bottlenecks by automating implementation. It didn't — it just moved the bottleneck.

## Verification, not generation, is the new constraint

Controlled experiments show individual developers completing tasks over 50% faster with AI assistance. But organizational telemetry tells a different story: PR volume and size are up, median review time has risen by hundreds of percent, and a meaningful share of pull requests now merge with no human review at all. In a landmark trial, experienced maintainers working in their own mature repositories actually took *longer* with AI assistance — while still believing, afterward, that they had been faster. No human can read thousands of AI-generated lines carefully enough to maintain true ownership. Trust has to come from executable specifications and automated verification, not manual line-by-line review.

## Three kinds of debt — and AI only pays down one of them

Software debt isn't one thing. **Technical debt** is defects in the code itself. **Cognitive debt** is the erosion of the shared mental models developers hold about a system. **Intent debt** is the absence of recorded goals, constraints, and design rationale. AI agents are good at reducing technical debt — boilerplate and superficial refactors become frictionless. But because every agent session starts with zero tacit context, agents fill unrecorded rationale with guesses, quietly piling up cognitive and intent debt even as the code looks clean.

## The fix: Bounded Delegation

> **The Bounded Delegation Hypothesis (H₀):** Delegating implementation to coding agents is sustainable if, and only if, delegation is bounded on one side by human-owned **Intent** (problem statement, domain language, architectural decisions) and on the other side by human-readable **Evidence** (executable scenarios and test results).

In other words: stop reading implementation diffs. Humans own the *why* (problem, domain, architectural decisions) and the *proof* (executable, domain-readable test scenarios). Agents own everything in between — structure, patterns, and the implementation steps — within a path whose two ends are locked by humans. The full paper formalizes this as **seven knowledge layers**, three owned by humans (Problem, Domain, Decisions/ADRs) plus a fourth human-owned layer at the far end (Evidence), with the delegated path (Structure, Patterns, Steps) in between — and shows how to enforce it physically, e.g. by giving agents read-write access to `src/` but read-only access to the acceptance test suite.

## Everything downstream of that changes

If human decision bandwidth — not typing speed — is the bottleneck, twenty-year-old Agile rituals built to ration scarce programmer hours (sprints, velocity, GitFlow, line-by-line review, hand-off boards) lose their rationale and get replaced by flow-based, decision-gated, boundary-reading practices. And "clean code" matters *more*, not less, in this world: deep modules and co-located README contracts keep an agent's context window small enough to reason safely, while convoluted, over-abstracted code degrades machine reasoning just as it degrades human reasoning.

## The scarce resource is human attention

The software engineer's role isn't vanishing — it's moving upstream (domain language, constraints, ADRs) and downstream (executable scenarios, code health gates, real-world evaluation), while implementation in the middle is delegated within strict bounds. The full paper closes with concrete diagnostics — onboarding velocity, explain-back capacity at approval gates, knowledge dispersion — that engineering leaders can use to catch cognitive and intent debt before it causes system-level collapse.

**Read the full paper** → [`paper/main.tex`](./paper/main.tex) (LaTeX source; arXiv preprint coming soon) · **Discuss** → [linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/)

---

## License

Released under [CC0 1.0](./LICENSE) — public domain.

## Citing this work

```bibtex
@misc{neves2026boundeddelegation,
  author = {Neves, Matheus Bastos},
  title  = {Why AI Coding Agents Are Breaking Software Engineering (And What to Do About It)},
  year   = {2026},
  note   = {Preprint},
  url    = {https://github.com/mtheus/bounded-delegation}
}
```
