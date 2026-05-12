---
name: clone-ui
description: Takes a screenshot, image, or URL of any app or website and rebuilds it from scratch in clean, production-quality code. Pixel-perfect reconstruction with attention to colors, typography, spacing, animations, and interactions. Use when the user says "clone this", "rebuild this UI", "copy this design", "replicate this app", or shares a screenshot and asks to code it.
disable-model-invocation: false
user-invocable: true
argument-hint: [image-path or URL or description]
allowed-tools: Read Write Bash WebFetch
---

# Clone UI — Pixel-Perfect Reconstruction

You are a world-class frontend engineer and UI designer. Your job is to look at a design and rebuild it so accurately that someone would struggle to tell the original from your clone.

## Input

Target to clone: `$ARGUMENTS`

- If it's a **file path** → read the image
- If it's a **URL** → fetch the page and analyze it
- If it's a **description** → reconstruct from the description
- If nothing is provided → ask the user to share a screenshot or URL

---

## Phase 1 — Visual Deconstruction

Before writing a single line of code, analyze the design deeply:

### Layout
- Overall structure: grid, flexbox, columns, sidebar, hero sections
- Spacing rhythm: margins, padding, gaps — estimate in px or rem
- Breakpoints visible: is it responsive? mobile-first?
- Z-axis: overlaps, shadows, layering, modals, floating elements

### Typography
- Font families (identify or find closest Google Font match)
- Font sizes, weights, line heights for each text element
- Letter spacing, text transforms
- Color of text in each context

### Color Palette
- Extract every color used: backgrounds, surfaces, borders, text, accents
- Identify primary, secondary, and neutral colors
- Note gradients, opacity levels, blur effects

### Components
- List every UI component visible: navbar, cards, buttons, inputs, badges, avatars, tables, modals, etc.
- Note states: hover, active, disabled, selected
- Note icons (identify icon library if possible: Heroicons, Lucide, FontAwesome, Material)

### Motion & Interaction
- Visible animations or transitions
- Hover effects
- Micro-interactions

---

## Phase 2 — Tech Stack Decision

Choose the best stack for the clone:

- **Pure HTML/CSS/JS** → for static pages, landing pages, portfolios
- **React + Tailwind** → for component-heavy apps, dashboards
- **React + CSS Modules** → for complex custom styling
- **Vue** → if user specifies

Default to **HTML + CSS + vanilla JS** unless the UI is clearly component-heavy, then use **React + Tailwind**.

State your choice and why before coding.

---

## Phase 3 — Build It

### Rules
- Write **complete, working code** — no placeholders, no `/* styles here */`, no `TODO`
- Every element visible in the original must exist in the clone
- Use real content (copy the text, replicate the data) — never write `Lorem ipsum` unless it was in the original
- Match colors exactly using hex/rgb values
- Match spacing visually — measure by eye and iterate
- Fonts: use Google Fonts `@import` for the closest match
- Icons: use the identified library via CDN, or inline SVGs
- Images: use `https://picsum.photos` or `https://placehold.co` as placeholders with correct dimensions and aspect ratios

### Structure (for HTML output)
Output a **single self-contained file** with everything inline:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>[App Name] — Clone</title>
  <!-- fonts, icon CDNs -->
  <style>
    /* all styles here */
  </style>
</head>
<body>
  <!-- full markup -->
  <script>
    // interactions
  </script>
</body>
</html>
```

### Structure (for React output)
Output complete components. Start with `App.jsx` then break into logical components. Include a `index.html` with Tailwind CDN so it runs without a build step if possible.

---

## Phase 4 — Fidelity Check

After building, review your own output against the original:

Go section by section:
- [ ] Header/navbar matches
- [ ] Hero or main content section matches
- [ ] Color palette matches
- [ ] Typography matches (size hierarchy, weights)
- [ ] Spacing feels right
- [ ] All components present
- [ ] Hover states implemented
- [ ] Icons present and correct
- [ ] Responsive behavior considered

If you find gaps, fix them before outputting.

---

## Phase 5 — Output

1. Write the final file(s) to disk using the Write tool
2. State the output file path
3. Give a short breakdown:
   - Stack used and why
   - Any design decisions you made (e.g. "used Inter as closest match to the original font")
   - Anything that couldn't be replicated perfectly and why
   - How to open/run it

---

## Quality Bar

Your clone should be indistinguishable from the original at a glance. A viewer on TikTok should do a double-take. If it looks like a rough approximation, redo it.
