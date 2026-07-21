# Quality Check

Fix every failed item before delivery.

## First-use gate

- [ ] On the first invocation in this task, all user-facing rules were explained before the script was analyzed or any style work began.
- [ ] The user explicitly acknowledged the rules before the style shortlist was produced.
- [ ] The onboarding briefing was not repeated after acknowledgement within the same task.

## Style-reference gate

- [ ] Current online references were inspected from original project or studio pages, with direct links retained.
- [ ] Each proposed direction names concrete borrowed principles instead of vague words such as "premium" or "modern."
- [ ] No composition, logo, illustration, or branded asset was copied from a reference.
- [ ] Every candidate reference uses the same representative script beat.
- [ ] Candidate references differ by style, not by meaning or information content.
- [ ] Short labels are legible and correct; no semantic node is duplicated, missing, or invented.
- [ ] A failed generated reference was regenerated before the set was shown to the user.

## Script fidelity

- [ ] Every page lists a real source span.
- [ ] Base frames have no `data-source-order`; click-triggered reveals start at `1` and are unique, gapless, and strictly increasing.
- [ ] Forward navigation follows the approved storyboard exactly.
- [ ] No later idea appears early; no claim, number, quote, or source is invented.
- [ ] Screen copy is selective and does not reproduce the full narration.

## Visual communication

- [ ] Every page has one explanatory non-text visual.
- [ ] Every page has one dominant element; nothing reads as an equal-card template.
- [ ] Visual metaphors explain the current point rather than decorate it.
- [ ] Layouts vary with information structure while the locked style stays consistent.
- [ ] Images are sharp, intentionally cropped, and never used as dim unreadable backgrounds.
- [ ] There are no emoji icons, rainbow accents, generic purple gradients, fake UI, or meaningless decoration.
- [ ] No headline uses a thick decorative underline beneath or through the glyphs; emphasis uses color, weight, spacing, a separate label, or a bounded block.
- [ ] The result avoids generic AI defaults: equal rounded cards, decorative glass panels, neon orbs, stock 3D icons, isometric networks, random blobs, and repeated bento layouts.
- [ ] Every page contains at least one topic-specific choice that could not be reused unchanged for an unrelated AI or productivity script.

## Layout safety

- [ ] Every page uses an approved `split`, `visual-first`, `stack`, or `evidence` layout model.
- [ ] Major content stays in Grid or Flexbox flow; absolute positioning is limited to small annotations inside a bounded visual container.
- [ ] Grid and Flex children that contain text or images use `min-width: 0` and `min-height: 0` where needed.
- [ ] Pages and visual containers have explicit overflow boundaries; no important content relies on `overflow: visible` to remain readable.
- [ ] A page that cannot fit at the required type sizes was split instead of clipped, hidden, or arbitrarily scaled down.
- [ ] Supplied screenshots are completely visible with `object-fit: contain`, unless an approved storyboard crop explicitly says otherwise.
- [ ] Every click's related visual and text changes share one `.reveal` wrapper and one unique `data-source-order`.

## Readability at 1920x1080

- [ ] Main title is at least 88px.
- [ ] Body text is at least 32px.
- [ ] Labels and supporting text are at least 22px.
- [ ] Text contrast is sufficient and lines are not excessively long.
- [ ] No content overlaps, clips, or leaves the stage boundary.
- [ ] Important content remains legible after scaling the browser window down.

## Motion and interaction

- [ ] Only `transform` and `opacity` are animated.
- [ ] Reveal opacity and transform animate in the same Web Animations call; the element does not jump to its final position before fading.
- [ ] Every reveal has a meaningful `data-motion` value: `rise`, `place`, `slide`, `connect`, `fade`, or `emphasis`.
- [ ] Cards, text, relationships, large images, and conclusions do not all reuse one generic pop-in.
- [ ] Forward reveals use roughly 420-480 ms, reverse hides 280-320 ms, and page entry about 420 ms, while navigation state still updates immediately.
- [ ] The motion uses a gentle start-and-settle curve rather than a front-loaded ease-out or near-instant flash; control responsiveness is not achieved by shortening visual interpolation below perceptible duration.
- [ ] Reveal travel is 10-14px where movement is useful and semantic scale change is at most 3%; the full 1920x1080 stage is never scaled or translated as an animation.
- [ ] Persistent `will-change`, blur, backdrop blur, displacement filters, and other layer-heavy effects are not applied across all reveals.
- [ ] Only the currently animating element receives transient `will-change`; it is prepared one frame before playback and released after settling.
- [ ] Embedded raster images are asynchronously decoded before their first reveal to avoid a first-frame hitch.
- [ ] Large raster images remain stationary or use only a short opacity transition; they are not repeatedly scaled.
- [ ] Each click has one clear semantic purpose and settles without autoplay.
- [ ] Navigation state updates immediately; code does not await `animation.finished` or drop input while an animation is active.
- [ ] Rapid repeated clicks cancel or replace affected animations without queueing, freezing, or leaving an element half-visible.
- [ ] Right-half click, Space, Right, Down, and PageDown advance.
- [ ] Left-half click, Left, Up, Backspace, and PageUp go backward.
- [ ] Vertical wheel down advances and wheel up reverses; one continuous wheel or trackpad gesture triggers only one step.
- [ ] Horizontal wheel gestures do nothing, and Ctrl+wheel remains available for browser zoom.
- [ ] Backward navigation restores the exact prior settled state.
- [ ] Moving backward from a page's base frame opens the previous page with all its reveals visible.
- [ ] Home, End, and segmented-progress navigation work without wrapping at boundaries.
- [ ] The footer is compact and recording-safe: a simple page number and thin segmented page rail, without reveal-step fractions or a dense row of circular dots.
- [ ] The stage stays centered and proportional at multiple viewport sizes.
- [ ] Actual forward and reverse transitions were watched for stutter and stiffness, not inferred from settled screenshots alone.

## Single-file integrity

- [ ] No external JavaScript or animation library is required.
- [ ] Project-bound raster images are embedded as data URIs.
- [ ] Inline SVG has accessible labels when it conveys information.
- [ ] Opening the final HTML directly in a browser produces the complete presentation.
