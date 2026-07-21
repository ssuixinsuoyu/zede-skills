---
name: interactive-explainer
description: Turn a Chinese narration script into a polished 1920x1080 click-through visual explainer HTML for screen recording. Use for knowledge videos, tutorials, concept explanations, story-led explainers, and presentation-like scenes that must reveal content in strict script order, support forward/backward navigation, research current high-quality design references online before styling, compare visual reference images before storyboarding, avoid full-script captions or generic AI-looking visuals, and refine this skill's own rules or template when the user explicitly requests a persistent skill-level improvement.
---

# Zede Interactive Explainer（交互式视觉讲解）

Create one self-contained 16:9 HTML presentation that the user can advance and reverse while recording the screen. Keep every visual and click aligned to the narration order.

## First-use onboarding gate

On the first invocation of this skill in each new task or conversation, explain the complete user-facing rules before reading or analyzing the script, browsing design references, recommending styles, generating images, storyboarding, or building. Use the user's language and title the message `使用规则（首次使用必读）` for Chinese requests.

The briefing must clearly cover every category below:

1. **Required input** — the user must provide a complete narration script or a readable local file path. If it was already supplied, do not ask for it again.
2. **Fixed deliverable** — the result is a 1920x1080, 16:9, self-contained HTML file for manual screen recording. It does not produce PPTX, Remotion, TTS, autoplay, or a finished video.
3. **Confirmation flow** — onboarding acknowledgement, five-style recommendation, selection of 1-3 directions, comparable reference images, one locked style, storyboard and click-plan approval, then assets, HTML, and QA. Nothing later may begin before its confirmation gate is passed.
4. **Script fidelity** — pages and clicks follow the original order exactly. Do not preview later ideas, reorder the argument, or invent facts. Transitional or repeated narration may be omitted from the screen.
5. **Screen copy** — show only titles, keywords, short labels, and essential emphasis. Never spread the complete narration across the screen as subtitles.
6. **Visual standard** — every page needs one meaningful non-text visual and one clear focal point. No pure-text pages, generic AI decoration, meaningless imagery, repetitive equal-card layouts, thick decorative underlines, or unapproved screenshot cropping. Use HTML/CSS/SVG for simple explanatory graphics and generated raster imagery only when it adds real meaning.
7. **Motion standard** — one click reveals one idea, example, relationship, step, or conclusion. Motion must be smooth, restrained, semantic, reversible, and settle before waiting for the narration; no autoplay or distracting full-stage movement.
8. **Controls** — right-half click, forward keys, Space, or vertical wheel down advances; left-half click, backward keys, or wheel up reverses. Segmented page navigation, Home, and End are supported. Boundaries do not loop, and returning must restore the exact prior state.
9. **Revision behavior** — user feedback may revise the current deliverable. Change the reusable skill itself only when the user explicitly asks to feed the lesson back into the skill; keep such changes general rather than project-specific.

End with: `如果你已了解并接受以上规则，请回复“已了解，继续”。如果你还没有提供口播稿，请同时粘贴完整稿件或给出可读取的文件路径。`

Stop and wait for explicit acknowledgement. Do not begin Phase 1 in the same response. After acknowledgement, do not repeat this briefing again within the same task; if a task resumes, continue from its last unfinished confirmation gate.

## Non-negotiable gates

Do not skip or combine these confirmation gates:

0. **First-use onboarding** — explain all user-facing rules and obtain explicit acknowledgement, then stop.
1. **Style shortlist** — read the complete script, recommend styles, then stop.
2. **Reference images** — generate references only for the 1-3 styles selected by the user, then stop.
3. **Style lock** — obtain one final selected style before storyboarding.
4. **Storyboard approval** — show every page and click in source order, then stop.
5. **Build and QA** — generate assets and HTML only after storyboard approval.

If the user provides an explicit style or reference image and says to use it, treat that as the style lock. Still produce and confirm the storyboard before building.

## Required input

Require the complete narration script as pasted text or a readable local file path. Read the entire source before responding. Use Chinese for Chinese requests.

Fixed output contract:

- 1920x1080, 16:9.
- One self-contained `.html` file.
- Manual forward/backward interaction by stage click, keyboard, segmented page-progress controls, and vertical mouse wheel; no autoplay, TTS, PPTX, Remotion, or final video export.
- Native Web Animations API only; no external animation library.

## Phase 1: Recommend styles

Read [references/styles.md](references/styles.md) and [references/visual-research.md](references/visual-research.md). Analyze the script's subject, argument shape, emotional tone, evidence type, and dominant visual structures.

Before recommending styles, browse current online work from original design studios, motion studios, editorial designers, and reputable award platforms. Find topic- and structure-relevant examples rather than searching only for generic "presentation inspiration." Extract the grid, hierarchy, typography, palette, image treatment, material language, and motion principle. Do not copy a branded composition, logo, illustration, or proprietary asset.

In the first response after the onboarding acknowledgement, show all five built-in styles in a compact table. Include the exact immutable style ID plus a natural-language label; never translate, rename, or omit the ID. Include:

- style name;
- palette and typography;
- composition;
- imagery;
- motion character;
- best-fit topics;
- one limitation.

For each direction, include one direct link to an online project that informed the design language and name the specific principle being borrowed. Mark exactly one style as **recommended** and explain the content-specific reason in one sentence. Also allow a custom style description or reference image. Ask the user to select 1-3 directions. Do not produce a storyboard yet.

## Phase 2: Generate comparable references

Choose one representative beat from the script and use the same beat for every selected direction. Generate exactly one 16:9 reference image per direction with the built-in image generation tool.

Prompt rules:

- classify as `productivity-visual`, `scientific-educational`, or `stylized-concept` as appropriate;
- describe a presentation frame, not a website or dashboard;
- compare layout, palette, texture, illustration language, and hierarchy;
- use no long Chinese copy; allow only 1-3 short labels when necessary;
- prohibit logos, watermarks, fake data, decorative UI chrome, and unreadable pseudo-text;
- keep the same content and semantic visual across directions.

Build each prompt from a concrete reference synthesis: name the grid logic, type scale, color restraint, material treatment, image behavior, and motion character inferred from the selected online examples. Do not prompt with vague adjectives such as "premium," "modern," or "high-end" by themselves.

Show the generated images inline and ask the user to lock one style or request one targeted revision. Preview-only images may remain in the default generated-image location. Do not make the storyboard until one direction is locked.

Before showing any reference, inspect it at full readable size. Verify that all compared directions preserve the same semantic nodes and relationships, every short label is correct, and nothing is duplicated, missing, invented, or visually misleading. Regenerate a failed reference before presenting the set; never ask the user to choose from a semantically wrong image.

## Phase 3: Map the script

Read [references/storyboard-rules.md](references/storyboard-rules.md). Produce the required storyboard table in strict source order.

Use one click for one meaningful point: a claim, example, relationship, step, contrast, or conclusion. Omit redundant or transitional wording from the screen, but never reorder, prefigure later content, change the argument, or invent facts.

Every page must include at least one explanatory non-text visual. Prefer HTML/CSS/SVG for shapes, arrows, diagrams, and simple illustrations. Reserve raster image generation for imagery that materially improves understanding or mood.

Choose a safe layout model for every page before approval. Use flow-based `split`, `visual-first`, `stack`, or `evidence` layouts. Treat the 1920x1080 stage as a fixed recording canvas with a protected content area; do not plan major objects that depend on freehand pixel placement.

For screenshots and supplied evidence images, default to complete `object-fit: contain` display. Crop only when the storyboard explicitly names the crop and the omitted region is irrelevant to the spoken beat.

Stop and wait for explicit storyboard approval.

## Phase 4: Build

1. Copy [assets/base-template.html](assets/base-template.html) to the requested output location.
2. Read the chosen file under `assets/styles/` and inline it into the template's style-token slot.
3. Replace the sample pages with approved storyboard pages. Keep `data-source-order` values strictly increasing.
4. Build the complete layout skeleton before decoration or motion. Keep every major copy block, image, diagram, and relationship in normal Grid or Flexbox flow inside the template's safe content area. Use absolute positioning only for small annotations inside a bounded visual container; never use it for the page's main structure.
5. Verify the static settled state of every page before adding animation. Fix overflow by changing the layout model or splitting the page, never by hiding, clipping, or arbitrarily shrinking important content.
6. Give each page one dominant visual and vary composition according to the content structure.
   Never use a thick decorative underline beneath or through headline text. Use color, weight, spacing, a separate label, or a bounded color block instead.
7. Generate only the approved raster assets. Copy project-bound images out of the generated-image directory, resize/compress them, and embed them as data URIs so the deliverable remains one HTML file. Display screenshots with `contain` unless an approved crop says otherwise.
8. Wrap every click's complete semantic change in one `.reveal` container. DOM reveal order must equal `data-source-order`; do not duplicate the same order across separate elements.
9. Keep the supplied navigation state machine. Extend it only when required by the approved storyboard; do not replace it with browser timers, CSS keyframes, or an external library.

Motion contract:

- assign every reveal a semantic `data-motion`: `rise` for short copy, `place` for cards or objects, `slide` for ordered entries, `connect` for relationships, `fade` for screenshots or large raster images, and `emphasis` for supported conclusions. Do not give unrelated elements the same generic pop-in;
- animate reveal `opacity` and `transform` together; never let CSS jump to the final transform while only opacity animates;
- separate response time from visual duration: update navigation state immediately, but let forward reveals interpolate for about 420-480 ms, reverse hides for 280-320 ms, and page entry for about 420 ms. Use a gentle start-and-settle curve such as `cubic-bezier(.25,.1,.25,1)`; avoid front-loaded ease-out curves that make most opacity arrive in the first few frames;
- use 10-14 px of travel for `rise`, `place`, and `slide`, 1.5-3% scale change for placed objects or supported conclusions, and opacity only for large raster images. Do not scale or move the entire 1920x1080 stage;
- do not apply persistent `will-change`, blur, SVG displacement, or filters to every reveal; large numbers of promoted layers and raster effects cause stutter;
- prepare only the active reveal with transient `will-change` one animation frame before playback, then remove it immediately after settling. Warm embedded raster images with asynchronous decode at startup so their first reveal does not hitch;
- never gate navigation on `animation.finished`. Update state immediately, cancel or replace an in-flight animation on the affected element, and allow rapid clicks, keys, or wheel input to continue without dropped commands;
- after input stops, the current state must settle completely and remain still for narration.

For a custom locked style, follow the token contract in [references/styles.md](references/styles.md) and create an invocation-specific inline token block. Do not modify the installed skill.

## Phase 5: Validate

Read [references/quality-check.md](references/quality-check.md). Inspect the final file in a browser and fix failures before delivery.

Test at minimum:

- every forward state from the first page to the last;
- every backward state from the last page to the first;
- rapid repeated clicks while animation is active;
- left/right stage clicks, keyboard controls, segmented-progress jumps, and vertical mouse-wheel gestures;
- wheel down advances once and wheel up reverses once; trackpad inertia must not skip multiple steps, horizontal scrolling must do nothing, and Ctrl+wheel must remain available for browser zoom;
- multiple viewport sizes while preserving the 1920x1080 stage;
- a compact recording-safe footer: page number plus a thin segmented progress rail, without reveal-step fractions or a dense row of circular dots;
- settled-frame screenshots for overflow, overlap, hierarchy, and readability.

Inspect actual transitions, not only settled screenshots. If local-file browser access is blocked, run all structural checks but do not claim visual QA passed. Ask the user to open the file and provide the affected page number or settled-frame screenshot, then iterate before final completion.

Deliver the HTML path and a short control reminder. Do not claim completion before the final browser check passes.

## User-directed skill iteration

Update this skill itself only when the user clearly requests a persistent change, using language such as “以后默认这样”, “修改这个 Skill”, “把问题反馈到 Skill”, or “记住这条规则”. Treat ordinary requests to change one current HTML as project-only unless the user signals persistence.

When a persistent change is requested:

1. Inspect the concrete failure, correction, or desired behavior.
2. Separate project-specific taste from a reusable rule. Never store the current script, supplied images, brand details, personal data, output path, or one-off composition as a skill default.
3. Identify the smallest reusable change: workflow instructions in `SKILL.md`, planning rules in `references/storyboard-rules.md`, acceptance criteria in `references/quality-check.md`, style tokens in `assets/styles/`, or deterministic interaction behavior in `assets/base-template.html`.
4. Preserve the confirmation gates and fixed output contract unless the user explicitly changes them.
5. Patch only the necessary files. Do not create changelogs, retrospective notes, or extra documentation.
6. Validate edited HTML/JavaScript resources, verify structural invariants, and run `skill-creator/scripts/quick_validate.py` against the skill. Use a temporary dependency directory if PyYAML is unavailable; do not modify system Python.
7. Report which skill files changed, what future behavior changed, and what remained project-specific.

Do not silently broaden permission to modify other skills, unrelated files, or external systems. If a requested persistent rule conflicts with higher-priority instructions or would make the skill internally inconsistent, explain the conflict and request direction instead of applying it.
