# Introducing Parley
status: active
turn: 1 · last updated: 2026-06-29 by Kevin
built with: parley v0.4
target: open exploration — help a first-time reader understand what Parley is, get straight answers to whatever they actually wonder about (without wading through the rest), and form their own view. No decision is forced: they might just leave understanding it, or decide they want to use or build on it.
participants: Kevin (Parley's designer, introducing it), Agent (participant + guide). Newcomers accrete as they take a turn.

> ▶ **First time here? Pick a door — don't let me lecture you.**
> The short version: Parley hands off *thinking* — you work something out with an AI, and it lets
> the next person walk your full reasoning, question it, and push past where you stopped, on their
> own time. From here you can:
> - **(a) Just the gist** — two sentences and you're oriented; stop there if you like.
> - **(b) Walk me through it** — the fuller picture, a bit at a time; stop me anytime to ask.
> - **(c) Ask me anything** — got a doubt or a "yeah, but…"? Fire it; Kevin has likely already
>   answered it (below), and where he hasn't I'll say so and flag it for him.
> - **(d) Poke the honest holes** — jump to what's still unsolved and push on it.

## Decision Target
Exploratory. The reader isn't being asked to commit to anything. It's working if they come away
understanding Parley well enough to form their own view and genuinely push back — and if they got
answers to the questions *they* had, not a lecture they didn't ask for.

## Synthesis (the agent's current read — the intro to lead with)
Parley hands off *thinking*, not a summary of it. You work something out with an AI on your own
time; it captures your **full reasoning**; then whoever you pass it to can **walk** that reasoning
at their own depth, ask the AI *"wait, why not X?"*, **extend** it down forks you never took, and
disagree — with you or with the AI. The async, multi-person part is just the delivery; the value
is that the *reasoning itself* survives the hand-off, where a summary keeps the conclusion and
drops the why. A decision is one thing it can produce — not the point.

(Lead with a couple of sentences and offer more — don't deliver this whole thing at once. The
answers below surface only as the reader's questions call for them.)

## Statement Log
- [T1 · Kevin] (Isn't this just asking an AI to summarize a long message?) It's the opposite. A
  summary saves time by letting you *skip* — gist in, the rest lost. Parley walks you through the
  whole of someone's thinking, in order, with the AI as an expert you can stop and ask anything.
  Not less content — the *whole* of it, actually absorbed.
- [T1 · Kevin] (Why not just use Slack or email?) A thread forces one bad choice: a short message
  that gets misread, or a long one you over-draft trying to pre-empt every reaction. Parley lets
  you lay out every branch of your thinking once, and the reader walks only the branch they care
  about — the effort you'd burn guessing what they'll ask is spent only where it lands.
- [T1 · Kevin] (How do I know a surfaced answer is really me, not the AI guessing?) The AI only
  plays back what I actually said, labeled by how I said it — stated clearly, touched on briefly,
  or not at all. Where I never weighed in, it speaks in its own name and flags the question back to
  me. It never invents my position. The line is authorship: my words, never a guess wearing my name.
- [T1 · Kevin] (Isn't laying out all those branches a lot of work?) Mostly the same effort you'd
  spend anyway, spent differently — the AI draws the branches out of you and prunes them, so you
  react to prompts instead of enumerating cold. And often it's by design: whoever has the time
  preps, so whoever's time-poor doesn't have to.
- [T1 · Kevin] (What is it, exactly — a group chat with a bot?) No. One shared space with hidden
  threads: what you tell the AI is held privately, and others only see what becomes relevant to
  them. It also keeps each of you consistent with your own earlier thinking, gently, so positions
  sharpen instead of drifting.
- [T1 · Kevin] (Is the AI secretly arguing the other side?) No — it's collaborative, not
  adversarial. Nobody's trying to win. Its job is to save everyone time and keep the reasoning
  honest — and you're free to reject its read as much as anyone's.
- [T1 · Kevin] (Is the record exact?) Your key statements are kept close to word-for-word; the
  rest is summarized. Compression has a floor — something can be lost in the write-up — so anything
  that really matters, ask to see in the original words, and treat whatever you type as readable by
  the others.
- [T1 · Kevin] (Does it actually work? — a real run) A real engineering call (per-PR preview
  environments) went one person + AI, reached *no decision*, and was obviously worth handing to a
  colleague: a non-obvious load-bearing insight surfaced, and a litter of forks the author didn't
  walk were left open for the next person to explore. That's the shape Parley is for.
- [T1 · Kevin] (What's the AI's role, in one line?) Expert when it can be, scribe as best it can
  from summary context, mediator and messenger as best it can.

## Open Questions
- [ ] Summary fidelity: the AI compresses people to each other, and a dropped nuance is silent
      until it bites. How big is that risk in practice? (Honest answer: we expect to learn it only
      as more parleys happen.) If you have a read, it's welcome. — posed to: open
- [ ] Should Parley be a portable standard any AI just recognizes, or a hosted bot/app you log
      into? Passing files around is annoying; a full app is slicker but re-silos the thing that
      made Parley portable. Live question. — posed to: open

## Branch Map — roads not taken & anticipated forks
*(My map of where a curious reader tends to push, and the still-open design questions you can dive
into. Anticipations are my own labeled guesses — never anyone's position.)*
- **Skeptic: "why not just a doc, a call, or an AI summary?" — anticipated, the most common.**
  *Where it leads:* the transmit/inhabit/extend reframe — a summary drops the reasoning, a call is
  lossy and one-shot; Parley moves the reasoning itself, walkable. *My intent:* meet it head-on —
  it's the thing most worth landing.
- **Wants a concrete example — anticipated.** Introducing Parley *via* itself is its weakest case
  (it strips out the real-stakes asymmetry). *My intent:* point at a real run rather than argue in
  the abstract.
- **Privacy-minded: "is what I type private?" — anticipated.** One shared space, hidden threads;
  others see only what's relevant — but treat anything you type as readable by the others.
- **Summary fidelity / portable-vs-hosted — genuinely open** (see Open Questions). A reader's read
  is welcome on either.

## Parked Tensions
- Summary fidelity — a real, unsolved risk; dropped-nuance failures are silent. Mitigations in
  progress: a preview of how you'll be represented; the exact words on demand.
- The agent holds its own view, which not everyone wants inside their decision — kept in check by
  labeling what's a person's vs. the agent's, and never herding.
- Demo-of-itself is Parley's weakest test: introducing it via itself removes the real-stakes
  asymmetry that gives it value. A real topic shows it better than this intro can.
