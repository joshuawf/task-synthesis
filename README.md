# Task Value Synthesis

An interactive visualization for analyzing staff task value rankings using the job crafting and Job Demands-Resources frameworks.

Built for the SCAD Office of Curriculum & Assessment. Adapts to any team.

## Live demo

Host on GitHub Pages (instructions below) or open `index.html` directly in any browser — no build step, no dependencies to install.

## Updating the data

All cluster data lives in the `CLUSTERS` array near the top of the `<script>` block in `index.html`. Each cluster looks like this:

```js
{
  id: 'banner',
  name: 'Banner & system error correction',
  desc: 'Short description of the cluster',
  action: 'remove',          // 'remove' | 'structural' | 'revise' | 'protect'
  con: 'low',                // 'low' | 'high' | 'divergent'
  items: [
    { p: 'P2', l: 'Editing / fixing Banner errors', s: 50 },
    { p: 'P4', l: 'Updating catalog info in CourseLeaf', s: 0 },
  ],
  ins: null,                 // insight callout (string or null)
  fw: ['Framework 1', 'Framework 2'],
  reco: 'Your recommended action text here.'
}
```

### Scoring formula

Scores are normalized 0–100 where 100 = most valued:

```
score = round(((total_items - rank) / (total_items - 1)) * 100)
```

Examples with a 5-item list: rank 1 → 100, rank 2 → 75, rank 3 → 50, rank 4 → 25, rank 5 → 0  
Examples with a 7-item list: rank 1 → 100, rank 2 → 83, rank 3 → 67, rank 4 → 50, rank 5 → 33, rank 6 → 17, rank 7 → 0

### Person colors

Edit the `PC` object to change person labels and colors:

```js
const PC = {
  P1: '#378ADD',   // blue
  P2: '#7F77DD',   // purple
  P3: '#1D9E75',   // teal
  P4: '#D85A30',   // coral
  P5: '#BA7517',   // amber
};
```

## Hosting on GitHub Pages

1. Create a new public GitHub repository
2. Upload `index.html` to the root of the repo
3. Go to **Settings → Pages**
4. Under **Source**, select `Deploy from a branch` → `main` → `/ (root)`
5. Click **Save**
6. Your visualization will be live at `https://your-username.github.io/your-repo-name/` within a minute or two

No additional files needed. GitHub Pages serves `index.html` automatically.

## Frameworks referenced

| Framework | Source |
|-----------|--------|
| Job Characteristics Model (JCM) | Hackman & Oldham, 1976 |
| Job Crafting Theory | Wrzesniewski & Dutton, 2001 |
| Job Demands-Resources (JD-R) | Bakker & Demerouti, 2007 |
| Self-Determination Theory (SDT) | Deci & Ryan |
| Administrative Burden Framework | Herd & Moynihan |
| Value Stream Mapping | Lean methodology |
