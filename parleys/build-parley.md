# How should we build parley — and what should it be?
status: active
id: build-parley
turn: 5 · last updated: 2026-06-09 by Eval
built with: parley v0.1
target: Working assumption — build parley (a soft "probably yes"); this stays open and
        anyone who joins may dissent. The substantive question is design: how to build it,
        what it should be, what it should NOT be, and how it should work. Done = enough
        shared design direction to act on, with the build decision still revisable by joiners.
participants: Kevin (initiator), Claude (mediator + participant — the ".5", never routed to),
              Claudia (participant, joined T2),
              Eval (evaluation agent — holds the original design intent and reviewed parley's
              prior art; took T4 as a bootstrapping turn, source-cited below)

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

**Scope — known and accepted.** Parley's sweet spot is two people passing a file back and
forth; a file in version control is nearly as good. It gets harder and more unwieldy the
more participants you add — and that unwieldiness at scale is itself a sign that
synchronous conversation still wins there. Parley is *not* a replacement for real-time
conversation; it's for the async case where people genuinely can't all be in the room.

**Prior-art check (T4 · Eval).** Parley was measured against its own v0 — Zemora's
maturity-algorithm interview framework (`docs/maturity-algorithm-design-framework.md`,
`.claude/commands/run-latest-interview.md`, `docs/maturity-algorithm-decisions/STATUS.md`),
the hand-crafted predecessor Kevin and Tarun used well across sequential sessions. Its power
came less from record-keeping than from two behaviors parley has **not yet defined as its
job**:

- **(A) Adaptive expertise / blind-spot discernment.** The agent could *tell when one
  participant likely missed something another caught* — and step into the expert role to
  surface it. This is **discerning, not constant**: a smooth, complete turn can be a simple
  scribe-and-reflect; the agent leans in as the expert only when it senses a gap, an
  over/under-simplification, or a divergence between participants. Always-on challenging is
  exhausting and wrong; never doing it forfeits the core value. Knowing *which the moment
  calls for* is the skill. Parley's "have a view / probe" doesn't name this discernment.
- **(B) Transfer the *reasoning*, not the *conclusions*.** A newcomer (Tarun) wasn't handed
  the current answers to approve — he was walked through the same forks and line of thinking
  so *his* eyes opened the way Kevin's had, and he could genuinely dissent. Parley's current
  newcomer orientation does the opposite: it summarizes decision-target + synthesis + open
  questions (the conclusions), which yields rubber-stamping, not understanding.

Supporting / secondary (real, lower priority): **(C) anti-herding** — preserve live
disagreement, never declare consensus; this is what makes (B) safe (don't herd the newcomer
toward the prior answer). **(D) delta recap** — for a *returning* participant, recap what
changed since they were last involved (efficiency, not the heart). **(E)** typed open items +
structured deferrals; soft **(F)** per-answer provenance (Source/Scope) — structural polish.

My read (deliberately **not** re-converged): the prior "converging toward shippable" line was
itself (C) in action — the mediator herding toward closure — so I'm declining to repeat it.
But the bigger correction: parley's *job* isn't defined yet. The mechanics (orientation,
transport, storage) look solid; whether parley reproduces the prior art's success hinges on
(A) and (B) — does it know *when* to be the expert, and does it transfer reasoning rather than
conclusions? Those are skill-mandate questions, not plumbing. **Convergence is for the
participants to confirm, not for the mediator to declare.**

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
- [T3 · Kevin] Known/accepted scope: parley works most solidly for two people passing a
  file back and forth; a file in version control is almost as good. The more people added,
  the more difficult and unwieldy it becomes — a sign that synchronous conversations still
  win, and that parley is not a replacement for them.
- [T3 · Kevin] HANDOFF.md should be deleted — it was the bootstrap document and is now
  superseded by the live artifact and the repo's README/skill.
- [T3 · Claude] Synthesized newcomer orientation as three-case detection in step 2.
  Identified "what build means" as skill-as-product + GitHub, no code for v1. Surfaced
  fan-out/fan-in as a merge-turn design gap; proposed sequential ingest as a v1 approach
  with token-cost caveat.
- [T4 · Eval] Brought external evidence: compared parley to its prior art, Zemora's
  maturity-algorithm interview framework (cited in the synthesis) — the v0 Kevin and Tarun
  used well across sequential sessions. Its power came from two behaviors parley hasn't
  defined as its job, plus three lower-priority mechanisms.
- [T4 · Eval] **(A) Adaptive expertise — primary.** The agent could discern when one
  participant likely missed something another caught, and step into the expert role to
  surface it. Adaptive, not constant: smooth turns stay simple scribe-and-reflect; it leans
  in only when it senses a gap, an over/under-simplification, or a divergence between people.
  Parley's "have a view / probe" doesn't name this discernment as the job.
- [T4 · Eval] **(B) Transfer reasoning, not conclusions — primary.** A newcomer should be
  walked through the live forks and reasoning so they form their own view and can dissent —
  not handed the current answers to approve. Parley's newcomer orientation currently
  summarizes conclusions (target + synthesis + open questions), which yields rubber-stamping.
- [T4 · Eval] **(C) Anti-herding — supporting.** Preserve live disagreement; the mediator may
  observe convergence but never declares it. This is what makes (B) safe — don't herd the
  newcomer toward the prior answer.
- [T4 · Eval] **(D) Delta recap — secondary.** For a *returning* participant, recap what
  changed since they were last involved. Useful efficiency, not the heart.
- [T4 · Eval] **(E)/(F) — secondary.** Lightly type open items (decided / open-fork /
  deferred-with-trigger) so the next move is legible; optional per-answer provenance
  (Source / Scope) in the log. Structural polish.
- [T4 · Eval] Demonstrated (C) in this write-up: declined to re-converge the synthesis,
  reopened shippability on (A)/(B), and parked the convergence tension rather than smoothing
  it. (Bootstrapping turn — Eval was both source and scribe with warm context, which breaks
  cold-start purity; acceptable only because every input is logged, attributed, and
  source-cited. Not a precedent for normal turns.)
- [T5 · Kevin] Confirmed (A) adaptive expertise and (B) transfer-reasoning as parley's job and
  approved folding A/B/C into the skill. Flagged two backwards behaviors: catch-up scoped only
  to "posed to you" (drops others' turns taken since you were last here), and open questions
  getting posed back to whoever raised them. Separately raised ACK / mark-read (see Open
  Questions).
- [T5 · Eval] Folded A/B/C into SKILL.md and added a "What it's for" section to the README.
  Fixed catch-up to recap everything since a participant's last turn ("posed to you" is a
  spotlight, not a filter). Defined `posed to:` = whoever the question awaits next (almost
  never the raiser) and added `open` for unowned items; retagged the backwards ones below.
  Deferred the heavy half of D (tracked last-seen field), plus E and F.

## Open Questions
- [x] **(A) Adaptive expertise:** define the agent's job to include *discerning when to act
      as the expert* — surfacing blind spots / divergences when it senses them, while staying
      a simple scribe when the conversation is smooth? — answered T5 (folded into the skill:
      "read the room, then choose your altitude")
- [x] **(B) Transfer reasoning, not conclusions:** change newcomer handling so a new
      participant is walked through the forks and reasoning (to form their own view and
      dissent) rather than handed the conclusions to approve? — answered T5 (skill step 3 +
      README "What it's for")
- [x] **(C) Anti-herding:** guardrail that synthesis preserves disagreement and the mediator
      never declares consensus — the discipline that makes (B) safe? — answered T5 (new
      guardrail: "Preserve disagreement; never herd toward consensus")
- [ ] **(D) Delta recap:** the *scoping* half is done (T5 — catch-up now recaps everything
      since a participant's last turn). The heavy half — a tracked per-participant last-seen
      field — is deferred until use demands it. — posed to: open
- [ ] **(E/F) Structural (secondary):** typed open items + structured deferrals; optional
      Source/Scope provenance on log entries? Deferred until use demands it. — posed to: open
- [ ] What should parley explicitly NOT be or do, even in later versions, beyond the YAGNI
      list (no backend, notifications, auth, real-time)? — posed to: Kevin
- [ ] What's the bar that turns the soft "build" into a firm "build"? — posed to: Kevin
- [ ] How does publishing a skill work — is "clone + copy" the intended install story, or
      is there a registry/convention to conform to? — posed to: open
- [ ] Fan-out/fan-in: when N parallel responses return from the same artifact state, how
      does the skill handle ingesting them? Sequential merge turns? Simultaneous? How do
      we avoid burning tokens on repeated shared context? — posed to: open  (Kevin raised it)
- [ ] ACK / mark-read: should parley make **assent** first-class (so closure can count who's
      signed off), and let a participant privately **mark-read** without broadcasting? The
      latter needs per-participant read-state (heavy-D) and changes how "since your last turn"
      is computed. — posed to: open  (Kevin raised it, T5)
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
- **Convergence pressure vs. preserving disagreement (surfaced T4).** Parley's synthesis is
  built to converge; the prior art deliberately held contradictions open as signal. Until the
  anti-herding question is resolved, treat any mediator "we're converging / this is shippable"
  read as *provisional* — a participant confirms convergence; the mediator never declares it.
- (Resolved earlier: embedded-skill portability vs. code/data purity — settled via the
  on-demand bundle + the "you never change your own rules" guardrail.)
