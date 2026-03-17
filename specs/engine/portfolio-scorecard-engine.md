# The Engine — Portfolio Scorecard
## Workshop Activity: Evaluate Your Portfolio

---

## 1. What This Tool Does

A structured evaluation of a designer's portfolio — both the portfolio site as a container and the individual case studies within it. It works for self-assessment, peer review, or mentor feedback. The reviewer rates dimensions on the same 1–5 dot scale used in the Designer Scorecard.

The tool produces two layers of output: an overall portfolio health score, and per-case-study quality breakdowns that reveal which projects are carrying the portfolio and which are dragging it down.

---

## 2. Relationship to the Designer Scorecard

**Loosely coupled.** The 7 archetypes from the Competency Radar exist in this tool as context, not dependency:

- The reviewer can optionally select the portfolio owner's archetype (or "unsure / skip")
- If an archetype is selected, the results panel shows **archetype-specific guidance** — what a strong portfolio looks like *for that type of designer*
- Scoring is fully independent — no data flows in from the Designer Scorecard, no shared state

### Archetype-Specific Portfolio Expectations

These are guidance notes, not scoring modifiers. They appear in the results panel when an archetype is selected.

```javascript
const PORTFOLIO_GUIDANCE = {
  storyteller: {
    strength: "Narrative arc and emotional resonance across case studies",
    watch_for: "Portfolio itself should feel like an experience, not just a container",
    case_study_emphasis: "Process should read like a story — setup, tension, resolution",
  },
  systems: {
    strength: "Before/after clarity showing complexity made navigable",
    watch_for: "Dense information needs a guiding narrative — don't just show the system, explain why it works",
    case_study_emphasis: "Data visualization, information hierarchy, scalability evidence",
  },
  brand: {
    strength: "Visual cohesion — the portfolio itself is a brand artifact",
    watch_for: "Every detail (typography, spacing, micro-copy) should feel intentional and unified",
    case_study_emphasis: "Show the whole world: logo, type, color, packaging, environment, motion",
  },
  interaction: {
    strength: "Prototypes, motion studies, and interaction details front and center",
    watch_for: "Static screenshots undersell this archetype — embedded prototypes or video are essential",
    case_study_emphasis: "Micro-interactions, state transitions, responsiveness to user intent",
  },
  service: {
    strength: "Journey maps, blueprints, ecosystem diagrams showing the big picture",
    watch_for: "Can feel abstract without grounding in real human stories and outcomes",
    case_study_emphasis: "End-to-end journey, stakeholder maps, before/after service flows",
  },
  strategist: {
    strength: "Insight frameworks, research synthesis, evidence of changing what gets built",
    watch_for: "Portfolio can feel text-heavy — needs visual anchors and clear structure",
    case_study_emphasis: "Problem reframing, research methodology, impact on product direction",
  },
  technologist: {
    strength: "Live demos, interactive prototypes, things that make you ask 'how?'",
    watch_for: "Technical impressiveness without user context feels like a tech demo, not design work",
    case_study_emphasis: "Creative use of technology in service of design goals, not technology for its own sake",
  },
};
```

---

## 3. Evaluation Sections

The portfolio is evaluated in three sections: the portfolio shell (the site/container), per-case-study quality, and portfolio strategy (the collection as a whole).

### Section 1: Portfolio Shell (8 dimensions)

These rate the portfolio website/presentation itself — the container that holds the work.

```javascript
const SHELL_DIMENSIONS = [
  {
    id: "first_impression",
    name: "First Impression",
    desc: "Does the portfolio make a strong visual impact in the first 5 seconds? Is the design quality itself a signal of competence?",
    anchor_low: "Generic template feel, no visual point of view",
    anchor_high: "Immediately distinctive, craft is evident, you want to keep looking",
  },
  {
    id: "navigation",
    name: "Navigation & Structure",
    desc: "Can you find what you need? Is the information architecture clear? Does the hierarchy guide you or confuse you?",
    anchor_low: "Confusing structure, buried content, unclear where to go",
    anchor_high: "Effortless navigation, logical grouping, clear hierarchy at every level",
  },
  {
    id: "about_story",
    name: "About & Personal Brand",
    desc: "Does the designer come through as a person? Is there a clear point of view, personality, or positioning?",
    anchor_low: "Generic bio, no personality, could be anyone",
    anchor_high: "Distinct voice, clear positioning, memorable — you know who this person is",
  },
  {
    id: "visual_quality",
    name: "Visual Design Quality",
    desc: "Typography, spacing, color, imagery — does the portfolio site itself demonstrate design skill?",
    anchor_low: "Sloppy spacing, inconsistent type, poor image quality",
    anchor_high: "Every detail is intentional — type, color, spacing, imagery all reinforce each other",
  },
  {
    id: "responsiveness",
    name: "Responsiveness & Accessibility",
    desc: "Does the site work across devices? Is text readable? Are images optimized? Can it be navigated by keyboard?",
    anchor_low: "Broken on mobile, slow loading, inaccessible",
    anchor_high: "Flawless across devices, fast, accessible, progressive enhancement",
  },
  {
    id: "writing_quality",
    name: "Writing & Copy Quality",
    desc: "Is the writing clear, concise, and free of errors? Does it communicate with confidence without jargon overload?",
    anchor_low: "Typos, jargon-heavy, unclear or rambling",
    anchor_high: "Crisp, confident, well-edited — writing matches the visual quality",
  },
  {
    id: "contact_cta",
    name: "Contact & Call to Action",
    desc: "Is it clear what the designer wants you to do? Is contact information easy to find? Is there a sense of invitation?",
    anchor_low: "No clear next step, buried contact info, feels like a dead end",
    anchor_high: "Clear CTA, easy contact, inviting tone — you know exactly how to engage",
  },
  {
    id: "loading_perf",
    name: "Performance & Polish",
    desc: "Does the site load fast? Are there broken links, missing images, or rough edges? Does it feel finished?",
    anchor_low: "Slow, broken elements, clearly unfinished areas",
    anchor_high: "Snappy, zero rough edges, every page feels complete and cared for",
  },
];
```

**Scale:** 1–5 per dimension. Max section total: 40.

### Section 2: Case Study Quality (per-case-study, variable count)

The reviewer adds 1–6 case studies by name, then rates each one across 6 dimensions.

```javascript
const CASE_STUDY_DIMENSIONS = [
  {
    id: "problem_framing",
    name: "Problem Framing",
    desc: "Is the design challenge clearly stated? Do you understand the context, constraints, and why this problem mattered?",
    anchor_low: "Jumps straight to solutions, no context for why this project exists",
    anchor_high: "Crystal clear setup — you understand the stakes, the users, and the constraints before seeing any design work",
  },
  {
    id: "process_depth",
    name: "Process & Methodology",
    desc: "Is there evidence of a design process? Research, ideation, iteration, testing — not just final screens.",
    anchor_low: "Final mockups only, no evidence of how decisions were made",
    anchor_high: "Rich process documentation — research artifacts, sketches, iterations, decision rationale",
  },
  {
    id: "storytelling",
    name: "Narrative & Flow",
    desc: "Does the case study read as a coherent story with a beginning, middle, and end? Is there a logical progression?",
    anchor_low: "Disjointed, feels like a random collection of images with captions",
    anchor_high: "Compelling narrative arc — you're pulled through the story and want to see what happens next",
  },
  {
    id: "outcomes",
    name: "Outcomes & Impact",
    desc: "Are results shown? Metrics, user feedback, business impact, lessons learned — evidence that the work mattered.",
    anchor_low: "Ends abruptly with final screens, no indication of whether it worked",
    anchor_high: "Clear outcomes with evidence — quantitative metrics, qualitative feedback, honest reflection on what worked and what didn't",
  },
  {
    id: "visual_execution",
    name: "Visual Execution",
    desc: "Is the design work itself well-crafted? Are the mockups, diagrams, and artifacts presented with care?",
    anchor_low: "Low-quality screenshots, poor presentation of the actual work",
    anchor_high: "Beautiful presentation — the work speaks for itself and is shown in its best light",
  },
  {
    id: "role_clarity",
    name: "Role & Contribution",
    desc: "Is it clear what this designer specifically did versus what the team did? Is the scope of their contribution honest?",
    anchor_low: "Unclear who did what — could be taking credit for team work or underselling their role",
    anchor_high: "Precise about their contribution — honest, specific, gives credit to collaborators",
  },
];
```

**Scale:** 1–5 per dimension per case study. Max per case study: 30. Max section total: depends on case study count.

### Section 3: Portfolio Strategy (5 dimensions)

These evaluate the portfolio as a curated collection — the editorial choices about what to include and how to position it.

```javascript
const STRATEGY_DIMENSIONS = [
  {
    id: "variety",
    name: "Range & Variety",
    desc: "Does the portfolio show breadth of skill? Different project types, industries, or problem spaces?",
    anchor_low: "All projects look the same — same industry, same deliverable type, no range",
    anchor_high: "Demonstrates versatility — different contexts, scales, and challenges while maintaining a coherent identity",
  },
  {
    id: "depth_vs_breadth",
    name: "Depth vs. Breadth Balance",
    desc: "Is the right amount of work shown? Too many shallow case studies or too few deep ones?",
    anchor_low: "Either 10 shallow thumbnails or 1 case study that goes on forever",
    anchor_high: "Right number of projects (3–5) at the right depth — enough to understand the designer without overwhelming",
  },
  {
    id: "recency",
    name: "Recency & Relevance",
    desc: "Is the work current? Does it reflect where the designer is now, not where they were 5 years ago?",
    anchor_low: "Oldest work is most prominent, nothing from the last 1–2 years",
    anchor_high: "Freshest and strongest work is featured, older work is archived or removed",
  },
  {
    id: "target_audience",
    name: "Audience Awareness",
    desc: "Does the portfolio speak to its intended audience? If targeting product companies, does it show product thinking? If agencies, does it show client work?",
    anchor_low: "No clear audience — generic portfolio that doesn't signal who it's for",
    anchor_high: "Clearly positioned — you can tell what kind of role and company this designer is targeting",
  },
  {
    id: "differentiation",
    name: "Differentiation & Point of View",
    desc: "Does this portfolio stand out from the thousands of other designer portfolios? Is there a unique angle, voice, or perspective?",
    anchor_low: "Interchangeable with any other designer's portfolio — nothing memorable",
    anchor_high: "Unmistakably this person — unique voice, distinct perspective, memorable positioning",
  },
];
```

**Scale:** 1–5 per dimension. Max section total: 25.

---

## 4. Case Study Management

Unlike the Designer Scorecard (fixed sections), this tool has a **dynamic list** of case studies. The reviewer creates entries, names them, and rates each one.

### Case Study State

```javascript
// Each case study:
{
  id: string,          // Generated: "cs_1", "cs_2", etc.
  name: string,        // User-entered: "Checkout Redesign", "Patient Portal", etc.
  scores: {
    problem_framing: 0–5,
    process_depth: 0–5,
    storytelling: 0–5,
    outcomes: 0–5,
    visual_execution: 0–5,
    role_clarity: 0–5,
  },
}
```

### Constraints
- Minimum: 1 case study (can't score an empty portfolio)
- Maximum: 6 case studies (forces prioritization — if a portfolio has more, rate the 6 most important)
- Case studies can be added and removed
- Removing a case study recalculates all totals

---

## 5. Scoring Engine

### Section Scoring

```javascript
// Section 1: Portfolio Shell
const shellTotal = SHELL_DIMENSIONS.reduce(
  (sum, dim) => sum + (shellScores[dim.id] || 0), 0
);
// Max: 40 (8 dimensions × 5)

// Section 2: Case Studies (averaged)
// Each case study has a max of 30 (6 dimensions × 5)
// The section score is the AVERAGE across all case studies, scaled to 30
const caseStudyScores = caseStudies.map(cs => {
  return CASE_STUDY_DIMENSIONS.reduce(
    (sum, dim) => sum + (cs.scores[dim.id] || 0), 0
  );
});
const caseStudyAvg = caseStudyScores.length > 0
  ? caseStudyScores.reduce((a, b) => a + b, 0) / caseStudyScores.length
  : 0;
// Max: 30 (this is already on a 30-point scale since 6 dims × 5 = 30)

// Section 3: Portfolio Strategy
const strategyTotal = STRATEGY_DIMENSIONS.reduce(
  (sum, dim) => sum + (strategyScores[dim.id] || 0), 0
);
// Max: 25 (5 dimensions × 5)
```

### Composite Score

```javascript
const grandTotal = shellTotal + Math.round(caseStudyAvg) + strategyTotal;
const grandMax = 40 + 30 + 25; // = 95
const pct = Math.round((grandTotal / grandMax) * 100);
```

### Section Breakdown (for display)

```javascript
const sections = [
  { label: "Portfolio Shell",     score: shellTotal,                max: 40 },
  { label: "Case Studies (avg)",  score: Math.round(caseStudyAvg),  max: 30 },
  { label: "Strategy",            score: strategyTotal,             max: 25 },
];
```

### Why Average Case Studies?

A portfolio with 2 excellent case studies should score higher than one with 5 mediocre ones. Averaging rewards quality over quantity. The strategy section's "Depth vs. Breadth Balance" dimension separately captures whether the right number of projects is shown.

---

## 6. Per-Case-Study Analysis

Each case study gets its own mini-report in the results panel.

### Case Study Score

```javascript
function getCaseStudyScore(cs) {
  const total = CASE_STUDY_DIMENSIONS.reduce(
    (sum, dim) => sum + (cs.scores[dim.id] || 0), 0
  );
  return {
    total,           // 0–30
    pct: Math.round((total / 30) * 100),
    dimensions: CASE_STUDY_DIMENSIONS.map(dim => ({
      name: dim.name,
      score: cs.scores[dim.id] || 0,
    })),
  };
}
```

### Case Study Ranking

```javascript
const rankedCaseStudies = [...caseStudies]
  .map(cs => ({ ...cs, ...getCaseStudyScore(cs) }))
  .sort((a, b) => b.total - a.total);
```

Display shows strongest case study first, weakest last. This naturally surfaces "your portfolio is only as strong as your weakest case study" — or reveals when one project is carrying everything.

### Case Study Strength Classification

```javascript
function classifyCaseStudy(total) {
  if (total >= 25) return { label: "Standout",     tier: "A" };
  if (total >= 20) return { label: "Solid",         tier: "B" };
  if (total >= 15) return { label: "Needs Work",    tier: "C" };
  if (total >= 10) return { label: "Weak",          tier: "D" };
  return                   { label: "Consider Removing", tier: "F" };
}
```

Thresholds:
- **25–30 (A):** This case study is a portfolio anchor. Feature it prominently.
- **20–24 (B):** Solid work. Keep it, consider strengthening weak dimensions.
- **15–19 (C):** Middling. Needs significant revision to pull its weight.
- **10–14 (D):** Actively hurting the portfolio. Major rework or remove.
- **0–9 (F):** Remove this. An unfinished or weak case study is worse than no case study.

---

## 7. Portfolio Health Detection

Instead of archetypes, this tool detects **portfolio health patterns** — common problems and strengths.

```javascript
const PORTFOLIO_PATTERNS = [
  {
    id: "all_sizzle",
    name: "All Sizzle, No Steak",
    desc: "Beautiful portfolio shell, but case studies lack depth and outcomes.",
    detect: (shell, csAvg, strategy) =>
      shell >= 32 && csAvg <= 18,
  },
  {
    id: "buried_treasure",
    name: "Buried Treasure",
    desc: "Strong case studies hidden behind a weak portfolio shell.",
    detect: (shell, csAvg, strategy) =>
      shell <= 24 && csAvg >= 22,
  },
  {
    id: "no_proof",
    name: "No Proof of Impact",
    desc: "Good process documentation but outcomes are missing across the board.",
    detect: (shell, csAvg, strategy, dimScores) =>
      dimScores.outcomes_avg <= 2,
  },
  {
    id: "one_trick",
    name: "One-Trick Portfolio",
    desc: "Low variety — all projects look the same.",
    detect: (shell, csAvg, strategy, dimScores) =>
      dimScores.variety <= 2,
  },
  {
    id: "graveyard",
    name: "The Graveyard",
    desc: "Work is outdated — portfolio doesn't reflect current abilities.",
    detect: (shell, csAvg, strategy, dimScores) =>
      dimScores.recency <= 2,
  },
  {
    id: "identity_crisis",
    name: "Identity Crisis",
    desc: "No clear audience or positioning — portfolio tries to be everything to everyone.",
    detect: (shell, csAvg, strategy, dimScores) =>
      dimScores.target_audience <= 2 && dimScores.differentiation <= 2,
  },
  {
    id: "strong_foundation",
    name: "Strong Foundation",
    desc: "Solid across the board — ready for targeted polish, not a rebuild.",
    detect: (shell, csAvg, strategy) =>
      shell >= 28 && csAvg >= 20 && strategy >= 18,
  },
  {
    id: "portfolio_ready",
    name: "Portfolio Ready",
    desc: "This portfolio is a competitive asset. Focus on keeping it current.",
    detect: (shell, csAvg, strategy) =>
      shell >= 34 && csAvg >= 25 && strategy >= 21,
  },
];
```

Detection runs top-to-bottom; first match wins (negative patterns checked before positive ones). If no pattern matches, display a neutral "Keep going — rate more dimensions for a diagnosis."

### Dimension Averages for Pattern Detection

```javascript
// For patterns that need per-dimension analysis across all case studies:
const dimScores = {};
CASE_STUDY_DIMENSIONS.forEach(dim => {
  const vals = caseStudies
    .map(cs => cs.scores[dim.id] || 0)
    .filter(v => v > 0);
  dimScores[dim.id + "_avg"] = vals.length > 0
    ? vals.reduce((a, b) => a + b, 0) / vals.length
    : 0;
});
// Add strategy dimensions directly
STRATEGY_DIMENSIONS.forEach(dim => {
  dimScores[dim.id] = strategyScores[dim.id] || 0;
});
```

---

## 8. Growth Areas

Same concept as the Designer Scorecard — surface the lowest-rated dimensions.

```javascript
const growthAreas = [
  // Shell dimensions
  ...SHELL_DIMENSIONS.map(dim => ({
    name: dim.name,
    score: shellScores[dim.id] || 0,
    section: "Portfolio Shell",
  })),
  // Strategy dimensions
  ...STRATEGY_DIMENSIONS.map(dim => ({
    name: dim.name,
    score: strategyScores[dim.id] || 0,
    section: "Strategy",
  })),
  // Case study dimensions (averaged across all case studies)
  ...CASE_STUDY_DIMENSIONS.map(dim => ({
    name: dim.name,
    score: Math.round(
      caseStudies.reduce((sum, cs) => sum + (cs.scores[dim.id] || 0), 0)
      / Math.max(caseStudies.length, 1)
    ),
    section: "Case Studies",
  })),
]
  .sort((a, b) => a.score - b.score)
  .slice(0, 3);
```

---

## 9. Reviewer Context

Since this tool works for self-review, peer review, and mentor feedback, the reviewer's relationship to the portfolio is captured as metadata.

```javascript
const REVIEWER_TYPES = [
  { id: "self",   label: "Self-Assessment" },
  { id: "peer",   label: "Peer Review" },
  { id: "mentor", label: "Mentor / Leader Review" },
];
```

This affects display copy only (e.g., "Your portfolio" vs. "This portfolio") — not scoring. It's captured in the state for export context.

---

## 10. State Shape

### Full Application State

```javascript
{
  // Meta
  designerName: string,             // Who owns the portfolio
  reviewerName: string,             // Who is reviewing (may be same person)
  reviewerType: "self" | "peer" | "mentor",
  archetype: string | null,         // Optional: one of 7 archetype keys
  date: string,                     // Auto-generated ISO date

  // Section 1: Portfolio Shell
  shellScores: {
    first_impression: 0–5,
    navigation: 0–5,
    about_story: 0–5,
    visual_quality: 0–5,
    responsiveness: 0–5,
    writing_quality: 0–5,
    contact_cta: 0–5,
    loading_perf: 0–5,
  },

  // Section 2: Case Studies (dynamic array)
  caseStudies: [
    {
      id: "cs_1",
      name: "Project Name",
      scores: {
        problem_framing: 0–5,
        process_depth: 0–5,
        storytelling: 0–5,
        outcomes: 0–5,
        visual_execution: 0–5,
        role_clarity: 0–5,
      },
    },
    // ... up to 6
  ],

  // Section 3: Portfolio Strategy
  strategyScores: {
    variety: 0–5,
    depth_vs_breadth: 0–5,
    recency: 0–5,
    target_audience: 0–5,
    differentiation: 0–5,
  },
}
```

### Derived State (computed, not stored)

```javascript
{
  shellTotal: number,               // 0–40
  caseStudyAvg: number,             // 0–30
  strategyTotal: number,            // 0–25
  grandTotal: number,               // 0–95
  pct: number,                      // 0–100

  rankedCaseStudies: Array<{        // Case studies sorted by score
    id, name, total, pct, tier, label,
    dimensions: Array<{name, score}>
  }>,

  pattern: PortfolioPattern | null, // Detected health pattern
  growthAreas: Array<{name, score, section}>, // Bottom 3 dimensions
  
  archetypeGuidance: {              // If archetype selected
    strength, watch_for, case_study_emphasis
  } | null,
}
```

---

## 11. Dimension Count Summary

| Section | Dimensions | Scale | Max Score |
|---------|-----------|-------|-----------|
| Portfolio Shell | 8 | 1–5 each | 40 |
| Case Studies (per study) | 6 | 1–5 each | 30 per study |
| Case Studies (section) | averaged | — | 30 (normalized) |
| Portfolio Strategy | 5 | 1–5 each | 25 |
| **Total** | **19 unique + 6 per case study** | | **95** |

For a reviewer evaluating a portfolio with 3 case studies, that's 19 + 18 = **37 individual ratings** — completable in 15–20 minutes.

---

## 12. What's NOT in This Engine

These are skin concerns:
- Colors assigned to each dimension or section
- Whether case studies are rendered as cards, an accordion, or tabs
- Layout of the results panel
- Animation on the radar chart
- How the case study ranking is visually presented
- Typography and spacing
- The grain overlay and glow effects
- Print styling
