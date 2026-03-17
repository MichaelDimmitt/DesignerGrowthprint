# File Architecture

```
designers-compass/
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
│       ├── # Future router / hub page
│       ├── index.html
│       │
│       ├── portfolio-scorecard/
│       │   ├── portfolio-scorecard-v0.1.html
│       │   ├── portfolio-scorecard-v0.2.html
│       │   └── portfolio-scorecard-v0.3.html
│       │
│       ├── ux-designer-scorecard/
│       │   └── ux-designer-scorecard-v0.1.html
│       │
│       └── competency-radar/
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
