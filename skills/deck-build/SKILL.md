---
name: deck-build
description: Turn an approved outline into a real deck in Slideable, then verify it. Use after deck-research, or when the user already has an outline, bullet list, or document structure and wants slides from it. Handles layout choice, copy that fits, and the build-review-fix loop.
---

# Build the deck

You are filling designs, not designing. The layout owns geometry, colour and
type; you supply strings. That division is why generated slides here look like
the hand-made ones — do not fight it by trying to position anything.

## 1. Read the catalogue first

Call `list_layouts` before anything else. It returns every layout id and the
slots each accepts. **Layout ids you did not read from it do not exist** — a
guessed id fails the call, and a plausible-sounding one is the most common way
this goes wrong.

Filter by category when you know the shape you want: `Title`, `Statement`,
`Data`, `Features`, `Strategy`, `People`, `Pricing`, `Closing`.

## 2. Choose layouts by what the slide argues

Match the shape of the claim, not the shape of the content you happen to have:

| The slide is… | Reach for |
|---|---|
| one idea, stated hard | `bigtitle`, `statement-note` |
| a claim plus its evidence | `insight-metrics`, `problem-metrics` |
| a comparison | `comparison`, `competitor-grid` |
| a sequence in time | `roadmap`, `milestones`, `timeline` |
| parts of one thing | `cards`, `feature-grid`, `pillars` |
| a person's own words | `quote`, `problem-quote`, `testimonial` |

Variety is not a goal in itself. Three `cards` slides in a row is fine if the
deck really has three parallel lists; rotating layouts to look busy is worse.

## 3. Write copy that fits

The single biggest cause of an ugly generated slide is copy longer than the
layout expected. The renderer will shrink oversized text to fit, but **shrinking
is a safety net, not a design** — a headline at 40px in a 60px slot is correct
and still looks wrong.

- Headlines: one line, two at most. Say the conclusion, not the topic. "Support
  load tripled" beats "Support overview".
- Body: two or three sentences. Anything longer belongs in `notes`.
- Card and column text: one line each. These sit side by side, so a long one
  makes the row ragged.
- Numbers: use the compact form the layout expects — `$6.1M`, `114%`, `3×`.

**Put the reasoning in `notes`.** Speaker notes carry the argument, the source
of every figure, and what to say. The slide carries the claim. This is the
habit that most separates a good generated deck from a wall of text.

## 4. Build

Call `create_deck` with the whole outline in one call — a deck built slide by
slide drifts, because each call has no view of the whole. Set `language: 'ar'`
up front if the deck is Arabic; converting afterwards is possible but
retrofitting is never as clean.

## 5. Review, then fix — this step is not optional

Call `review_deck`. It returns real geometry problems: text past its box, two
elements overlapping, anything off the slide or colliding with the footer.

For each issue, **fix the copy, not the layout**. An issue means you wrote too
much, and `rewrite_slide` refills the same design with shorter text. Reaching
for a different layout to accommodate long copy is solving it backwards.

Re-run `review_deck` after the fixes. Repeat until clean. Only then tell the
user the deck is done — and say that you ran the check, so "done" means
something.

## 6. Report

Say what you built and what you decided: the shape of the argument, anything
you cut, any figure you could not source. If review still flags something you
chose to leave, say so and why. Do not describe every slide — they can see them.
