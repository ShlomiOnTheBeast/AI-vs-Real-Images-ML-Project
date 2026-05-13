> **Academic Project Notice**  
> This project was developed as part of an academic Machine Learning assignment focused on supervised learning, image classification, feature engineering, hyperparameter tuning, and model evaluation.

# AI vs Real Images Classification 🧠🖼️

A Machine Learning project for classifying images as either **AI-generated** or **Real** using a full supervised learning pipeline.

The project focuses on building the pipeline manually and explaining each step clearly:

- Dataset loading
- Data balancing
- Train/Test spliting
- Feature engineering
- KNN implementation from scratch
- Hyperparameter experiments
- Grid Search with 5-Fold Cross Validation
- Final model evaluation

The learning algorithm used in this project is **K-Nearest Neighbors (KNN)**, implemented from scratch without using ready-made machine learning implementations such as `scikit-learn`.

---

## Shortcuts 🛣️

--> **Main notebook:**  
[AI_VS_Real_Images.ipynb](./AI_VS_Real_Images.ipynb)

--> **Dataset source:**  
[AI vs Real Images Dataset on Kaggle](https://www.kaggle.com/datasets/rhythmghai/ai-vs-real-images-dataset)

--> **Final model section:**  
Look for: `Final Model Evaluation on Test Set`

--> **Grid Search CV section:**  
Look for: `Grid Search Cross Validation`

---

## Table of Contents 📌

- [About the Project](#about-the-project-)
- [Dataset](#dataset-)
- [Project Workflow](#project-workflow-)
- [Feature Engineering Methods](#feature-engineering-methods-)
- [KNN From Scratch](#knn-from-scratch-)
- [Model Evaluation](#model-evaluation-)
- [Grid Search Cross Validation](#grid-search-cross-validation-)
- [Final Results](#final-results-)
- [Project Structure](#project-structure-)
- [How to Run](#how-to-run-)
- [Use of AI Tools](#use-of-ai-tools-disclosure-)
- [Final Conclusion](#final-conclusion-)

---

## About the Project 📌

The goal of this project is to classify images into two classes:

- `AI` — AI-generated images
- `Real` — real images

The project uses a Kaggle dataset containing AI-generated and real images from several categories, such as:

- animals
- city
- food
- nature
- people

Since the original dataset was imbalanced, we applied undersampling to create a balanced dataset before training.

---

## Dataset 📦

The dataset was taken from Kaggle:

**AI vs Real Images Dataset**  
https://www.kaggle.com/datasets/rhythmghai/ai-vs-real-images-dataset

After balancing, the dataset contains:

| Class | Number of Images |
| --- | ---: |
| AI-generated | 250 |
| Real | 250 |

Final split:

| Set | Number of Images |
| --- | ---: |
| Train | 400 |
| Test | 100 |

---

## Project Workflow 🔄

The project follows a complete supervised machine learning workflow:

1. Load the dataset
2. Convert image paths and labels into a DataFrame
3. Analyze class distribution
4. Handle data imbalance using undersampling
5. Split the dataset into train and test sets
6. Extract image features
7. Implement KNN from scratch
8. Run baseline experiment
9. Run hyperparameter experiments
10. Perform Grid Search with 5-Fold Cross Validation
11. Train the final selected model on the full training set
12. Evaluate the final model once on the test set

---

## Feature Engineering Methods 🧪

A major part of the project was testing different ways to represent images numerically.

We implemented and compared four feature engineering methods:

| Method | Description | Feature Size |
| --- | --- | ---: |
| RGB Flatten | Resize image, normalize RGB pixels, flatten into a vector | 3072 |
| Grayscale Flatten | Convert to grayscale, resize, normalize, flatten | 1024 |
| Color Histogram | Represent RGB color distribution using histograms | depends on bins |
| Grayscale Histogram | Represent brightness distribution using grayscale histogram | depends on bins |

### Why Feature Engineering Matters

KNN compares samples using distances.

Therefore, the way an image is represented has a major impact on model performance.

Raw flattened pixels keep exact pixel positions, but they may not capture useful global patterns.  
Histogram-based features summarize color or brightness distributions, which worked much better for this dataset.

---

## KNN From Scratch ⚙️

The K-Nearest Neighbors algorithm was implemented manually.

The implementation includes:

- `fit()` function
- `predict_one()` function
- `predict()` function
- Euclidean distance
- Manhattan distance
- configurable `k`
- majority voting

The project does not use `scikit-learn` for the KNN implementation.

### KNN Logic

For each test image:

1. Calculate the distance between the test image and all training images.
2. Select the `k` nearest neighbors.
3. Count the labels of those neighbors.
4. Predict the majority label.

---

## Model Evaluation 📊

The project evaluates the models using several metrics:

- Accuracy
- Precision
- Recall
- F1-score
- Macro F1-score
- Confusion Matrix

### Main Metric

The main evaluation metric is:

**Macro F1-score**

Macro F1 was selected because both classes are equally important:

- AI-generated images
- Real images

Accuracy alone can be misleading if the model predicts mostly one class.

---

## Hyperparameter Experiments 🧮

We tested several hyperparameter combinations.

For KNN:

| Hyperparameter | Values |
| --- | --- |
| `k` | 1, 3, 5, 7, 9, 11 |
| `distance_metric` | Euclidean, Manhattan |

For histogram-based feature engineering:

| Hyperparameter | Values |
| --- | --- |
| `bins` | 8, 16, 32 |

These experiments helped compare feature engineering methods and understand how different parameters affect performance.

---

## Grid Search Cross Validation 🔍

To select the final model correctly, we used **Grid Search with 5-Fold Cross Validation**.

The Grid Search included:

- 4 feature engineering methods
- 6 values of `k`
- 2 distance metrics
- 3 histogram bin values for histogram methods

In total, the Grid Search evaluated:

```text
96 configurations
