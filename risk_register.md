# Risk Register: Student Academic Support Risk Prediction

## Project Purpose

This project explores whether a simple prediction system could help educators identify students who may benefit from additional academic support. The system is intended only to support human decisions, not replace them.

| Risk | Potential impact | Mitigation |
|---|---|---|
| False negative | A student who needs support is not identified | Monitor recall and provide a way for educators or students to request support independently |
| False positive | A student is flagged unnecessarily | Use supportive, non-punitive follow-up and allow human review |
| Biased predictions | Some student groups may be flagged more often or missed more frequently | Evaluate error rates across relevant groups only when lawful, appropriate data is available |
| Missing or inaccurate data | Predictions may be unreliable | Check data quality and missingness; abstain when required information is insufficient |
| Data leakage | Evaluation results appear better than actual performance | Exclude information unavailable at prediction time and evaluate on unseen data |
| Privacy breach | Student information is exposed | Minimize collection, restrict access, and apply appropriate retention and security controls |
| Over-reliance on predictions | Educators treat predictions as facts | Explain limitations and require human review before action |
| Distribution shift | Performance degrades as student circumstances change | Monitor data quality and performance; review or suspend the system when needed |
| Misuse for punishment | Students may be unfairly penalized | Prohibit punitive use and use predictions only to offer supportive assistance |

## Abstention and Human Review

The system should abstain from producing a recommendation when essential inputs are missing, data quality checks fail, or the case falls outside validated conditions. An educator should review uncertain or high-impact cases. Students must not be denied support solely because of a model output.

## Monitoring and Rollback

- Review false positives and false negatives periodically.
- Check data quality and changes in the student population.
- Investigate disparities before continued deployment.
- Suspend automated recommendations if performance or fairness checks fail.
- Return to a transparent rule-based process or direct human assessment while issues are investigated.

## Current Limitations

This project uses a small synthetic dataset. No real student data was used. The risks and controls described here are proposed safeguards, not evidence that a real system has been validated.

## Conclusion

The baseline is a demonstration, not a deployment-ready model. Any future real-world use would require authorized data, appropriate evaluation, privacy and fairness safeguards, and educator oversight.
