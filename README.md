# AI vs Real Images Classification

This project was created as part of a Machine Learning course assignment.

The goal of the project is to classify images as either:

- AI-generated
- Real

## Dataset

The dataset was taken from Kaggle:

AI vs Real Images Dataset  
https://www.kaggle.com/datasets/rhythmghai/ai-vs-real-images-dataset

## Project Overview

The project includes a full supervised machine learning pipeline:

1. Dataset loading
2. Data imbalance handling using undersampling
3. Train/test split
4. Feature engineering
5. KNN implementation from scratch
6. Hyperparameter experiments
7. Grid Search with 5-Fold Cross Validation
8. Final model evaluation on the test set

## Feature Engineering Methods

The following feature engineering methods were tested:

- RGB Flatten
- Grayscale Flatten
- Color Histogram
- Grayscale Histogram

## Algorithm

The learning algorithm used in this project is K-Nearest Neighbors (KNN), implemented from scratch.

The implementation supports:

- different values of k
- Euclidean distance
- Manhattan distance
- fit function
- predict function

## Final Selected Model

The final model was selected using Grid Search with 5-Fold Cross Validation.

Final configuration:

- Feature method: Color Histogram
- Image size: 64x64
- bins = 32
- k = 9
- Distance metric = Manhattan

## Final Test Results

The final selected model achieved:

- Test Accuracy = 0.84
- Test Macro F1 = 0.8399

## Files

- `AI_VS_Real_Images.ipynb` — the full project notebook including code, explanations, outputs and visualizations.
