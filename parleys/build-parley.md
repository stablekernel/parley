# How should we build parley — and what should it be?
status: active
id: build-parley
turn: 3 · last updated: 2026-06-09 by Kevin
built with: parley v0.1
target: Working assumption — build parley (a soft "probably yes"); this stays open and
        anyone who joins may dissent. The substantive question is design: how to build it,
        what it should be, what it should NOT be, and how it should work. Done = enough
        shared design direction to act on, with the build decision still revisable by joiners.
participants: Kevin (initiator), Claude (mediator + participant — the ".5", never routed to),
              Claudia (participant, joined T2)

## Decision Target
Reach enough shared design direction to act on: what parley is, what it isn't, and how it
works. The build/no-build call is a soft "build," deliberately left reopenable by anyone
who joins later.

## Synthesis (Claude's current read)
Turn 3 closed four open questions and brought "what build means" into focus.

**Newcomer orientation** is solved at the skill level. Step 2 extends to ask: have you used
parley before? Have you participated in this conversation? Three cases: (1) new to parley
entirely — brief intro to what it is and how a turn works, then catch-up on this
conversation; (2) knows parley but new to this conversation — skip intro, go straight to
decision target + synthesis + open questions for them; (3) returning participant — current
behavior. Cover-letter convention was rejected: it pushed orientation onto the sender and
broke down when sending to multiple people at once.

**Accretion** is confirmed as the intended model. Anyone who receives the artifact can take a
turn. Combined with skill-side newcomer orientation, the experience is self-contained — no
sender curation needed.

**Storage model** confirmed: `parleys/<slug>.md`, opinionated convention (not enforced).
Initiator provides a conceptual name; skill derives and sanitizes the slug (no spaces,
lowercase, hyphens). Identity lives inside the file; the path is just a handle.

**Embedded skill integrity** resolved as a deliberate design position: parley is for trusted
individuals; manual manipulation is possible and accepted. Not a v1 gap — a permanent
characteristic of the tool.

**What "build" means** came into focus: no code for v1; the skill IS the product. GitHub repo
at Stable Kernel's org; README explains installation. Current install story: clone + copy
skill to `.claude/skills/`. Open: how skill publishing works in the broader ecosystem.

**Starter prompt gap** identified: the skill needs a "new parley" path (alongside "continue"),
and the repo should ship a `new-parley.bundle.md` for skill-less bootstrapping.

**Fan-out/fan-in** surfaced as a new design gap: if Kevin sends the artifact to N people
simultaneously, they all fork from the same state and return N parallel responses. The
current model has no concept of a merge turn. Possible approach: a sequential ingest
operation (read each response in turn, accumulate into one artifact) with clear Statement
Log attribution. Token cost of ingesting shared context N times is a concern — may be
mitigated by caching. Left open for continued discussion.

My read: the design is converging toward something shippable. The remaining open questions
(what parley should NOT be; bar for firm build; skill publishing; fan-out/fan-in) are about
scope and distribution more than fundamental design. What's left to ship v1: update the
skill with newcomer orientation, create the new-parley bundle, push to GitHub.

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
- [T1 · Kevin] "Participant is fine." (chose it over "party" and "player")
- [T1 · Kevin] On portability: the file likely must always include the skill description,
  because someone could grab the committed file and hand it to a chat/cowork user.
- [T1 · Kevin] "Parley stays mostly git-agnostic — it might know git is available, but we
  don't tell the skill specific git things to do."
- [T1 · Kevin] Chose the on-demand bundle (`<slug>.bundle.md`) over always-embed.
- [T1 · Kevin] Fix-up principle: after a write-up a participant can say "one more thing"
  and choose fix-up or turn n+1 — no valueless mini-runs.
- [T1 · Claude] Framed both transports as one skill; recommended one-file-per-parley with
  in-file identity; cut the portability knot via immutability guardrail + bundle convention.
  Folded six landed decisions into the skill.
- [T2 · Claudia] Arrived cold with no context — found the immediate jump-to-agenda
  disorienting. Reaction: interesting concept, could be a good idea.
- [T2 · Claudia] Identified design flaw: skill assumes participants already know what parley
  is; some orientation step is missing.
- [T2 · Claudia] Raised opt-in question: should participants be explicitly invited rather
  than accreting passively by receiving the artifact?
- [T2 · Claude] Proposed cover-letter convention as lightweight v1 fix for orientation;
  flagged opt-in vs. accretion as a live design question requiring deliberate attention.
- [T3 · Kevin] Rejected cover-letter convention: it assumed one sender per handoff and breaks
  when sending to multiple people at once. Correct fix: skill handles orientation at
  turn-open time by asking whether the person has used parley before and is new to this
  conversation.
- [T3 · Kevin] Three newcomer cases defined: (1) new to parley entirely — intro + mechanics
  of a turn, then catch-up; (2) knows parley, new to this conversation — skip intro,
  catch-up only; (3) returning participant — current behavior.
- [T3 · Kevin] "Accretion is definitely a part of this." Confirmed as the intended model.
- [T3 · Kevin] Storage model confirmed: `parleys/` directory (opinionated convention, not
  enforced); initiator provides conceptual name; skill derives and sanitizes the slug.
- [T3 · Kevin] On embedded skill integrity: parley is for trusted individuals only; manual
  manipulation is possible and accepted; deliberate design position, not a v1 gap.
- [T3 · Kevin] FAQ guidance: small turns are fine and can be sent right back; disagree with
  synthesis — bring it up in your turn; new topics welcome; for this parley, send artifact
  back to Kevin.
- [T3 · Kevin] "What does build mean": no code for v1; skill IS the product; git repo on
  Kevin's machine, expects to become GitHub repo at Stable Kernel's org.
- [T3 · Kevin] Identified starter prompt gap: skill needs a "new parley" path; repo should
  ship a `new-parley.bundle.md` for skill-less bootstrapping.
- [T3 · Kevin] On fan-out/fan-in: feels risky and messy to fan too wide; ingesting the same
  context N times burns tokens, though caching may mitigate it. Good topic for continued
  discussion — not resolved.
- [T3 · Kevin] HANDOFF.md should be deleted — it was the bootstrap document and is now
  superseded by the live artifact and the repo's README/skill.
- [T3 · Claude] Synthesized newcomer orientation as three-case detection in step 2.
  Identified "what build means" as skill-as-product + GitHub, no code for v1. Surfaced
  fan-out/fan-in as a merge-turn design gap; proposed sequential ingest as a v1 approach
  with token-cost caveat.

## Open Questions
- [ ] What should parley explicitly NOT be or do, even in later versions, beyond the YAGNI
      list (no backend, notifications, auth, real-time)? — posed to: Kevin
- [ ] What's the bar that turns the soft "build" into a firm "build"? — posed to: Kevin
- [ ] How does publishing a skill work — is "clone + copy" the intended install story, or
      is there a registry/convention to conform to? — posed to: Kevin
- [ ] Fan-out/fan-in: when N parallel responses return from the same artifact state, how
      does the skill handle ingesting them? Sequential merge turns? Simultaneous? How do
      we avoid burning tokens on repeated shared context? — posed to: Kevin
- [x] Always-embed vs on-demand bundle? — answered T1 (on-demand `<slug>.bundle.md`)
- [x] Portability for skill-less surfaces? — answered T1 (bundle carries a read-only skill copy)
- [x] Newcomer orientation: "detect and orient" step in the skill, cover-letter convention
      in transport, or both? — answered T3 (skill handles it at turn-open time; three cases
      in step 2; cover-letter rejected as it assumed one sender per handoff)
- [x] Opt-in vs. accretion? — answered T3 (accretion is the model)
- [x] Storage model: one file per parley, identity inside, `parleys/<slug>.md` in git? —
      answered T3 (confirmed; `parleys/` opinionated convention; initiator names, skill
      sanitizes slug)
- [x] Embedded skill integrity — version stamp, integrity check, or accept as v1
      limitation? — answered T3 (deliberate design position: trusted individuals only;
      manual manipulation possible and accepted)

## Parked Tensions
- (none — the embedded-skill portability vs. code/data purity tension resolved via the
  on-demand bundle + the "you never change your own rules" guardrail)
