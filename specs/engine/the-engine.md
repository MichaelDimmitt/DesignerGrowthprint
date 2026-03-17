# The Engine — Data Models, Algorithms & Logic
## Extracted from UX Designer Scorecard + Competency Radar

Everything in this document is **what the system knows and how it thinks**. Nothing about colors, fonts, layouts, or animations. You could render this engine as a spreadsheet, a CLI tool, or a voice interface and it would still work.

---

## 1. Two Separate Frameworks (The Core Tension)

The Scorecard and the Radar currently run on **completely different competency models**. This is the most important thing to understand about the engine as it stands today.

### Framework A: Craft Skills (Scorecard)
Measures **what a designer can do** — their hands-on discipline expertise.

| ID | Skill | Description |
|----|-------|-------------|
| `research` | User Research | Interviews, usability testing, synthesis, insight generation |
| `ia` | Information Architecture | Content structure, navigation, taxonomy, sitemaps |
| `interaction` | Interaction Design | Flows, wireframes, prototyping, micro-interactions |
| `visual` | Visual Design | Layout, typography, color, iconography, brand expression |
| `systems` | Design Systems | Components, tokens, documentation, governance |
| `accessibility` | Accessibility | WCAG, assistive tech, inclusive patterns |
| `strategy` | Product Strategy | Roadmapping, metrics, stakeholder alignment, OKRs |
| `leadership` | Design Leadership | Mentoring, critique, team building, org influence |
| `ops` | Design Operations | Process, tooling, team scaling, workflow management |
| `craft` | Prototyping & Craft | Hi-fi execution, motion, code awareness, tool mastery |

**Scale:** 1–5 (Novice → Expert). User self-rates. Max total: 50.

### Framework B: Leadership Competencies (Radar)
Measures **how a designer operates** — their behavioral and strategic profile. Adapted from the Korn Ferry Leadership Architect framework.

| Index | Competency | Description |
|-------|-----------|-------------|
| 0 | Strategic Thinking | Seeing the big picture, anticipating future needs |
| 1 | Business Acumen | Understanding organizational context and value |
| 2 | Stakeholder Influence | Persuading, aligning, building coalition |
| 3 | Craft Mastery | Depth of design skill and judgment |
| 4 | User Empathy | Understanding people deeply |
| 5 | Communication & Story | Translating ideas across audiences |
| 6 | Team Development | Growing others, building culture |
| 7 | Systems Thinking | Connecting parts to wholes |
| 8 | Innovation | Pushing boundaries, tolerating ambiguity |
| 9 | Execution & Delivery | Shipping, quality, reliability |

**Scale:** 1–10 (in benchmark data). Not currently user-rated — these are reference profiles only.

### The Gap
There is no mapping between these two frameworks. A user rates themselves on Framework A, gets an archetype from Framework A's model, but then looks at Framework B's radar chart which uses a completely different lens. The two tools don't share data.

---

## 2. Archetype Models (Also Divergent)

### Scorecard Archetypes (6)

These are detected from the user's **craft skill self-ratings**:

```javascript
const ARCHETYPES = [
  {
    name: "The Researcher",
    focus: "Deep in discovery — insight & evidence",
    peaks: ["research", "strategy", "accessibility"]
  },
  {
    name: "The Craftsperson",
    focus: "Pixel-perfect polish, motion & detail",
    peaks: ["visual", "craft", "interaction"]
  },
  {
    name: "The Architect",
    focus: "Systems thinker — scalable foundations",
    peaks: ["systems", "ia", "ops"]
  },
  {
    name: "The Strategist",
    focus: "Big-picture, design meets business",
    peaks: ["strategy", "leadership", "research"]
  },
  {
    name: "The Generalist",
    focus: "Adaptable, cross-functional, fills gaps",
    peaks: []  // No peaks — detected by low variance
  },
  {
    name: "The Champion",
    focus: "Evangelist — teams, culture, buy-in",
    peaks: ["leadership", "ops", "strategy"]
  },
];
```

### Radar Archetypes (7)

These are predefined profiles with **no detection algorithm** — the user manually selects one:

```javascript
const ARCHETYPES = {
  storyteller:  { name: "Experience Storyteller",  sub: "Disney · Pixar · Immersive" },
  systems:      { name: "Systems Architect",       sub: "Enterprise · Fintech · Data" },
  brand:        { name: "Brand Worldbuilder",      sub: "Agencies · Startups · Luxury" },
  interaction:  { name: "Interaction Crafter",     sub: "Product · Design Systems" },
  service:      { name: "Service Designer",        sub: "Gov · Healthcare · Consulting" },
  strategist:   { name: "Research Strategist",     sub: "R&D · Innovation · Policy" },
  technologist: { name: "Creative Technologist",   sub: "Labs · Installations · Experimental" },
};
```

### The Mismatch
| Scorecard | Radar | Notes |
|-----------|-------|-------|
| The Researcher | Research Strategist | Closest match |
| The Craftsperson | Interaction Crafter | Partial overlap |
| The Architect | Systems Architect | Close match |
| The Strategist | (no direct match) | Radar has no pure "business strategist" |
| The Generalist | (no equivalent) | Radar doesn't detect blends |
| The Champion | (no equivalent) | Radar has no "evangelist" type |
| (no equivalent) | Experience Storyteller | Scorecard has no narrative/emotion type |
| (no equivalent) | Brand Worldbuilder | Scorecard has no brand identity type |
| (no equivalent) | Service Designer | Scorecard has no service design type |
| (no equivalent) | Creative Technologist | Scorecard has no code-craft hybrid |

---

## 3. Career Level Models (Also Different)

### Scorecard Career Levels (8)

```javascript
const CAREER_LEVELS = [
  { id: "student",   label: "Student / Intern",     yrs: "0 yrs" },
  { id: "junior",    label: "Junior",               yrs: "0–2 yrs" },
  { id: "mid",       label: "Mid-Level",            yrs: "2–5 yrs" },
  { id: "senior",    label: "Senior",               yrs: "5–8 yrs" },
  { id: "lead",      label: "Lead",                 yrs: "7–10 yrs" },
  { id: "principal", label: "Principal / Staff",     yrs: "10+ yrs" },
  { id: "manager",   label: "Manager / Director",   yrs: "8+ yrs" },
  { id: "vp",        label: "VP / Head of Design",  yrs: "12+ yrs" },
];
```

### Radar Career Levels (5)

```javascript
const LEVELS = {
  junior:    "Designer I–II",
  senior:    "Senior Designer",
  staff:     "Staff Designer",
  principal: "Principal / Director",
  fellow:    "Fellow / Sr. Director",
};
```

### The Mismatch
The Scorecard has finer granularity (student, junior, mid, senior, lead, principal, manager, VP) while the Radar collapses these into broader bands. The Scorecard mixes IC and management into one list; the Radar is IC-only (no explicit management track). There is no mapping between the two.

---

## 4. The Benchmark Data Matrix (Radar Only)

350 values: 7 archetypes × 5 levels × 10 competencies. This is the heart of the Radar — each combination produces a unique shape.

```javascript
const DATA = {
  storyteller: {
    //         Strat  Biz  Stake Craft Empa  Comm  Team  Sys   Innov Exec
    junior:    [2,    1,   2,    5,    7,    5,    1,    2,    4,    5],
    senior:    [4,    3,   4,    8,    8,    7,    3,    3,    6,    7],
    staff:     [5,    4,   6,    9,    9,    8,    5,    5,    7,    8],
    principal: [7,    6,   8,    9,    8,    9,    6,    6,    8,    7],
    fellow:    [9,    7,   9,    10,   8,    10,   7,    7,    9,    7],
  },
  systems: {
    junior:    [2,    2,   1,    4,    4,    3,    1,    5,    3,    5],
    senior:    [5,    5,   4,    7,    6,    5,    3,    8,    4,    7],
    staff:     [7,    6,   6,    8,    6,    7,    4,    9,    5,    8],
    principal: [8,    8,   8,    8,    6,    8,    6,    10,   5,    8],
    fellow:    [9,    9,   9,    8,    7,    9,    7,    10,   6,    8],
  },
  brand: {
    junior:    [2,    2,   2,    6,    4,    5,    1,    2,    6,    4],
    senior:    [4,    4,   5,    8,    5,    7,    2,    3,    8,    6],
    staff:     [6,    5,   7,    9,    6,    8,    4,    4,    9,    7],
    principal: [7,    7,   8,    9,    6,    9,    6,    5,    9,    7],
    fellow:    [9,    8,   9,    10,   7,    10,   7,    6,    9,    7],
  },
  interaction: {
    junior:    [1,    1,   1,    7,    5,    3,    1,    3,    5,    6],
    senior:    [3,    3,   3,    9,    7,    5,    2,    5,    7,    8],
    staff:     [4,    4,   5,    10,   7,    6,    4,    7,    8,    9],
    principal: [6,    5,   7,    10,   7,    7,    6,    8,    8,    9],
    fellow:    [7,    6,   8,    10,   8,    8,    7,    9,    9,    8],
  },
  service: {
    junior:    [3,    2,   2,    3,    6,    4,    1,    4,    3,    4],
    senior:    [5,    5,   5,    5,    8,    6,    3,    7,    4,    6],
    staff:     [7,    6,   7,    6,    9,    8,    5,    8,    5,    7],
    principal: [8,    8,   8,    6,    9,    9,    7,    9,    6,    7],
    fellow:    [9,    9,   9,    7,    9,    10,   8,    10,   7,    7],
  },
  strategist: {
    junior:    [3,    2,   2,    2,    7,    4,    1,    3,    4,    3],
    senior:    [6,    4,   5,    4,    9,    6,    2,    5,    6,    5],
    staff:     [7,    6,   7,    5,    9,    8,    4,    7,    7,    6],
    principal: [9,    7,   8,    5,    9,    9,    6,    8,    8,    6],
    fellow:    [10,   8,   9,    6,    10,   10,   7,    9,    9,    6],
  },
  technologist: {
    junior:    [1,    1,   1,    6,    3,    2,    1,    3,    7,    6],
    senior:    [3,    2,   3,    8,    5,    4,    2,    5,    9,    8],
    staff:     [4,    3,   5,    9,    5,    6,    3,    6,    9,    9],
    principal: [6,    5,   6,    9,    6,    7,    5,    7,    10,   9],
    fellow:    [7,    6,   7,    9,    7,    8,    6,    8,    10,   9],
  },
};
```

### Patterns in the Data

Reading across archetypes at the same level reveals how each type is shaped:

- **Storyteller** peaks on Craft (3) + Empathy (4) + Communication (5). Low Business Acumen.
- **Systems** peaks on Systems Thinking (7) — always its highest. Strong Business Acumen growth.
- **Brand** peaks on Craft (3) + Innovation (8) + Communication (5). Balanced but visual-heavy.
- **Interaction** peaks on Craft (3) — often at 10 by staff level. Strongest single-axis spiker.
- **Service** peaks on Empathy (4) + Systems Thinking (7). Most balanced shape overall.
- **Strategist** peaks on Strategic Thinking (0) + Empathy (4) + Communication (5). Low Craft.
- **Technologist** peaks on Innovation (8) + Execution (9). Highest Execution of any archetype.

Reading across levels within one archetype shows the growth pattern:
- Strategic Thinking, Business Acumen, Stakeholder Influence grow the most (career-maturity skills)
- Craft Mastery plateaus early (you hit your ceiling by staff)
- Team Development is always the latest bloomer
- Communication is the universal competency — high for everyone by senior level

---

## 5. Scoring Engine (Scorecard Only)

### Section Scoring

```javascript
// Competencies: sum of 10 ratings (each 0–5)
const compTotal = Object.values(compScores).reduce((a, b) => a + b, 0);
// Max: 50

// Soft Skills: sum of 6 ratings (each 0–5)
const softTotal = Object.values(softScores).reduce((a, b) => a + b, 0);
// Max: 30

// Professional Assets: weighted by status
let assetScore = 0;
Object.values(assetStatuses).forEach(v => {
  if (v === 'ready')    assetScore += 3;
  else if (v === 'wip') assetScore += 2;
  else if (v === 'outdated') assetScore += 1;
  // 'none' = 0
});
// Max: 30 (10 assets × 3)

// Experience: 2 points per checked item
const expCount = Object.values(experienceChecks).filter(Boolean).length;
// Max: 20 (10 items × 2)
```

### Composite Score

```javascript
const grandTotal = compTotal + softTotal + assetScore + expCount * 2;
const grandMax = 50 + 30 + 30 + 20; // = 130
const pct = Math.round((grandTotal / grandMax) * 100);
```

### Section Breakdown (for display)

```javascript
const sections = [
  { label: "Competencies", score: compTotal,     max: 50, color: "#ff4d6a" },
  { label: "Soft Skills",  score: softTotal,     max: 30, color: "#ffc645" },
  { label: "Prof. Assets", score: assetScore,    max: 30, color: "#00e5c7" },
  { label: "Experience",   score: expCount * 2,  max: 20, color: "#a78bfa" },
];
```

---

## 6. Archetype Detection Algorithm (Scorecard Only)

```javascript
function getArchetype(scores) {
  // 1. Collect all competency ratings into an array
  const vals = COMPETENCIES.map(c => scores[c.id] || 0);
  const total = vals.reduce((a, b) => a + b, 0);

  // 2. Bail if nothing rated
  if (total === 0) return null;

  // 3. Check for Generalist: low variance + sufficient total
  const avg = total / vals.length;
  const variance = vals.reduce((s, v) => s + Math.pow(v - avg, 2), 0) / vals.length;
  if (variance < 0.8 && total >= 20) {
    return ARCHETYPES.find(a => a.name === "The Generalist");
  }

  // 4. For each archetype with peaks, average the user's scores on those peaks
  let best = null, bestScore = -1;
  for (const arch of ARCHETYPES) {
    if (!arch.peaks.length) continue; // skip Generalist
    const s = arch.peaks.reduce((sum, p) => sum + (scores[p] || 0), 0) / arch.peaks.length;
    if (s > bestScore) {
      bestScore = s;
      best = arch;
    }
  }
  return best;
}
```

**How it works:**
- Each archetype defines 3 "peak" skill IDs
- The algorithm averages the user's self-rating across those 3 peaks
- Highest average wins
- Exception: if the variance across ALL skills is below 0.8 AND total score is ≥20, the user is classified as "The Generalist" (their skills are too evenly distributed to have a peak)
- The algorithm only runs after ALL 10 competencies have been rated

**Weaknesses:**
- Only 3 peaks per archetype — doesn't capture nuance
- No secondary archetype or confidence score
- Generalist threshold (0.8 variance) is arbitrary
- The Strategist and Champion share 2 of 3 peaks (strategy, leadership) — hard to distinguish
- No tie-breaking mechanism

---

## 7. Top Competencies Calculation (Radar Only)

```javascript
const topCompetencies = useMemo(() => {
  return currentData
    .map((v, i) => ({ name: COMPETENCIES[i], value: v }))
    .sort((a, b) => b.value - a.value)
    .slice(0, 3);
}, [currentData]);
```

Simple: take the benchmark data for the selected archetype+level, sort descending, take top 3.

---

## 8. Growth Area Detection (Scorecard Only)

```javascript
const growthAreas = [
  ...COMPETENCIES.map(c => ({
    name: c.name,
    score: compScores[c.id] || 0,
    sec: "Competency"
  })),
  ...SOFT_SKILLS.map(s => ({
    name: s.name,
    score: softScores[s.id] || 0,
    sec: "Soft Skill"
  })),
]
  .sort((a, b) => a.score - b.score)  // ascending — lowest first
  .slice(0, 3);                        // bottom 3 = biggest growth areas
```

Growth areas are simply the 3 lowest-rated skills across both competencies and soft skills.

---

## 9. Rose Chart Geometry (Radar)

This is pure math — no opinions about what the data means.

### Polar Coordinate Mapping

```javascript
const n = 10;                              // number of competencies
const angleSlice = (Math.PI * 2) / n;      // 36° per slice
const maxR = chartSize * 0.38;             // chart radius = 38% of container

// Convert (competencyIndex, scoreValue) → (x, y)
function dataPoint(index, value) {
  const angle = angleSlice * index - Math.PI / 2;  // -π/2 = start at top
  const r = (value / 10) * maxR;                    // scale 0–10 → 0–maxR
  return [Math.cos(angle) * r, Math.sin(angle) * r];
}
```

### Bezier Path Generation

```javascript
function rosePath(values) {
  const points = values.map((v, i) => dataPoint(i, v));
  points.push(points[0]); // close the loop

  let path = `M${points[0][0]},${points[0][1]}`;
  for (let i = 0; i < points.length - 1; i++) {
    const curr = points[i];
    const next = points[(i + 1) % points.length];
    // Control point = current data point
    // End point = midpoint between current and next
    const cpx = (curr[0] + next[0]) / 2;
    const cpy = (curr[1] + next[1]) / 2;
    path += `Q${curr[0]},${curr[1]} ${cpx},${cpy}`;
  }
  path += "Z";
  return path;
}
```

This creates the smooth, organic blob shapes rather than sharp polygon corners.

### Animated Interpolation

```javascript
function animatePath(selection, fromData, toData) {
  const fromValues = fromData || toData.map(() => 0);
  selection
    .attr("d", rosePath(fromValues))
    .transition()
    .duration(800)
    .ease(d3.easeCubicOut)
    .attrTween("d", () => {
      // Create individual interpolators for each of the 10 values
      const interp = fromValues.map((from, i) =>
        d3.interpolate(from, toData[i])
      );
      // At each animation frame, compute the intermediate path
      return (t) => rosePath(interp.map(fn => fn(t)));
    });
}
```

The chart remembers its previous state (`prevDataRef`) and morphs from old shape to new shape when selections change.

### Sidebar Radar Geometry (Scorecard — simpler)

```javascript
const c = size / 2;             // center
const r = size / 2 - 28;        // radius with label margin
const levels = 5;               // ring count (matching 1–5 scale)
const step = (Math.PI * 2) / ids.length;

// Grid rings: polygonal (not circular)
const rings = Array.from({ length: levels }, (_, i) => {
  const rr = ((i + 1) / levels) * r;
  return ids.map((_, j) => {
    const a = step * j - Math.PI / 2;
    return `${c + rr * Math.cos(a)},${c + rr * Math.sin(a)}`;
  }).join(" ");
});

// Data shape: straight polygon (no Bezier)
const dataPts = ids.map((id, i) => {
  const a = step * i - Math.PI / 2;
  const d = (scores[id] / 5) * r;  // scale 0–5 → 0–r
  return `${c + d * Math.cos(a)},${c + d * Math.sin(a)}`;
}).join(" ");
```

---

## 10. Professional Assets Model

### Status Enum

```javascript
const ASSET_STATUSES = [
  { id: "none",     label: "Don't have" },
  { id: "outdated", label: "Outdated" },
  { id: "wip",      label: "In Progress" },
  { id: "ready",    label: "Up to Date" },
];
```

### Scoring Weights
| Status | Points |
|--------|--------|
| none | 0 |
| outdated | 1 |
| wip | 2 |
| ready | 3 |

### Items (10)

| ID | Title | Description |
|----|-------|-------------|
| `resume` | Resume / CV | Tailored, current, keyword-optimized |
| `portfolio_site` | Portfolio Website | Custom domain, case studies, contact |
| `case_studies` | Case Studies (3+) | Process, decisions, and outcomes documented |
| `linkedin` | LinkedIn Profile | Photo, headline, summary, experience |
| `dribbble` | Dribbble | Active shots showcasing visual craft |
| `behance` | Behance | Full project presentations with context |
| `figma_community` | Figma Community | Published files, templates, resources |
| `github` | GitHub / CodePen | Code contributions, prototypes |
| `blog` | Blog / Writing | Design articles on Medium, Substack, etc. |
| `social` | Design Social Presence | X, Threads, or other design engagement |

---

## 11. Experience Model

### Items (10)
Binary yes/no. Worth 2 points each.

| ID | Title | Description |
|----|-------|-------------|
| `solo_projects` | Solo / Side Projects | Personal projects showing initiative |
| `client_work` | Client / Agency Work | Projects with external stakeholders |
| `product_team` | Product Team Experience | In-house with cross-functional teams |
| `enterprise` | Enterprise / Complex Systems | B2B, internal tools, healthcare, fintech |
| `consumer` | Consumer / B2C Products | Consumer apps, e-commerce, social |
| `zero_to_one` | 0 → 1 Product Work | Built from concept to launch |
| `redesign` | Major Redesign | Led a significant product overhaul |
| `mentored` | Mentored Others | Guided juniors, interns, career switchers |
| `speaking` | Public Speaking / Teaching | Talks, workshops, courses, conferences |
| `open_source` | Open Source / Community | Tools, libraries, or community resources |

---

## 12. Soft Skills Model

### Items (6)
Rated 1–5, same scale and input pattern as competencies.

| ID | Skill | Description |
|----|-------|-------------|
| `presentation` | Presenting & Storytelling | Pitching ideas, presenting to stakeholders |
| `communication` | Cross-Functional Comms | Working with engineers, PMs, marketing, execs |
| `critique` | Giving & Receiving Feedback | Constructive critique, iterating on input |
| `facilitation` | Workshop Facilitation | Leading sprints, brainstorms, alignment sessions |
| `negotiation` | Pushback & Negotiation | Advocating for users, defending decisions |
| `timemanagement` | Time & Project Mgmt | Scoping, deadlines, managing ambiguity |

---

## 13. State Shape (Scorecard)

The complete user state at any moment:

```javascript
{
  name: string,                    // Free text
  careerLevel: string | null,      // One of 8 career level IDs
  compScores: {                    // Craft skill ratings
    research: 0–5,
    ia: 0–5,
    interaction: 0–5,
    visual: 0–5,
    systems: 0–5,
    accessibility: 0–5,
    strategy: 0–5,
    leadership: 0–5,
    ops: 0–5,
    craft: 0–5,
  },
  softScores: {                    // Soft skill ratings
    presentation: 0–5,
    communication: 0–5,
    critique: 0–5,
    facilitation: 0–5,
    negotiation: 0–5,
    timemanagement: 0–5,
  },
  assetStatuses: {                 // Professional asset statuses
    resume: "none" | "outdated" | "wip" | "ready",
    portfolio_site: ...,
    case_studies: ...,
    linkedin: ...,
    dribbble: ...,
    behance: ...,
    figma_community: ...,
    github: ...,
    blog: ...,
    social: ...,
  },
  experienceChecks: {              // Experience booleans
    solo_projects: boolean,
    client_work: boolean,
    product_team: boolean,
    enterprise: boolean,
    consumer: boolean,
    zero_to_one: boolean,
    redesign: boolean,
    mentored: boolean,
    speaking: boolean,
    open_source: boolean,
  },
}
```

### Derived State (computed, not stored)
```javascript
{
  compTotal: number,               // 0–50
  softTotal: number,               // 0–30
  assetScore: number,              // 0–30
  expCount: number,                // 0–10
  grandTotal: number,              // 0–130
  pct: number,                     // 0–100
  archetype: Archetype | null,     // Detected archetype object
  growthAreas: Array<{name, score, section}>,  // Bottom 3 skills
}
```

## 14. State Shape (Radar)

```javascript
{
  archetype: string,               // One of 7 archetype keys
  level: string,                   // One of 5 level keys
  compareArchetype: string | null,  // Optional second archetype key
}
```

### Derived State
```javascript
{
  currentData: number[10],          // Benchmark scores for archetype+level
  compareData: number[10] | null,   // Benchmark scores for compare archetype
  topCompetencies: Array<{name, value}>,  // Top 3 from currentData
}
```

---

## 15. What's NOT in the Engine

These things are skin concerns, not engine concerns:
- What colors represent each skill or archetype
- What font renders the score number
- Whether the radar uses Bezier curves or straight polygons
- Whether the layout is a sidebar or a stacked view
- How long animations take
- Whether there's a grain overlay
- The size of rating dots
- Print stylesheet behavior
- Responsive breakpoints
