# Assignment 5: Health Data Classification Results

This file contains your manual interpretations and analysis of the model results from the different parts of the assignment.

## Part 1: Logistic Regression on Imbalanced Data

### Interpretation of Results

In this section, provide your interpretation of the Logistic Regression model's performance on the imbalanced dataset. Consider:

- Which metric performed best and why?
- Which metric performed worst and why?
- How much did the class imbalance affect the results?
- What does the confusion matrix tell you about the model's predictions?

The highest metric was accuracy, and the lowest metric was recall. In this case, recall is the ability of the model to correctly identify smokers and former smokers from the features in the test dataset. Since the training data was resampled, I believe that this affected results since there is much less variance in the features of smokers and former smokers compared to nonsmokers, leading to the model being much better at identifying nonsmokers. The confusion matrix shows an extremely high number of correctly predicted nonsmokers, and relatively high numbers of false positives and false negatives compared to true negatives.

## Part 2: Tree-Based Models with Time Series Features

### Comparison of Random Forest and XGBoost

In this section, compare the performance of the Random Forest and XGBoost models:

- Which model performed better according to AUC score?
- Why might one model outperform the other on this dataset?
- How did the addition of time-series features (rolling mean and standard deviation) affect model performance?

The two models performed about the same based on AUC score. However, it's possible for one model to outperform the other in different situations because Random Forest is a bagging method whereas XGBoost is a boosting method. In the case of imbalanced data, XGBoost should theoretically perform better on average because boosting allows each iterative model to weight mistakes and learn from it in future iterations. The time-series features can also improve the model by reducing the noise in the features and allowing the model to be trained more based on a trend than the individual noisy data points.

## Part 3: Logistic Regression with Balanced Data

### Improvement Analysis

In this section, analyze the improvements gained by addressing class imbalance:

- Which metrics showed the most significant improvement?
- Which metrics showed the least improvement?
- Why might some metrics improve more than others?
- What does this tell you about the importance of addressing class imbalance?

Recall showed the greatest improvement while all other metrics actually decreased (AUC stayed about the same with a decrease of about 2.17%). The improvement of recall makes sense in the context of addressing class imbalance; in part 1, the class imbalance caused the model to have a very hard time correctly predicting smokers because of the low frequency of smokers in the data. By resampling, the weight of the features for smokers was effectively increased in the training, allowing the model to become more sensitive. However, the other metrics decreased because sensitivity and specificity is a tradeoff; taking measures to increase one metric will decrease the other. Addressing class imbalance can be very important to making a model with higher sensitivity of a low frequency category, especially in contexts such as this data, where the advantages of correctly identifying smokers i.e. people at risk of adverse health effects due to smoking far outweigh the disadvantage of incorrectly labeling nonsmokers as smokers.

## Overall Conclusions

Summarize your key findings from all three parts of the assignment:

- What were the most important factors affecting model performance?
- Which techniques provided the most significant improvements?
- What would you recommend for future modeling of this dataset?

The most important factors affecting model performance were the relative frequencies of outcome categories and the noisiness and density of features. In this assignment, addressing class imbalance was more important for model improvement than the reduction of noise in the features. Future modeling of the dataset could be improved if including a higher number of smoker data  was prioritized, thought I would also be wary of this leading to the usage of data that is unrepresentative of the general population of interest.