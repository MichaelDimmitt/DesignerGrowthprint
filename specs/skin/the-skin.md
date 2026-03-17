# The Skin — Visual Design Language
## Extracted from UX Designer Scorecard + Competency Radar

Everything in this document is **how it looks and feels**. Nothing about what data exists, how scores are calculated, or what archetypes mean. You could swap this entire skin onto a cooking app and it would still work.

---

## 1. Typography Stack

Three fonts, three jobs. This is the hierarchy that gives both tools their character.

### Display: Bebas Neue
- **Role:** Headlines, section numbers, big scores, the "wow" moments
- **Where it shows up:** Page title ("UX DESIGNER / SCORECARD"), section numbers (01, 02, 03), composite score in the progress ring, archetype name reveal, stat numbers in the sidebar, footer logo
- **Character:** Tall, compressed, all-caps. Feels athletic, editorial, like a magazine cover. Zero subtlety — it demands attention.
- **Sizes used:** 68px (page title), 32px (archetype name), 26px (card index numbers), 24px (section headers, stat numbers), 22px (score value next to rating dots), 16px (footer logo)
- **Note:** The Radar uses **Syne 700/800** for its title instead — rounder, more geometric, feels more "tech" than "editorial." Decision needed: pick one or keep both for distinct tool personalities.

### Body: DM Sans
- **Role:** Everything readable — descriptions, labels, buttons, body copy
- **Where it shows up:** Card names, card descriptions, button labels, meta input, subtitle text, archetype descriptions, tooltip text, all paragraph content
- **Weights used:** 300 (subtitle, light labels), 400 (body), 500 (buttons, career level buttons), 600 (check titles, growth item names), 700 (card names, archetype card names)
- **Sizes used:** 14px (card names, meta input), 13px (subtitle, archetype buttons), 12px (career buttons, check titles, skill labels), 11px (card descriptions, archetype focus, bar labels, italic disclaimers), 10px (check sub-text, asset names, compare buttons)
- **Character:** Clean, geometric sans. Reads well at small sizes without feeling clinical.

### Data/Labels: Space Mono
- **Role:** Anything that feels "system-level" — labels, statuses, metadata, tiny uppercase section dividers
- **Where it shows up:** "WORKSHOP ACTIVITY" tag, "DESIGNER" label, date display, "Novice / Expert" rating labels, all `.rp-` section titles, stat labels, asset statuses, year display in career buttons, status buttons, footer sub-text
- **Sizes used:** 10px (meta label, date), 9px (section titles, rating labels, stat max, growth scores, bar values), 8px (stat labels, status buttons, section titles, career years, footer sub), 7px (smallest stat labels)
- **Character:** Monospace = data. The mechanical precision signals "this is measured, this is a system." The heavy letter-spacing (1–3px) on uppercase labels creates that dashboard instrument feel.
- **Key pattern:** Always uppercase. Always letter-spaced. Never used for readable prose.

### Font Loading
```html
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;600;700&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
```
Radar additionally loads:
```html
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@700;800&display=swap" rel="stylesheet">
```

---

## 2. Color System

### Dark Theme Surfaces (the foundation)

| Token | Hex | Role |
|-------|-----|------|
| `--bg` | `#08090E` | Deepest background. Page canvas. Almost-black with a blue undertone. |
| `--surface` | `#10121A` | Sidebar background. One step up from void. |
| `--surface2` | `#181B27` | Elevated surfaces: stat cards, career badges, growth items, bar tracks. |
| `--surface3` | `#1E2133` | Card background. The "paper" things sit on. |
| `--border` | `#252836` | Default borders. Barely visible separation lines. |
| `--border-accent` | `#2D3147` | Hover border state. Slightly more visible. |

The Radar uses slightly different values but the same logic: `#0B0B0F` as its deepest bg.

**The key insight:** The surface stack is extremely tight — only ~15 lightness points from darkest to lightest. This keeps the dark theme feeling like one continuous space rather than a stack of boxes. Things "emerge from the dark" rather than "sit on layers."

### Text Opacity Hierarchy

| Token | Hex | Opacity Equivalent | Role |
|-------|-----|--------------------|------|
| `--text` | `#E8EAF0` | ~92% white | Primary text. Card names, input text, selected states. |
| `--text-dim` | `#6B7194` | ~42% white | Secondary text. Descriptions, labels, unselected items. |
| `--text-muted` | `#3D4162` | ~24% white | Tertiary. Barely-there labels, card index numbers, disabled states. |

The Radar uses raw `rgba(255,255,255,0.XX)` values instead of tokens — same concept, less organized:
- 0.55 = unselected archetype names
- 0.45 = radar axis labels
- 0.35 = section labels, unselected buttons
- 0.25 = sub-descriptions
- 0.20 = italic disclaimers
- 0.06–0.08 = grid lines, faint borders

### Accent Colors (per-skill / per-archetype)

**Scorecard — Skill Colors (10 competencies):**

| Skill | Color | Glow (12% opacity) |
|-------|-------|---------------------|
| User Research | `#FF4D6A` | `rgba(255,77,106,0.12)` |
| Information Architecture | `#FF8A4D` | `rgba(255,138,77,0.12)` |
| Interaction Design | `#FFC645` | `rgba(255,198,69,0.12)` |
| Visual Design | `#4DDB6A` | `rgba(77,219,106,0.12)` |
| Design Systems | `#00E5C7` | `rgba(0,229,199,0.12)` |
| Accessibility | `#38BDF8` | `rgba(56,189,248,0.12)` |
| Product Strategy | `#818CF8` | `rgba(129,140,248,0.12)` |
| Design Leadership | `#A78BFA` | `rgba(167,139,250,0.12)` |
| Design Operations | `#F472B6` | `rgba(244,114,182,0.12)` |
| Prototyping & Craft | `#FB7185` | `rgba(251,113,133,0.12)` |

**Radar — Archetype Colors (7 archetypes):**

| Archetype | Color | Glow (30% opacity) |
|-----------|-------|---------------------|
| Experience Storyteller | `#FF3C64` | `rgba(255,60,100,0.3)` |
| Systems Architect | `#00D4FF` | `rgba(0,212,255,0.3)` |
| Brand Worldbuilder | `#FFB800` | `rgba(255,184,0,0.3)` |
| Interaction Crafter | `#A855F7` | `rgba(168,85,247,0.3)` |
| Service Designer | `#34D399` | `rgba(52,211,153,0.3)` |
| Research Strategist | `#F472B6` | `rgba(244,114,182,0.3)` |
| Creative Technologist | `#FB923C` | `rgba(251,146,60,0.3)` |

**The color-glow pattern:** Every accent color has a companion "glow" at low opacity. This glow is used for: backgrounds of selected/active states, box-shadows on rated cards, icon badge backgrounds, checked item highlights. The formula is `rgba(r,g,b, 0.08–0.15)` for subtle fills and `rgba(r,g,b, 0.25–0.30)` for ambient atmosphere (Radar's background blobs).

### Named CSS Variables (Scorecard only)

The Scorecard promotes its most-used accents to named variables:
```css
--coral: #ff4d6a;        /* Primary accent, CTAs, gradient start */
--amber: #ffc645;        /* Gradient end, section 2 accent */
--teal: #00e5c7;         /* Checked state default, section 3 */
--sky: #38bdf8;          /* Section 4 accent */
--purple: #a78bfa;       /* Section 5 accent */
```
The Radar has no CSS variables — all color is inline.

---

## 3. Layout Patterns

### Scorecard: Sidebar + Main (Two-Column Sticky)

```
┌──────────────────────────────┬──────────────────┐
│                              │                  │
│          MAIN FORM           │  STICKY SIDEBAR  │
│       (scrolls, 760px)       │   (380px, fixed  │
│                              │    full-height)  │
│  ┌────────┐  ┌────────┐    │                  │
│  │ Card   │  │ Card   │    │  Progress Ring   │
│  └────────┘  └────────┘    │  Archetype       │
│  ┌────────┐  ┌────────┐    │  Stats Grid      │
│  │ Card   │  │ Card   │    │  Radar           │
│  └────────┘  └────────┘    │  Bars            │
│                              │  Growth Areas    │
│                              │                  │
└──────────────────────────────┴──────────────────┘
```

- Main column: `max-width: 760px`, centered with `margin: 0 auto`, `padding: 44px 32px 80px`
- Sidebar: `width: 380px`, `position: sticky; top: 0; height: 100vh; overflow-y: auto`
- Sidebar has its own thin scrollbar (`scrollbar-width: thin`)
- At `≤1060px`: sidebar hides, mobile-results div appears below the form
- At `≤640px`: card grid goes single column
- At `≤560px`: checklist goes single column

### Radar: Controls + Chart (Side by Side)

```
┌───────────────────────────────────────────────────┐
│  HEADER (title + subtitle)                         │
├──────────────┬────────────────────────────────────┤
│              │                                    │
│  CONTROLS    │         ROSE CHART                 │
│  (280px      │      (responsive SVG,              │
│   fixed)     │       340–560px)                   │
│              │                                    │
│  Archetype   │                                    │
│  Level       │                                    │
│  Compare     │                                    │
│  Strengths   │                                    │
│              │                                    │
└──────────────┴────────────────────────────────────┘
```

- Container: `max-width: 1100px`, centered, `padding: 40px 24px 60px`
- Controls: `flex: 0 0 280px; min-width: 240px`
- Chart area: `flex: 1; min-width: 300px`
- Chart sizes itself via JS: `Math.min(Math.max(containerWidth * 0.7, 340), 560)`
- The whole thing wraps at narrow widths via `flex-wrap: wrap`

### Card Grid

- `display: grid; grid-template-columns: 1fr 1fr; gap: 12px`
- Cards have `padding: 20px`, `border-radius: 8px`
- Each card has a large faded index number (`opacity: 0.3`) in the top-right corner — purely decorative, gives the grid a magazine-editorial feel

### Checklist Grid

- Same `1fr 1fr` grid at `gap: 10px`
- Items are `display: flex; align-items: flex-start; gap: 10px`
- Checkbox is `20×20px`, `border-radius: 4px`

---

## 4. Signature Visual Effects

### The Grain Overlay

Both tools use an identical film-grain texture layered over everything:

```css
.grain {
  position: fixed; inset: 0;
  pointer-events: none;
  z-index: 9999;
  opacity: 0.025;  /* Scorecard: 0.025, Radar: 0.03 */
  background-image: url("data:image/svg+xml,...feTurbulence...");
}
```

This is an SVG `feTurbulence` filter (`fractalNoise`, `baseFrequency: 0.9`, `numOctaves: 4`) rendered as a data URI. It adds a subtle analog texture that prevents the UI from feeling like a flat Figma mockup. Barely visible but you'd miss it if removed.

### Ambient Glow Blobs (Radar only)

Two huge radial gradients pinned to opposite corners, blurred to 80px:
```
Top-left: radial-gradient(circle, archetypeGlow 0%, transparent 70%)
Bottom-right: radial-gradient(circle, compareGlow 0%, transparent 70%)
```
These shift color with archetype selection (0.8s ease transition). They create a "mood lighting" effect — the whole page breathes the archetype's color.

### Card Glow on Interaction

When a scorecard card is rated:
```css
.card.rated {
  box-shadow: 0 0 18px var(--card-glow);
  border-color: [skill-color]35;  /* 35 = ~21% opacity hex */
}
```
The glow radiates outward, making rated cards subtly "light up" compared to unrated ones.

### Rating Dot Fill Animation

- Empty dot: `border: 2px solid var(--border)`, transparent fill
- Hover: `border-color` shifts to skill color, `transform: scale(1.12)`
- Filled: `background` and `border-color` match skill color, plus `box-shadow: 0 0 10px [glow]`
- The number inside flips from `--text-muted` to `--bg` (dark on colored background), gains `font-weight: 700`
- Toggle behavior: clicking an already-filled dot clears it (sets to 0)

### Progress Ring (SVG)

- Two overlapping `<circle>` elements on the same center
- Background ring: `stroke: #1e2133`
- Progress ring: `strokeDasharray: circumference`, `strokeDashoffset: circumference - (pct/100) * circumference`
- `strokeLinecap: round` for soft endpoints
- `transition: stroke-dashoffset 0.6s ease` for smooth fill animation
- Bebas Neue number centered inside, Space Mono "/ 100" below it

### D3 Rose Chart (Radar)

The rose chart isn't a polygon — it uses **quadratic Bezier curves** between data points for organic shapes:

```javascript
// For each pair of adjacent points, draw a Q curve through the point
// with the control point AT the data point and the endpoint at the
// midpoint between current and next
path += `Q${curr[0]},${curr[1]} ${cpx},${cpy}`;
```

**Layer stack (bottom to top):**
1. Grid rings — 5 concentric circles at `rgba(255,255,255,0.06)`, outermost slightly thicker
2. Axis spokes — lines from center to each competency label
3. Compare shape (if active) — dashed stroke (`6,4`), very low fill opacity (0.08), separate Gaussian blur glow filter
4. Main glow shape — same path, no stroke, 12% fill opacity, `feGaussianBlur stdDeviation="8"` filter
5. Main shape — 15% fill, 2px solid stroke at 90% opacity
6. Data point dots — three concentric circles per point: 6px outer glow (25% opacity), 3.5px solid dot, 1.5px white center highlight
7. Score labels — per-competency number positioned just beyond the data point

**Animation:** All shapes animate from previous state to new state using D3's `attrTween` with per-value interpolation over 800ms (`easeCubicOut`). Data point dots stagger in with 50ms delays. Score labels fade in after 600ms.

### Sidebar Radar Chart (Scorecard)

Simpler SVG — straight `<polygon>` (no curves), no animation, no glow filters. A static React-rendered SVG:
```jsx
<polygon points={dataPts} fill="url(#rg)" stroke="#ff4d6a" strokeWidth="1.5" opacity="0.85" />
```
With a three-stop linear gradient fill (coral → purple → teal, all at 10–20% opacity).

---

## 5. Interaction Patterns

### Hover States
- Cards: `border-color` brightens one step (`--border` → `--border-accent`)
- Dots: scale to 112%, border shifts to skill color
- Buttons (career, compare): background fills with `[color]12` (very faint), border brightens
- Status buttons: border shifts to status color
- Ghost buttons: border and text shift to `--coral`
- Fill buttons: background darkens slightly (`#ff4d6a` → `#ff3355`)

### Selected / Active States
- Career buttons: border goes `--coral`, bg goes `--coral-glow`, text goes full `--text`
- Status buttons: border, text, and bg all shift to the status color at appropriate opacities
- Checked items: border goes check-color, bg goes check-glow, checkbox fills solid, checkmark fades in
- Archetype buttons (Radar): bg tints with archetype color, dot gets `box-shadow: 0 0 12px`, name goes bold + white

### Transitions
- Almost everything: `0.2–0.3s ease` for interaction feedback
- Theme/color shifts: `0.5–0.8s ease` for ambient mood changes
- D3 chart morphing: `800ms easeCubicOut`
- Progress ring: `0.6s ease` on stroke-dashoffset
- Bar fills: `0.5s ease` on width

---

## 6. Light / Dark Mode Toggle (Standard Component)

Every tool ships with a theme toggle. **Default is light mode.** The toggle lives fixed in the top-right corner and persists across the session.

### The Toggle Element

A pill-shaped track (48×24px) with a sliding circle knob (18px). Moon icon on the left, sun icon on the right. The knob slides from left (dark) to right (light) with a springy `cubic-bezier(0.68, -0.15, 0.32, 1.15)` easing over 0.4s. Hidden during print.

```css
.theme-toggle {
  position: fixed;
  top: 20px;
  right: 24px;
  z-index: 1000;
  width: 48px;
  height: 24px;
  border-radius: 12px;
  border: 1px solid var(--border);
  background: var(--surface2);
  cursor: pointer;
  display: flex;
  align-items: center;
  padding: 0 4px;
  justify-content: space-between;
  transition: background 0.4s, border-color 0.4s;
}
.theme-toggle .knob {
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background: var(--text);
  position: absolute;
  transition: left 0.4s cubic-bezier(0.68, -0.15, 0.32, 1.15);
}
/* Dark mode: knob on left. Light mode: knob on right. */
```

### Implementation Pattern

The toggle sets a `data-theme` attribute on the `<html>` element (`"light"` or `"dark"`). All CSS variables are defined twice — once at `:root` (light, the default) and once at `[data-theme="dark"]`.

```css
/* LIGHT (default) */
:root {
  --bg: #f2f3f7;
  --surface: #ffffff;
  --surface2: #f5f6fa;
  --surface3: #ffffff;
  --border: #dfe1e8;
  --border-accent: #c8cad4;
  --text: #1a1a2e;
  --text-dim: #5c5f7a;
  --text-muted: #9b9db3;
  /* Accent colors stay the same or shift slightly darker for contrast on light bg */
}

/* DARK */
[data-theme="dark"] {
  --bg: #08090e;
  --surface: #10121a;
  --surface2: #181b27;
  --surface3: #1e2133;
  --border: #252836;
  --border-accent: #2d3147;
  --text: #e8eaf0;
  --text-dim: #6b7194;
  --text-muted: #3d4162;
}
```

### Light Theme Surface Stack

| Token | Hex | Role |
|-------|-----|------|
| `--bg` | `#F2F3F7` | Page canvas. Warm off-white with slight blue undertone. |
| `--surface` | `#FFFFFF` | Sidebar, elevated panels. Pure white. |
| `--surface2` | `#F5F6FA` | Stat cards, growth items, bar tracks. Barely-gray. |
| `--surface3` | `#FFFFFF` | Card backgrounds. White. |
| `--border` | `#DFE1E8` | Default borders. Soft gray. |
| `--border-accent` | `#C8CAD4` | Hover borders. Slightly more visible. |

### Light Theme Text

| Token | Hex | Role |
|-------|-----|------|
| `--text` | `#1A1A2E` | Primary text. Near-black with blue undertone. |
| `--text-dim` | `#5C5F7A` | Secondary. Descriptions, labels. |
| `--text-muted` | `#9B9DB3` | Tertiary. Faint labels, placeholders. |

### Accent Color Adjustments for Light

Accent colors from the dark theme are generally vivid enough to work on white, but some need slight darkening to maintain contrast:

- Yellows/ambers: Darken 10–15% (e.g., `#ffc645` → `#e6a800`)
- Light greens/teals: Darken 10% (e.g., `#4ddb6a` → `#2db84d`, `#00e5c7` → `#00c4aa`)
- Light blues: Generally fine as-is
- Everything else: Test at 4.5:1 contrast ratio against white; darken if needed

### Grain Overlay in Light Mode

Reduce opacity from 0.025 to 0.012 — the noise shouldn't dirty the white backgrounds but should still prevent the flat-digital feel.

### Ambient Glows in Light Mode (Radar only)

Reduce glow opacity from 0.3 to 0.08. The colored blobs should tint the background subtly, not overpower the light canvas.

### What Transitions on Theme Switch

All of these animate at `0.4s ease`:
- `background` and `background-color` on body, surfaces, cards, inputs
- `color` on all text
- `border-color` on all bordered elements
- `box-shadow` on glows
- Toggle knob position

### Toggle State Management

```javascript
// React: useState — always start light
const [isDark, setIsDark] = useState(false);

useEffect(() => {
  document.documentElement.setAttribute('data-theme', isDark ? 'dark' : 'light');
}, [isDark]);
```

**Default is light.** Always. The toggle is there for people who prefer dark, but the first thing they see is light mode.

---

## 7. Print Styles

The Scorecard includes a full print stylesheet:
- Background goes white, text goes dark
- Grain overlay hidden
- Sidebar hidden; mobile-results forced visible
- Cards and items get light gray backgrounds (`#fafafa`) and borders (`#ddd`)
- `break-inside: avoid` on all cards and items
- `print-color-adjust: exact` on filled dots, selected buttons, checked items
- Action buttons hidden
- Title gradient replaced with solid `#c0392b`

---

## 8. Responsive Breakpoints

| Breakpoint | What Changes |
|------------|--------------|
| `≤1060px` | Scorecard sidebar hides, mobile results panel appears below form |
| `≤640px` | Card grid goes single column |
| `≤560px` | Checklist goes single column |
| `≤500px` (Radar) | Axis label font-size drops from 10.5px to 9px |

---

## 9. What's NOT in the Skin

These things are engine concerns, not skin concerns:
- What the 10 competencies are or what they're called
- How many career levels exist
- How archetype detection works
- What the scoring formula is
- What the benchmark data values are
- Whether there are 6 or 7 archetypes
- What "Professional Presence" items exist
- The JSON shape of user assessment data
