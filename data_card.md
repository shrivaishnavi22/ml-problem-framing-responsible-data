# Responsible Data Card

## 1. Project Information

**Project Title:** Student Academic Support Risk Prediction

**Purpose:** To evaluate whether data-driven methods can help educators identify students who may benefit from additional academic support.

**Document Type:** Responsible Data Card

**Project Stage:** Data Planning and Responsible AI Assessment

**Current Status:** No real student data has been collected or analyzed.

## 2. Intended Use

The proposed system is intended to support educators in identifying students who may benefit from a supportive academic check-in, tutoring, or additional learning resources.

The system is designed to assist human decision-making rather than replace it.

### Intended Users
- Teachers and academic support staff.
- Authorized educational administrators.
- Researchers evaluating responsible approaches to academic support.

### Out-of-Scope Uses
- Punishing or permanently labeling students.
- Making automated admission, exclusion, or disciplinary decisions.
- Measuring a student's intelligence or personal worth.
- Denying academic assistance based solely on a prediction.
- Using predictions for purposes unrelated to academic support.

## 3. Data Provenance

Data provenance describes where data comes from, how it is collected, and how it is maintained.

No real student records are currently being used in this project. The following table describes the proposed data sources for a future feasibility study.

| Proposed data | Possible source | Purpose |
|---|---|---|
| Attendance percentage | Authorized institutional records | Understand recent attendance patterns |
| Previous assessment scores | Authorized academic records | Understand academic performance |
| Assignment completion rate | Authorized learning records | Identify possible learning difficulties |
| Historical support outcome | Documented academic support records | Define the prediction target |
| Prediction timestamp | Data processing system | Prevent future information from entering predictions |

Before collecting or using any real data, the project must document the source, collection method, data owner, access permissions, update frequency, and applicable retention requirements.

These sources are proposed possibilities, not confirmed datasets.

## 4. Consent, Authorization, and Legal Considerations

Educational records may contain personal and sensitive information.

Before accessing real student data, the project must:

- Obtain the necessary institutional authorization.
- Establish the appropriate lawful basis for data processing.
- Obtain informed consent where required.
- Explain the purpose of data use in understandable language.
- Follow applicable privacy laws, institutional policies, and data protection requirements.
- Restrict access to authorized individuals.
- Define data retention and deletion procedures.

Consent or authorization must not be assumed merely because an institution possesses the records.

For the initial notebook, synthetic data should be used so that real student information is not exposed.

## 5. Sensitive Attributes and Fairness

Potentially sensitive or relevant contextual attributes may include age, disability-related information, socioeconomic circumstances, and other protected or vulnerable characteristics, depending on the population and jurisdiction.

The project will follow these principles:

1. Do not collect sensitive attributes without a clear, justified purpose and appropriate authorization.
2. Do not use sensitive information as a model feature merely because it is available.
3. Consider whether apparently neutral variables, such as attendance, may indirectly reflect personal circumstances.
4. Where lawful, ethical, and supported by sufficient data, assess differences in model performance across relevant groups.
5. Do not interpret differences in observed outcomes as proof of differences in student ability.

Sensitive attributes may sometimes be necessary for fairness auditing, even when they are excluded from model inputs. Any such use requires separate justification and appropriate safeguards.

## 6. Data Quality and Missingness

Missing data can occur for many reasons, including incomplete records, administrative errors, differences in reporting practices, or information that was never collected.

### Potential Data Quality Issues

- Missing attendance records.
- Incomplete assessment scores.
- Duplicate student records.
- Inconsistent date formats.
- Different grading scales across courses.
- Incorrect or outdated records.
- Inconsistent definitions of academic support needs.

### Proposed Mitigation

- Measure missingness for every feature.
- Investigate why data are missing before selecting an imputation method.
- Validate ranges, types, and date consistency.
- Remove or resolve duplicate records using documented rules.
- Avoid assuming that a missing value represents poor performance.
- Document every preprocessing decision.
- Fit imputation and other preprocessing steps using training data only.

The project must report any limitations that remain after data cleaning.

## 7. Data Leakage Risks

Data leakage occurs when information unavailable at prediction time influences the model or its evaluation.

| Leakage risk | Example | Mitigation |
|---|---|---|
| Future information | Using next month's assessment result to predict current support needs | Restrict features to information available before prediction |
| Target leakage | Using a field created after an educator has already identified a student for support | Review feature definitions and timestamps |
| Train-test contamination | Fitting an imputer using the entire dataset before splitting | Split data before fitting preprocessing |
| Student overlap | Repeated records for the same student appear in training and test data | Use suitable group-based splitting or chronological evaluation |
| Outcome-window confusion | Features include information recorded during the prediction period | Define a clear prediction timestamp and outcome window |

A documented data audit must be completed before model training.

## 8. Data Minimization and Security

Only data required for the defined purpose should be collected.

The project proposes the following safeguards:

- Use synthetic data during initial development.
- Avoid storing names, email addresses, student IDs, or other direct identifiers in the baseline dataset.
- Use pseudonymous identifiers only when necessary and appropriately protected.
- Store any necessary identification mapping separately with restricted access.
- Avoid uploading confidential records to a public GitHub repository.
- Use appropriate access controls and secure storage for authorized data.
- Define retention and deletion procedures.
- Do not include private records or credentials in notebooks, logs, or screenshots
