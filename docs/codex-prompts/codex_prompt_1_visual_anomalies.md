# Codex Prompt 1 — Visual anomalies for `properties.db`

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

# 1. Add `plant_process.exe`

## Purpose

A small plant grows only when the user’s cursor is close to it. It represents attention, care, light, and the way meaning grows only near presence.

## Where it should appear

Show it only on selected properties:
- `p02`
- `p16`
- `p27`

It should appear only once per property opening. It should not appear globally on every page.

## Visual style

- Use inline SVG or DOM/CSS lines.
- Monoline outline style.
- No fill, or very minimal fill.
- Color should use existing CSS variables, preferably `var(--accent-2)`, `var(--accent)`, or `var(--line)`.
- The plant should look like a living line growing out of the interface, not a cute cartoon flower.

## Growth sequence

1. Initially show a tiny sprout with two very small leaves.
2. When the cursor is near the plant, the stem slowly grows upward.
3. Then one larger leaf appears.
4. Then four additional leaves appear gradually, one by one.
5. Leaf placement should be alternate along the stem, not symmetrical all at once.
6. Growth progresses only while the cursor is within a defined radius around the plant.
7. If the cursor leaves the radius, growth pauses immediately.
8. If the cursor comes back, growth resumes from the same growth stage.
9. Do not reset growth unless the property modal/page is closed.

## When fully grown

Show a subtle terminal toast:

```text
the plant reached its available explanation
```

The plant becomes clickable only after full growth.

## On click after full growth

- The plant should collapse/disintegrate into falling question marks.
- Question marks should fall downward with a gravity-like animation.
- They should remain lying near the bottom/near the plant for a few seconds.
- Then they should fade out.
- After disintegration, show:

```text
the plant exceeded lexical capacity
```

## Important

- The question marks should be elegant, not chaotic.
- Use maybe 12–20 question marks max.
- Some may be slightly rotated.
- Do not cover the main content.
- Performance must remain light.

---

# 2. Add `contemporary_shadow`

## Purpose

A black silhouette / simple human figure dances while the cursor is moving. It is connected to contemporary dance, bodily expression, and movement continuing after thought.

## Where it should appear

Show it only on:
- `p10`
- `p25`
- `p29`

It should appear only when the property is open.

## Visual style

- A small black figure or very dark silhouette.
- It can be SVG or CSS/HTML.
- It should be abstract and elegant, not cartoonish.
- It should resemble a minimal human silhouette or stick-figure-like body with filled black shape.
- It should feel like a shadow rather than an icon.

## Behavior

- The figure is idle when the mouse is still.
- When the user moves the mouse, the figure begins dancing.
- It should not follow exact mouse direction.
- It simply dances while motion is detected.
- It should not react to clicks.

## Dance movements

Cycle through several contemporary-dance-like poses:
1. Body undulates like a wave with raised arms.
2. Arms open to the sides and move like a sine wave.
3. Alternating lunges to left and right.
4. Slight fold/contract/release movement.
5. A delayed final reach upward.

## Duration

- The animation should last up to 15 seconds total after first activation.
- If the mouse stops, the figure pauses/freezes in its current or nearest pose.
- If the mouse moves again before 15 seconds, it continues.
- After 15 seconds of total dance time, it dissolves/fades away.

After disappearance, show a subtle toast:

```text
shadow completed movement without body
```

## Implementation notes

- Use CSS keyframes or class switching.
- Keep it lightweight.
- No complex physics.
- No canvas required unless already used elsewhere.

---

# 3. Add light leak effect

## Purpose

A soft light leak follows the cursor on selected properties. It should feel like light leaking through the interface.

## Where it should appear

Enable light leak only on:
- `p02`
- `p09`
- `p19`

It may also be reused locally by future lightbulb anomalies, but do not add that now unless the structure is easy.

## Behavior

- When the cursor moves over the property modal/content area, show a soft radial gradient following the cursor.
- It should feel like light leaking through the interface.
- Use CSS variables and subtle opacity.
- It should not reduce readability.
- It should disappear when the cursor leaves the area.

## Implementation idea

- Use CSS variables `--mouse-x` and `--mouse-y` updated on `mousemove`.
- Use a pseudo-element or absolutely positioned overlay.
- Respect `prefers-reduced-motion` if possible.

---

# 4. Add cursor reflection effect

## Purpose

On reflection/dream-boundary properties, the cursor briefly gets ghost reflections.

## Where it should appear

Only on:
- `p01`
- `p24`

## Behavior

- When the property opens, create 2 or 3 ghost cursor elements.
- They follow the real cursor with delay.
- One can mirror horizontal movement relative to the viewport center.
- Another can lag behind normally.
- They fade out after 10 seconds.
- Remove them from DOM after fade.

Message on start:

```text
cursor reflection detached
```

## Performance

- Use `requestAnimationFrame`.
- Only active for 10 seconds.
- No more than 3 ghost cursors.
- Respect reduced motion if possible.

---

# 5. Add memory focusing effect for `p06`

## Purpose

The main image/sample on `p06` is initially blurred. The user can hold the image to increase “memory resolution”.

## Where

Only on:

```text
p06 — Привычка возвращаться к пережитому с повышенной разрешающей способностью
```

## Behavior

- The main image/sample should initially be blurred.
- Show caption:

```text
hold to increase memory resolution
```

- While user holds mouse down or touch on the image:
  - blur gradually decreases;
  - saturation/contrast gently increases;
  - additional text layers appear one by one if available:
    - date
    - place
    - field note

If user releases early, show:

```text
focus interrupted
```

If held long enough, e.g. 4 seconds, show:

```text
image clear
meaning unstable
```

When released after full focus:
- image returns only slightly blurred, not fully blurred.

## Implementation

- Use CSS transitions and a timer.
- Support mouse and touch.
- Do not break normal image rendering for other properties.

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
- `maybeShowPlantProcess(propertyId)`
- `createPlantProcess(container)`
- `updatePlantGrowth(...)`
- `disintegratePlantIntoQuestions(...)`
- `maybeShowContemporaryShadow(propertyId)`
- `startShadowDance(...)`
- `enableLightLeak(container)`
- `startCursorReflections()`
- `enableMemoryFocus(propertyId, sampleElement)`
