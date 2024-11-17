# Predictive_Maintenance_Project_Summary
Predictive Maintenance Project Summary
Here’s a comprehensive summary of my results, key findings, and insights from the predictive maintenance project using the AI4I 2020 Predictive Maintenance Dataset from the UC Irvine – Machine Learning Repository.
Project Overview
My goal was to develop a predictive maintenance model capable of accurately predicting equipment failures, allowing for timely interventions to prevent unplanned downtime. Using the ai4i_2020 dataset, which includes features such as sensor readings and operational metrics, I followed a structured approach from data preprocessing to model deployment.
1. Data Preprocessing and Feature Engineering
Data Cleaning: After confirming there were no missing values, I capped outliers at the 99th percentile in critical features like `Rotational Speed [rpm]` and `Torque [Nm]`.
Feature Engineering: I created new features to capture key aspects of equipment behavior:
•	• Temperature Delta: This feature represents the difference between process and air temperature, highlighting potential overheating issues.
•	• Vibration Indicator: A proxy for vibration levels, combining rotational speed and torque, which are often associated with mechanical stress.
•	• Tool Wear Level: I categorized tool wear into 'Low Wear,' 'Medium Wear,' and 'High Wear' to simplify analysis and improve model interpretability.
Insight: These engineered features provided additional context for the model, emphasizing patterns of thermal and mechanical stress, which are critical indicators of failure.
2. Model Selection and Performance Comparison
I tested several models, including Logistic Regression, Random Forest, Gradient Boosting, and LightGBM. The cross-validated F1 scores for each model were as follows:
•	• Logistic Regression: 0.214
•	• Random Forest: 0.734
•	• Gradient Boosting: 0.731
Among these, LightGBM was the best-performing model, with a high recall (82%) and reasonable precision (59%). It outperformed other models in identifying true failures while maintaining a balance with false positives.
Insight: LightGBM was the most suitable model for predicting failures, as it achieved the best recall without excessive false positives. This high recall is crucial in predictive maintenance, as it ensures that potential failures are captured, reducing unplanned downtime.
3. Feature Importance Analysis
Using the Random Forest model, I analyzed feature importance to understand which variables were most influential in predicting equipment failures. The 'Feature Importance in Random Forest Model' chart highlights the top contributing features:
•	• Vibration Indicator: A strong indicator of potential failure due to mechanical stress.
•	• Temperature Delta: Highlights the role of overheating in equipment failure.
•	• Torque: Captures operational force applied, which can increase wear and lead to breakdowns.
Insight: These insights validated that vibration, thermal stress, and torque were the primary drivers of failure. Monitoring these features can help prioritize maintenance and operational checks on at-risk equipment.
4. Precision-Recall Analysis and Confusion Matrix Insights
Precision-Recall Curve: This curve showed the trade-off between precision and recall, confirming that a balanced threshold allows for high recall while managing false positives.
Confusion Matrix: The matrix showed high true positive and true negative rates, with limited false positives and few false negatives.
•	• True Positives (TP): Detected failures, allowing for proactive maintenance.
•	• False Positives (FP): Non-failures predicted as failures, which can trigger preventive checks but don’t lead to downtime.
•	• True Negatives (TN): Correctly identified non-failures, ensuring no unnecessary alerts.
•	• False Negatives (FN): Missed failures, which could lead to unplanned downtime but were minimized by the model.
Insight: By optimizing recall, I minimized missed failures while maintaining reasonable precision. This setup is valuable in a maintenance context where identifying most failures is crucial.
5. Hyperparameter Tuning and Final Model Selection
Hyperparameter Tuning: Using GridSearchCV, I optimized LightGBM’s parameters (num_leaves, max_depth, learning_rate, and n_estimators), enhancing its accuracy and reliability. The final model achieved a strong F1-score, indicating robust performance on the minority (failure) class.
Insight: Hyperparameter tuning helped fine-tune the model’s ability to detect subtle failure patterns, improving both recall and precision for failure predictions.
6. Deployment for Real-Time Monitoring and Alerting
Deployment Setup: Using FastAPI, I created an endpoint that allows the model to make real-time predictions based on incoming sensor data. The model returns alerts if a failure is predicted, enabling preemptive maintenance.
Monitoring and Alerting: The API setup allows for continuous monitoring, where predictions can trigger alerts that maintenance teams can use to address issues proactively.
Insight: The deployment setup provides real-time visibility into equipment health, allowing maintenance teams to act on potential issues before they result in downtime. This setup enhances operational efficiency and minimizes unexpected maintenance costs.
Overall Project Summary and Key Takeaways
•	• Thermal and Mechanical Stress as Key Drivers: Features related to vibration, temperature, and torque are primary predictors of failure, highlighting critical areas for operational monitoring.
•	• Model Selection: LightGBM was the best-performing model, especially after tuning, offering a high recall that ensures most failures are detected.
•	• Precision-Recall Balance: The model’s configuration allows for a balance between high recall and manageable precision, minimizing both missed failures and excessive false alarms.
•	• Real-Time Deployment for Proactive Maintenance: The API deployment enables continuous monitoring, allowing for timely alerts and actions to prevent unexpected downtimes.
This predictive maintenance model demonstrates a comprehensive approach to minimizing equipment failures, combining accurate failure prediction with real-time monitoring to support efficient and proactive maintenance strategies.
