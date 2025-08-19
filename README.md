# Marvel Character Alignment Predictor

## Project Goal
This project explores whether a Marvel character’s physical stats can help predict if they’re **good** or **bad**. It walks through the complete data science workflow — from cleaning and preprocessing data all the way to training and evaluating a machine learning model.

## Dataset
The dataset comes from Kaggle’s *Marvel Characters Info*. It includes character details like height, weight, publisher, and alignment.

## Process Workflow
1. **Data Loading & Initial Cleaning**  
   * Loaded the raw CSV with Pandas.  
   * Converted custom missing values (`-` and `-99`) into `NaN` using the `na_values` parameter.  

2. **Data Preprocessing**  
   * Filtered the dataset to only include characters from *Marvel Comics*.  
   * Filled missing `Height` and `Weight` values with the median.  
   * Cleaned the target variable (`Alignment`) by removing rows with missing values and dropping the *neutral* class to make it a binary problem.  
   * Converted `Alignment` into numeric values: `good = 1`, `bad = 0`.  

3. **Model Training & Evaluation**  
   * Split the data into 80% training and 20% testing sets.  
   * Trained a Logistic Regression model.  
   * Evaluated performance on the test set.  

## Key Challenges & Learnings
* **`SettingWithCopyWarning`**: Solved this by using `.copy()` after filtering, avoiding unstable modifications.  
* **Data Type Issues**: Learned to make sure numeric data is truly numeric before running operations like `median()`.  
* **Target Variable Cleaning**: Discovered the model can’t train if `y` has `NaN` values — another reminder of why thorough cleaning matters.  

## Results
The baseline Logistic Regression model scored **62.67% accuracy** on the test set. That suggests physical stats *do* provide some predictive power for character alignment.  

## Future Improvements
* Add more features (e.g., gender, race) with one-hot encoding.  
* Try more powerful models like Random Forests to push accuracy further.  
