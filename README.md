# Designer Growthprint

Self-assessment tools for designers to understand their skills, archetypes, and career growth paths.

## What's Inside

### Web Applications (`src/websites/`)

- **Portfolio Scorecard** — Rate your portfolio across key dimensions and get actionable feedback
- **UX Designer Scorecard** — Self-assess across 10 craft skills from Research to Design Ops
- **Competency Radar** — Visualize your leadership competencies across career levels and archetypes

### Specifications (`specs/`)

Documentation separating concerns:

- **Engine** — Data models, scoring algorithms, and logic (what the system *knows*)
- **Skin** — Visual design language, typography, and color system (how it *looks*)
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

## Running Locally

Open any HTML file directly in a browser:

```bash
open src/websites/portfolio-scorecard/portfolio-scorecard-v0.1.html
```

No build step required — these are self-contained HTML files with embedded CSS and JavaScript.

## License

See [LICENSE](LICENSE) for details.
