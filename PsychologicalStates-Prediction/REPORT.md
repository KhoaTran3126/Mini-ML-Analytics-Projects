# Psychological State Identification
## About the Dataset
The data contains simulated physiological, behavioral, and environmental data collected from biosensors to evaluate psychological states of individuals during ideological and political education (IPE) activities. The purpose is to analyze students' psychological states, stress levels, and emotional involvement during educational activities. The data is a mix of numeric and categorical features, and the target **Psychological States** has 4 categories: Relaxed, Focused, Anxious, Stressed. The target distribution is uniform, with an approximate proportion of 0.25 for each category. 

## Metric
Accuracy score is used for assessing the performance of classifiers, judging from the uniformity of classes. 

## Cross-Validation Scheme
A cross-validation scheme using **10 folds** with shuffling and a seed of 3126 was used. 

## Analysis
The analysis focused on using two models for classifying psychological states: LGBMClassifier and CatBoostClassifier. The untuned LGBMClassifier with OneHotEncoder attained a mean accuracy score of **0.25**, and the untuned CatBoostClassifier a score of **0.25**. After tuning, the LGBMClassifier with OneHotEncoder attained a mean accuracy score of **0.263** and the tuned CatBoostClassifier has a score of **0.22**. The reduction is score is likely because a validation scheme of 5-fold was used instead of 10-fold whilst optimizing CatBoostClassifier's hyperparameters to reduce time complexity. Interestingly, the tuned LGBMClassifier has learned to maximize its score by simply classifying all samples with the label of the class with the highest proportion in the data: class 3. Since the proportion of class **3 (Stressed)** has the highest proportion in the data, the tuned LGBMClassifier could maximize its accuracy by simply maximizing the recall for class 3. This, perhaps, reveals a revelation to the data: due to its synthetic nature, relationships between variables are unrealistic, resulting in muddied distinctions between classes; classifiers hardly can discriminate classes with high accuracy when such distinctions have been muddled away. The simplest way to maximize the metric, then, is to provide only the class which occupies the greatest proportion of the data. 
