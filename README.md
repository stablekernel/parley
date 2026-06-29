# parley

**A way to hand off your thinking — not a summary of it — to someone who can't be at the keyboard
when you are.** You work a problem through with an AI; it captures your *full reasoning*; then
anyone you pass it to can **walk** that reasoning at their own depth, ask the AI *"wait, why not
X?"*, push down forks you never explored, and disagree — with you or with the AI. A decision is
one thing that can come out of it, not the point. No meetings, no real-time, no backend, no
recurring cost.

## What it's for

The honest reframe: a **summary** keeps conclusions and drops the reasoning; a **transcript**
keeps everything so nobody reads it; a **meeting** is lossy and one-shot. Parley is the medium
that transmits *the reasoning itself* — walkably, at the recipient's chosen depth, with an expert
at their elbow — and lets them extend it down paths you didn't take.

So it's for any time you've thought something through and need someone else to genuinely *get
there too*, on their own time: a design decision, a findings report, a pitch, a hard call you
want pressure-tested. The multi-person, async part is the *delivery context*; the value is the
thinking-transmission. The agent is an active expert, not a scribe — it leans in when it spots a
blind spot, stays quiet when the conversation is smooth, and never herds anyone to a conclusion.

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

- **Start one anywhere, no skill installed:** paste the contents of
  `.claude/skills/parley/SKILL.md` into any AI chat and just say what you want to work out.
  The rules are self-contained, so it'll run the parley and hand you back an artifact to pass
  to whoever goes next.
- **Start a parley:** just tell the agent what you want to work out — a sentence or a
  brain-dump is plenty; it draws the rest out in conversation, no form to fill in. It creates
  the artifact (in `parleys/<slug>.md` when there's a filesystem), and that opening
  conversation *is* turn 1. You never touch a template.
- **Continue one:** point the agent at the parley — it finds it in `parleys/`, or you paste it
  in — and say who you are. It offers you a door rather than a lecture: the bottom line, a walk
  through the reasoning, or jump straight to an open fork and run with it — and you're free to
  disagree (with the author or the agent). When you're done, tell it to write up; then pass it
  to whoever goes next.
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
    worked-example.md           a filled single-author, no-decision example
parleys/                        live conversation artifacts (Document 2 instances)
```

The name: *parley* — a talk across a divide between sides who aren't in the room together. It
names the **hand-off between people**, whether or not it ends in agreement. Renaming is a
one-line change in the skill frontmatter plus this file.
