# Codex Prompt 3 — Archive behavior anomalies for `properties.db`

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

Do not break existing navigation, existing property modals, existing piano behavior, or existing cluster rendering.

---

# 1. Upgrade existing cat anomaly

## Purpose

The cat should become a strange unregistered animal process. It should still be cute/warm, but also slightly uncanny and dreamlike.

## Visual style

- If possible, use inline SVG cat, not external image.
- It should be a monoline/outline walking cat with tail raised.
- It should not just slide across the screen.
- It should simulate walking through 2–3 simple frame states:
  - different leg positions;
  - slight tail movement;
  - small head/body bob.
- It should remain minimal and elegant.

## States

The cat should have these states:
- `walking`
- `sleeping`
- `purring`
- `detached` / `teleported`

## Basic behavior

1. Cat appears from screen edge.
2. Cat walks along bottom edge.
3. Cat may lie down near a card or near the `drift` button.
4. On click:
   - play cat purr audio if available:
     `assets/audio/cat-purr.mp3`
   - if the audio file is missing, show textual fallback:
     `purr...`
   - show:

```text
purr detected...
emotional noise reduced by 12%
```

## Click count behavior

Keep click count in session memory or local state.

### After 3 clicks

- Cat freezes and looks at the user.
- Show:

```text
cat refuses classification
```

- Tail stops moving for a moment.

### After 5 clicks

1. Cat glitches/shivers briefly.
2. Cat disappears abruptly, as if cut out from the screen.
3. From the place where the cat disappeared, symbolic paw traces begin moving toward the nearest screen edge.
4. Paw traces should look like elegant symbols, e.g.:

```text
∴ ∵ ∴ ∵
```

5. Some traces can rarely become:

```text
N
AT
GC
сон
trace
```

6. The traces move outward, then fade gradually.
7. Show:

```text
unregistered animal process is modifying the archive
```

8. Then show:

```text
visible body detached
```

9. When traces vanish, show:

```text
cat continued elsewhere
```

## If the cat appears again later

- It can reappear in a different part of the screen.
- Show:

```text
cat ignored spatial indexing
```

## Terminal command behavior

Remove or avoid explicit `summon cat` command.

If a terminal command `cat` already exists:
- It should not directly summon cat.
- It may answer:

```text
cat cannot be summoned
```

and then maybe the cat appears later with delay.

---

# 2. Add “database refuses linear reading” behavior

## Purpose

If the user clicks too quickly through clusters/properties/navigation, the archive should mildly object.

## Trigger

Detect rapid navigation clicks.

Example rule:
- 4 or more navigation actions within 2 seconds.

Navigation actions include:
- opening clusters;
- opening properties;
- random drift;
- unstable exits;
- map/back buttons.

## Effect

- Apply a brief text/interface glitch class for 300–600 ms.
- Show one random toast from:

```text
archive refuses linear reading
please stop pretending this is a normal database
navigation speed exceeds semantic tolerance
meaning requires slower access
the archive is not a menu
some entries prefer not to be opened in this order
```

## Important

- Do not block navigation.
- Do not show too often.
- Add cooldown, e.g. 10 seconds.
- Keep the glitch subtle.

---

# 3. Add genome assembly widget with CIGAR and falling letters

## Purpose

The widget should look like a terminal-based bioinformatics process, but gradually become poetic and uncanny. It should reference genome assembly, CIGAR strings, reads, contigs, annotation, and unstable meaning.

## Where

Show on:

```text
p28 — Смена языка без потери голоса
```

## UI

Add a button:

```text
[ run assembly ]
```

On click:
- Open or expand a terminal log area.
- Lines appear progressively, like a running process.
- Do not render all instantly.
- Use monospace.

## Core log content

Include this core sequence:

```text
$ sciaridae_assembly --input archive_reads.fastq --mode unresolved

loading reads...
read_001 ATGCTAGGCTAANNNCTAG
read_002 TTAACGATCGGATTA
read_003 NNNGCTAGGCTTAC

checking CIGAR strings...
read_014  37M2I5M1D12M
read_015  18M4S  soft-clipped: silence
read_016  9M1I9M  insertion: voice

reference genome: unavailable
using memory as temporary scaffold...

annotation:
gene_01: language_shift
gene_02: structural_tenderness
gene_03: unfinished_music

warning:
letters falling out of alignment...

contig_07 started singing and was excluded from the analysis

assembly complete: incomplete by design
```

## Randomization

Each run may include a few random additional genes/events selected from arrays.

Important:
- Do not use AI generation.
- Use predefined arrays only.
- Keep the style controlled.

Example genes:
```text
dream_syntax
mirror_instability
light_storage
soft_clipped_silence
care_without_label
delayed_poetry_response
unresolved_tenderness
voice_preservation
```

Example events:
```text
read_023 aligned to a childhood object
reference genome refused to stay external
soft-clipped silence expanded during annotation
one insertion was identified as tenderness
unmapped reads formed a small animal
contig_07 started singing and was excluded from the analysis
```

## Falling letters effect

When the log reaches:

```text
letters falling out of alignment...
```

spawn 10–20 falling tokens near the terminal.

Tokens can be:

```text
A
T
G
C
N
voice
trace
сон
```

They should:
- fall slowly downward;
- fade;
- remain sparse;
- not cover important content;
- not become Matrix rain.

## Performance

- Use simple DOM spans and CSS animations.
- Remove tokens after animation ends.

---

# 4. Fragile entry warning and cracks

## Purpose

Add a one-time fragile entry experience for `p23`.

## Where

Only on:

```text
p23 — Наличие трещин в системе самоописания
```

## Before opening `p23`

Intercept opening and show warning modal:

```text
CAUTION: FRAGILE ENTRY.
Further access may alter the surface.
Proceed?
```

Buttons:

```text
[ proceed carefully ]
[ return ]
```

If user chooses return:
- Do not open `p23`.

If user proceeds:
- Open `p23`.
- Add cracks overlay around screen edges.

## Crack behavior

- Stage 1 cracks appear immediately upon entering `p23`.
- Count user interactions while `p23` is open:
  - mouse clicks;
  - key presses.
- After 2 interactions, add stage 2 cracks.
- After 4 interactions, add stage 3 cracks.
- After stage 3, no more cracks appear.
- Cracks should be thin, subtle, edge-based.
- They must not block reading content.
- Do not place cracks over main text.

## Fade logic

- Cracks should NOT begin fading while user remains in `p23`.
- Once user leaves `p23`, start a 30-second timer.
- After 30 seconds, cracks gradually fade out.
- Remove cracks from DOM after fade.

## One-time behavior

The warning should appear only once per session or once per localStorage state.

Cracks can appear again if the user resets archive state.

---

# 5. Improve tunnel mechanics with unstable exits

## Problem

Users should not need to guess hidden connections.

## Solution

Inside each property modal/card, show a small section:

```text
unstable exits:
[ into non-existing colors ]
[ dream boundary ]
```

These buttons correspond to linked property IDs already stored in each property’s `links` array.

## Behavior

When the user clicks an unstable exit:
- Open the linked property.
- Show a tunnel toast.

## Example tunnel messages

### `p14 → p19`

```text
tunnel stabilized:
p14 → p19
language leaked into non-existing colors
```

### `p05 → p27`

```text
tunnel stabilized:
p05 → p27
small things retained biological significance
```

### `p11 → p20`

```text
tunnel stabilized:
p11 → p20
damage successfully converted into contour
```

### `p17 → p28`

```text
tunnel stabilized:
p17 → p28
sound crossed into syntax
```

### `p01 → p23`

```text
tunnel stabilized:
p01 → p23
reflection exposed a crack in self-description
```

### `p07 → p22`

```text
tunnel stabilized:
p07 → p22
presence detected unspoken state before language did
```

## Milestone messages

If 3 tunnels are stabilized in one session, show:

```text
labyrinth topology updated
nonlinear reading confirmed
```

If 5 tunnels are stabilized, show:

```text
the archive recognizes your route
```

## Implementation

- Add optional `tunnelLabels` or `tunnelMessages` to properties data.
- If not present, fallback to generic `unstable exit`.
- Track stabilized tunnel count in localStorage or session state.

---

# 6. Optional subtle glitch effect

Add a reusable subtle glitch effect, used by:
- rapid navigation warning;
- maybe `p01`;
- maybe `p24`;
- maybe `drift`.

Effect:
- the text/interface slightly shakes for 300–500 ms;
- perhaps one layer shifts by 1–2 px;
- no strong flashing;
- no aggressive visual noise.

Message example:

```text
signal found at the wrong frequency
```

Use sparingly.

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
- `upgradeCatProcess()`
- `showCatTraceAnomaly(...)`
- `recordNavigationAction()`
- `maybeRefuseLinearReading()`
- `renderGenomeAssemblyWidget(container)`
- `runGenomeAssembly()`
- `spawnFallingAlignmentTokens(...)`
- `interceptFragileEntry(propertyId)`
- `showFragileWarning()`
- `activateFragileCracks()`
- `renderUnstableExits(property)`
- `stabilizeTunnel(fromId, toId)`
- `triggerSubtleGlitch(message)`
