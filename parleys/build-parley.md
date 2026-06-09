# How should we build parley — and what should it be?
status: active
id: build-parley
turn: 1 · last updated: 2026-06-08 by Kevin
built with: parley v0.1
target: Working assumption — build parley (a soft "probably yes"); this stays open and
        anyone who joins may dissent. The substantive question is design: how to build it,
        what it should be, what it should NOT be, and how it should work. Done = enough
        shared design direction to act on, with the build decision still revisable by joiners.
participants: Kevin (initiator), Agent (mediator + participant — the ".5", never routed to)

## Decision Target
Reach enough shared design direction to act on: what parley is, what it isn't, and how it
works. The build/no-build call is a soft "build," deliberately left reopenable by anyone
who joins later.

## Synthesis (the agent's current read)
Turn 1 was design groundwork (amended once via a fix-up to fold in the bundle decision and
the fix-up principle itself). My read of where we are:

**Landed.** (1) *Minimal friction to start* — topic-only kickoff, participants accrete, a
parley begins as "1.5 parties" (one human + me). (2) *What a turn is* — orient → free
conversation (no artifact writes mid-turn) → write-up only on the done-signal. (3)
*Vocabulary* — "participant" canonical; "parties" optional flavor; "player" out. (4)
*Git-agnostic* — the skill may know git exists but prescribes no git steps. (5) *Transport*
— the canonical artifact stays **pure state**; a generated `<slug>.bundle.md` (a fenced,
read-only copy of the skill + the artifact) is the on-demand export for skill-less surfaces.
(6) *Fix-ups* — a write-up isn't sealed: a participant can add "one more thing" and choose
whether it amends the turn (fix-up) or starts turn n+1; never manufacture an empty turn.

**Tentative (proposed, uncontested, not locked).** One file per parley (not a directory of
turn-files); identity lives *inside* the file (slug + title + turn); multiple concurrent
parleys = multiple files; visible `parleys/<slug>.md` in git; filename-convention + agent
explicitness in the non-git case.

All six landed items are folded into the skill. The tentatives wait on your confirmation.

## Statement Log
- [T1 · Kevin] "Minimal friction to start — no one should be required to pick the number of
  participants or who they are. The first person establishes what's being discussed; they
  plus the agent become the first '1.5 parties.'"
- [T1 · Kevin] "Probably build parley, but people joining can disagree. The larger question
  is how to build it, what it should and shouldn't be, and how it should work."
- [T1 · Kevin] Mused two usage modes: (a) installed skill + git — discussion on a branch,
  turns committed/pushed, next person pulls and takes their turn; (b) copy/paste or import
  markdown into a Claude tool, then pass the resulting file/markdown to the next participant.
- [T1 · Kevin] "This is not a turn — we're mid-conversation. A turn begins with 'you're an
  agent, here's what we're doing' and ends with 'good chat, let's write things up to hand
  back to the other participant(s).'"
- [T1 · Kevin] "Participant is fine." (chose it over "party" — singular "party" reads
  ambiguously as the group — and over "player," which carries a game/competition tone.)
- [T1 · Kevin] On portability: the file likely must always include the skill description,
  because someone could grab the committed file and hand it to a chat/cowork user — "but I
  don't want any participant to work the agent, knowingly or otherwise, into changing the skill."
- [T1 · Kevin] "Parley stays mostly git-agnostic — it might know git is available, but we
  don't tell the skill specific git things to do."
- [T1 · Kevin] Chose the on-demand bundle (`<slug>.bundle.md`) over always-embed: people who
  have the skill pass the one pure-state file; people without it get the bundle.
- [T1 · Kevin] Fix-up principle: nothing should feel friction-filled. After a write-up a
  participant can say "oh, one other thing" / "let's keep talking," and they decide whether
  it folds into the write-up (a fix-up) or becomes an n+1 run — no valueless mini-runs.
- [T1 · Agent] Framed both transports as one skill with different artifact journeys;
  recommended one-file-per-parley with in-file identity; cut the portability knot by
  separating "carry the rules" from "change the rules" + an immutability guardrail. Folded
  six landed decisions into the skill (turn definition, start/end verbiage, git-agnostic,
  skill-immutability, the bundle convention, and fix-ups).

## Open Questions
- [ ] How (if at all) do we protect an embedded skill copy from hand-tampering before it
      reaches a skill-less agent — version stamp now, integrity check later, or accept as a
      known v1 limitation? — posed to: Kevin
- [ ] Confirm the storage model: one file per parley, identity inside the file, visible
      `parleys/<slug>.md` in git, filename-convention in non-git. — posed to: Kevin
- [ ] What should parley explicitly NOT be or do, even in later versions, beyond the YAGNI
      list (no backend, notifications, auth, real-time)? — posed to: Kevin
- [ ] What's the bar that turns the soft "build" into a firm "build"? — posed to: Kevin
- [x] Always-embed vs on-demand bundle? — answered (on-demand `<slug>.bundle.md`)
- [x] Portability for skill-less surfaces? — answered (the bundle carries a read-only skill copy)

## Parked Tensions
- (none — the embedded-skill portability vs. code/data purity tension resolved via the
  on-demand bundle + the "you never change your own rules" guardrail)
