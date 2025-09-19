# Brigade Workshop Report

A consolidated analysis of participant feedback collected during the Brigade Workshop & Inauguration event. This report summarizes quantitative satisfaction ratings and qualitative text feedback to highlight strengths, areas for improvement, and actionable recommendations.

## 📁 Project Contents
- `event_feedback.ipynb` – Jupyter Notebook containing full exploratory analysis, visualizations, and insight generation code.
- `Event Feedback (Responses) - Form Responses 1.csv` – Raw feedback dataset exported from the form platform.
- `Event Feedback Analysis.png` – Summary visualization (static) for quick reference.
- `Workshop_Registration_Cleaned.csv` / `Workshop_final_cleaned.csv` – Cleaned registration / processed datasets (if used for cross-reference).
- `Photos/` – Event media assets (not analyzed here but useful for reporting/presentation).

## 🎯 Objectives
1. Assess participant satisfaction across key aspects of the event.
2. Extract common themes from open-ended feedback (comments, suggestions, improvements).
3. Provide measurable indicators to guide future event planning.
4. Produce a reusable analysis framework (rating parsing, sentiment approximation, text frequency analysis).

## 🧠 Methodology Overview
| Component | Approach |
|-----------|---------|
| Data Loading | Pandas read of CSV export |
| Rating Normalization | Custom parser mapping “Very Satisfied” → 5 … “Very Dissatisfied” → 1 |
| Satisfaction Detection | Column name pattern match: contains the term `satisfied` (case-insensitive) |
| Aggregation | Mean score per aspect; horizontal & vertical bar charts |
| Text Processing | Tokenization → stop word filtering → frequency count (Top 10 words) |
| Sentiment Approximation | Keyword-based (positive vs negative lexicon; remainder neutral) |
| Insight Generation | Completion rate, most common responses, qualitative length metrics |

## 📊 Satisfaction Analysis
The notebook automatically:
- Identifies all satisfaction-related columns.
- Converts responses to a 1–5 numeric scale.
- Computes average score per aspect.
- Highlights highest and lowest rated dimensions.
- Renders both horizontal and vertical comparative bar plots with a Red→Yellow→Green color scale.

Example console summary (structure produced by the notebook):
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
(Actual values depend on the dataset contents at execution time.)

## 🗣️ Text Feedback Insights
Steps performed:
- Consolidates all columns containing keywords: `feedback`, `comment`, `suggestion`, `improve`.
- Builds a frequency distribution of the top 10 non-trivial words.
- Simple sentiment proxy using curated positive/negative keyword lists.
- Generates dual-panel visualization: (1) Top terms bar chart, (2) Sentiment pie chart.

Limitations:
- No lemmatization/stemming (e.g., “improving” vs “improve”).
- Sentiment is rule-based — consider upgrading to VADER/TextBlob/spaCy or transformer models for richer nuance.

## 🧾 Insight Generation Module
The `generate_insights(df)` function prints:
- Total survey responses.
- Average completion rate (percentage of non-null answers per question).
- Count of satisfaction and text-based questions.
- Most common responses for first three satisfaction items.
- Average character length of open-ended feedback.
- Recommendation flags (e.g., survey length optimization, standardization of rating scales).

## 🖼️ Visualizations
Embedded static export (ensure the file exists at path):
![Event Feedback Analysis](Event%20Feedback%20Analysis.png)

Additional plots are produced dynamically inside the notebook:
- Horizontal satisfaction bar chart.
- Vertical satisfaction bar chart.
- Word frequency bar chart.
- Sentiment distribution pie chart.

## ✅ Key Benefits of This Framework
- Reusable parsing logic for varied survey exports.
- Clean separation of numeric vs text feedback workflows.
- Human-readable console summaries for quick reporting.
- Easily extensible (add NPS, correlation between aspects, demographic splits if data available).

## 🚀 Potential Enhancements
| Enhancement | Rationale |
|-------------|-----------|
| Advanced Sentiment (VADER / transformers) | Improve nuance & accuracy |
| Topic Modeling (LDA / BERTopic) | Group suggestion themes |
| Outlier Detection in Ratings | Identify unusually low-scoring segments |
| Demographic Segmentation | Tailor improvements per participant group |
| Time-Based Trends (if timestamped) | Detect satisfaction drift during event |
| Dashboard (Streamlit/Plotly Dash) | Interactive stakeholder access |

## 🛠️ How to Reproduce
```bash
# 1. Ensure Python 3.10+ environment
# 2. Install core libraries if missing
pip install pandas numpy matplotlib seaborn

# 3. Open the notebook
ejupyter notebook event_feedback.ipynb

# 4. Execute all cells to regenerate visuals and summaries
```
(Optional) For text enhancements:
```bash
pip install nltk textblob vaderSentiment spacy
python -m textblob.download_corpora
```

## 📂 File Naming Notes
Spaces and special characters (like `&`) in directory names may require quoting or escaping in some shells. In Windows PowerShell, commands generally handle them if you tab-complete paths. In bash, wrap in quotes: `"Brigade_Workshop & Inauguration"`.

## 🔒 Data & Privacy
Ensure that no personally identifiable information (PII) is published if the response dataset includes names/emails. Consider anonymizing before public release.

## 📌 Summary
The Brigade Workshop feedback indicates strong participant engagement with structured satisfaction metrics and actionable qualitative insights. This repository serves as a foundation for iterative analytics improvements and future event intelligence.

---
*Maintained by the Data Analytics Club. Contributions and iterative enhancements are welcome.*
