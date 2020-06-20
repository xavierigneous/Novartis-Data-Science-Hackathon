# Novartis-Data-Science-Hackathon
Local F1 Score : 99.947%

Test Score : 99.53%

My approach to this dataset and ways I solved the issues:

1. The dataset had huge class imbalance, so I experimented base classifier with undersampling, oversampling and SMOTE (Synthetic Sampling). The later had the best results.
2. Null values were observed in X_12 column. The distribution was continuous but highly right skewed. To avoid discrepancy in single value_imputation, I opted for KNN Imputation (Unsupervised learning based Imputation). This maintained the randomness of the column and didn't distort the distribution of the column.
3. Feature Importance of columns were determined by statistical tests on the categorical (Chi-Square test) and numerical (T-Test) columns. Subsequent columns that had lower statistical significance were removed. 
4. I choose XGBoost as my final classifier to boost my initial score of 99.43 achieved with Random Forest Classifier.  After hyperparameter tuning, the feature importance plot of the algorithm showed me 4 columns had very less to almost 0 significance to the prediction. So those columns were removed (except 'Day' which reduced the performance), and re-ran the algorithm.
5. An AUC Score of 100% and F1 Score on validation of 99.947% was achieved, thus concluded the modeling.

Conclusions:

1. From statistical tests, the Day of the week has a significant impact in determining the target variable. The 'countplot' doesn't show any trend (especially which on which day most offences occur), but certainly this variable is helpful, as also seen from the dramatic drop in performance upon its removal.
2. Among the Logging parameters, X_10 variable has significant importance in predicting the target variable, followed by X_15 and X_12.
3. X_1, X_9, X_14 didn't have significant contribution in the predictive power of the classifier.
