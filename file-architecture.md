# File Architecture

```
designer-growthprint/
│
├── # Orientation — auto-loaded by Claude Code
├── CLAUDE.md
│
├── # Human-facing project overview
├── README.md
│
├── # Project vision
├── designer-compass-outline.md
│
├── src/
│   └── websites/
│       │
│       ├── # Hub page with version selector
│       ├── index.html
│       ├── index-v0.2.html              ← Timeline version selector variant
│       │
│       ├── portfolio-scorecard/
│       │   ├── releases.json            ← Version metadata (descriptions, dates)
│       │   ├── portfolio-scorecard-v0.1.html
│       │   └── portfolio-scorecard-v0.2.html
│       │
│       ├── ux-designer-scorecard/
│       │   ├── releases.json
│       │   └── ux-designer-scorecard-v0.1.html
│       │
│       └── competency-radar/
│           ├── releases.json
│           └── competency-radar-v0.1.html
│
├── # What Claude Code READS to understand the system
├── specs/
│   ├── engine/
│   │   ├── the-engine.md
│   │   └── portfolio-scorecard-engine.md
│   ├── skin/
│   │   └── the-skin.md
│   └── templates/
│       └── engine-template.md
│
├── # What Claude Code READS to know what to build
├── backlog/
│   ├── portfolio-scorecard-requirements.md
│   └── portfolio-scorecard-requirements.pdf
│
├── # Background material — consult rarely
├── reference/
│   └── jacksonville-design-community-guide.md
│
├── # Conversation history — archived, searchable
├── transcripts/
│   └── .gitkeep
│
├── .gitignore
└── LICENSE
```

## releases.json Format

Each tool folder contains a `releases.json` that drives the hub page version selector:

```json
{
  "tool": "Portfolio Scorecard",
  "releases": [
    {
      "version": "v0.2",
      "file": "portfolio-scorecard-v0.2.html",
      "date": "2024-03-17",
      "description": "Description of what changed",
      "cheeky": false
    }
  ]
}
```

- **version**: Display label (e.g., "v0.1", "v0.2")
- **file**: Filename within the tool folder
- **date**: Release date (YYYY-MM-DD)
- **description**: Shown in hub page when version is selected
- **cheeky**: If true, description gets playful purple styling
