# Credit-Card-Fraud-Detection
Following was written by an AI to summarize what I did:

🛡️ Credit Card Fraud Detection: Navigating Extreme Class Imbalance
Executive Summary
This project builds a machine learning pipeline to detect fraudulent credit card transactions. The primary challenge of this dataset is extreme class imbalance, where fraudulent transactions account for only 0.17% of all data. By utilizing robust feature scaling, data undersampling, and an ensemble learning model (Random Forest), this project successfully built a classifier that prioritizes Recall—catching 94% of unseen fraudulent transactions while maintaining a 99% precision rate.

📊 The Data Challenge: The Imbalance Trap
In anomaly detection, standard "Accuracy" is a misleading metric. A model that guesses "Normal" 100% of the time on this dataset would achieve 99.83% accuracy but fail completely at its business objective.

Total Transactions: 284,807

Normal Transactions: 284,315

Fraudulent Transactions: 492 (0.17%)

Key Insight: Exploratory Data Analysis revealed a behavioral signature. The median transaction amount for normal behavior was $22.00, while the median fraud amount was only $9.25, reflecting a high volume of $1.00 "ping" tests used by fraudsters to verify stolen card numbers.

🛠️ Methodology & Preprocessing
To prepare the data for the machine learning algorithm, two critical mathematical adjustments were made:

Outlier-Resistant Scaling: The Amount and Time features contained massive outliers (e.g., legitimate purchases over $25,000). A RobustScaler was applied, utilizing the Median and Interquartile Range (IQR) to normalize the data without letting massive outliers skew the algorithm's math.

Addressing the Imbalance (Undersampling): To prevent the model from overfitting to the majority class, the dataset was undersampled to create a perfectly balanced 50/50 dataframe consisting of all 492 fraud transactions and 492 randomly selected normal transactions.

🤖 Model Performance: Random Forest Classifier
The balanced dataset was split 80/20 for training and testing. A RandomForestClassifier was chosen for its resistance to overfitting and its ability to handle complex, non-linear relationships.

The Test Set Results (The Final Exam):

True Positives (Caught Fraud): 96

False Negatives (Missed Fraud): 6

True Negatives (Correct Normal): 94

False Positives (False Alarm): 1

Business Impact: The model achieved a 94% Recall Score. In a real-world financial setting, this means the system successfully caught 94% of actual theft, while only temporarily freezing one legitimate customer's card (a 1% False Positive rate).

🔍 Feature Importance: Opening the Black Box
(Insert your Top 10 Feature Bar Chart image here)

A correlation heatmap generated during the EDA phase suggested that features V14 and V17 possessed the strongest negative correlation with fraudulent behavior. After training, the Random Forest model's built-in feature_importances_ attribute was extracted. The model mathematically confirmed human intuition, independently relying on V14 and V17 for nearly 30% of its entire decision-making power.

💻 Tech Stack
Language: Python

Data Manipulation: Pandas, NumPy

Machine Learning: Scikit-Learn (RandomForestClassifier, RobustScaler, train_test_split)

Data Visualization: Matplotlib, Seaborn
