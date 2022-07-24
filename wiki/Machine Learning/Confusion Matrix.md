|               | Actual Yes          | Actual No           |
| -             | -                   |                     |
| Predicted Yes | True Positive (TP)  | False Positive (FP) |
| Predicted No  | False Negative (FN) | True Negative (TN)  |

- Recall - AKA sensitivity, true positive rate, completeness.  Pecent of positives predicted correctly.  Good choice of metric where false negatives are important e.g. fraud detection (missing a case of fraud is worse than accidently marking a legitimate transaction as fraud)
    - Formula: TP/(TP+FN)
- Precision - AKA correct positives.  Percent of relevant results. Good choice when false positives are more important e.g. drug testing
    - Formula: TP/(TP+FP)
- Specificity - AKA true negative rate
    - Formula: TN/(TN+FP)
- F1 Score - harmonic mean of precision and recall
    - Formula: (2 TP) / (2 TP + FP + FN) = ( 2 * precision * recall ) / ( precision * recall )
- Accuracy - fraction of correct predictions.  Can be very misleading especially in inbalanced classification problems
    - Formula: (TP + TN) / (TP + TN + FP + FN)
# ROC Curve
- ROC Curve - Receiver operating characteristic curve.
		Plot of recall (true positive rate) vs false positive rate at various thresholds
		Diagonal line represents random guessing
		AUC is a good metric of classifier's ability - equal to probability that a classifier will rank a randomly chosen positive instance higher than a randomly chosen negative one
