# Storyboard and Source-Order Rules

## Required table

After the style is locked, output one row per page:

| Page | Source span | Spoken logic | On-screen text | Main visual | Layout model | Motion cue | Click sequence |
|---|---|---|---|---|---|---|---|

Use stable source spans such as paragraph and sentence identifiers: `P03-S01..P03-S03`.

For `Click sequence`, number each reveal and state what appears or changes:

```text
Base frame (no order): problem symbol and short title
Click 1 / order 1: reveal the first cause
Click 2 / order 2: connect cause to consequence
Click 3 / order 3: emphasize the conclusion keyword
```

For `Motion cue`, assign the reveal by meaning, not decoration:

- `rise`: a short label or keyword enters with 10-14px vertical travel and smooth deceleration;
- `place`: a card, object, or module settles with about 10px travel and no more than 1.5% scale change;
- `slide`: an ordered entry moves 10-14px along its reading direction;
- `connect`: a relationship or flow expands subtly from its source edge;
- `fade`: screenshots, photos, and large raster images change opacity only;
- `emphasis`: a conclusion already supported on screen uses at most a 3% scale change.

Do not use one motion cue for every click on a page. The motion should clarify whether the new content is being introduced, placed, connected, or concluded.

## Ordering invariant

The base frame is visible before any click and must not consume a source-order number. Assign every click-triggered reveal a global integer `data-source-order` beginning at `1`. Values must increase from left to right in the table and from the first page to the last page without gaps.

Never:

- reveal material from a later source span;
- reorder examples to make the visual easier;
- turn a later conclusion into an opening hook;
- merge separated claims across intervening logic;
- invent numbers, quotes, sources, interfaces, or outcomes.

Screen omission is allowed only for filler, repetition, and spoken transitions. The underlying spoken argument remains intact.

## Page boundaries

Start a new page when any of these changes:

- the core question;
- the information structure;
- the time, place, actor, or example;
- the dominant visual metaphor;
- the conclusion level.

Keep one core idea per page. Split rather than shrinking text or placing many equal elements.

## Layout model

Assign one model before building:

- `split`: copy and visual share two safe columns;
- `visual-first`: a larger evidence or diagram column plus a smaller copy column;
- `stack`: short header above one wide visual flow;
- `evidence`: a complete screenshot or source beside a bounded annotation list.

Use Grid or Flexbox for the main structure. Major titles, images, diagrams, and relationship nodes must remain in normal flow inside the safe content area. Absolute positioning is allowed only for small callouts inside a bounded visual container.

Do not approve a page whose layout depends on guessed stage coordinates. If the planned content cannot fit at the required type sizes, split the page before approval.

## Click boundaries

Use one click for one meaningful cognitive step. A click may:

- introduce one claim or example;
- add one item to a sequence;
- connect two existing elements;
- transform a before state into an after state;
- highlight a conclusion already supported on screen.

Do not make every sentence a click. Do not reveal multiple independent list items in one click.

When one click changes several pieces of the same idea, place them in one semantic reveal group. The implementation must use one `.reveal` wrapper and one `data-source-order` value for that whole group.

## Screen-copy rules

- Preserve important proper nouns, dates, numbers, and quoted terms exactly.
- Use short titles, labels, and emphasis phrases instead of complete narration sentences.
- Keep body copy to a practical maximum of 40 Chinese characters per page unless the content is a source excerpt.
- If a source excerpt is essential, show only the relevant lines and clearly mark it as a quotation or source.

## Visual requirement

Every page needs one semantic non-text visual. Select from:

- metaphorical object or illustration;
- process, relationship, hierarchy, or timeline diagram;
- comparison composition;
- number or data visualization;
- user-provided screenshot or evidence image;
- source-grounded generated image.

Abstract gradients, blobs, grids, sparkles, or ornamental icons do not satisfy this requirement by themselves.

For supplied screenshots and evidence images, the default is the complete image with `object-fit: contain`. State an intentional crop in the storyboard if one is necessary. Never use `cover` merely to fill a frame when it hides source content.
