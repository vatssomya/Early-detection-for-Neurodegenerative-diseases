# AI driven system for Early-detection-for-Neurodegenerative-diseases
### Introduction

Neurodegenerative diseases, such as Alzheimer's and Parkinson's disease, present significant challenges to healthcare systems worldwide. These conditions are characterized by a progressive decline in neuronal function, leading to various cognitive and motor impairments. Early detection and accurate diagnosis are crucial for effective intervention and management of symptoms. This project aims to develop an integrated approach for early detection of neurodegenerative diseases through four innovative methods: **MRI Analysis**, **Parkinson's detection**, and a series of **Cognitive tests**. By leveraging machine learning techniques and advanced imaging methods, we seek to enhance diagnostic accuracy and improve patient outcomes.

### Features
- **MRI Analysis**: Utilizes CNNs to analyze brain images for neurodegenerative changes.
- **Parkinson's detection**: Studies the patterns of your medical data to predict parkinson's disease
- **Speech Tests**: Assesses speech patterns and language skills using machine learning models.
- **Coordination Tests**: Evaluates hand-eye coordination through real-time hand tracking and a graphical interface.
- **Memory Games**: Tests visual recall and memory through a series of timed questions.

### Methods

#### MRI Analysis

The MRI analysis involves the application of Convolutional Neural Networks (CNNs) to classify brain images. The process begins with importing the necessary libraries, including TensorFlow and Keras, to build and train the CNN model.

1. **Data Preparation**: The images are pre-processed using `ImageDataGenerator` for data augmentation, enabling the model to generalize better during training. The training and validation datasets are split using an 80-20 ratio.

2. **Model Architecture**: A deep CNN architecture is constructed with multiple convolutional and max-pooling layers. The model employs batch normalization to enhance training stability and improve performance. The final layer utilizes a softmax activation function to classify the input images into two categories, indicating the presence or absence of neurodegenerative changes.

3. **Training**: The model is compiled with the categorical cross-entropy loss function and optimized using Stochastic Gradient Descent (SGD). It is then trained over 15 epochs, with model checkpoints to save the best-performing model based on validation loss.

4. **Performance Evaluation**: The model’s performance is evaluated on the validation dataset, with metrics such as accuracy and loss tracked throughout the training process.

```python
# 
cnn_model.fit(
    train_data,
    epochs=15,
    validation_data=val_data,
    callbacks=[checkpoint_cnn]
)
```


#### Parkinson's Disease Detection

This analysis utilizes a Random Forest Classifier to diagnose Parkinson's disease based on patient data.

1. **Data Loading**: The dataset is loaded from a CSV file, containing features relevant to Parkinson's diagnosis, such as speech and motor function metrics.

2. **Data Preprocessing**: The dataset is split into features (X) and target labels (y). Features such as `PatientID`, `BMI`, and `DoctorInCharge` are excluded, while `Diagnosis` is retained as the target variable. The data is then split into training and validation sets using an 80-20 ratio.

3. **Feature Scaling**: The features are standardized using `StandardScaler`, which improves the model's performance by ensuring all features contribute equally.

4. **Model Training**: A Random Forest Classifier is instantiated and trained on the training data. K-fold cross-validation is performed to evaluate the model's performance, yielding accuracy scores across multiple folds.

5. **Evaluation**: The model is tested on the validation set, and a classification report, including metrics like precision, recall, and F1-score, is generated to assess the model's effectiveness.

```python
#
rf_model.fit(X_train, y_train)
print(classification_report(y_val, y_val_pred))
```

### Coordination Test

This method assesses hand-eye coordination using a graphical interface and real-time hand tracking.

1. **Setup**: The application utilizes the MediaPipe library for hand tracking and Pygame for the graphical user interface. A circular target is displayed on the screen, which moves away from the user's cursor.

2. **Hand Tracking**: A webcam feed is captured, and hand landmarks are identified to track the position of the index finger. This position is used to move the cursor on the screen.

3. **Game Logic**: The target circle moves away from the cursor position, requiring the user to catch it. The time taken to catch the circle is recorded for performance analysis.

4. **Data Logging**: The performance data is stored in CSV files, allowing for analysis of user performance over time and the calculation of average times.


#### Speech Test

This analysis uses machine learning to evaluate speech patterns and language skills.

1. **Data Preparation**: The dataset is loaded and preprocessed, excluding non-essential identifiers. The data is split into training and validation sets.

2. **Model Training**: Various models (Logistic Regression, Decision Trees, Random Forests) are evaluated using K-fold cross-validation.

3. **Performance Evaluation**: The models are compared based on accuracy, with the best-performing model identified.


#### Memory Game

This component evaluates memory through a visual recall test using a Tkinter-based GUI.

1. **Image Display**: Images are shown for a limited time, and questions related to the images are asked afterward to assess recall ability.

2. **Questioning**: Questions are presented with multiple-choice answers. The user's selection is validated, providing feedback on their recall performance.


### Multi-Model Approach

In this phase, we compile the accuracy from each test to assess the overall health of the user. Each test is assigned a different weight based on its importance in diagnosing Alzheimer's disease.

1. **Weight Assignment**: Different weights are allocated to the tests based on their relevance (e.g., MRI Analysis has a higher priority than the memory Test).

2. **Accuracy Compilation**: The accuracy results from each test are combined to calculate a mean accuracy score. This score helps identify potential indicators of neurodegenerative's disease.

3. **Results Interpretation**: The mean accuracy is interpreted to provide a comprehensive overview of the user's cognitive health, allowing for early intervention strategies.

### Final Compilation + GUI

In this phase, we integrated all components of the project into a unified graphical user interface (GUI). This comprehensive application allows users to seamlessly navigate through different diagnostic tests, including MRI analysis, speech detection, memory tests, and coordination assessments.

1. **Integrated GUI**: The application features a user-friendly interface that consolidates all functionalities, enabling users to access each diagnostic method easily.

2. **Unified Experience**: By combining all aspects into one GUI, we provide a holistic approach to assessing neurodegenerative diseases. Users can engage with each test in a streamlined manner, enhancing their overall experience.

3. **Data Visualization**: The GUI also incorporates data visualization elements, allowing users to view results and insights derived from each test, making it easier to interpret their cognitive health status.

4. **Multi-Model Approach**: The final application compiles the accuracy from each test into a comprehensive assessment. This mean accuracy score, weighted based on the relevance of each test, helps identify potential indicators of neurodegenerative diseases like Alzheimer's.

5. **Future Enhancements**: The GUI serves as a foundation for future enhancements, such as incorporating additional tests, improving user interaction, and refining diagnostic algorithms for better accuracy.

This integrated approach not only simplifies the diagnostic process but also empowers users with actionable insights regarding their cognitive health.


