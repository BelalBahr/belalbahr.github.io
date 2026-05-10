# Case Study Playbook

## Workflow

1. Discuss and negotiate each section in chat first
2. Propose written content for the section
3. User refines or pushes back
4. Write agreed content into the HTML file
5. Repeat until all sections are done, then do a final review pass

Never write a section to the file without chat agreement first.

---

## HTML Template

### Design Tokens
```css
:root {
  --bg: #ffffff;
  --text: #111827;
  --muted: #6b7280;
  --border: #e5e7eb;
  --accent: #111827;
  --accent-light: #f3f4f6;
  --max-w: 760px;
}
```

### Font
```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap" rel="stylesheet" />
```

### Key Components

**Stat grid (unit economics cards)**
```html
<div class="stat-grid"> <!-- 3-column grid -->
  <div class="stat-card negative"> <!-- negative = red, warning = amber, positive = green -->
    <div class="stat-label">LTV:CAC</div>
    <div class="stat-value">0.85x</div>
    <div class="stat-note">Healthy benchmark is 3x+</div>
  </div>
</div>
```

**Callout block**
```html
<div class="callout">
  <strong>Label</strong><br/>
  Body text here.
</div>
```

**Section header**
```html
<div class="section-header">
  <span class="section-num">01</span>
  <h2>Section Title</h2>
</div>
```

**MoSCoW tags**
```html
<span class="tag p0">Must Have</span>
<span class="tag p1">Should Have</span>
<span class="tag p2">Could Have</span>
```

**Wide table (breaks out of 760px wrapper)**
```css
.table-wrap-wide {
  overflow-x: auto;
  margin: 20px -80px;
  padding: 0 80px;
}
```

**Cover meta separator (middle dot)**
```css
.cover-meta span + span::before { content: '\B7'; margin-right: 24px; color: var(--border); }
```

**Impact vs. Effort SVG chart**
- viewBox: `0 0 640 510`
- Chart area: x=60 to x=610, y=20 to y=380
- Midpoint (dividing lines): x=335 (effort), y=200 (impact)
- Quadrants: Quick Win (top-left, green), Strategic (top-right, blue), Consider (bottom-left, grey), Avoid (bottom-right, red)
- Items: dark filled circles with white number labels
- Legend below chart, two columns at x=60 and x=340

---

## Analytical Frameworks

### Unit Economics (SaaS)
- LTV = ARPU x User Lifetime
- LTV:CAC ratio (healthy = 3x+, break-even = 1x)
- Payback Period = CAC / ARPU
- Monthly Churn = 1 / User Lifetime
- Lever hierarchy: Churn (primary) > ARPU (secondary) > CAC (tertiary)

### Prioritization: MoSCoW + Impact vs. Effort
- Table columns: #, Solution, MoSCoW, Impact, Effort
- MoSCoW column before Impact/Effort
- Note that effort ratings are indicative and should be validated with engineering
- Note that impact ratings should be data-driven
- Always include an SVG Impact vs. Effort chart with items plotted

### Backlog (B2B product)
- User story format for features: "As a [role], I want to [action] so that [outcome]"
- Bug format only for actual bugs, not missing features
- Include: priority tag, category, effort estimate

---

## Writing Rules

- No em dashes (—) anywhere, including CSS `content` properties and title tags
- No numbered labels on solutions in a "Proposed Solutions" section if the prioritization order differs — use names only to avoid false correspondence
- Problems should be root causes, not consequences of other problems
- When sequencing initiatives, explicitly state whether they run in parallel or sequentially
- For any redesign or significant product change, mention A/B testing / phased rollout
- Weekly cadence metrics must be measurable weekly (not lagging metrics like Day-30 retention)
- Bold the candidate name on the cover

## Quality Bar

- Senior PM at Stripe / Figma / Notion level
- Framework-driven, precise, no fluff
- Confident takes with clearly stated assumptions and named trade-offs
- Reads like someone who has shipped in complex environments
- Every claim in the metrics section should trace back to numbers established earlier

---

## Final Review Checklist

- [ ] No em dashes anywhere in the file (including CSS)
- [ ] All cross-references between sections are consistent (problem numbers, solution names, priority order)
- [ ] Math in metrics section is correct and traces back to Part 1 figures
- [ ] Weekly cadence metrics are actually measurable weekly
- [ ] Lagging metrics (Day-30+) have baselines established before targets are set
- [ ] Candidate name is bolded on the cover
- [ ] No numbered solution labels if ordering differs from prioritization section
- [ ] Significant product changes mention validation approach (A/B test, phased rollout)
- [ ] Problems are root causes, not consequences
- [ ] Parallel vs. sequential initiative execution is explicitly stated
