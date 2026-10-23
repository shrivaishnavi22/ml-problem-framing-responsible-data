# ML Problem Framing & Responsible Data Card

## 1. Project Overview

**Project Title:** Student Academic Support Risk Prediction

**Task:** ML Problem Framing & Responsible Data Card

**Project Stage:** Problem Definition and Feasibility Assessment

**Status:** Before Model Training

### Objective

The objective of this project is to determine whether machine learning can help identify students who may benefit from additional academic support. Before developing a model, the project defines the decision to be supported, the prediction target, data requirements, evaluation metrics, potential harms, and fallback procedures.

The system is intended to support educators in offering timely assistance. It must not be used to label students permanently, punish them, or make important academic decisions automatically.

## 2. Problem Definition

### Real-World Problem

Educators may find it difficult to identify students who need additional academic support early enough. Reviewing attendance, previous assessment results, assignment completion, and other relevant academic indicators manually can take time.

A data-driven system could help prioritize students for supportive follow-up. However, a simple rule-based approach may be sufficient, and machine learning should only be considered if it demonstrates measurable improvements.

### Decision to Be Supported

The system will help educators decide which students may benefit from an academic check-in, tutoring session, or additional learning resources.

The prediction will be used as a recommendation for human review, not as a final decision about a student's ability or future performance.

### Prediction Target

The proposed prediction target is whether a student will require additional academic support during the next four weeks.

For an initial feasibility study, this outcome must be defined using a consistent and documented criterion, such as a student meeting a pre-agreed academic support threshold.

The target must not be treated as an objective measure of a student's intelligence, effort, or potential.

### Unit of Observation

One observation represents one student at a specific prediction date.

If a student has multiple observations across different weeks, those records must be handled carefully to prevent the same student's information from leaking between training and evaluation datasets.

### Prediction Time and Action Window

- **Prediction time:** At the beginning of each four-week support period.
- **Action window:** The following four weeks.
- **Available information:** Only information recorded and available before the prediction time.
- **Intended action:** A teacher or authorized support staff member reviews the recommendation and decides whether to offer assistance.

## 3. Is Machine Learning Justified?

Machine learning is not automatically the best solution for this problem.

### Proposed ML Approach

A supervised binary classification model could estimate whether a student may need additional academic support during the next four weeks.

Potential input features include:

- Recent attendance percentage.
- Previous assessment scores.
- Assignment completion rate.
- Changes in academic performance over time.
- Previous support participation, if appropriately collected and justified.

The proposed target would be a consistently defined indicator of whether additional support was needed during the outcome period.

These features are hypotheses, not proven predictors. Their usefulness, availability, quality, and fairness must be assessed before model development.

### Non-ML Baseline

The initial baseline will be a transparent rule-based method.

For example, an educator could flag students for review when their recent assessment results fall below a predefined academic threshold or when attendance falls below an institution-approved threshold.

The thresholds must be documented and validated with educators before use. They are illustrative and are not intended to be universal standards.

The baseline will be compared with the proposed ML approach using the same held-out evaluation data and evaluation period.

### Conditions for Using ML

Machine learning will only be considered justified if:

1. Sufficient, reliable, appropriately authorized, and representative historical data are available.
2. The target outcome can be defined consistently.
3. The ML approach improves useful outcomes compared with the rule-based baseline.
4. False predictions and their potential harms are acceptable.
5. The system can be monitored and reviewed by authorized humans.
6. The benefits justify the additional complexity, cost, and maintenance.

**Fallback:** If these conditions are not met, retain the transparent rule-based approach or use manual educator review.

## 4. Data Requirements and Assumptions

No real student records have been collected or analyzed as part of this problem-framing stage.

The following data requirements are proposed for a future feasibility study.

| Data element | Purpose | Main consideration |
|---|---|---|
| Attendance percentage | Understand recent attendance patterns | Absence may have legitimate reasons |
| Previous assessment scores | Understand academic performance | Assessments may not measure every learning outcome |
| Assignment completion rate | Identify possible learning difficulties | Missing submissions may have different causes |
| Historical support outcome | Define the prediction target | Must use a consistent, documented criterion |
| Prediction date | Establish when information became available | Prevent temporal data leakage |

The project must document the source, collection purpose, access permissions, retention period, and limitations of each data element before using real data.

Sensitive information must not be collected merely because it is available. Access must be restricted to authorized personnel.

## 5. Success Criteria and Evaluation Metrics

The project will evaluate both model performance and practical usefulness.

### Model Evaluation Metrics

- **Precision:** Of the students flagged by the system, how many met the defined support criterion?
- **Recall:** Of the students who met the support criterion, how many were identified?
- **F1-score:** A combined measure of precision and recall.
- **Confusion matrix:** Counts of true positives, false positives, true negatives, and false negatives.
- **Calibration:** Whether predicted probabilities correspond reasonably to observed outcome frequencies, if the model produces probabilities.

Accuracy alone will not be sufficient because the proportions of students needing support and not needing support may be unequal.

### Business and Educational Success Metrics

The project will examine whether the approach:

- Identifies students who may benefit from timely assistance.
- Improves identification compared with the rule-based baseline.
- Supports educators without creating an excessive review workload.
- Avoids unacceptable differences in error rates across appropriately assessed groups.
- Provides useful recommendations without replacing educator judgment.

No performance improvement is claimed at this stage. Numerical acceptance thresholds must be agreed upon with relevant stakeholders before evaluating a model.

## 6. False-Positive and False-Negative Costs

### False Positive

A student is flagged for additional support but does not meet the defined support criterion.

**Potential cost:** Unnecessary follow-up, wasted staff time, or a student feeling incorrectly labeled.

**Mitigation:** Use supportive, non-stigmatizing communication and allow educators to review the recommendation before taking action.

### False Negative

A student who needs additional support is not flagged.

**Potential cost:** The student may miss an opportunity for timely assistance.

**Mitigation:** Maintain existing support channels, teacher referrals, and self-referral options. The model must never be the only way to access assistance.

### Error-Cost Principle

Missing a student who needs help may be more harmful than conducting an unnecessary supportive check-in. However, the appropriate trade-off must be agreed upon with educators and students' representatives where appropriate. It should not be assumed without evidence.

## 7. Data Leakage Prevention

Data leakage occurs when information unavailable at prediction time influences model training or evaluation.

Potential leakage risks include:

- Using future assessment scores as input features.
- Including records created after the prediction date.
- Using the future support outcome to construct an input feature.
- Allowing repeated records from the same student to create an unrealistically easy evaluation.
- Applying preprocessing or feature selection using the full dataset before splitting it.

To reduce these risks:

1. Define the prediction timestamp and outcome window before preparing the dataset.
2. Exclude future information from input features.
3. Fit preprocessing steps using training data only.
4. Prefer chronological evaluation when the intended use is predicting future outcomes.
5. Group records by student where needed to prevent inappropriate overlap.
6. Document any remaining limitations.

## 8. Responsible AI and Potential Harms

### Privacy

Student records can contain sensitive personal information. Only necessary and authorized data should be used. Identifiable student records must not be uploaded to a public repository.

### Bias and Fairness

Attendance and assessment patterns may reflect differences in access to resources, disability-related needs, personal circumstances, or other factors unrelated to a student's potential.

The project will assess whether the system produces systematically different errors across relevant groups where lawful, ethical, and supported by adequate data.

### Transparency

Educators must understand the intended purpose, important limitations, and basis of the recommendation to the extent possible. Uncertain predictions must not be presented as facts.

### Human Oversight

A qualified educator must review recommendations before any student-specific intervention is made. Students must retain access to ordinary academic support regardless of the model's output.

### Misuse Prevention

The system must not be used for automated punishment, exclusion, admissions decisions, or permanent student labeling. Such uses are outside the project's intended purpose.

## 9. Abstention and Human Review

The system must be able to decline to provide a recommendation when its output is unreliable.

Abstention or escalation to human review should occur when:

- Required input data are missing or invalid.
- The student record differs substantially from the data used during evaluation.
- The model's uncertainty exceeds a threshold established during validation.
- The system detects a data-quality problem or an unexpected input pattern.
- The model has not been adequately validated for the relevant population.

When the system abstains, the educator should use the existing manual review process. Abstention must not prevent a student from receiving support.

## 10. Monitoring and Rollback Conditions

Before any deployment, the project will define monitoring procedures for:

- Changes in input-data distributions and missingness.
- Precision, recall, and false-positive and false-negative rates when reliable outcome labels become available.
- Differences in performance across relevant groups.
- Human-review decisions and disagreement with model recommendations.
- Changes in educational processes that may affect the target outcome.
- Access control, privacy incidents, and data-quality failures.

The system must be suspended or rolled back to the rule-based or manual process if performance falls below predefined acceptance criteria, serious fairness concerns arise, data integrity cannot be established, or a significant privacy or safety incident occurs.

Deployment must not proceed until the responsible institution has approved the monitoring and incident-response process.

## 11. Implementation Plan

The project will follow these stages:

1. Define the decision, prediction target, observation unit, and action window.
2. Document data provenance, consent or other applicable authorization, sensitive attributes, missingness, and leakage risks.
3. Establish a transparent non-ML baseline.
4. Create a baseline notebook using appropriate synthetic or authorized data.
5. Define model metrics, practical success criteria, and error-cost trade-offs.
6. Create a risk register covering privacy, fairness, false predictions, and misuse.
7. Decide whether ML provides sufficient benefit to justify further development.
8. If justified, evaluate a model against the baseline before considering deployment.

## 12. Expected Deliverables

- `problem_framing.md` - Decision definition, prediction target, baseline, and evaluation plan.
- `data_card.md` - Data provenance, authorization, sensitive attributes, missingness, and leakage risks.
- `baseline.ipynb` - Reproducible baseline implementation and evaluation.
- `risk_register.md` - Potential harms, mitigations, human review, monitoring, and rollback conditions.

## 13. Current Conclusion

Machine learning may help educators identify students who could benefit from additional academic support, but its usefulness has not yet been demonstrated.

The first priority is to define a reliable outcome, establish a transparent baseline, and assess whether suitable data can be used responsibly. An ML model should only be developed if it demonstrates meaningful benefits over the baseline and satisfies the project's safety, fairness, privacy, and oversight requirements.

**Project status:** Problem framing documented. Data collection, baseline implementation, and empirical evaluation remain to be completed.

## References

1. Google for Developers, *Understand the Problem*: https://developers.google.com/machine-learning/problem-framing/problem
2. Google for Developers, *Framing an ML Problem*: https://developers.google.com/machine-learning/problem-framing/ml-framing
3. Google for Developers, *Responsible AI*: https://developers.google.com/machine-learning/glossary/responsible-ai
