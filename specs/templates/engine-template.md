# The Engine — [Activity Name]
## Workshop Activity: [One-line description]

---

## 1. What This Tool Does

[2–3 sentences. What is being evaluated? What does the reviewer walk away with?]

---

## 2. Relationship to Other Tools

**Connection type:** [Standalone / Loosely coupled / Tightly coupled]

[If connected: what data flows in or out? What's shared (archetypes, career levels, etc.) and what's independent?]

---

## 3. Evaluation Sections

[List each section. For each section, define:]

### Section N: [Name] ([dimension count] dimensions)

```javascript
const SECTION_DIMENSIONS = [
  {
    id: "",           // snake_case, unique across all sections
    name: "",         // Display name
    desc: "",         // What the reviewer is evaluating (1–2 sentences)
    anchor_low: "",   // What a 1 looks like
    anchor_high: "",  // What a 5 looks like
  },
  // ...
];
```

**Scale:** [1–5 / checklist / status enum]
**Max section score:** [number]

[Repeat for each section]

---

## 4. Dynamic Elements (if any)

[Does the tool have a variable-length list? (e.g., case studies, team members, projects)
If so: what's the min/max count? What fields does each entry have?
If not: delete this section.]

---

## 5. Scoring Engine

### Section Scoring

```javascript
// [For each section, define how the raw score is calculated]
```

### Composite Score

```javascript
const grandTotal = /* sum or weighted combination */;
const grandMax = /* theoretical maximum */;
const pct = Math.round((grandTotal / grandMax) * 100);
```

### Section Breakdown

```javascript
const sections = [
  { label: "", score: number, max: number },
  // ...
];
```

---

## 6. Detection / Classification (if any)

[Does the tool detect patterns, archetypes, tiers, or health states?
If so: define the algorithm and the possible outcomes.
If not: delete this section.]

---

## 7. Growth Areas

```javascript
// How are the "top things to improve" identified?
// Usually: collect all dimension scores, sort ascending, take bottom N.
```

---

## 8. Reviewer Context (if applicable)

[Who fills this out? Does the tool adapt based on the reviewer's role?
If not: delete this section.]

---

## 9. State Shape

### Full Application State

```javascript
{
  // Meta fields
  // Section scores (one key per dimension)
  // Dynamic elements (arrays if applicable)
}
```

### Derived State

```javascript
{
  // Computed totals, percentages, classifications
  // Sorted/ranked lists
  // Detected patterns
}
```

---

## 10. Dimension Count Summary

| Section | Dimensions | Scale | Max Score |
|---------|-----------|-------|-----------|
| | | | |
| **Total** | | | |

**Estimated completion time:** [X] minutes for [N] total ratings.

---

## 11. What's NOT in This Engine

These are skin concerns:
- Colors, fonts, spacing, layout
- Animation and transition behavior
- Responsive breakpoints
- Print styling
- Component visual treatment
