# Results

## Objective

The goal of this project was to tune a classifier and achieve at least a 5 percentage-point improvement in ROC-AUC over a proper baseline.

## Dataset

The project uses the Breast Cancer Wisconsin Diagnostic dataset available through scikit-learn.

- **Samples:** 569
- **Features:** 30
- **Task:** Binary classification
- **Metric:** ROC-AUC

The data was divided into training and test sets using a stratified 80/20 split.

## Baseline

A `DummyClassifier` using the `prior` strategy was used as the baseline.

The baseline achieved:

- **Mean 5-fold CV ROC-AUC:** 0.5000
- **Test ROC-AUC:** 0.5000

## Candidate Models

Three candidate models were compared using 5-fold cross-validation.

| Model               | Mean CV ROC-AUC | Std CV ROC-AUC |
| ------------------- | --------------: | -------------: |
| Logistic Regression |        0.995872 |       0.004960 |
| SVM                 |        0.995562 |       0.004758 |
| Random Forest       |        0.990351 |       0.007194 |

Logistic Regression achieved the highest mean cross-validation ROC-AUC and was selected for hyperparameter tuning.

## Hyperparameter Tuning

Logistic Regression was tuned using `GridSearchCV` with 5-fold stratified cross-validation.

### Best Parameters

```text
C = 1
solver = liblinear
```

**Best cross-validation ROC-AUC:** 0.995975

## Final Result

The tuned Logistic Regression model achieved:

**Test ROC-AUC:** 0.995701

**Improvement over the baseline:** 49.57 percentage points

The required improvement was 5 percentage points, so the target was exceeded.

## Evaluation Method

All hyperparameter tuning was performed using cross-validation on the training set.

The test set was not used during model selection or hyperparameter tuning. It was used only for the final evaluation of the selected tuned model.

## Conclusion

The tuned Logistic Regression model substantially outperformed the DummyClassifier baseline. Its test ROC-AUC increased from 0.5000 to 0.9957, representing an improvement of 49.57 percentage points.

This demonstrates the importance of establishing a baseline, comparing multiple candidate models, and performing hyperparameter tuning within cross-validation rather than evaluating models based only on a single test result.
