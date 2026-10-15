---
name: deck-translate
description: Move a deck between English and Arabic, including right-to-left layout. Use when the user asks to translate a deck, make an Arabic version, switch a deck to RTL, or prepare the same deck for a bilingual audience.
---

# Translate a deck

Translating a deck is two jobs. `set_deck_language` does the mechanical one;
only you can do the other.

## 1. Flip the deck

`set_deck_language` with `language: 'ar'` sets right-to-left, applies an Arabic
typeface and flips text alignment.

**`mirror: true` also reflects the geometry**, so an image on the right moves to
the left. Use it when the layout has a strong directional read — a split slide,
a timeline, anything the eye traverses. Skip it for centred and symmetrical
slides, where mirroring changes nothing and can unbalance deliberate asymmetry.

Pick the face deliberately with `font`: `cairo` and `tajawal` are the neutral
modern choices, `almarai` reads well small, `amiri` is classical and belongs on
formal or ceremonial decks, `noto-kufi-arabic` is geometric and display-ish.
Leaving it to the default is fine; choosing badly is worse than not choosing.

## 2. Translate the copy — the part that matters

Read the deck with `read_deck` and rewrite each slide with `rewrite_slide`.

**Do not translate literally.** Deck copy is compressed and idiomatic, and word-
for-word Arabic of an English headline reads as machine output. Rewrite the
claim as an Arabic speaker would state it.

Three things that reliably go wrong:

- **Arabic runs longer than English**, often 20–30% for the same meaning. A
  headline that fitted in two lines will wrap to three. Cut, do not let it
  shrink — see the fit check below.
- **Numerals are a choice.** Western digits (`2026`, `40%`) are normal in Gulf
  business decks; Eastern Arabic numerals (`٢٠٢٦`) suit formal and government
  contexts. Ask if you do not know the audience, and be consistent.
- **Leave proper nouns alone.** Product names, company names and technical terms
  usually stay in Latin script. Transliterating them makes a deck look
  translated rather than written.

## 3. Check the fit

Call `review_deck` after translating. Longer Arabic copy is the most common
source of overflow, and this is exactly what the check catches.

Fix by shortening the Arabic, not by reaching for another layout.

## 4. Bilingual decks

If both languages need to exist, make **two decks**, not one with mixed slides.
A deck has one reading direction; a slide that runs left-to-right inside a
right-to-left deck fights every alignment decision in the layout. Build the
English deck, duplicate it, then translate the copy.
