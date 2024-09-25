# Financial Transaction Data for Anti-Money Laundering (AML) Detection

## Introduction

This project focuses on detecting potential money laundering activities within a dataset of synthesized financial transactions provided by **IBM (International Business Machines Corporation)**. These transactions represent interactions between individuals, businesses, and banks, covering a wide range of financial activities such as consumer purchases, industrial orders, salary payments, loan repayments, and more.

The dataset aims to simulate a real-world scenario where a small subset of individuals and businesses are involved in illicit activities like smuggling, illegal gambling, and extortion. The project follows the **money laundering cycle**—**Placement**, **Layering**, and **Integration**—which criminals use to obscure the origins of illegally obtained funds. The primary objective of this project is to utilize data analysis and machine learning techniques to help authorities identify and distinguish potential money laundering cases hidden within the legitimate financial transactions.

## Table of Contents
- [Introduction](#introduction)
- [Money Laundering Cycle](#money-laundering-cycle)
- [Objective](#objective)
- [Dataset Features](#dataset-features)
- [Data Preprocessing Steps](#data-preprocessing-steps)
- [Model Training](#model-training)
- [Analysis](#analysis)
- [Key Insights](#key-insights)
- [Conclusion](#conclusion)
- [Requirements](#requirements)
- [Instructions](#instructions)
- [Acknowledgement](#acknowledgement)

## Money Laundering Cycle

- **Placement**: Introduction of illegal funds into the financial system.
- **Layering**: Complex series of financial transactions to obscure the origins of illegal money.
- **Integration**: Final stage where the illegal money appears to be legitimate and is used in normal financial activities.

## Objective

The primary goal is to employ machine learning and data analysis techniques to detect and identify potential money laundering activities among the provided transactions. The dataset contains a mix of legitimate and suspicious transactions, allowing for the creation of models that can distinguish between the two.

## Dataset Features

1. **Timestamp**: Date and time when the transaction occurred.
2. **From Bank**: Bank sending the money.
3. **To Bank**: Bank receiving the money.
4. **Amount Received**: Amount of money received in the transaction.
5. **Receiving Currency**: Currency in which the amount was received.
6. **Amount Paid**: Amount of money paid in the transaction.
7. **Payment Currency**: Currency in which the amount was paid.
8. **Payment Format**: Mode of payment (e.g., ACH, Bitcoin, Credit Card, etc.).
9. **Is Laundering**: Flag indicating if the transaction is suspected of laundering (1 for laundering, 0 for non-laundering).

## Data Preprocessing Steps

1. **Undersampling**: Given the imbalance between legitimate transactions and money laundering cases, undersampling is employed to balance the dataset. This technique reduces the number of non-laundering transactions to equalize the distribution with laundering transactions, which improves model performance by avoiding bias toward the majority class.

2. **Feature Engineering**:
   - Temporal features such as year, month, day, and hour are extracted from the timestamp.
   - Currency and payment format columns are encoded using one-hot encoding, with less frequent categories grouped under an "Others" category.
   - Categorical features such as bank and account numbers are frequency encoded to avoid high dimensionality caused by one-hot encoding.
   
3. **Scaling**: Robust scaling is applied to numerical features like `Amount Received` and `Amount Paid` to handle outliers and ensure proper normalization.

## Model Training

The dataset is split into training and test sets to ensure unbiased model evaluation. Machine learning algorithms will be applied to predict the `Is Laundering` variable, helping identify suspicious transactions that may indicate money laundering.

## Analysis

- **Exploratory Data Analysis (EDA)**: Histograms, boxplots, and scatter plots are used to understand data distributions and correlations between transaction amounts.
- **Outliers**: Significant outliers in `Amount Received` and `Amount Paid` indicate unusual transactions, which are crucial for identifying money laundering patterns.
- **Correlation Analysis**: A strong correlation exists between `Amount Received` and `Amount Paid`, providing insights into typical versus suspicious financial behaviors.

## Key Insights

- The ACH payment format is the most commonly used for both laundering and non-laundering transactions.
- Money laundering transactions frequently involve USD as both receiving and payment currency.
- Certain banks and accounts exhibit higher transaction frequencies, which could be indicative of repeated or organized laundering activities.

## Conclusion

This dataset allows for robust analysis of money laundering activities, providing insights into financial behaviors that could help authorities detect and prevent illicit financial transactions. Through effective data preprocessing, machine learning models can be trained to flag suspicious activities, helping reduce the prevalence of financial crime.

## Requirements

- Python 3.x
- Libraries:
  - pandas
  - numpy
  - scikit-learn
  - matplotlib
  - seaborn

## Instructions

1. **Data Preprocessing**: Use the provided Python scripts to clean and preprocess the dataset (including undersampling and encoding).
2. **Model Training**: Train machine learning models using the processed data and evaluate performance on the test set.
3. **Visualization**: Use visualizations to understand the data distribution and highlight potential laundering transactions.
4. **Model Evaluation**: Evaluate the trained models using standard metrics such as accuracy, precision, recall, and F1-score to determine their effectiveness in identifying money laundering activities.

## Acknowledgement

This project is part of the **Data Science Competition Olympiad 2023**, organized by the **Data Science Club of Binus University**.
