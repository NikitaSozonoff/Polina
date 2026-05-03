# Codex Prompt 2 — Object and media anomalies for `properties.db`

You are editing an existing static one-page GitHub Pages site called `properties.db`.

## Project constraints

Tech stack:
- vanilla HTML
- CSS
- JavaScript
- no React
- no build tools
- no npm
- preserve current architecture
- do not rewrite the whole app
- add features modularly

Current project structure includes:
- `index.html`
- `style.css`
- `script.js`
- `data/clusters.js`
- `data/properties.js`
- `assets/photos/`
- `assets/videos/`
- `assets/audio/`
- `assets/drawings/`

The site is a poetic terminal/database archive with property cards `p01`–`p29`. It uses a dark monospace interface with CSS variables, modals/cards, clusters, and easter eggs.

## Visual language

All new features must match the existing visual style:
- dark soft-terminal aesthetic
- monoline / outline SVG objects
- no emoji
- no external image dependencies for UI objects
- no heavy libraries
- no autoplay audio
- all interactions must be lightweight and mobile-safe
- all animations should be subtle, dreamlike, slightly uncanny, not cartoonish

Use existing CSS variables where possible:
- `var(--bg)`
- `var(--bg-soft)`
- `var(--panel)`
- `var(--text)`
- `var(--muted)`
- `var(--accent)`
- `var(--accent-2)`
- `var(--line)`
- `var(--glow)`

Do not break existing navigation, existing property modals, existing piano/cat behavior, or existing cluster rendering.

---

# 1. Add `microscope_field`

## Purpose

A microscope appears as a small monoline archival object. When clicked, it opens a dark microscope-view overlay with a circular illuminated field in the center. Inside the circle, one random image from five user-provided specimen images is shown.

These are real specimen images that the user will add later.

## Where it should appear

Show it primarily on:

```text
p28 — Смена языка без потери голоса
```

Optionally also on:
- `p19`
- `p24`

It should appear only once per property opening. After use, the microscope disappears.

## Visual style

- The microscope itself should be an inline SVG.
- Monoline, no fill, stroke only.
- It should look like a recognizable microscope:
  - eyepiece
  - tube
  - arm
  - stage
  - base
- Use `currentColor` and CSS variables.
- It should match the piano/cat/object aesthetic.
- Do not use external images for the microscope icon.

## Behavior

1. Show microscope icon/object in a corner or inside the property modal.
2. On click:
   - open a full-screen or modal overlay;
   - overlay background should be almost black;
   - in the center, show a soft circular microscope field;
   - the circle should be light but not pure white;
   - use muted warm light, e.g. `rgba(230,224,214,0.75)`;
   - inside the circular field, display one random image from five specimen images.
3. The image should be clipped to the circular field.
4. On click anywhere on overlay or on a close control:
   - close the overlay;
   - remove/hide the microscope object.
5. Do not autoplay anything.
6. The microscope should not come back in the same property view.

## Expected image paths

```text
assets/photos/microscope/specimen_01.jpg
assets/photos/microscope/specimen_02.jpg
assets/photos/microscope/specimen_03.jpg
assets/photos/microscope/specimen_04.jpg
assets/photos/microscope/specimen_05.jpg
```

## If images are missing

Render a styled placeholder inside the circle:

```text
specimen image pending
```

Do not break the site.

Optional tiny caption inside/under overlay:

```text
specimen selected without stable reason
```

---

# 2. Add `light_cache` / oral lamp anomaly

## Purpose

A small lightbulb object appears as a surreal archive object connected with stored light, absurd warmth, and the existing photograph where a bulb/light is held in the mouth.

## Where it should appear

Show only on:
- `p02`
- `p09`
- `p25`

It should not appear on every page.

## Visual style

- Inline SVG lightbulb.
- Monoline outline.
- Visible bulb, small filament, base.
- Slightly floating or gently swaying.
- No emoji.
- No external image.
- Use existing CSS variables.

## Behavior

1. On hover, the bulb starts glowing softly.
2. It should also create a local light leak effect around it.
3. On click, randomly choose one of two behaviors.

## Behavior A: “stored light”

- The bulb disappears instantly, as if taken out of the interface.
- A soft afterglow remains for 1–2 seconds.
- Show toast:

```text
light stored orally for unknown reasons
```

## Behavior B: “external illumination failure”

- The bulb flashes brighter once.
- Then disappears.
- Small particles/dots/short light strokes disperse outward and fade.
- Show toast:

```text
illumination was not meant to remain external
```

## Important

- The flash must not be too bright or uncomfortable.
- No full-screen white flash.
- Respect reduced motion preferences if possible.

---

# 3. Add gothic cyberpunk terminal player

## Purpose

Add a terminal-style audio player for the unfinished `gothic cyberpunk` draft. It should not look like a normal audio player at first.

## Where it should appear

Show on:
- `p17`
- and/or `p29`

## UI

Render as a terminal-style object:

```text
gothic_cyberpunk_draft.wav
duration: 00:07
status: unfinished / therefore alive
signal quality: locally warm

[ play fragment ]
```

## Behavior

On click:
- Play `assets/audio/gothic-cyberpunk.mp3` if present.
- If file is missing, show:

```text
audio sample pending
```

After playback ends, show:

```text
composition ended before becoming a composition
```

## Implementation

- Do not autoplay.
- Browser audio should only start after user click.
- It is okay to use a hidden real `<audio>` element or JS-created `Audio`.
- If audio fails to load, show the missing-file message and do not throw console errors.

---

# 4. Improve existing piano SVG

If the project already has a piano easter egg SVG, improve it visually.

## Goal

Replace the current piano SVG with a more recognizable monoline grand piano in three-quarter view.

## Required visible elements

The piano must include:
- asymmetrical grand piano body;
- raised lid;
- lid prop/stick;
- visible keyboard;
- three legs;
- pedal lyre / pedal block;
- subtle internal soundboard line;
- no fill, only stroke;
- `currentColor`;
- technical sketch / archival diagram style.

## Behavior

Do not change existing piano behavior unless necessary. This task is mainly visual.

If behavior is already:
- appear after `p17`;
- play finite fragment;
- fade away;
- show final toast;

preserve it.

Preferred final toast remains:

```text
the fragment chose not to remain
```

---

# 5. Optional: media missing placeholders

Make sure all media samples can fail gracefully.

If an image/audio/video path is missing or a sample has `missing: true`, render a styled placeholder instead of broken UI.

Examples:
- image: `image sample pending`
- audio: `audio sample pending`
- video: `temporal sample pending`

This is important because real media files will be added later.

---

# General QA after this PR

After implementation, ensure:

1. The site still loads with no console errors.
2. All existing properties still open.
3. Missing images/audio do not break the app.
4. New features are only active on intended property IDs.
5. GitHub Pages-compatible relative paths are used:
   - `./assets/...`
6. No absolute paths starting with `/assets`.
7. No external dependencies except existing Google Font.
8. Motion is not excessive.
9. Features do not overlap each other in a broken way.
10. All new functions are named clearly and commented.

Suggested function names:
- `maybeShowMicroscope(propertyId)`
- `openMicroscopeField()`
- `getRandomSpecimenImage()`
- `maybeShowLightCache(propertyId)`
- `triggerLightBulbBehavior()`
- `renderGothicCyberpunkPlayer(container)`
- `playGothicCyberpunkFragment()`
- `renderMissingMediaPlaceholder(type)`
