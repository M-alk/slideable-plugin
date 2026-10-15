---
name: deck-research
description: Gather and structure the material for a presentation before any slide exists. Use when the user asks for a deck about a topic they have not yet outlined — "make me a deck on X", "pitch deck for our seed round", "QBR for the board" — or when they hand over raw notes, a transcript, or a document to turn into slides. Produces an outline, not slides.
---

# Research a deck before building it

A deck built straight from a prompt is a list of headings. A deck built from an
argument persuades. This skill produces the argument; `deck-build` renders it.

**Do not call `create_deck` in this skill.** Ending with an outline is the point.

## 1. Find out what you are actually arguing

Before gathering anything, answer three questions. Ask the user only what you
genuinely cannot infer:

- **Who is in the room?** A board, a customer, a hiring panel and an all-hands
  need different evidence for the same claim.
- **What do they do differently afterwards?** A deck with no ask is a document.
- **What will they push back on?** The objection is usually the real content.

If the user gave you source material, read it first — the answers are often
already there, and asking about what you were just handed reads as not looking.

## 2. Gather

Use whatever tools you have: read the files they pointed at, search the web for
figures they cited but did not source, look at the repo if the deck is about
software. Two rules:

- **Every number needs a source.** A slide that says "40% faster" with no basis
  will be the one someone asks about. Note where each figure came from — you
  will put it in the slide's `notes`.
- **Prefer their words.** If you have a transcript or their existing writing,
  the phrases they already use are better than ones you invent.

## 3. Structure it

Write an outline as a numbered list. For each slide:

```
3. The problem is getting worse, not staying flat
   layout:  problem-metrics
   says:    Support load grew 3x while headcount grew 1.2x
   evidence: Zendesk export, Jan–Nov — see notes
   note:    Sets up why the current approach cannot just be scaled
```

Shape the whole thing as an argument:

- **Open on the change**, not on your company. "Something is different now" earns
  the next slide; "Founded in 2021" does not.
- **One claim per slide.** If a slide needs "and", it is two slides.
- **Put the evidence next to the claim it supports**, not in an appendix.
- **Close on the ask**, stated plainly enough to be repeated.

Then call `list_layouts` and assign a real layout id to each line. If nothing
fits a slide, that is a signal the slide is doing too much — split it.

## 4. Hand off

Show the outline and stop. Ask whether to build it. The user correcting an
outline costs a sentence; correcting a built deck costs a rebuild.
