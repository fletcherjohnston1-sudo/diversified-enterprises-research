---
name: theme-scanner
description: Scans RSS sources for investment themes, maintains scoring, detects convergence
---

# Theme Scanner Skill

## Purpose
Run blogwatcher scans, extract investment themes from new articles, maintain theme scores with decay and convergence bonuses, and produce structured theme reports for the CEO.

## RSS Sources
- The Innermost Loop blog
- Moonshots podcast

## Data Files (in data/investment/shared/)
- `themes.json`: Theme database with scores, sources, dates
- `watchlist.json`: Pipeline tracker for companies progressing through tiers
- `extraction-log.json`: Audit trail of processed articles

## Scoring Rules
- New mention from any source: +1 point
- Convergence bonus: theme mentioned by BOTH Innermost Loop AND Moonshots within 7 days: +2 points
- Decay: subtract 0.1 points per week since last mention (minimum score: 0)
- Top themes: filter for score >= 3

## Usage
1. Scan RSS sources for new content
2. Extract themes using keyword matching / NLP
3. Update theme scores in themes.json
4. Detect convergence (themes appearing in multiple sources)
5. Add new companies to watchlist pipeline
6. Generate theme report for CEO
7. Log extraction to extraction-log.json

## Output
- Updated themes.json
- Updated watchlist.json
- Theme report sent to CEO

## Notes
- Use blogwatcher for RSS scanning
- Store tokens in workspace-research config
- Run weekly or on CEO request
