# Clothing Size Recommendation Engine

A machine learning model that predicts clothing sizes (Small, Medium, Large) based on a user's physical measurements and body type. 

## Overview

Online clothing shopping has a massive return rate, largely due to sizing issues. Most brands use static size charts (Height + Weight) that fail to account for body shape. 

This project takes the body types, Age, Height, and Weight, to accurately predict a user's clothing size category.

## Dataset

- **Source:** [RentTheRunway / Modcloth Dataset](https://www.kaggle.com/datasets/rmisra/clothing-fit-dataset-for-size-recommendation) (via Kaggle)
- **Utilized Dataset:** From these two datasets, 1 utilised the [RentTheRunway] Dataset.
- **Raw size:** 192,544 records
- **Cleaned size:** 141,591 records
- **Features used:** Age, Height (inches), Weight (lbs), Mapped Body Type.
- **Target:** Clothing Size Category (Small, Medium, Large).

## Approach

### 1. Data Cleaning
- Parsed messy height strings (e.g., `"5' 6\""`) into pure numerical inches.
- Parsed weight strings (e.g., `"137lbs"`) into pure numbers.
- Mapped RentTheRunway's body type categories (e.g., `hourglass`, `pear`) to our Project 1 categories (`Average`, `Broad`).
- Dropped rows with missing critical data.

### 2. Exploratory Data Analysis (EDA)
- Found that **Weight** has the strongest correlation with Size (`r = 0.85`).
- Height (`r = 0.25`) and Age (`r = 0.17`) are weak secondary signals.
- **Body Type Averages:** Broad mapped to Size 14.6, Average to 11.4, and Petite to 5.4, validating our mapping logic.

### 3. Modeling
- **Algorithm:** Random Forest Classifier.
- **Target grouping:** Instead of predicting exact sizes (e.g., Size 4 vs Size 6, which vary wildly by brand), the model groups sizes into **Small** (≤6), **Medium** (7–12), and **Large** (>12).
- **Data Split:** 80% Train, 20% Test.

## Results

| Metric | Score |
|---|---|
| **Accuracy** | **71.13%** |
| Large (F1-Score) | 0.77 |
| Small (F1-Score) | 0.73 |
| Medium (F1-Score) | 0.64 |

The model performs exceptionally well at distinguishing between Small, Medium, and Large sizes, proving that combining Weight with Body Type is a highly effective strategy for size prediction.

## Project Structure

```text
clothing-size-recommender/
├── README.md
├── requirements.txt
├── size_recommendation.ipynb
├── models/
│   ├── size_category_model.pkl    # Trained Random Forest model
│   └── model_columns.pkl          # Saved columns for prediction alignment
└── data/
    └── (dataset files)
```

## Future Scope

I can use this project "Size Recommendation project" with the project "Body type project" to bring more accurate results using Streamlit for interface.