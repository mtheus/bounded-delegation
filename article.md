# Bounded Delegation: Dividing Context and Decision Between Humans and Coding Agents

*A comparative review of agent-oriented development techniques and a research agenda for 2027*

**Matheus Bastos Neves** · Independent Researcher
[linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/) · November 2026

*This is a short summary. Read the complete review, the full comparison tables, and the formal model in the [full paper](./paper/main.pdf) ([LaTeX source](./paper/main.tex)) — arXiv preprint coming soon.*

---

Coding agents now write most of the implementation in many teams, and a market of techniques has rushed in to tell them what a system is and what it should do: specification kits (GitHub Spec Kit, Kiro, OpenSpec, Tessl), multi-agent review methods (BMAD, AWS AI-DLC, Google's Elephant-Goldfish Model), knowledge-base formats (LLM Wiki, Open Knowledge Format, C4/arc42/ADRs), and code-as-specification workflows (Adam Tornhill's AI-first approach). We reviewed eleven of them against nine criteria — unit of knowledge, directory structure, verification, drift control, and more — and found three gaps no single technique closes.

## What the market gets wrong

**Intent is captured once and then forgotten.** Almost every technique records the *why* behind a change at delivery time, but only a few have any mechanism to keep that record current as the system evolves.

**Cognitive debt is a blind spot.** None of the eleven techniques measures whether the *team* still understands the system — only whether a document or a test exists.

**Verification is split into two disconnected worlds.** Prose-based techniques check that a specification is clear and complete. Tornhill's executable-test approach checks that behaviour is correct. No technique checks both, and none keeps an explicit architecture model across the whole system while doing it.

## The proposal: Bounded Delegation

> **The Bounded Delegation hypothesis.** Delegating implementation to coding agents is sustainable when, and only when, the delegation is bounded on both sides by artifacts that humans own: *intent* before the work (problem, domain language, decisions) and *evidence* after it (inspectable, executable scenarios and their results). What lies between the bounds can be written, read, and maintained by agents — provided the bounds are verified independently of their authors and kept current by feedback.

We operationalize this as **seven knowledge layers** (Problem, Domain, and Decisions as human-owned intent; Structure, Patterns, and Steps as the delegated path; Evidence as human-owned, agent-unwritable proof), **three roles** borrowed and extended from Google's Elephant-Goldfish Model (context-rich "elephants" draft, zero-context "goldfish" review, humans decide and must explain changes back in their own words), and an **eight-step increment cycle** with a feedback ring that routes drift signals back up through the layers. In one sentence: humans read intent and evidence; agents read and write the path between them.

## What has to change, and what doesn't

Measured against the software engineering canon — Brooks, Sommerville, Parnas, Naur, the Agile Manifesto — the fundamentals hold. What changes is the allocation of work: implementation becomes cheap and delegated, while specification and validation become the whole of the human job. Practices built to ration scarce programmer-hours (GitFlow, two-week sprints, velocity estimation, line-by-line review, release trains) lose their rationale once the scarce resource is human *attention* instead — while the principles beneath them (small batches, fast feedback, limited work in progress) matter more than ever.

## This is a hypothesis, not a result

None of this has been validated empirically. The full paper states six falsifiable sub-hypotheses (H1–H6), an evaluation agenda with concrete experimental designs for each, and a full threats-to-validity discussion — because a single-author, narrative review building a model to fit its own findings is exactly the kind of result that needs independent testing before anyone should trust it.

**Read the full paper** → [PDF](./paper/main.pdf) · [LaTeX source](./paper/main.tex) (arXiv preprint coming soon)
**Discuss** → [linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/)

---

## License

Released under [CC0 1.0](./LICENSE) — public domain.

## Citing this work

```bibtex
@misc{neves2026boundeddelegation,
  author = {Neves, Matheus Bastos},
  title  = {Bounded Delegation: Dividing Context and Decision Between Humans and Coding Agents},
  year   = {2026},
  note   = {Preprint},
  url    = {https://github.com/mtheus/bounded-delegation}
}
```
