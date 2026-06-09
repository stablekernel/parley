# parley

An async conversation mediator. The agent is an **active participant and mediator** in a
multi-person conversation that moves toward a decision or agreement — where the people are
never in the room together. Each person talks to the agent on their own time; the agent carries
the thread between them and hands off cleanly to whoever goes next. No meetings, no
real-time, no backend, no recurring cost.

## What it's for

Parley exists for when two or more people need to think something through together but can't
all sit down at once. Instead of one person meeting each of the others and laboriously
re-explaining *"here's what we've figured so far,"* the agent carries the **thinking**
between them — it's an active expert, not a scribe. When it senses a blind spot, an over- or
under-simplification, or a place where one person saw something another missed, it leans in
and says so; when the conversation is smooth, it just listens and records. When a new person
joins, it walks them through the actual reasoning and the open questions so they reach their
*own* understanding and can genuinely disagree — not rubber-stamp a summary. Each person
engages on their own time, talks to the expert directly, and the decision still belongs to
the humans.

## How it works — two documents

1. **The skill** (`.claude/skills/parley/SKILL.md`) — the "product": the facilitation
   rules, the per-turn loop, the guardrails, and the artifact schema. Versioned and
   swappable. Contains no conversation content.
2. **The artifact** (`parleys/<slug>.md`) — one file per conversation, holding all the
   state. Self-describing and stamped with the skill version that produced it, so a cold
   agent with no memory can pick it up and resume.

This code/data split is the heart of the design: the tool can evolve without touching any
live conversation, and a conversation can outlive any single session.

## Using it

- **Start a parley:** tell the agent what you want to work out and your opening position.
  It creates the artifact (in `parleys/<slug>.md` when there's a filesystem), takes the
  first turn — logging your position, writing its first read, and posing open questions —
  and hands off. You never touch a template.
- **Continue one:** point the agent at the parley — it finds it in `parleys/`, or you paste
  it in — and say who you are. If you're new to the conversation it walks you through the
  reasoning and the live questions (not just the conclusions) so you can form your own view;
  if you're returning, it catches you up on what's waiting for *you*. Then you talk it
  through. When you're done, tell it to write up: it records the turn and revises its read.
  Then you pass the parley to whoever goes next.
- **Transport:** paste/send the artifact however your team already communicates. A shared
  file location works too — it's the same thing with nicer storage.
- **Non-installable surfaces (Slack/Chat):** the agent can export the parley as a **bundle**
  — a single `<slug>.bundle.md` file holding a read-only copy of the skill plus the
  artifact — so someone with no skill installed can paste it in and pick up the conversation.

## Layout

```
.claude/skills/parley/
  SKILL.md                      the facilitation skill (Document 1)
  references/
    artifact-template.md        blank artifact the agent starts from
    worked-example.md           a filled 2-person, 3-turn example
parleys/                        live conversation artifacts (Document 2 instances)
```

The name: *parley* — a discussion or negotiation between sides working toward terms. It
names the **purpose** (reaching agreement between parties), not just the mechanics of
handoff. Renaming is a one-line change in the skill frontmatter plus this file.
