# Worked example — single-author exploration, no decision

What most parleys actually look like: **one person + the agent, working a hard problem, reaching
no decision** — and obviously worth handing to a colleague. (Decisions are just one thing
thinking sometimes produces.) This is the artifact after turn 1, paused at an open fork. Use it
to ground the v0.4 schema and the voice.

~~~markdown
# Per-PR preview environments — worth it, and how?
status: paused
turn: 1 · last updated: 2026-06-25 by Sam
built with: parley v0.4
target: open exploration — no fixed decision. Should this app get a preview environment per
        open PR, and if so the cheapest shape that delivers the value? Paused at one open fork.
participants: Sam (Eng Lead), Parley (participant + guide — never routed to)

> ▶ **Picking this up? Start here.** Short version: build per-PR previews on the *shared-infra*
> model, start simple, keep a clean seam to tighten later. One fork is genuinely open. You can:
> (a) agree & move on — *heads up, you'd be signing past 4 open forks, one untouched*;
> (b) just the bottom line (the Synthesis); (c) walk me through how we got here; (d) jump to any
> fork in the Branch Map and run with it.

## Decision Target
Open exploration. Do per-PR preview envs earn their keep here, and what's the cheapest shape?
No decision is forced; it deliberately paused before deciding access control.

## Synthesis (Parley's current read)
**My read: build it, shared-infra model, simplest data isolation with a clean seam to tighten
later.** Strong fit — designers with repo access will want a live place to try per-PR work. The
load-bearing insight: the two viable isolation options are the *same architecture*, differing
only by one `DATABASE_URL`, so moving between them is additive and free. Ship the shared-DB
version; flip to per-PR-DB the day two people stomp each other's content.

*Reasoning trail:* when Sam asked **which direction is cheaper to change later** (not "which is
right"), that reframed the question and surfaced the same-architecture insight; when Sam scoped
**demos out**, that fixed this as a low-blast-radius internal tool — which is what makes shared
infra defensible.

## Statement Log
- [T1 · Sam] Audience: design/content review + eng integration testing. **Not** client demos.
  *"Option 3 is probably fine given how small the team is — but we could change our minds."*
- [T1 · Sam] *standing position:* a full per-PR stack (own CDN/LB/DB per PR) is off the table —
  too slow/costly. If a later participant reopens it, this is Sam's pre-authored objection.
- [T1 · Parley] *reasoning entry:* pushed back on treating this as a foregone good idea — flagged
  that payoff waits for the real app and that naive full cloning is the standard failure mode.
  **Why:** the value is real but conditional. **What it caused:** Sam narrowed the audience and
  signaled comfort with the cheapest option, which set up the direction-of-travel question.

## Open Questions
- [ ] Access control — public vs. protected preview URLs? Nobody has taken a position. — posed to: open
- [x] Which isolation *direction* is cheaper to change later? — answered T1: shared → per-PR-DB
      (purely additive, no infra rebuild).

## Branch Map — roads not taken & anticipated forks
- **Full per-PR isolation — closed by Sam's standing position.** Leads to max prod-parity but
  ~20–40 min standup/teardown + recurring cost. *If reopened:* surface Sam's objection **as
  Sam's**, then let them argue it — closed, not welded.
- **Access control: protected vs. public — genuinely open.** *My own read (a labeled guess):*
  protected likely wins given pre-launch content — but present both honestly; don't herd.
- **Lifecycle triggers — open.** Auto-on-PR-open vs. label-gated. *Anticipate:* cost pushes
  label-gated, developer-experience pushes auto.

## Parked Tensions
- Build-now vs. premature — the plumbing is worth building before the real app exists, but the
  payoff waits for the app. Held, not resolved.
~~~

What this example demonstrates:
- **Single author + agent, no decision** — and plainly valuable to hand off. The value is
  transmit → inhabit → extend, not reaching consensus.
- **Decision-first menu** (the ▶ block): the recipient picks a door — agree (with disclosure) /
  bottom line / walk it / jump to a fork — instead of being force-marched through a recap.
- **Reasoning entry + reasoning trail:** the agent's *own* thinking is captured (what it offered,
  why, what it caused; what moved the read), so a cold successor can replay the expert — not just
  inherit conclusions.
- **Branch Map:** roads not taken and anticipated forks, in the agent's voice — a labeled guess
  marked as the agent's, a *standing position* delivered as Sam's, facilitation intent if a fork
  reopens. This is what lets a later reader **extend** down a path Sam never walked.
- **`~~~` fences, no triple-backticks** — so the example survives being bundled inside a code block.
