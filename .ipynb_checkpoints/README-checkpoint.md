## Data Science Job Postings with Salaries (2025)

1. Project Objective:
To determine the relationship between Data Scientist and Machine Learning Engineer salaries, based on features in job postings.

Quick overview of results: 
  - Random Forest was the most successful model, with accuracy = 0.78 and AUC-ROC = 0.87.
  - The top predictor was the location of headquarters of the company offering the job (USA).

2. Data Collection and Cleaning
Objective: Obtain, clean, and understand the dataset to prepare it for analysis and modeling.

  - 2.1 Dataset Information
    - Dataset Name: Data Science Job Postings with Salaries (2025)
    - Source: [Dataset Link]( https://www.kaggle.com/datasets/elahehgolrokh/data-science-job-postings-with-salaries-2025)
    - Shape of Data: 944 x 13

  - 2.2 Data Cleaning
    - We droped the null values in 'job_title' and 'revenue' and changed null values in 'seniority_level', 'status' and 'ownership to 'unknown'.
    - The 'location' column can be dropped, as it contains the info already in 'status' and repeats the country info in 'headquarter', which we will rename 'headquarters'.
    - The 'skills' column is problematic: Some cells contain many items, some are empty lists. We will replace the column's values with the number of items in the lists.
    - The 'salary' column is also problematic: It needs to be converted to numerical data, and if there is a range given we will use the mean of the range.
    - The 'revenue' column contains some numerical data, but many cells which contain info like 'private' and 'education'. We will drop this column. Also, we will make sure company_size contains only numerical values.
    - In company_size, we filled in any NaN values with the median of the column.
    - Finally, we removed 'post_date', since these are all from 2025 anyway.
    - Target Variable: Salary > $100K = 1, otherwise 0.

  - 2.3 Feature Classification
    - The categorical columns are: job_title, seniority_level, status, company, post_date, headquarters, industry, ownership
    - The numerical columns are: company_size and skills
    - The target column is: salary

  - 2.4 Descriptive Statistics:
    - Summary statistics for continuous features: **********************************


3. Exploratory Data Analysis (EDA)

  - 3.1 Key Observations from EDA
    - Only Data Scientist and Machine Learning Engineer have enough rows for analysis
  - Strong associations:
    - There were no strong correlations among the features.

  - 3.2 Correlation Analysis:
    - Heatmaps showed no significant correlations among features

4. Model Development
Objective: Build and evaluate logistic regression and alternative models for predicting Risk Level.

  - 4.1 Feature Engineering
    - Encoded categorical variables using one-hot encoding.
    - Normalized continuous variables for consistent scaling.

  - 4.2 Model Selection
    - Logistic Regression
    - Random Forest Classifier.
    - XGBoost

  - 4.3 Model Performance Metrics: ******************************************


5. Steps to Reproduce:
  - Run the code in the "Notebooks" folder in Jupyter Notebooks or other Python IDE. 

6. Model Interpretability
  - Top feature contributing to predictions: Location of the company's headquarters (USA).

7. Hypothesis Testing
 - We cannot conclude that there is a difference in mean salaries offered under the two job descriptions, Data Scientist and ML Engineer.
 - Also, there is no significant difference in the distributions of the salaries between the two job titles.
 - However, there is one feature of the plots that is startling: the much higher median for the Data Scientist jobs.
 - We dropped the lowest 10% of salaries from our already-small MLE sample and ran the Mann Whitney test again. Now it shows all 3 quartiles as nearly identical.

8. Conclusions:
 - The means of the salaries posted for Data Scientist and Machine Learning Engineer are nearly identical.
 - The medians of the salaries, in our dataset, were widely disparate.
 - By doing a little more data cleaning, removing the bottom 10% of MLE salaries, we were able to show that the medians and other quartiles are nearly idntical.
 - This is justified, since some of the salaries for the MLE column were absurdly low, as low as $55!



All code for this project is available in the: [Notebook Folder](https://github.com/markcoty/data-science-jobs-2025/tree/main/Notebook)