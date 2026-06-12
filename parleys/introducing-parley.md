# Introducing Parley
status: active
turn: 1 · last updated: 2026-06-12 by Kevin
built with: parley v0.3
target: open exploration — help a first-time reader understand what Parley is, get straight answers to whatever they actually wonder about (without wading through the questions they don't have), and form their own view. No decision is forced: they might just leave understanding it, or decide they want to use or build on it.
participants: Kevin (Parley's designer, introducing it), Agent (participant + guide). Newcomers accrete as they take a turn.

## Decision Target
Exploratory. The reader isn't being asked to commit to anything. It's working if they come away understanding Parley well enough to form their own view and genuinely push back — and if they got answers to the questions *they* had, not a lecture they didn't ask for.

## Synthesis (the agent's current read — the intro to lead with)
Parley is for working something out *with other people* when you can never all sit down at once. Each person talks it through with an AI on their own time; the AI carries the thread between them — catching the next person up, surfacing what's relevant, and recording where things stand so nothing is lost.

What makes it more than a group thread or a summarizer: when it carries your thinking to someone else, it doesn't hand them a summary to skim — it *walks* them through it, in order, with an expert (itself) at their elbow they can stop and ask anything before moving on. You lay your reasoning out once; the next person actually takes it in, and can push back for real. It's collaborative, not a debate — the point is to save everyone's time and keep the reasoning honest, not to win.

(Lead with a sentence or two of the above and offer more — don't deliver this whole thing at once. The answers in the log below are here to surface *only* as the reader's questions actually call for them.)

## Statement Log
- [T1 · Kevin] (Isn't this just asking an AI to summarize a long message?) It's the opposite. A summary saves time by letting you *skip* — gist in, the rest lost. Parley walks you through the whole of someone's thinking, in order, with the AI as an expert you can stop and ask anything. Not less content — the *whole* of it, actually absorbed.
- [T1 · Kevin] (Why not just use Slack or email?) A thread forces one bad choice: a short message that gets misread, or a long one you over-draft trying to pre-empt every reaction. Parley lets you lay out every branch of your thinking once, and the reader walks only the branch they care about — the effort you'd burn guessing what they'll ask is spent only where it lands.
- [T1 · Kevin] (How do I know a surfaced answer is really me, not the AI guessing?) The AI only plays back what I actually said, labeled by how I said it — stated clearly, touched on briefly, or not at all. Where I never weighed in, it speaks in its own name and flags the question to bring back to me. It never invents my position. The line is authorship: my words, never a guess wearing my name.
- [T1 · Kevin] (Isn't laying out all those branches a lot of work?) Mostly the same effort you'd spend anyway, spent differently — the AI draws the branches out of you and prunes them, so you react to prompts instead of enumerating cold. And often it's by design: whoever has the time preps, so whoever's time-poor doesn't have to.
- [T1 · Kevin] (What is it, exactly — a group chat with a bot?) No. One shared space with hidden threads: what you tell the AI is held privately, and others only see what becomes relevant to them. It also keeps each of you consistent with your own earlier thinking, gently, so positions sharpen instead of drifting.
- [T1 · Kevin] (Is the AI secretly arguing the other side?) No — it's collaborative, not adversarial. Nobody's trying to win. Its job is to save everyone time and keep the reasoning honest.
- [T1 · Kevin] (Is the record exact?) Your key statements are kept close to word-for-word; the rest is summarized. Compression has a floor — something can be lost in the write-up — so anything that really matters, ask to see in the original words, and treat whatever you type as readable by the others.
- [T1 · Kevin] (Does it actually work? — the first real run) An algorithm-design problem; both people unsure of their own blind spots. One handed it off — "probably simple, but maybe not." Exploring with the AI surfaced far more depth than expected, much of it raised by the AI itself. Instead of reporting back "it's complicated, let's meet," they curated each option in — their own call on each, alternative paths left walkable — and the handoff landed at "they may already know this, so lay out the plan; be ready to go deep on demand; and where I made a call they might reject, let them tell me what to reconsider."
- [T1 · Kevin] (What's the AI's role, in one line?) Expert when it can be, scribe as best it can from summary context, mediator and messenger as best it can.

## Open Questions
- [ ] Summary fidelity: the AI compresses people to each other, and a dropped nuance is silent until it bites. How big is that risk in practice? (Honest answer: we expect to learn it only as more parleys happen.) If you have a read, it's welcome. — posed to: open
- [ ] Should Parley be a portable standard any AI just recognizes, or a hosted bot/app you log into? Passing files around is annoying; a full app is slicker but re-silos the thing that made Parley portable. Live question. — posed to: open

## Parked Tensions
- Summary fidelity — a real, unsolved risk. Dropped-nuance failures are silent, so it needs a cheap way to surface them (a preview of how you'll be represented; the exact words on demand).
- The AI holds its own view, which not everyone wants inside their decision — kept in check by the collaborative frame and by always labeling what's a person's vs. the AI's.
