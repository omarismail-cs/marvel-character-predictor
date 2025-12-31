# Marvel Character Alignment Predictor

This project demonstrates the power of **feature engineering** in machine learning. It starts by building a baseline model to predict if a Marvel character is 'good' or 'bad' using only their physical stats. It then enriches the dataset with biographical information scraped from Wikipedia to create a significantly more accurate final model.

## The Impact of Feature Engineering: A Tale of Two Models

The success of this project is best shown by comparing the baseline model to the final, enriched model:

#### 1. Baseline Model
-   **Features Used:** `Height`, `Weight`
-   **Accuracy:** **62.67%**

#### 2. Enriched Model
-   **Features Used:** `Height`, `Weight`, plus `Hero_Score` and `Villain_Score` (engineered from Wikipedia biographies)
-   **Accuracy:** **77.33%**

> **Key Result:** By engineering text-based features, model accuracy saw a **23% relative improvement**, proving that a character's narrative context is a far more powerful predictor than their physical stats.

## Process Workflow
The project followed these key steps:

1.  **Data Loading & Initial Cleaning**
    *   Loaded the raw CSV from Kaggle with Pandas.
    *   Handled custom missing values (`-`, `-99`) during import using `na_values`.

2.  **Data Preprocessing**
    *   Filtered the dataset to only include characters from *Marvel Comics*.
    *   Imputed missing `Height` and `Weight` values using the median.
    *   Cleaned the `Alignment` column by removing `neutral` values and converting `good`/`bad` to `1`/`0`.

3.  **Baseline Model Training & Evaluation**
    *   Trained a Logistic Regression model using only the `Height` and `Weight` features.
    *   Established the baseline performance at **62.67% accuracy**.

4.  **Feature Engineering with Wikipedia**
    *   Scraped the first two sentences of each character's biography using the Wikipedia API.
    *   Engineered two new features: `Hero_Score` and `Villain_Score`, by counting the occurrences of predefined hero/villain keywords in the text.

5.  **Final Model Training & Evaluation**
    *   Trained a new Logistic Regression model using the original physical stats **plus** the new text-based scores.
    *   Achieved a final, improved accuracy of **77.33%**.

## Key Challenges & Learnings
*   **`SettingWithCopyWarning`**: Learned the importance of using `.copy()` after filtering a DataFrame to ensure stable modifications.
*   **Web Scraping Robustness**: Implemented `try-except` blocks to handle cases where a character's Wikipedia page could not be found, preventing the scraping process from crashing.
*   **Data Integrity**: Reinforced the need for thorough data cleaning, as the model cannot train if the target variable (`y`) contains `NaN` values.

## Future Improvements
With a strong feature-engineered model now in place, next steps could include:
*   **Advanced NLP:** Move beyond keyword counting to use TF-IDF or word embeddings to capture more nuanced information from the biographies.
*   **More Features:** Properly encode and add other categorical features from the original dataset (e.g., `Gender`, `Race`).
*   **More Powerful Models:** Experiment with algorithms like Random Forests or Gradient Boosting to see if they can further improve accuracy.
