# Designer Growthprint

Self-assessment tools for designers to understand their skills, archetypes, and career growth paths.

## What's Inside

### Web Applications/Tools (`src/websites/`)

**Portfolio Scorecard** — Rate a designer's portfolio across three sections: shell (first impression, navigation, brand), case studies (problem framing, process, outcomes), and strategy (differentiation, positioning). Produces a composite score with per-section breakdowns and growth areas.

**UX Designer Scorecard** — Self-assessment covering 10 craft skills, 6 soft skills, 10 professional assets, and 10 experience types. Auto-detects a designer archetype from skill ratings. Total score out of 130.

**Competency Radar** — Benchmark radar charts showing expected competency profiles for 7 designer archetypes across 5 career levels. Based on the Korn Ferry Leadership Architect framework, adapted for design.

## How it works:

### Specifications (`specs/`)

Documentation separating concerns:

- **Engine** — Data models, scoring algorithms, and logic (what the system _knows_)
- **Skin** — Visual design language, typography, and color system (how it _looks_)
- **Templates** — Patterns for building new assessment tools

### Planning (`backlog/`)

Requirements and feature planning documents.

### Reference (`reference/`)

Background materials including the Jacksonville Design Community Guide.

## Architecture

The tools follow an **engine/skin separation**:

- **Engine**: Competency frameworks, scoring logic, archetype definitions — could run as a spreadsheet or CLI
- **Skin**: Typography (Bebas Neue, DM Sans, Space Mono), dark theme, radar charts — pure presentation

This separation allows the same assessment engine to power different visual experiences.

## Designer Archetypes

The tools recognize seven designer archetypes:

1. **Experience Storyteller** — Emotion, narrative, delight
2. **Systems Architect** — Clarity from complexity, scalability
3. **Brand Worldbuilder** — Identity, cohesion, cultural resonance
4. **Interaction Crafter** — Micro-moments, motion, precision
5. **Service Designer** — End-to-end journeys, systemic change
6. **Research-Led Strategist** — Evidence, insight, problem framing
7. **Creative Technologist** — Merging code and craft

## Quick Start

No build step. Open any HTML file in a browser.

```bash
open src/websites/portfolio-scorecard/portfolio-scorecard-v0.1.html
```

No build step required — these are self-contained HTML files with embedded CSS and JavaScript.

## License

See [LICENSE](LICENSE) for details.
