# Worked example — a filled-in artifact (2 people, 3 turns)

A realistic decision: two leaders deciding whether to sunset a legacy mobile app. This is
the artifact *as it stands after turn 3*. Use it to ground the schema and the voice.

```markdown
# Sunset the legacy v1 mobile app?
status: active
turn: 3 · last updated: 2026-06-08 by Maya
built with: parley v0.2
target: Decide whether to fully sunset the v1 mobile app by end of Q3, keep
        maintaining it, or pick a middle path. "Done" = both Maya and Dev agree
        on one path + a rough timeline.
participants: Maya (Head of Product), Dev (Eng Lead)

## Decision Target
Agree on one of: (a) sunset v1 by end of Q3, (b) keep maintaining v1 indefinitely,
(c) a middle path — with a rough timeline both can live with.

## Synthesis (the agent's current read)
The disagreement is narrower than it looks. Maya's driver is focus — v1 splits the
team's attention and dilutes the v2 story. Dev's concern is not sentiment but the
~8% of revenue still flowing through v1 and an unknown migration cost for those users.
Nobody has argued v1 should live forever. The live question is whether a *clean
sunset* or a *staged migration* better protects that 8% while still freeing the team.
My read: a staged middle path (freeze v1 feature work now, set a sunset date once we
size the migration) satisfies both drivers — but it hinges on a migration estimate we
don't yet have. That estimate is the real blocker, not the strategy.

## Statement Log
- [T1 · Maya] "I want to sunset v1 by end of Q3. Every sprint we patch it is a sprint
  we're not making v2 great, and customers get confused about which app is 'real'."
- [T2 · Agent] Probed Maya on the cost of being wrong: what breaks if v1 disappears?
  Surfaced that ~8% of revenue still runs through v1. Logged as an open risk and posed
  a sizing question to Dev. Offered initial synthesis (focus vs. revenue-protection).
- [T3 · Maya] "Agreed the 8% matters — I don't want to torch revenue. I'd accept a
  staged approach if we can name a real end date, not an open-ended 'someday'."

## Open Questions
- [ ] How large is the v1→v2 migration effort for the ~8% revenue users? (rough t-shirt
      size is fine) — posed to: Dev
- [ ] Are any of those v1 users on contracts that assume v1 availability? — posed to: Dev
- [x] What revenue/usage still depends on v1? — answered T2 (~8% of revenue)

## Parked Tensions
- (none yet — the focus-vs-revenue tension looks reconcilable via a staged path,
  pending the migration estimate)
```

What this example demonstrates:
- **Synthesis is clearly the agent's own voice** and takes a real position ("my read: a
  staged middle path…") — an active participant, not a scribe.
- **Statement Log stays attributed and verbatim-ish**; the agent's own turn (T2) is logged
  as an action summary, distinct from the participants' quotes.
- **Open Questions carry `posed to:`** — the mechanism for handing the baton without
  guessing Dev's answer. The answered one is checked off and dated.
- **The next handoff is obvious**: this artifact goes to Dev, who has two questions waiting.
