# Predicting Day-14 Player Retention Using Machine Learning 

## 🔎 Overview

This project builds **machine learning models** to predict **whether a mobile game player will return 14 days after installation** using early gameplay behavior signals.

The goal is to help game teams detect high-risk churn early, personalize player experiences, and design targeted retention strategies that improve long-term engagement and revenue.

The final model was also applied to a future validation dataset to test generalizability and simulate real-world deployment.

## 🔐 Business Problem

Player retention is one of the most critical metrics in free-to-play and live-service games.

Most players drop off within the first few days after installing a game, making it essential for game developers to identify at-risk players early and intervene before they churn.

Predicting Day-14 retention helps game teams:
- Identify players likely to become long-term users
- Detect high-value players early in their lifecycle
- Personalize onboarding and engagement strategies
- Optimize marketing acquisition channels
- Improve player progression and game design

A predictive retention model enables teams to prioritize resources toward players most likely to churn while reinforcing engagement among high-value users.

## 📊 Dataset

The dataset contains 42K+ player records capturing gameplay behavior and contextual attributes from a mobile game.

### Target variable
- **retention_14** — whether a player returns to the game 14 days after installation.
- This is a key metric in mobile games and a strong indicator of long-term engagement and player lifetime value. 

### Key feature categories
- Player and acquisition details
- Total sessions played
- Total playtime
- Activity across gameplay modes (Campaign Missions, PvP Matches, Side Missions)
- Time-based player behaviors (D0, 1, 3, 7, 14)

## 📍 Methodology

The modeling pipeline followed several stages.

### 1. Data Preprocessing
- Cleaned and validated gameplay records
- Handled categorical variables using encoding techniques
- Scaled numerical features when appropriate
- Combined categorical and numerical features into a unified ML pipeline

### 2. Feature Engineering

Additional behavioral features were derived to capture player engagement patterns:
- Total sessions across days 0–7
- Active days in the first week
- Session intensity
- Early spending signals
- Player progression pace through game chapters

These features capture engagement depth, consistency, and early commitment to the game.

### 3. Model Training

Three machine learning models were trained:
- Logistic Regression (baseline model)
- Random Forest
- XGBoost

The dataset was split into training and test sets, and models were evaluated using the F1 score, which balances precision and recall for imbalanced classification problems.

### 4. Model Evaluation

- Logistic Regression: F1 Score = 0.548
- Random Forest: F1 Score =	0.571
- **XGBoost: F1 Score = 0.619**

XGBoost achieved the best performance and was selected as the final model.

### 5. Feature Importance Analysis

Feature importance from the XGBoost model was analyzed to identify key behavioral signals driving retention predictions.

<img width="790" height="590" alt="image" src="https://github.com/user-attachments/assets/025c78fc-20bb-4d9b-bb0e-fff4593e69d2" />

### 6. Future Data Prediction

The final model was applied to a new unseen dataset to simulate predicting retention for future players, ensuring the model generalizes beyond the training data.

Here is the [prediction result](https://github.com/plvu99/Predicting-Day-14-Player-Retention-Using-Machine-Learning/blob/main/day14_player_retention_predictions.csv).

## 🔑 Key Insights

- Players who remain active and continue progressing by Day 7 are significantly more likely to stay in the game long-term.
- Players predicted to retain showed ~7× more sessions and ~10× more playtime during the first week compared to players predicted to churn.
- Players who advance through game chapters early are more likely to remain engaged.
- Frequent gameplay sessions across multiple days (consistency) predict retention more strongly than short bursts of activity (intensity).
- Retention likelihood differs across ad networks, countries, and device types, suggesting that some acquisition channels deliver higher-quality players.

## ✍️ Business Recommendations

### 1. Optimize the Day-7 experience

Since Day-7 activity is the strongest retention signal, game teams should:
- Introduce Day-7 milestone rewards
- Launch special weekly events
- Unlock new gameplay features during the first week

These mechanisms encourage players to remain engaged through the critical early lifecycle stage.

### 2. Reduce early onboarding friction

Many churned players disengage during the first few sessions.

Potential improvements include:
- Simplifying early missions
- Reducing tutorial complexity
- Improving early game rewards
- Providing clearer progression goals

A smoother early experience can improve first-week retention.

### 3. Implement early churn detection

The model can be deployed to identify high-risk players within their first few days.

Possible interventions:
- Personalized rewards
- Push notifications encouraging return sessions
- Time-limited events
- Re-engagement incentives

### 4. Optimize user acquisition channels

Since retention varies by acquisition source:
- Increase marketing spend on channels that bring high-retention players
- Reduce investment in low-quality acquisition sources
- Tailor onboarding experiences based on player demographics

## ⚙ Tools & Technologies
- Python (Pandas, NumPy, Scikit-learn, XGBoost)
- Modeling (Logistic Regression, Random Forest, Gradient Boosting (XGBoost))
- Jupyter Notebook/Google Colab
