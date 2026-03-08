# Stack Skills

<p align="right">
  <a href="README.md">English</a> · <a href="README.ko.md">한국어 (Korean)</a>
</p>

**5 cognitive firewalls for your AI coding agent.**

Each one defends against a specific reasoning failure — hallucination, anchoring bias, confirmation bias, black-box logic, and blind optimism.

```
npx skills add whynowlab/stack-skills --all
```

> Built for [Claude Code](https://claude.com/claude-code) | Compatible with AI agents via [Agent Skills](https://agentskills.io) open standard
> Created by [@thestack_ai](https://github.com/whynowlab)

---

## The Problem

Your AI writes code fast. But it reasons poorly.

Ask it to choose a database — it says "use PostgreSQL." The safe default, every time.

Ask it to review your architecture — it says "looks good." Agreeing is easier than thinking.

Ask it to research a claim — it makes up a plausible answer you can't distinguish from fact.

Ask it why it recommends something — it gives you a conclusion with no visible reasoning chain.

Ask it what could go wrong — it lists generic risks that apply to everything and nothing.

**These are five distinct reasoning failures. Stack Skills installs a firewall against each one.**

---

## Five Failures, Five Firewalls

| Cognitive Failure | What Happens | Firewall | What It Forces |
|:---|:---|:---|:---|
| **Hallucination** | AI states claims without verification | `cross-verified-research` | Source-traced, cross-verified claims with S/A/B/C tier grading |
| **Anchoring bias** | AI locks onto the first "obvious" answer | `creativity-sampler` | 5 probability-weighted options including unconventional alternatives |
| **Confirmation bias** | AI agrees with you instead of challenging | `adversarial-review` | Steel-man then 3-vector attack. "Looks good" is structurally banned |
| **Black-box reasoning** | AI gives conclusions without showing why | `reasoning-tracer` | Visible assumption inventory, confidence decomposition, weakest-link analysis |
| **Optimism bias** | AI assumes the plan will work | `pre-mortem` | Assumes failure, identifies 5 specific failure scenarios with circuit breakers |

---

## Skills

### cross-verified-research

4-stage verified research pipeline with anti-hallucination safeguards.

```
Deconstruct → Search & Collect → Cross-Verify → Synthesize
```

- Every claim must be traced to a specific, citable source — or labeled `Unverified`
- Source tiering: S (academic/specs), A (official docs), B (community — flagged), C (general)
- Cross-verification: key claims require 2+ *independent* sources (same-origin rewrites don't count)
- Adaptive depth: narrow questions get 2-3 queries, broad landscape gets 8+

```
Try: /cross-verified-research Is gRPC better than REST for mobile backends?
```

### creativity-sampler

Probability-weighted option generator that breaks anchoring bias.

- 5 options by default, each assigned a typicality zone (Conventional → Wild card)
- At least 1 option from the unconventional or wild card zone — ideas your AI normally suppresses
- **Hidden Assumptions** section exposes *why* the obvious answer seems obvious
- Decision matrix with criteria derived from your stated constraints + 1 hidden criterion you didn't consider

```
Try: /creativity-sampler Which database for a real-time leaderboard?
```

### adversarial-review

Structured Devil's Advocate that finds real problems, not nitpicks.

- **Steel-man first**: articulates the strongest case FOR the current approach before attacking
- **3 independent vectors**: Logical Soundness / Edge Case Assault / Structural Integrity
- Severity classification: Critical (must fix) / Major (should fix) / Minor / Note
- Every Critical and Major finding includes a counter-proposal with trade-off analysis
- Explicit verdict thresholds: any unmitigated Critical = FAIL

```
Try: /adversarial-review We chose Kubernetes for our 3-person startup
```

### reasoning-tracer

Makes AI reasoning visible, auditable, and decomposable.

- **Assumption inventory**: every assumption numbered, rated for criticality and verifiability
- **Decision tree**: at each reasoning fork, what alternative was considered and why it was rejected
- **Confidence decomposition**: overall confidence broken into sub-components with justifications
- **Weakest link**: which single assumption, if wrong, would most change the conclusion
- **Alternative conclusion**: "If [weakest assumption] is wrong, then the answer changes to [X]"

```
Try: /reasoning-tracer Why do you recommend microservices for this project?
```

### pre-mortem

Prospective failure analysis — assumes your plan failed and works backward.

- "It is 6 months from now. This failed completely. What went wrong?"
- 5 failure scenarios across categories: Technical / Organizational / External / Temporal / Assumption
- Likelihood x Impact matrix → focus on top 3 risks
- **Leading indicators**: measurable early-warning signals for each top risk
- **Circuit breakers**: specific trigger conditions for when to stop and pivot

```
Try: /pre-mortem We're migrating our monolith to microservices over Q3
```

---

## Which Skill Should I Use?

| Your situation | Skill | Why |
|:--------------|:------|:----|
| Researching a technology or verifying a claim | `cross-verified-research` | Source-traced verification prevents hallucination |
| Choosing between options (DB, framework, architecture) | `creativity-sampler` | Breaks anchoring, surfaces unconventional alternatives |
| Made a decision, want to stress-test it | `adversarial-review` | Finds real flaws through structured adversarial analysis |
| Want to understand WHY the AI recommends something | `reasoning-tracer` | Makes assumptions and reasoning chain auditable |
| Planning a project and want to de-risk it | `pre-mortem` | Identifies specific failure modes before they happen |

### Recommended Chains

- **Tech Decision**: `creativity-sampler` → `cross-verified-research` → `adversarial-review`
- **Architecture Review**: `reasoning-tracer` → `adversarial-review`
- **Project Kickoff**: `pre-mortem` → `creativity-sampler` (for mitigations)
- **Full Rigor**: `creativity-sampler` → `cross-verified-research` → `adversarial-review` → `pre-mortem`

---

## How They Work Together

```
Your AI's default reasoning:

  [Question] ──→ [First plausible answer] ──→ [Ship it]


With Stack Skills:

  [Question]
       │
       ├──→ creativity-sampler ──→ "What are ALL the options?"  (breaks anchoring)
       │
       ├──→ cross-verified-research ──→ "Is this actually true?"  (blocks hallucination)
       │
       ├──→ reasoning-tracer ──→ "WHY do I believe this?"  (exposes assumptions)
       │
       ├──→ adversarial-review ──→ "What's WRONG with this?"  (kills confirmation bias)
       │
       └──→ pre-mortem ──→ "HOW will this FAIL?"  (counters optimism bias)
```

Each firewall is independent — use one, or chain them.

---

## Benchmark: Baseline vs Stack Skills

Informal comparison using Claude Opus. Scores are subjective quality ratings (1-10) by the author. We share these to illustrate the *type* of improvement. Your results will vary.

| Scenario | Baseline | Stack Skills | Change |
|:---------|:--------:|:-----------:|:------:|
| Research: "Is SQLite viable for 1000 concurrent users?" | 5/10 | 9/10 | **+80%** |
| Decision: "Which state management for React e-commerce?" | 5/10 | 9/10 | **+80%** |
| Review: "Single PostgreSQL for OLTP + analytics?" | 4/10 | 8/10 | **+100%** |

**What changed:**
- **Research**: Baseline said "use PostgreSQL." With cross-verified-research, it found 1000 concurrent users = ~30 concurrent writes = 120x headroom for SQLite. Completely different conclusion, backed by cited benchmarks.
- **Decision**: Baseline said "use Zustand." With creativity-sampler, it discovered that *where* you store the cart (server vs client) matters more than *which* library you pick. A better question, not just a better answer.
- **Review**: Baseline listed 4 generic concerns. With adversarial-review, it found a Critical multi-tenant data leakage via analytics queries — and provided the RLS fix with SQL.

> We welcome community benchmarks — please open an issue with your own before/after comparisons.

---

## Install

### Quick Install (npx)

```bash
npx skills add whynowlab/stack-skills --all
```

### Individual Skills

```bash
npx skills add whynowlab/stack-skills/cross-verified-research
npx skills add whynowlab/stack-skills/adversarial-review
npx skills add whynowlab/stack-skills/creativity-sampler
npx skills add whynowlab/stack-skills/reasoning-tracer
npx skills add whynowlab/stack-skills/pre-mortem
```

### Manual

```bash
git clone https://github.com/whynowlab/stack-skills.git
cp -r stack-skills/skills/* ~/.claude/skills/
```

### Per-Project

```bash
cp -r stack-skills/skills/adversarial-review .claude/skills/
```

---

## Compatibility

| Platform | Status |
|:---------|:-------|
| Claude Code | Fully supported |
| Cursor | Compatible (Agent Skills standard) |
| GitHub Copilot | Compatible (Agent Skills standard) |
| Codex CLI | Compatible (Agent Skills standard) |

---

## License

MIT License. See [LICENSE](LICENSE).

---

**Stack Skills** by [@thestack_ai](https://github.com/whynowlab) — 5 cognitive firewalls for your AI.
