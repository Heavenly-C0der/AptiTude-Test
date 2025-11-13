# Machine Learning (ML) Fundamentals Study Guide

As you're applying for an ML Engineer role, a solid grasp of the fundamentals is expected. This guide covers the essential, non-negotiable concepts you should know.

---

### 1. Core Concepts

- **Types of Machine Learning:**
  - **Supervised Learning:** Learning from labeled data (input-output pairs). The goal is to learn a mapping function to predict the output for new, unseen input.
    - **Classification:** Predicting a category (e.g., spam or not spam).
    - **Regression:** Predicting a continuous value (e.g., house price).
  - **Unsupervised Learning:** Learning from unlabeled data. The goal is to find hidden patterns or intrinsic structures in the data.
    - **Clustering:** Grouping similar data points together (e.g., customer segmentation).
    - **Dimensionality Reduction:** Reducing the number of variables under consideration.
  - **Reinforcement Learning:** An agent learns to make decisions by taking actions in an environment to maximize a cumulative reward.

- **The ML Workflow:**
  - Be able to describe the end-to-end process: Data Collection -> Data Preprocessing -> Feature Engineering -> Model Training -> Model Evaluation -> Deployment.

- **Overfitting and Underfitting:**
  - **Overfitting:** The model performs great on the training data but poorly on unseen test data. It has learned the training data "too well," including its noise.
  - **Underfitting:** The model performs poorly on both the training and test data. It has failed to capture the underlying patterns in the data.
  - **How to handle them:**
    - **Overfitting:** Get more data, use regularization (L1/L2), use dropout, reduce model complexity.
    - **Underfitting:** Use a more complex model, add more features, train for longer.

- **Bias-Variance Tradeoff:**
  - **Bias:** The error from erroneous assumptions in the learning algorithm. High bias can cause an algorithm to miss the relevant relations between features and target outputs (underfitting).
  - **Variance:** The error from sensitivity to small fluctuations in the training set. High variance can cause an algorithm to model the random noise in the training data (overfitting).
  - **The Tradeoff:** A simple model has high bias and low variance. A complex model has low bias and high variance. The goal is to find a balance.

- **Cross-Validation:**
  - A technique for assessing how the results of a statistical analysis will generalize to an independent dataset. The most common form is **k-fold cross-validation**.

---

### 2. Essential Algorithms

You should understand the basic idea behind these algorithms, their pros and cons, and when to use them.

- **Linear Regression:** For regression tasks.
- **Logistic Regression:** For binary classification tasks.
- **Decision Trees:** Simple to understand, can be visualized. Prone to overfitting.
- **Random Forests:** An ensemble of decision trees. Reduces overfitting and is generally more robust.
- **Support Vector Machines (SVM):** Effective in high-dimensional spaces.
- **K-Means Clustering:** The most popular algorithm for clustering tasks.

---

### 3. Model Evaluation Metrics

How do you know if your model is any good?

- **For Classification:**
  - **Confusion Matrix:** A table showing the performance of a classification model (True Positives, False Positives, True Negatives, False Negatives).
  - **Accuracy:** (TP + TN) / Total. Can be misleading for imbalanced datasets.
  - **Precision:** TP / (TP + FP). Of all the positive predictions, how many were actually correct?
  - **Recall (Sensitivity):** TP / (TP + FN). Of all the actual positives, how many did the model correctly identify?
  - **F1-Score:** The harmonic mean of Precision and Recall. A good metric for imbalanced datasets.

- **For Regression:**
  - **Mean Squared Error (MSE):** The average of the squared differences between the predicted and actual values.
  - **Root Mean Squared Error (RMSE):** The square root of MSE. Interpretable in the same units as the target variable.
  - **R-squared (R²):** The proportion of the variance in the dependent variable that is predictable from the independent variable(s).

---

### 4. Essential Mathematics

- **Linear Algebra:** Vectors, matrices, dot products, matrix multiplication.
- **Probability & Statistics:** Basic probability rules, conditional probability, mean, median, mode, standard deviation.
- **Calculus:** Basic understanding of derivatives (gradients), used in optimization algorithms like Gradient Descent.

---

### 5. How to Prepare

- **Review Your Projects:** The best way to demonstrate your knowledge is through your projects. Be ready to explain every decision you made: Why did you choose that algorithm? How did you preprocess the data? How did you evaluate your model?
- **Intuitive Explanations:** Focus on developing an intuitive understanding. For example, be able to explain "what is logistic regression?" in simple terms to a non-technical person.
- **Code with Libraries:** Be familiar with the main ML libraries in Python: **NumPy** (for numerical operations), **Pandas** (for data manipulation), and **Scikit-learn** (for ML models and utilities).

---

### 6. Recommended Resources

- **YouTube:**
  - **StatQuest with Josh Starmer:** The absolute best resource for intuitive, visual explanations of ML concepts.
  - **3Blue1Brown:** For beautiful, visual explanations of the underlying math.
- **Books:**
  - **"Hands-On Machine Learning with Scikit-Learn, Keras & TensorFlow" by Aurélien Géron:** A comprehensive and practical guide.
- **Courses:**
  - **Andrew Ng's "Machine Learning" course on Coursera:** A classic and still one of the best introductions to the field.
