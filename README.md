🚰 Flint Water Line Replacement – Predictive Modeling for Public Health<br>
| A data-driven initiative to identify homes at high risk of lead contamination in Flint, Michigan, using advanced machine learning models.

📘 Overview<br>
In the wake of the Flint Water Crisis, thousands of residents were exposed to dangerous levels of lead due to outdated and corroded service lines. Our goal in this project was to predict which homes are most at risk of lead contamination, using property and infrastructure data, so that resources for pipe replacement could be allocated more efficiently.

🎯 Objective<br>
To build robust predictive models that accurately identify homes likely to have lead-contaminated service lines, thus reducing unnecessary excavation and improving public health outcomes.

🧩 Data Collection & Preprocessing<br>
We worked with a dataset of 20,697 records, provided by the Flint Water Crisis team. It included:<br>
- Property information (year built, land value, zoning, owner type)
- Service line test results (public/private)
- Geographic features (latitude, longitude, wards, zoning)
- Infrastructure data (hydrant types, building style, homestead status)

🔑 Key Preprocessing Steps:<br>
- Missing Value Imputation:
  - Year Built: Imputed using adjacent property IDs and neighborhood average
  - Building Style, Zoning: Filled based on most common neighborhood values
- Feature Engineering:
  - Combined multiple housing condition variables into one Property Condition variable
  - Created a new New_YearBuilt column to improve temporal data quality
- Variable Reduction:
  - Removed irrelevant/redundant fields: e.g., pid, latitude, Draft Zone
  - Dropped columns like sl_public_type, which directly revealed the target

📊 Exploratory Data Analysis (EDA)
- Visual Mapping showed clusters of dangerous homes tied to geographic location and build year
- Key Insight: Homes built before 1950 showed a strong correlation with high lead contamination risk
- Top Features Identified:
  - SL_Type (Service Line Material)
  - New_YearBuilt
  - Zoning
  - Hydrant Type
  - Residential Building Style
  - Land Value, Building Value, Homestead

🤖 Predictive Modeling<br>
We applied and compared multiple supervised learning models to predict the binary target Dangerous (1 = lead risk, 0 = safe):

1. Logistic Regression
- Accuracy: 91.52%
- R²: 0.6648
- Key predictors: SL_Type, New_YearBuilt, Zoning

2. CART (Classification & Regression Trees)
- Accuracy: 92.27%
- R²: 0.662
- Simple and interpretable, used for validation of logistic model

3. Boosted Tree
- Accuracy: 92.56%
- R²: 0.6762
- Powerful ensemble method, improved over CART

4. Bootstrap Forest ✅ (Best Performer)
- Accuracy: 92.41%
- R²: 0.6842
- Highest ROC AUC: 0.9672
- Most robust to overfitting, handles feature interactions well

5. Neural Network
- Accuracy: 92.08%
- R²: 0.7859
- Tuned for balance between complexity and performance

🏁 Final Model Selection <br>
The Bootstrap Forest model was selected based on the highest AUC and generalization performance. It demonstrated superior ability to classify homes at risk of lead contamination with high confidence.

