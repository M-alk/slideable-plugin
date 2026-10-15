---
name: deck-review
description: Critique an existing deck and fix what is wrong with it. Use when the user asks for feedback on a deck, says a deck looks off or broken, wants it tightened before presenting, or asks whether it is ready to send. Covers both layout problems and the argument.
---

# Review a deck

Two different reviews, and people usually mean the second while asking for the
first. Do both, in this order, because a broken layout distracts from the
argument.

## 1. The mechanical pass

Call `review_deck`. It reports what a human eye catches immediately: text
running past its box, elements overlapping, anything off the slide or sitting in
the footer.

Fix each with `rewrite_slide` — shorter copy in the same design. Do not change
layouts to accommodate long text; that is treating the symptom.

Re-run until clean.

## 2. The editorial pass

`review_deck` cannot tell you the deck is boring. Read it with `read_deck` and
judge it as a reader:

**Does it argue anything?**
A deck that lists features has no spine. Look for the change the audience is
being asked to believe in, and whether each slide moves it forward. Slides that
do not move it are the ones to cut.

**Is the conclusion on the slide, or hidden in it?**
"Q3 results" is a topic. "Q3 broke even three quarters early" is a claim. Every
headline should be the second kind. This is the single highest-leverage edit in
most decks.

**Can a number be challenged?**
Any figure without a source in `notes` will be the one someone asks about.
Flag them.

**Does it end with an ask?**
A closing slide that says "Thank you" wastes the last thing anyone remembers.

**Is there a slide doing two jobs?**
If a headline needs "and", it is two slides. Splitting is usually free — the
deck has room.

## 3. Report like an editor

Lead with the two or three things that would most improve it, not a slide-by-
slide list. Say what is already working — an author who thinks everything is
wrong stops reading.

Separate what you fixed from what you are recommending. Layout problems you
should just fix. Argument problems are the author's call: propose the rewrite,
show the before and after, and let them decide.

Be direct about a deck that is not ready. Softening it wastes their time and
yours, and they will find out in the room.
