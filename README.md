In the table shown below: *SVM used 3-fold CV, whereas KNN, LR, and DT used 5-fold CV, so its CV F1-score should be interpreted with that methodological difference in mind.

| Model | Best Hyperparameters | CV F1 | Test Accuracy | Class-1 Precision | Class-1 Recall | Class-1 F1 |
|---|---|---:|---:|---:|---:|---:|
| KNN | `n_neighbors=3, weights='distance'` | 0.1449 | 0.86 | 0.23 | 0.09 | 0.13 |
| Logistic Regression | `C=0.1, class_weight='balanced'` | 0.2558 | 0.58 | 0.16 | 0.62 | 0.25 |
| Decision Tree | `max_depth=10, min_samples_split=5, class_weight='balanced'` | 0.2563 | 0.65 | 0.17 | 0.54 | 0.26 |
| **SVM** | `C=10, kernel='rbf', class_weight='balanced'` | **0.2606*** | 0.63 | 0.17 | 0.59 | **0.26** |

INTERPRETATION:  

The tuning results show that class imbalance is the "central challenge". 
KNN achieved the highest accuracy (0.86) and precision (0.23), but its class-1 recall was only 0.09, meaning it detected only about 9% of actual positive cases. 
Therefore, its high accuracy is largely driven by the majority class and is misleading for this task.
LR produced the highest class-1 recall (0.62), making it the strongest model when minimizing missed positive cases is the main objective. 
However, its low precision (0.16) and accuracy (0.58) indicate many false-positive predictions.
DT achieved the best overall balance, with the highest accuracy (0.65) among the three models that effectively addressed class imbalance and a class-1 F1-score of 0.26. 
SVM matched this F1-score and achieved better recall (0.59 versus 0.54), but had slightly lower accuracy (0.63) and was substantially more computationally expensive.

CONCLUSION : After hyperparameter tuning, DT and SVM achieved the highest minority-class F1-score of 0.26. 
DT provided the best overall balance, achieving 0.65 accuracy and 0.54 recall, 
while SVM achieved higher recall of 0.59 but slightly lower accuracy of 0.63 and substantially greater computational cost. 
LR achieved the highest recall of 0.62, making it preferable when detecting the maximum number of positive cases is the primary objective. 
Although KNN achieved the highest overall accuracy of 0.86, its very low minority-class recall of 0.09 and F1-score of 0.13 indicate poor performance on the imbalanced classification task.
Overall, Dt is the most balanced model among those evaluated.
Because DT and SVM tie at 0.26 only after rounding to two decimals, we cannot confidently say they have exactly equal test F1-scores. 
If we want the most rigorous final selection, we need to print the metrics to four decimal places before concluding the best option.
