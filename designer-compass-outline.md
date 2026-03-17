# The Designer's Compass — Project Outline

## The Premise

Not all designers are the same creature. The field contains fundamentally different species of creative minds, each with their own instincts, strengths, and natural habitats. Understanding *what kind* of designer you are — and what kind you're becoming — is the first step toward a career with intention.

---

## I. Designer Archetypes

Each archetype represents a gravitational pull — where a designer's instincts naturally lead them.

### A. The Experience Storyteller
- Natural habitat: Disney, Pixar, theme parks, immersive entertainment, game studios
- Core drive: Emotion, narrative arc, delight, wonder
- Portfolio signature: Feels like a journey — you *experience* it, not just view it
- Superpower: Making people feel something specific at a specific moment

### B. The Systems Architect
- Natural habitat: Enterprise SaaS, fintech, healthcare platforms, data infrastructure
- Core drive: Clarity from complexity, structure, scalability
- Portfolio signature: Before/after transformations of dense information into navigable systems
- Superpower: Making the incomprehensible usable
- **Critical note:** The best systems designers are also storytellers — they translate complexity into narrative for stakeholders and users. Data without story is noise. The ability to explain *why* a system works the way it does, to walk a user through dense information with a guiding hand, is what separates good from great.

### C. The Brand Worldbuilder
- Natural habitat: Agencies, startups, luxury brands, media companies
- Core drive: Identity, cohesion, cultural resonance
- Portfolio signature: Complete visual universes — logo to packaging to environmental design
- Superpower: Making a brand feel inevitable

### D. The Interaction Crafter
- Natural habitat: Product studios, design systems teams, platform companies
- Core drive: Micro-moments, motion, precision of response
- Portfolio signature: Prototypes and motion studies that make you say "that feels *right*"
- Superpower: The invisible layer between intent and action

### E. The Service Designer
- Natural habitat: Government, healthcare, consulting, operations-heavy organizations
- Core drive: End-to-end journeys, touchpoint orchestration, systemic change
- Portfolio signature: Journey maps, blueprints, ecosystem diagrams — the big picture
- Superpower: Seeing the whole system, not just the screen

### F. The Research-Led Strategist
- Natural habitat: R&D labs, innovation teams, consulting firms, policy organizations
- Core drive: Evidence, insight, framing the right problem
- Portfolio signature: Insight decks, frameworks, before/after impact narratives
- Superpower: Changing what gets built before a single pixel is placed

### G. The Creative Technologist
- Natural habitat: Labs, studios, installations, experimental product teams
- Core drive: What's possible, merging code and craft
- Portfolio signature: Things that make you ask "how did they do that?"
- Superpower: Bridging the gap between vision and technical reality

---

## II. The Career Ladder

Based on the organizational model provided. Two tracks diverge after the Staff level.

### Entry
| Level | Description |
|-------|-------------|
| UX Intern | Learning the craft in a structured environment |
| UX Apprentice | Guided practice, building foundational skills |

### Individual Contributor Track
| Level | Description |
|-------|-------------|
| UX Designer I | Executing defined problems with guidance |
| UX Designer II | Independently owning design problems |
| Senior UX Designer | Leading complex projects, mentoring others |
| UX Staff Designer | Cross-team influence, setting quality bars |

### The Fork — IC Leadership
| Level | Description |
|-------|-------------|
| UX Principal Designer | Defining design direction for a product area |
| Distinguished Designer | Shaping practice across the organization |
| Design Fellow | Industry-level impact, thought leadership |

### The Fork — People Leadership
| Level | Description |
|-------|-------------|
| UX Manager | Leading a team, developing designers |
| Senior UX Manager | Leading managers, shaping team strategy |
| UX Director | Organizational design strategy |
| Sr. Director | Executive-level design leadership |

### Cross-Track Movement
- Movement between IC and management tracks is possible at every level beyond Staff
- Each transition shifts the competency profile (see Section III)
- The best leaders have walked both paths at some point

---

## III. Competency Radar — The Korn Ferry Layer

Using the Korn Ferry Leadership Architect Global Competency Framework, each role/archetype combination produces a unique radar chart shape.

### Competency Dimensions (adapted for design)
- **Strategic Thinking** — Seeing the big picture, anticipating future needs
- **Business Acumen** — Understanding organizational context and value
- **Stakeholder Influence** — Persuading, aligning, building coalition
- **Craft Mastery** — Depth of design skill and judgment
- **User Empathy & Research** — Understanding people deeply
- **Communication & Storytelling** — Translating ideas across audiences
- **Team Development** — Growing others, building culture
- **Systems Thinking** — Connecting parts to wholes
- **Innovation & Experimentation** — Pushing boundaries, tolerating ambiguity
- **Execution & Delivery** — Shipping, quality, reliability

### How the Shapes Differ
- A **Senior IC Experience Storyteller** peaks on Craft Mastery, User Empathy, Communication
- A **Director-level Systems Architect** peaks on Strategic Thinking, Business Acumen, Systems Thinking
- A **Principal Creative Technologist** peaks on Innovation, Craft Mastery, Execution
- Every archetype shares a need for **Communication & Storytelling** — it's the universal competency

---

## IV. Artifacts to Build

### Artifact 1: The Archetype Explorer
**Type:** Interactive React app
**What it does:**
- Visual cards or an interactive wheel for each designer archetype
- Click into any archetype to see: description, natural habitats, portfolio characteristics, famous examples
- Each archetype has a distinct visual identity / color palette

**Tasks:**
- [ ] Define final archetype list and descriptions
- [ ] Design visual identity per archetype (color, icon, mood)
- [ ] Build interactive card/wheel UI
- [ ] Write detailed content for each archetype

---

### Artifact 2: The Career Ladder Visualization
**Type:** Interactive flowchart / pathway diagram (React)
**What it does:**
- Recreates and enhances the career ladder diagram
- Interactive — click any role to see: level description, typical competencies, what the portfolio looks like at this level
- Shows the IC/Management fork visually with animated transitions
- Crossover paths shown as bridges between the tracks

**Tasks:**
- [ ] Map all roles and relationships from the provided diagram
- [ ] Design the interactive flowchart layout
- [ ] Write role descriptions for each level
- [ ] Build click-to-expand detail panels
- [ ] Animate the fork and crossover paths

---

### Artifact 3: The Competency Radar
**Type:** Interactive radar/rose chart (React + D3 or Recharts)
**What it does:**
- Select an archetype + career level → generates a unique radar chart
- Compare mode: overlay two profiles to see differences
- Animated transitions as you change selections
- Shows which competencies to develop for the next level

**Tasks:**
- [ ] Define competency scores for each archetype × level combination
- [ ] Build the radar chart component with smooth animations
- [ ] Add comparison/overlay mode
- [ ] Design the "growth gap" visualization (current vs. next level)
- [ ] Style with bold, energetic aesthetic per earlier direction

---

### Artifact 4: The Unified Dashboard (Stretch Goal)
**Type:** Single-page app combining all three
**What it does:**
- "Choose your archetype" → see the ladder → see the radar
- A guided flow: *Who am I → Where am I → Where could I go → What do I need to develop*
- The career compass itself

**Tasks:**
- [ ] Design the unified flow and navigation
- [ ] Integrate Artifacts 1–3 into a cohesive experience
- [ ] Add transitions between sections
- [ ] Final polish and storytelling layer

---

## V. Open Questions

1. Should the archetypes be pure types, or should the tool allow blended profiles (e.g., 60% Systems Architect / 40% Storyteller)?
2. How closely should we follow the Korn Ferry framework vs. adapting it for design specifically?
3. Should the career ladder be generic or customizable to specific company structures?
4. Is this a tool for individual designers, or also for managers building teams?
