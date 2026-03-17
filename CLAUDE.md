# CLAUDE.md

## What This Project Is

Designer Growthprint — a suite of interactive workshop tools for evaluating UX designers, their portfolios, and career trajectories. Built for the Jax UX design community in Jacksonville, Florida.

Potential alternate name The Designer's Compass
(Know where your going).

Three tools exist today. All are single-file HTML applications with embedded React (CDN), CSS, and vanilla JS. No build step.

## The Three Tools

**Portfolio Scorecard** (active development)
Structured evaluation of a designer's portfolio — shell, case studies, strategy. Reviewer rates dimensions on a 1–5 dot scale. Produces an overall health score and per-case-study breakdowns. 16 requirements in the backlog (REQ-01 through REQ-16).

**UX Designer Scorecard** (stable)
Self-assessment covering craft skills (10 competencies, 1–5 scale, max 50), soft skills (6 items, max 30), professional assets (10 items, 4-status enum, max 30), experience (10 binary checkboxes, max 20). Grand total: 130 pts. Auto-detects one of 6 archetypes from craft skill ratings.

**Competency Radar** (stable)
Benchmark radar charts for 7 archetypes × 5 career levels. 350-value data matrix. Rose chart with Bezier interpolation and animated transitions. The user selects an archetype and level — no self-rating.

## Architecture: Engine / Skin Separation

Every tool follows a strict separation. This is the most important pattern in the project.

- **Engine** = data models, scoring algorithms, state shape, archetype detection, dimension definitions. Framework-agnostic. Documented in `specs/engine/`.
- **Skin** = typography, colors, spacing, animation, responsive behavior, print styles. Documented in `specs/skin/`.

When modifying code, always identify whether a change is an engine concern or a skin concern. Never mix them in the same edit.

## File Map

```
src/websites/                          → What you EDIT (the apps)
  portfolio-scorecard/                 → Active development
  ux-designer-scorecard/               → Stable
  competency-radar/                    → Stable

specs/engine/                          → READ to understand scoring and data
  the-engine.md                        → Cross-tool models (both scorecards + radar)
  portfolio-scorecard-engine.md        → Portfolio scorecard–specific engine

specs/skin/                            → READ to understand visual language
  the-skin.md                          → Typography, color, surfaces, animation

specs/templates/                       → Blueprints for creating new tools
  engine-template.md

backlog/                               → READ to know what to build next
  portfolio-scorecard-requirements.md  → 16 REQs with specs, state changes, open Qs

reference/                             → Background material, consult rarely
  jacksonville-design-community-guide.md

transcripts/                           → Conversation history from claude.ai (JSON)
```

## Versioning Convention

Each tool iteration gets a new versioned file: `portfolio-scorecard-v0.1.html`, `portfolio-scorecard-v0.2.html`, etc. Always create a new version file. Never overwrite the previous version.

## Key Patterns in the Codebase

- **Single-file HTML apps**: React 18 via CDN, inline `<style>` blocks with CSS custom properties, inline `<script type="text/babel">` blocks
- **Rating dots**: 1–5 scale as a horizontal dot row. Tap fills dot + all previous. Tap active dot to deselect.
- **Pill buttons**: Career levels, archetypes, disciplines all use pill-style toggles
- **Dark theme surface stack**: Very tight lightness range (~15 pts). Things emerge from the dark, not sit on layers.
- **Typography hierarchy**: Bebas Neue (display/headlines), DM Sans (body), Space Mono (data labels — always uppercase, always letter-spaced)
- **Color accents**: Teal (#00b8a0) for Portfolio Scorecard, Coral (#e8365a) for UX Designer Scorecard. Each competency and archetype has a dedicated accent color via CSS custom properties.
- **Progress ring**: SVG circle with stroke-dasharray animation for composite percentage

## Two Divergent Archetype Systems (Known Tech Debt)

The Scorecard and Radar use completely different archetype and career level models with no mapping between them. This is documented in `specs/engine/the-engine.md` §1–3. Reconciliation is a future concern, not a current blocker.

## Requirements Backlog

REQ-01 through REQ-12 and REQ-14 through REQ-16 are ready to build. REQ-13 (Portfolio Purpose Framework) is exploratory and must always remain last — it requires a scorecard version bump before implementation. Each REQ includes: current state, requirement, suggested implementation, state changes, and open questions. Read the full spec before starting any REQ.

## Building New Tools

1. Read `specs/templates/engine-template.md` for the pattern
2. Define the engine (data model, scoring) first
3. Apply the skin (typography, colors) second
4. Create a new versioned file in `src/websites/<tool-name>/`

## How to Work on This Project

1. Read the relevant engine doc before touching scoring logic
2. Read the skin doc before touching visual presentation
3. Read the full REQ spec before implementing a requirement
4. Create a new versioned file for each iteration
5. Engine changes first, then skin changes — never both at once
6. Open the HTML file directly in a browser to test (no build step)
