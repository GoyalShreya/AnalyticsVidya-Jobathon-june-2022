Brief Approach
1. First step is to Split the training data into train and val set to evaluate the Model performance, for this I used sklearn.model_selection.train_test_split with stratification on column 'buy' (target column).
2. Keep the Val set aside and work on train set only.
3. describe() method on train set to get the overview of complete data.
4. Check the data statistics and worked on Features and data preprocessing.

================
Feature Engineering
1. Products purchased: This column has maximum NaN values and min value is 1 in the data and so, we can safely replace the missing values with 0, meaning the user hasn't purchased any product yet.
2. Created At: Calculated a new Feature 'Created Days' -> Number of Days the lead has been created (Max date - Created date)
3. Signup Date: Calculated 2 features -
    1. 'Is Signed' -> 1 is there is Signup date i.e., user has signed up else 0.
    2. 'Signed Days' -> Number of days before the user has signed from the last date lead was taken (Max Created Date - Signup date )
4. All Numeric Cols are taken as features:
    1. Products purchased
    2. Created days
    3. Is signed
    4. Signed Days
    5. Campaign Var 1&2
    6. User Activity Var1-Var12

================
Final Model Algo.

1. Tried Random Forest, SVM initially on the data.
2. Used RandomSearchCV and then GridSearchCV to reach better model performance.
3. Used Validation data for evaluating and comparing diff models.
4. Next tried XGBoost which gave a better performance than Random forest and SVM.
5. Tried some More Algorithms like AdaBoost and Neural networks(MLPClassifier)
6. Neural Nets gave the best performance among all.
7. Used Grid Search CV to get the best parameters for NeuralNets.