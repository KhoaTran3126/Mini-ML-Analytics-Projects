# Prediciting Valorant Game outcome
## About the Dataset
The dataset was obtained from Kaggle, containing 1000 entries of a gamer's gameplays and their outcomes (won, loss, or draw). The target is the outcome variable of the game. Due to there being only 12 entries which have 'draw' as the outcome, the 'draw' category was dropped, reducing the problem to a binary classification. Other features such as **round_wins** and **round_losses** were also dropped to prevent data leakage; **game_id** and **date** were dropped from their irrelevance. Additional features involving damange were recombined to create additional features; the **agent** feature was remapped in its values to reduce the feature to contain only the game characters which were used the most by the gamer, other game characters being used too infrequently (less than 10 times) to be significant. 

## Metric 
The balance of binary classes led to the usage of the **acuracy score** for maintaining a balance in predictions. 

## Cross-Validation Scheme
From the small length of the data, a **10-fold** validation scheme with KFold was used with shuffling enabled and a seed value of 3126. 

## Models Used
Three classification models were in consideration: CatBoostClassifier, LGBMClassifier, and SVMClassifier. CatBoostClassifier for its efficient handling of hihg-cardinality categorical features which are present in the data. LGBMClassifier was considered for its quick speed but notable performance. SVM Classifier was used for its ability to form complex nonlinear boundaries for classification, which may prove to be as strong as the partitioning technique employed by tree models. 

The data was also processed specifically for each classifier's training routine.
1. The data was used unchanged for CatBoostClassifier
2. The data was applied with OneHotEncoder before being used for LGBMClassifier
3. The data was filtered only for numerical features to use for SVMClassifier
## Analysis
After tuning, CatBoostClassifier displayed the highest mean Out-Of-Fold (OOF) accuracy with a score of 0.855; tuned LGBMClassifier and SVMClassifier performaned similarly with a score of 0.822. The optimal probability threshold for all classifiers - after tracking the mean accuracy scores across 10 folds per probability threshold - was found to be 0.5. Amongst all tuned models, recall scores between classes are relatively balanced, displaying a balanced discrimination power amongst each model in separating the classes and retrieving them correctly. However, even after tuning, performances did not significantly increase, aside CatBoostClassifier; it is possible that insufficient transformations were applied to the data for making it sufficiently informative, but the next improvement could be in blending model predictions by using tuned weights obtained from Ridge or Lasso regression. 
