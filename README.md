# ML Problem Framing & Responsible Data Card

## Project Overview

This project evaluates whether machine learning is justified for identifying students who may benefit from additional academic support.

Before training any model, it defines the decision, prediction target, baseline approach, data requirements, evaluation metrics, risks, and human-review safeguards.

## Objective

- Define a real-world decision and prediction target.
- Document data provenance, consent, missingness, privacy, and potential bias.
- Establish a transparent rule-based baseline.
- Evaluate baseline predictions using classification metrics.
- Identify false-positive and false-negative costs.
- Define abstention, human review, monitoring, and rollback safeguards.

## Dataset

This project uses a small synthetic dataset containing 15 demonstration records. It does not use real student data.

**Important:** The synthetic labels were intentionally aligned with the baseline rules. Therefore, the perfect evaluation scores are illustrative and do not demonstrate real-world performance.

## Implementation

The baseline flags a record when either:
- Attendance is below 75%, or
- Assignment completion is below 70%.

The notebook calculates accuracy, precision, recall, F1-score, and the confusion matrix.

## Project Files

| File | Description |
|---|---|
| `problem_framing.md` | Decision definition, target, baseline, and evaluation plan |
| `data_card.md` | Data sources, consent, quality, privacy, and fairness considerations |
| `risk_register.md` | Risks, mitigations, abstention, monitoring, and rollback |
| `baseline.ipynb` | Synthetic dataset, baseline predictions, and evaluation metrics |

## Responsible AI Safeguards

Predictions must support, not replace, educator judgment. False negatives, privacy risks, data leakage, missing data, and potential disparities require attention. Real-world use would require authorized data, validation on unseen records, fairness evaluation, and human oversight.

## Conclusion

This project demonstrates responsible ML problem framing and baseline evaluation before model training. It does not train or deploy a machine learning model and is not intended for real educational decisions.

## Tools Used

- Python
- Pandas
- Scikit-learn
- Kaggle Notebooks
- GitHub
