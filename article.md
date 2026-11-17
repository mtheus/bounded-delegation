# Why AI Coding Agents Are Breaking Software Engineering (And What to Do About It)

**Matheus Bastos Neves** · Independent Researcher
[linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/) · November 2026

## 1. Introduction: The AI Productivity Trap

We are living through a strange paradox in modern software engineering. AI coding agents are writing code with incredible fluency, boosting individual developer speed by over 50% on targeted implementation tasks. Yet, across engineering organizations, team-level outcomes tell a dawning, uncomfortable story. Engineering leaders report rising delivery instability, skyrocketing pull-request review times, and little to no measurable improvement in company-level business metrics.

For the past two years, the tech industry operated under the assumption that generative AI tools would resolve software engineering bottlenecks by automating line-by-line implementation. In reality, flooding repositories with machine-generated code has exposed a much deeper architectural issue: the rapid breakdown of human context, decision-making clarity, and structural software health. As coding agents generate lines of code faster than human teams can process them, engineering leaders must recognize that code generation is no longer the rate-limiting step — and fundamentally reshape their software development lifecycle.

## 2. Takeaway 1: Verification, Not Generation, Is the New Bottleneck

Empirical research across thousands of software developers reveals a stark discrepancy between individual speed and team delivery. Controlled experiments (Peng et al., 2023) show individual developers completing tasks 55.8% faster with AI assistance. However, organizational research by DORA (2025/2026) highlights that while high AI adoption correlates with increased task throughput, it simultaneously brings higher overall delivery instability.

Telemetry from Faros AI (2025–2026), analyzing over 22,000 developers across 1,255 teams, reveals the mechanical breakdown of this trap:

- Merged pull request (PR) volume per developer grew by 98%, accompanied by a 154% increase in PR size and a 9% increase in bugs per developer.
- Review time skyrocketed: the median time a PR spends in review rose by an astounding 441%.
- Rubber-stamping proliferated: 31% of pull requests were merged with no human review at all.

This breakdown is exacerbated by cognitive surrender (Shaw & Nave, 2026) — the psychological phenomenon where humans adopt AI-generated output with minimal scrutiny, leading to inflated confidence even when outputs contain hidden flaws or security vulnerabilities (Veracode benchmarked over 100 LLMs and found 45% of generated code samples introduced known security weaknesses).

Nowhere is this perception gap more starkly demonstrated than in a landmark trial by METR (2025/2026). When experienced maintainers worked on tasks in their own mature repositories, tasks actually took 19% longer with AI assistance. Yet, the developers had forecast a 24% speedup beforehand and afterwards still believed they had been 20% faster. Developers feel significantly faster while delivery actually slows down.

The emerging consensus among top industry practitioners — including Andrej Karpathy, Dave Farley, and Boris Cherny — is unanimous. As Dave Farley succinctly frames it:

> "Verification, not generation, is the new constraint in software engineering. In current workflows, the AI generates and the human verifies; because no human can read thousands of generated lines carefully enough to maintain true ownership, trust must come from executable specifications and continuous automated verification rather than manual code inspection."

When developers are tasked with inspecting thousands of machine-generated lines diff-by-diff, cognitive fatigue sets in. Line-by-line human code review becomes physically impossible at scale, forcing teams into a binary failure mode: either PR queues stall indefinitely or engineers rubber-stamp unverified, fragile code straight into production.

## 3. Takeaway 2: Technical Debt Is Falling, but Cognitive and Intent Debt Are Exploding

To understand why AI causes codebase instability despite writing superficially clean code, we must turn to Dr. Margaret-Anne Storey's Triple Debt Model (2026). Storey divides software debt into three distinct structural layers:

1. **Technical Debt**: code and structural defects that limit how easily a system can be modified.
2. **Cognitive Debt**: the erosion of shared mental models, domain intuition, and architectural understanding held by human developers about the system.
3. **Intent Debt**: the absence of recorded goals, constraints, domain definitions, and design rationale that both humans and agents can consult over time.

```
          ┌─────────────────────────────────────────┐
          │               INTENT DEBT                │
          │   (Missing rationale, goals & context)   │
          └────────────────────┬──────────────────────┘
                                │
                                ▼
          ┌─────────────────────────────────────────┐
          │              COGNITIVE DEBT              │
          │   (Erosion of human mental models)       │
          └────────────────────┬──────────────────────┘
                                │
                                ▼
          ┌─────────────────────────────────────────┐
          │              TECHNICAL DEBT              │
          │   (Code & structural defects)            │
          └─────────────────────────────────────────┘
```

While AI agents reduce technical debt by making boilerplate creation and superficial refactoring frictionless, they dramatically accelerate cognitive and intent debt. The core mechanism is straightforward: coding agents start every single session with zero tacit context about the system. Whatever business rationale, historical trade-offs, or architectural constraints are not explicitly recorded in written artifacts, the agent infers. It fills in the blanks by generating code that is syntactically correct, passes basic checks, and is structurally misaligned with unwritten domain rules.

This reality underscores Peter Naur's seminal 1985 insight:

> "Programming is theory building: the code is only the visible trace of an understanding held by the people who wrote it, and when that understanding is lost the program begins to die even if the code is intact."

When teams attempt to bridge this gap by prompting generative AI to auto-generate documentation, they suffer from what Storey terms the automation of understanding. Generating artifacts without human cognitive effort creates a dangerous illusion of documented knowledge while systematically destroying the human mental model required to maintain the software.

To diagnose cognitive debt before system collapse, engineering leaders must monitor concrete diagnostic signals rather than lines written:

- **Onboarding time to first unassisted PR**: how long it takes a new engineer to safely deliver changes.
- **Knowledge concentration**: the degree to which commit history and domain comprehension are locked in a single individual.
- **Approver explain-back capacity**: whether a human reviewer can explain, in their own words, the architectural impact of a change at a human approval gate.

## 4. Takeaway 3: Stop Reading Implementation Code — Adopt "Bounded Delegation"

To break out of the verification bottleneck, software teams must redefine the boundary between human responsibilities and machine tasks. Matheus Bastos Neves (2026) formalizes this structural solution in the Bounded Delegation hypothesis (H₀):

> **The Bounded Delegation Hypothesis (H₀):** Delegating implementation to coding agents is sustainable if, and only if, delegation is bounded on one side by human-owned Intent (problem statement, domain language, architectural decisions) and on the other side by human-readable Evidence (executable scenarios and test results).

```
   HUMAN BOUND                    DELEGATED PATH                   HUMAN BOUND
┌───────────────────┐        ┌───────────────────┐        ┌───────────────────┐
│   HUMAN INTENT     │ ─────▶ │   CODING AGENT     │ ─────▶ │  HUMAN EVIDENCE    │
│ (Problem, Domain,  │        │ (Implementation    │        │  (Executable       │
│  ADRs)             │        │  Code)              │        │   Tests)           │
└───────────────────┘        └───────────────────┘        └───────────────────┘
```

Under Bounded Delegation, software engineering knowledge is structured across **Seven Knowledge Layers**:

1. **Problem** (Intent Bound — Human Owned): problem statement, target user, constraints, and success criteria.
2. **Domain** (Intent Bound — Human Owned): ubiquitous business language, term by term.
3. **Decisions / ADRs** (Intent Bound — Human Owned): Architectural Decision Records with machine-checkable assertions.
4. **Structure** (Delegated Path): a C4 architecture model linked to co-located component contracts.
5. **Patterns** (Delegated Path): recurring implementation designs and workflow steps.
6. **Steps** (Delegated Path): active increments with delta specifications over the layers above.
7. **Evidence** (Evidence Bound — Human Owned): inspectable executable scenarios, architecture assertions, and automated evaluation suites.

Humans own the bounds (Layers 1–3 and Layer 7). Agents read, write, and maintain the implementation path between them (Layers 4–6). Humans stop spending hours reading raw implementation diffs line-by-line; instead, they verify that the evidence satisfies the intent.

### Comparing Test Specs: Raw Agent Output vs. Domain-Inspectable Evidence

Inspired by Adam Tornhill's AI-first workflow, executable evidence must be written in high-level domain language so human experts can verify system behavior at a glance without reading lower-level implementation details.

**Obscure agent-generated test** (obscures intent, hard for humans to verify):

```kotlin
@Test fun reschedule() {
  val r = http.post("/appointments/42/reschedule", """{"slotId": 7}""")
  assertEquals(200, r.status)
  assertEquals("TAKEN", db.query("select status from slot where id=7"))
  assertEquals(1, db.count("outbox where type='AppointmentRescheduled'"))
}
```

**Inspectable domain-specific scenario** (human-readable evidence):

```kotlin
@Test fun `patient reschedules and the old slot becomes free`() {
  val appointment = appointmentBooked(at = slot("Tue 9am"))
  val result = patient.reschedules(appointment, to = slot("Thu 2pm"))

  result.shouldSucceed()
  slot("Tue 9am").shouldBeFree()
  slot("Thu 2pm").shouldBeTakenBy(appointment)
  reminders.shouldAnnounceRescheduling(appointment)
}
```

### Enforcing Safety via Physical Suite Locking

A primary failure mode of autonomous agents is "cheating" — altering test assertions or deleting failing tests to make low-quality implementation code pass.

Under Bounded Delegation, suite locking is not a prompt-level request; it is physically enforced via CI/CD boundary permissions and file-system access control. The agent service account is granted read-write access to implementation paths (`src/`), but strictly read-only access to the acceptance suite (`tests/acceptance/`). The agent must write implementation code until the locked suite passes, without any ability to modify the evidence bounds.

## 5. Takeaway 4: Traditional Agile Practices Are Losing Their Rationale

Over the past twenty years, software methodologies like Scrum, GitFlow, and SAFe were engineered around one core constraint: rationing expensive human programmer hours. In Fred Brooks's classical framework (*No Silver Bullet*), engineering effort is divided between essential complexity (the domain problem and architectural design) and accidental complexity (syntax, compilation, boilerplate, and typing).

Coding agents represent the ultimate tool for eliminating accidental complexity. Because machine execution time is now virtually free, software delivery is shifting from capacity-constrained planning to attention-constrained queueing.

```
TRADITIONAL AGILE: Capacity-Constrained Planning
┌──────────────────┐     ┌──────────────────┐     ┌──────────────────┐
│  Developer Hours │ ──▶ │ Sprint Capacity  │ ──▶ │  Story Points    │
└──────────────────┘     └──────────────────┘     └──────────────────┘

AGENT-ERA FLOW: Attention-Constrained Queueing
┌──────────────────┐     ┌──────────────────┐     ┌──────────────────┐
│ Human Attention  │ ──▶ │  Decision & Gate │ ──▶ │ Flow of Bounded  │
│    Bandwidth     │     │    WIP Limits    │     │    Increments    │
└──────────────────┘     └──────────────────┘     └──────────────────┘
```

When human decision-making bandwidth — not typing capacity — is the bottleneck, 20-year-old process rituals lose their core rationale:

| Traditional Engineering Practice | Agent-Era Replacement | Structural Rationale |
|---|---|---|
| **Sprints & Velocity Estimation** (forecasts human capacity in 2-week boxes) | Flow Based on Pending Decision WIP Limits | Machine execution time is variable and near-zero; throughput is bounded strictly by human decision bandwidth. |
| **GitFlow / Long-Lived Feature Branches** (isolates slow human coding cycles) | Trunk-Based Flow with Ephemeral Workspaces | Parallel agents create massive integration debt; single-trunk integration behind feature flags avoids merge stalls. |
| **Line-by-Line Human Code Review** (human inspection of all implementation diffs) | Boundary Reading & Automated Pipeline Gates | Humans review domain scenarios, ADRs, and contracts; deterministic CI thresholds review syntax and health metrics. |
| **Multi-Stage Hand-Off Boards** (staged movement across Dev → QA → Review) | Automated Pipeline Gates + Human Decision Queues | Hand-offs between specialists decay context; agents run pipelines, presenting human gates with clear decision queues. |
| **Release Trains & Quarterly Planning** (synchronizes cross-team human dependencies) | Continuous Deployment with Contract Enforcement | Cross-team coordination shifts to machine-checked contracts, policy files, and flag-based rollouts. |

Core Agile values — such as customer collaboration and delivering working software — remain fully intact. However, operational tools like story points, velocity metrics, and time-boxed sprints lose their purpose when machine implementation takes minutes, shifting the central challenge entirely to managing human review queues.

## 6. Takeaway 5: Code Health Matters More for Machines Than It Ever Did for Humans

A common misconception in the age of generative AI is that "clean code" no longer matters because humans rarely read implementation details. Empirical research demonstrates the exact opposite.

Borg et al. (2026) evaluated LLM refactoring across 5,000 Python files and proved that code engineered for human comprehension (characterized by low cyclomatic complexity, clear module boundaries, and high cohesion) is modified significantly more safely by AI agents. Machine reasoning degrades rapidly when context windows are overloaded with convoluted logic.

### Architectural Patterns for Context-Window Isolation

David Parnas's classic principles of modular design (1972) and information hiding serve as essential context-isolation barriers for LLM context windows. Modern architects must adopt two explicit patterns:

1. **Deep Modules** (Ousterhout, 2021): systems should be composed of deep modules that provide simple, narrow interfaces while hiding complex implementation details behind the boundary. Deep modules allow an agent to modify internal code without needing to pull thousands of lines of external context into its context window.
2. **Co-Located README Contracts** (EGM "Peanuts and Hay"): following Google's Elephant-Goldfish Model, every leaf code directory contains a co-located `README.md` defining component interfaces, invariants, and side effects. Parent directory READMEs roll child contracts up into high-level system maps. An agent touching a directory reads its local contract immediately without searching the repository.

```
src/
├── scheduling/
│   ├── README.md                 <-- Component Contract (Interface, Invariants)
│   ├── AppointmentService.kt
│   └── SlotManager.kt
└── notifications/
    ├── README.md                 <-- Component Contract
    └── ReminderNotifier.kt
```

### Shifting Design Trade-Offs

To optimize for both human understanding and agent reasoning, software architects must recalibrate classic code patterns:

- **Reduce micro-abstractions**: extreme micro-abstractions — such as forcing an interface for every single class, creating layer-by-layer DTO mappers across dozens of directories, or splitting simple logic across tiny single-method files — consume context tokens unnecessarily and force agents into excessive multi-file hopping.
- **Strengthen macro-architecture**: enforce strict Clean Architecture dependency boundaries (domain code never depends on infrastructure), vertical domain slicing, and machine-checkable architecture assertions (e.g., using ArchUnit to block boundary violations in CI).

## 7. Conclusion: The Scarce Resource Is Human Attention

The role of the software engineer is not vanishing; it is shifting decisively upstream and downstream:

- **Upstream**: defining domain language, framing business constraints, capturing architectural decision records (ADRs), and bounding system intent.
- **Downstream**: designing domain-executable scenarios, establishing automated code health gates, and evaluating real-world system behavior.

Implementation in the middle is increasingly delegated to autonomous agents operating within strictly bounded constraints. Engineering leaders who attempt to scale teams by simply generating more lines of code will find themselves drowning in review delays, security vulnerabilities, and compounding cognitive debt.

### Measuring Debt Before System Collapse

Before scaling agent workflows, engineering organizations must establish concrete diagnostic proxies to measure cognitive and intent debt across their repositories:

1. **Onboarding Velocity**: measure the time required for new engineers to deliver their first unassisted production change.
2. **Explain-Back Capacity**: conduct periodic spot-checks at human decision gates requiring approvers to explain the structural impact of a change without reading the implementation diff.
3. **Knowledge Dispersion**: analyze commit history to ensure system context is distributed across the team rather than isolated in single individuals or machine-generated blobs.

### A Question for Engineering Leaders

As autonomous coding agents take over daily implementation in your repositories, what concrete mechanisms does your engineering organization have in place to measure and manage cognitive debt before the shared theory of your system disappears entirely?

---

This essay sketches the idea. The full academic treatment — a multivocal review of eleven agent-oriented development techniques, the formal Bounded Delegation model with six falsifiable sub-hypotheses, and a contrast with the software engineering canon — is written up as a separate paper, free to read online.

**Read the full academic review** → [HTML](./article.html) · [PDF](./paper/main.pdf)
**Discuss** → [linkedin.com/in/matheusbn](https://www.linkedin.com/in/matheusbn/)

---

## License

Released under [CC0 1.0](./LICENSE) — public domain.
