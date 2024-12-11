# **Conclusion**


### 1. **Introduction**
As part of this project, we aimed to build a tool that enables the University of Illinois to determine which courses require more recruitment or funding. Additionally, it provides students with data-driven insights to decide which classes they might want to take or avoid. The tool uses historical data from the University of Illinois' GPA dataset to predict grade distributions for upcoming semesters, addressing stakeholders such as university administrators and students.

---

### 2. **Description of the Model**
Our model is a neural network designed for categorical grade prediction. It features:
- **Embedding Layers**: Each categorical feature (e.g., subject, course number, term, schedule type, instructor) is mapped to a low-dimensional vector space using embedding layers, which help capture relationships between categories.
- **Fully Connected Layers**: The concatenated embeddings are processed through three fully connected layers with ReLU activations, with a dropout layer to prevent overfitting.
- **Output Layer**: The final layer outputs probabilities for each grade category, which are converted to predictions.
- **Optimization and Loss**: We used Adam optimizer and cross-entropy loss to train the model efficiently. 
- **Evaluation Metrics**: Predictions were evaluated using both standard accuracy and relaxed (relative) accuracy to capture the model's nuanced performance.

---

### 3. **Challenges Faced**
- **Data Preprocessing**: We had to make sure we were handling and cleaning the historical GPA dataset adequately to prepare it for modeling.
- **Accuracy Confusion**: Initially, we were puzzled by the model’s low accuracy (~50%), which seemed to misrepresent its predictive performance. This was resolved by implementing a relaxed accuracy, or relative accuracy, metric, which accounts for grade proximity. For example, predicting an A instead of an A+ is treated as more accurate than predicting a D. The relaxed accuracy (~95%) proved to be a much more meaningful evaluation of the model’s capability.

---

### 4. **Feature Importance Analysis**
#### a. **Overview**
The feature importance analysis provided valuable insights into the factors that influence grade prediction. Among the encoded features (subject, course number, term, schedule type, and instructor), it was evident that certain features had a higher impact on the performance of the model.

#### b. **Key Insights**
- **Instructor**: This feature consistently demonstrated a high contribution, suggesting that variations in teaching style or course format could substantially affect student performance.
- **Subject and Course Number**: These features showed a moderate level of importance, reflecting the influence of course content and difficulty level on grades.
- **Term and Schedule Type**: These features appeared less influential, indicating that semesterly variations or yearly differences have a minimal impact on grade distribution within the dataset.

#### c. **Detailed Observations**
- At the A+ and A level, the subject was the primary factor influencing predictions. In contrast, the instructor was the most significant factor for all other grade ranges.
- This suggests that easier subjects correlate strongly with achieving A and A+ grades, while the instructor’s role becomes more influential in other cases.

#### d. **Visualization**
The SHAP summary plot provided a clear visualization of the relative contributions, guiding future model iterations to emphasize instructor-level data collection or course-specific interventions. 

---

### 5. **Results and Validation**
#### a. **Model Performance**
- Baseline Logistic Regression Model:
  - **Mean Squared Error (MSE)**: 1.001
  - **Mean Absolute Error (MAE)**: 0.676
- **Relaxed Accuracy**: The model achieved approximately 95% relaxed accuracy compared to ~50% standard accuracy, emphasizing its ability to capture broader performance trends over exact matches.

#### b. **Real-World Validation**
- The model predictions were cross-validated using a subset of historical data to confirm alignment with actual distributions. Further refinements could include incorporating additional features.

---

### 6. **Key Learnings**
- **Data Matters**: The importance of clean and structured data became apparent as it directly impacted the model's performance.
- **Relative Accuracy as a Metric**: This approach allowed us to evaluate categorical predictions more realistically.
- **Feature Analysis**: Understanding feature importance was critical for optimizing and interpreting the model's output.

---

### 7. **Future Work**
- **Incorporate Additional Features**: Integrating more contextual features such as instructor history, class timings, and enrollment size.
- **Enhance Model Complexity**: Experimenting with more sophisticated models like decision trees or neural networks for better predictions.
- **Deployment**: Creating a user-friendly interface for students and administrators to interact with predictions.

---

### 8. **Conclusion**
This project successfully demonstrates the feasibility of using historical GPA data to predict grade distributions. The tool has the potential to assist both university stakeholders and students in making informed decisions. Future enhancements can expand its impact, offering a robust and scalable solution for academic planning.