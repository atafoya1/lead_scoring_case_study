# lead_scoring_case_study
# Lead Scoring Optimization: Enrollment Conversion Predictor

This repository contains a Python based logistic regression model built to streamline a student enrollment funnel by predicting exactly which prospective leads are most likely to convert. After cleaning historical inquiry data and isolating the top behavioral signals, such as direct SMS engagement and active CRM tags, the model successfully generated a reliable 0-100 Lead Score for every prospect, while also **identifying that a student's refusal to answer basic form questions was the strongest indicator of a dead lead.**

Simulating different score thresholds revealed an efficient strategy for optimizing the admissions pipeline. By setting the cutoff score at 40, the model eliminates nearly 64% of the low intent inquiries from the daily call queue. For the remaining 36% of leads that the team actually contacts, the resulting conversion rate jumps to 90.2%, surpassing the 80% target yield and allowing the team to shift away from volume dialing to focus exclusively on high value prospects.

Technical Stack

* Language: Python

* Environment: Jupyter Notebook / Anaconda Prompt

* Libraries: Pandas, NumPy, Scikit-Learn (LogisticRegression, RFE, StandardScaler, train_test_split), Matplotlib, Seaborn

# Methodology

Data Preprocessing & Cleaning:

* Handled a 9,240-row dataset with 37 initial CRM features.

* Exposed hidden "Select" form defaults as true NaN values.

* Dropped columns with >45% missing data and negligible row level nulls (<1.5% missing).

* Imputed middle tier categorical blanks (15-30% missing) with a "Not Provided" behavioral flag.

Exploratory Data Analysis:

* Visualized the baseline conversion rate of 38.5%.

* Mapped website engagement duration against conversion success rates using Seaborn boxplots.

* Evaluated lead origin quality to compare highly qualified channels against low yielding 3rd party sources.

Feature Selection:

* Applied One-Hot Encoding (pd.get_dummies()) to categorical variables, expanding the dataset to 164 total machine readable features.

* Split data into a 70/30 training and testing holdout set.

* Scaled continuous web metric variables using StandardScaler.

* Utilized Recursive Feature Elimination to isolate the top 15 most statistically significant predictors.

Model Training & Evaluation:

* Trained a Logistic Regression model on the optimized 15 feature set.

* Extracted formula coefficients to map the exact positive and negative mathematical impact of specific student behaviors.

* Translated predicted conversion probabilities into an actionable 0–100 Lead Score.

Threshold Simulation:

* Iterated through multiple Lead Score cutoffs (40 to 95) to balance total call volume against resulting conversion precision, identifying a 40+ score as the optimal target threshold.

Key Business Insights

* Internal Pipeline Tagging - CRM pipeline statuses such as "Closed by Horizzon", "Will revert after reading", are the most mathematically significant positive predictors of enrollment, showing that real time tagging by enrollment specialists is critical for dynamic automated scoring.

* High Intent Channels - Prospects who engage via active, two way channels such as SMS messaging, direct chat, show much higher conversion probabilities than passive website visitors.

* The "Refusal to Answer" - Submitting an inquiry while actively refusing to state primary educational goals was identified as the single strongest negative predictor of enrollment, outweighing even disconnected phone numbers.

Repository Structure

* lead_scoring_analysis.ipynb: The primary Jupyter Notebook containing the end-to-end Python code, statistical visualizations, and technical commentary.

* Lead_Scoring.csv: The raw X Education dataset used for training and testing.

* Leads_Data_Dictionary.xlsx: Business definitions for the original CRM variables.
