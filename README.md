# Brigade Workshop Report

Consolidated analysis of participant feedback from the Brigade Workshop & Inauguration event. It summarizes satisfaction ratings and qualitative comments to highlight strengths, improvement areas, and next-step guidance.

## ⚠️ Data Availability & Privacy Disclaimer
The original raw feedback dataset contains personal / student information and is NOT included in this public repository. Only derived, aggregate insights and non-identifying visuals are shared. Please do not upload or redistribute raw response exports (e.g., names, emails, phone numbers). If you clone this repository, you must supply your own local CSV file with equivalent structure to reproduce the analysis.

## Project Contents (Public)
- `event_feedback.ipynb` – Notebook with analysis logic (expects a local CSV; not tracked if sensitive).
- `Event Feedback Analysis.png` – Static summary visualization.
- (Local only, excluded / should be excluded): Raw CSV export with identifiable data.

## Objectives
1. Measure satisfaction across event dimensions.
2. Summarize common feedback themes.
3. Provide actionable indicators for future planning.
4. Offer a lightweight reusable survey analysis template.

## Method Summary
| Step | Technique |
|------|----------|
| Load & Inspect | Pandas read + structural printout |
| Normalize Ratings | Map qualitative scale → numeric 1–5 |
| Identify Satisfaction Fields | Column name pattern search (`"satisfied"`) |
| Aggregate Scores | Mean per aspect + ranking |
| Text Theme Extraction | Simple token frequency (stop word filtered) |
| Sentiment Approximation | Keyword polarity lists (positive / negative) |
| Insight Printout | Completion % + top response modes + recommendations |

## Satisfaction Analysis
Automatically:
- Detects satisfaction columns.
- Converts responses → numeric (1–5).
- Calculates per-aspect means + highlights extremes.
- Produces horizontal & vertical comparative color-coded charts.

Example console summary pattern:
```
==================================================
SATISFACTION ANALYSIS SUMMARY
==================================================
Total satisfaction questions analyzed: N
Overall average satisfaction: X.XX/5.0
Highest rated aspect: <Aspect Name> (Y.YY)
Lowest rated aspect: <Aspect Name> (Z.ZZ)

Detailed Scores:
  • Aspect A: 4.50/5.0
  • Aspect B: 4.20/5.0
  ...
```
(Actual values depend on the underlying private dataset.)

## Text Feedback
Performed:
- Merge text fields (feedback / comments / suggestions / improvement prompts).
- Frequency list (top 10 filtered terms).
- Basic polarity split (positive vs negative keyword hits; remainder neutral).

Limitations: rule‑based sentiment; no stemming; themes could be refined with NLP tooling if privacy constraints allow local processing.

## Insight Generation
`generate_insights(df)` outputs: total responses, question completion rate, counts of satisfaction vs text fields, most common early satisfaction responses, average text length, and heuristic recommendations.

## Visuals
Primary static graphic:
![Event Feedback Analysis](Event%20Feedback%20Analysis.png)

Generated in-notebook (not committed):
- Satisfaction comparison charts
- Word frequency bar
- Sentiment pie

## Benefits
- Lightweight & reproducible.
- Separation of numeric vs free-text logic.
- Clear console summaries for reporting.
- Extendable (add NPS, segmentation, advanced NLP offline).

## Minimal Reproduction (Internal Use Only)
```bash
pip install pandas numpy matplotlib seaborn
# Place a local CSV named similarly to the original form export (structure must match)
jupyter notebook event_feedback.ipynb
# Run all cells (will skip sensitive data export)
```
Optional NLP extensions (use locally only; do not upload enriched outputs):
```bash
pip install textblob vaderSentiment nltk
```

## Privacy & Responsible Use
All identifiable student data must remain local and confidential. Do not commit raw exports. Aggregated metrics and anonymized visuals are acceptable. For any external sharing, re-verify that no free-text contains accidental identifiers.

## Summary
Findings show actionable satisfaction patterns and thematic feedback while preserving participant privacy. This codebase serves as a lean template for future event insight generation without exposing personal data.

---
*Maintained by the Data Analytics Club (internal analytics resource).* 
