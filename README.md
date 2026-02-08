# Aequitas--The-Ethical-Hiring-Auditor
Aequitas: The Ethical Hiring Auditor ⚖️
Aequitas is a machine learning auditing project designed to detect and mitigate systemic bias in recruitment datasets. This project demonstrates the "Fairness-Accuracy Paradox"—the challenge of balancing high predictive performance with legal equity in automated hiring.

📊 The Challenge: "The Bias Mirror"
Initial exploratory data analysis (EDA) revealed that the raw historical data was deeply "poisoned" by human prejudice:
 * Baseline AIR: 0.62. (Women were hired at only 62% of the rate of men, failing the legal 80% Rule).
 * Predictive Trap: Early models achieved a 99.78% F1-score by simply "mirroring" historical discrimination.

🛠️ Methodology: The Audit Approach
I implemented a three-pillar audit to transform the model from a biased predictor into a merit-centric tool:
1. Controlled Outlier Mitigation
 * Action: Performed a single-pass outlier removal on Career_Gap_Months while retaining moderate edge cases.
 * Why: This raised the AIR from 0.62 to 0.707 while ensuring the model remained realistic and robust.
2. Statistical Stabilization (VIF Audit)
 * Action: Identified and removed Technical_Score (26.05) and KPI_Completion_Pct (26.55) due to extreme Multicollinearity (VIF > 26).
 * Why: High VIF values indicate redundant features that destabilize model weights. Removing them ensured the model's coefficients were mathematically reliable.
3. Proxy Decoupling
 * Action: Analyzed the feature correlation matrix to identify "hidden" bias.
 * Why: Confirmed that Career_Gap_Months acted as a proxy for gender, allowing for more transparent feature selection.

🔍 Visual Audit & Insights
Feature Correlation Matrix (Post-VIF Audit)
 * Key Finding: The heatmap reveals a significant -0.57 correlation between Gender and Career_Gap_Months. This proves that even after cleaning technical features, the "Career Gap" remains a strong proxy for gender bias in this dataset.
Fairness Progress (AIR Improvement)
 * Result: Through strategic data cleaning and auditing, the Adverse Impact Ratio was improved from a failing 0.62 to 0.707.

📈 Final Results
| Metric | Baseline (Raw) | Final Model (Audited) | Status |
|---|---|---|---|
| F1-Score | 99.78% | 94.67% | High Reliability ✅ |
| AIR (Fairness) | 0.62 | 0.707 | Equity Gain (+14%) 📈 |
| Max VIF | 26.56 | < 7.0 | Mathematically Stable ✅ |

🧠 Conclusion: The "Fairness Ceiling"
The audit successfully improved hiring equity by 14%. However, the final AIR of 0.707 reveals a "Fairness Ceiling"—a point where mathematical fixes cannot fully overcome structural bias in historical labels.
Key Takeaway: For a model to reach the 0.80 gold standard, the data collection process itself must be improved at the source. This project serves as evidence that Ethical AI requires auditing the integrity of the data foundation, not just the code.
