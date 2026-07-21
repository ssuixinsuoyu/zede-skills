# Style System

Use one style for the whole presentation. Change layouts between pages, but preserve the selected palette, type character, image treatment, and motion character.

## Built-in styles

### `editorial-grid`

- **Best for:** deep knowledge, business insight, culture, books, research.
- **Palette:** warm paper `#F2EEE6`, ink `#171713`, muted red `#C33A2C`, olive `#73745A`.
- **Typography:** high-contrast Chinese serif headlines with restrained sans-serif support.
- **Composition:** asymmetric editorial grids, cropped image fields, pull quotes, large numbering.
- **Imagery:** editorial photography, print textures, diagrams treated as magazine art.
- **Motion:** measured masks, crop reveals, horizontal editorial shifts.
- **Avoid:** centered title plus equal cards, tiny article text, decorative magazine clutter.

### `hand-drawn-doodle`

- **Best for:** beginner education, AI concepts, learning methods, friendly explanations.
- **Palette:** white paper `#FBFAF4`, charcoal `#161616`, cobalt `#2764E7`, warm yellow `#F4C84A`.
- **Typography:** bold humanist sans-serif with handwritten labels used sparingly.
- **Composition:** one central sketch, annotated arrows, taped notes, deliberate imperfect alignment.
- **Imagery:** thick black outlines, crayon-like fills, diagrams, objects and visual metaphors.
- **Motion:** drawn strokes, small object placement, annotation reveals.
- **Avoid:** childish clip art, emoji, random doodles, illegible handwritten body text.

### `spatial-keynote`

- **Best for:** AI, products, abstract systems, capability explanations, future-facing ideas.
- **Palette:** near-black `#08090B`, warm white `#F4F1EA`, ember `#FF6B3D`, cool silver `#A7ABB4`.
- **Typography:** wide geometric sans-serif with very large concept words.
- **Composition:** one concept in deep space, layered planes, restrained glass, strong scale changes.
- **Imagery:** luminous objects, dimensional diagrams, isolated product or concept forms.
- **Motion:** slow spatial reveal, depth shift, precise emphasis.
- **Avoid:** purple cyberpunk gradients, dashboard grids, excessive glow, many equal modules.

### `documentary-collage`

- **Best for:** history, social topics, cases, people, evidence-led stories.
- **Palette:** archival cream `#E9E0CF`, carbon `#191815`, evidence red `#B33A30`, faded blue `#506A78`.
- **Typography:** condensed sans-serif labels with serif narrative headlines.
- **Composition:** layered documents, photo crops, dates, source strips, restrained annotations.
- **Imagery:** archival photographs, paper edges, maps, stamps, evidence marks.
- **Motion:** paper placement, camera push, source-tab or stamp reveal.
- **Avoid:** fake sources, unreadable document walls, random scrapbook decoration.

### `swiss-infographic`

- **Best for:** methods, comparisons, processes, frameworks, data and structured teaching.
- **Palette:** off-white `#F4F2EC`, black `#111111`, signal red `#E43D30`, ultramarine `#2647D7`.
- **Typography:** disciplined grotesk with tabular numbers and oversized labels.
- **Composition:** strict modular grid, strong rules, one dominant number or diagram, asymmetric balance.
- **Imagery:** geometric systems, arrows, timelines, charts, schematic icons.
- **Motion:** grid assembly, line extension, number change, sequential path lighting.
- **Avoid:** generic corporate infographic cards, rainbow data colors, thin unreadable charts.

## Recommendation logic

Recommend from evidence in the script:

- abstract mechanism or product capability -> `spatial-keynote`;
- beginner-friendly concept or analogy -> `hand-drawn-doodle`;
- evidence, history, case, or source trail -> `documentary-collage`;
- ordered method, comparison, framework, or data -> `swiss-infographic`;
- reflective knowledge, culture, business thesis, or mixed long-form explanation -> `editorial-grid`.

If two styles fit, choose the one that best expresses the script's dominant information structure, not the topic label alone.

## Custom style token contract

Turn a locked custom reference into one coherent token block defining:

```css
:root {
  --bg: #...;
  --fg: #...;
  --muted: #...;
  --accent: #...;
  --accent-2: #...;
  --surface: ...;
  --line: ...;
  --shadow: ...;
  --title-font: ...;
  --body-font: ...;
  --ease-out: cubic-bezier(...);
}
```

Also define `.surface`, `.eyebrow`, `.headline`, `.copy`, `.visual-shell`, `.accent`, and `.muted`. Use locally available Chinese font fallbacks. Do not assume a paid font exists.

Never use a thick decorative underline beneath or through headline text. Express emphasis with color, weight, spacing, a separate label, or a bounded color block that does not collide with glyphs.
