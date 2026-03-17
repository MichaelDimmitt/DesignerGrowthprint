# CLAUDE.md

This file provides guidance for Claude Code when working on this project.

## Project Overview

Designer Growthprint is a collection of self-assessment tools for designers. The tools help designers understand their skills, identify their archetype, and plan career growth.

## Key Architecture: Engine/Skin Separation

This project strictly separates **engine** (logic) from **skin** (presentation):

- **Engine** (`specs/engine/`): Data models, scoring algorithms, competency frameworks. Could render as CLI, spreadsheet, or API.
- **Skin** (`specs/skin/`): Visual design language, typography, colors, animations. Pure presentation layer.

When building features, maintain this separation. Logic should never depend on visual implementation.

## File Structure

```
src/websites/           # HTML applications (self-contained, no build step)
specs/engine/           # Scoring logic and data model specs
specs/skin/             # Visual design system specs
specs/templates/        # Templates for new assessment tools
backlog/                # Requirements and planning docs
reference/              # Background materials (consult rarely)
transcripts/            # Archived conversation history
```

## Competency Frameworks

Two distinct frameworks exist (documented in `specs/engine/the-engine.md`):

1. **Craft Skills (Scorecard)**: 10 skills rated 1-5 (Research, IA, Interaction, Visual, Systems, Accessibility, Strategy, Leadership, Ops, Craft)

2. **Leadership Competencies (Radar)**: 10 dimensions rated 1-10 (Strategic Thinking, Business Acumen, Stakeholder Influence, Craft Mastery, User Empathy, Communication, Team Development, Systems Thinking, Innovation, Execution)

These frameworks are not yet unified.

## Visual Design System

Key specs from `specs/skin/the-skin.md`:

- **Fonts**: Bebas Neue (display), DM Sans (body), Space Mono (data/labels)
- **Theme**: Dark mode with blue undertones (`#08090E` base)
- **Accent**: Neon green (`#00FF85`) for primary actions

## Building New Tools

1. Read `specs/templates/engine-template.md` for the pattern
2. Define the engine (data model, scoring) first
3. Apply the skin (typography, colors) second
4. Keep HTML self-contained (embedded CSS/JS, no build step)

## Commands

No build system. Open HTML files directly:

```bash
open src/websites/portfolio-scorecard/portfolio-scorecard-v0.1.html
```

## What to Read

- **Before building**: `specs/engine/the-engine.md`, `specs/skin/the-skin.md`
- **For requirements**: `backlog/portfolio-scorecard-requirements.md`
- **For context**: `designer-compass-outline.md`
- **Rarely needed**: `reference/`, `transcripts/`
