**Human-Directed, AI-Executed Development Pipeline**

[简体中文](README.zh-CN.md)

A methodology for solo developers (or small teams) using LLM coding agents as the primary executor.

**Artifacts:**
- `SPEC.md` — permanent implementation spec. Types, structure, wiring patterns, milestones with verification protocols, constraints, known unknowns. The agent's single source of truth.
- `DECISIONS.md` — append-only decision log. Human seeds it from initial planning; agent appends during execution. One-line entries, categorized, milestone-scoped or project-scoped.
- `CHANGELOG.md` — append-only record of what was actually built. Agent writes after human verifies each milestone. Tracks deviations from SPEC.
- `todo.md` — disposable checklist scoped to one milestone. Only one exists at a time. Regenerated per milestone, deleted after completion.

**Process:**
1. **Plan** — human works through architecture, tradeoffs, and decisions (conversational or solo). Produces a PRD or equivalent for human reference.
2. **Translate** — convert planning into SPEC.md optimized for the agent: terse, typed, ordered, no narrative prose. Seed DECISIONS.md with initial choices.
3. **Execute in gated cycles:**
   - Generate `todo.md` for current milestone
   - Agent executes
   - Human verifies (each milestone has concrete pass/fail commands)
   - Agent appends CHANGELOG.md
   - Human course-corrects, generates next todo.md

**Principles:**
- **Separate thinking from execution artifacts.** PRD is for humans. SPEC is for the agent. Different audiences, different formats.
- **One concern per milestone.** If verification needs "and also check..." — split it.
- **Late binding.** Don't pre-generate all todos. Early execution informs later planning.
- **Negative constraints.** Tell the agent what never to do — prevents reasonable-but-wrong autonomous decisions.
- **Known unknowns.** Flag what's likely to go sideways and which milestone to investigate — primes the agent to research instead of assume.
- **Human at the gate, not at the wheel.** Verify outcomes and course-correct at seams. Don't micromanage code.