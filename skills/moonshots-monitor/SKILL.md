---
name: moonshots-monitor
description: Monitors Moonshots podcast for investment themes and company mentions
---
# Moonshots Monitor Skill

## Purpose
Track the Moonshots podcast RSS feed for new episodes, extract investment themes and company mentions, and feed them into the theme scoring system.

## RSS Source
Moonshots podcast feed (configured in blogwatcher)

## Workflow
1. Run blogwatcher scan to check for new Moonshots episodes
2. For each new episode found:
   a. Extract all investment themes mentioned
   b. Extract all company names and tickers mentioned
   c. Note any specific bull/bear cases discussed
3. Update data/investment/shared/themes.json:
   - +1 score for each theme mentioned
   - Tag the source as "moonshots" with episode date
4. Update data/investment/shared/extraction-log.json with processing details
5. Check for convergence: if any extracted theme also appears in Innermost Loop within 30 days, flag it

## Output
No separate output file. Updates themes.json and extraction-log.json directly. Convergence flags will be picked up by the theme-scanner skill during weekly prep.
