# Recipe Entity Extraction Using Conditional Random Fields (CRF)

## Project Overview

This project focuses on identifying and extracting key entities from unstructured recipe ingredient data using Natural Language Processing (NLP) and Named Entity Recognition (NER).

A Conditional Random Field (CRF) model is developed to automatically identify three important entity categories:

- **Ingredient:** Names of ingredients used in recipes.
- **Quantity:** Numerical or descriptive quantities associated with ingredients.
- **Unit:** Measurement units such as grams, teaspoons, tablespoons, and cups.

The objective is to transform unstructured recipe ingredient descriptions into structured information that can be used for recipe management, food analysis, and intelligent food applications.

## Problem Statement

Recipe ingredient descriptions are generally available in unstructured text formats. Extracting meaningful information such as ingredient names, quantities, and measurement units manually can be time-consuming.

This project applies NLP techniques and CRF-based sequence labelling to automate the extraction of these key entities from recipe data.

## Dataset Description

- **Dataset file:** `ingredient_and_quantity.json`
- **Original records:** 285
- **Records removed:** 5 (due to mismatched input tokens and entity labels)
- **Final cleaned records:** 280
- **Entity labels:** Ingredient, Quantity, Unit

### Dataset Structure

The JSON dataset contains two main attributes:

| Column | Description |
|---|---|
| `input` | Raw recipe ingredient text |
| `pos` | Corresponding entity labels for each token |

## Technologies and Libraries Used

- Python
- Pandas
- NumPy
- Scikit-learn
- sklearn-crfsuite
- spaCy
- Matplotlib
- Seaborn
- Jupyter Notebook / Google Colab
- Natural Language Processing (NLP)
- Named Entity Recognition (NER)
- Conditional Random Fields (CRF)

## Project Workflow

### 1. Data Loading and Exploration
- Loaded the JSON dataset.
- Examined dataset dimensions, columns, and data types.
- Identified missing values and checked token-label alignment.

### 2. Data Cleaning and Preprocessing
- Tokenised recipe ingredient descriptions.
- Tokenised corresponding entity labels.
- Identified and removed five records with mismatched token and label counts.
- Prepared the cleaned dataset containing 280 records.

### 3. Exploratory Data Analysis (EDA)
- Identified unique entity labels.
- Analysed token distributions.
- Examined frequently occurring ingredients and measurement units.
- Categorised tokens into ingredient, quantity, and unit classes.

### 4. Train-Validation Split
The cleaned dataset was divided into training and validation sets using a 70:30 split.

| Dataset | Number of Recipes |
|---|---:|
| Training | 196 |
| Validation | 84 |
| Total | 280 |

### 5. Feature Engineering
Extracted meaningful token-level features to improve entity recognition.

Features included:
- Token and lemma information
- Part-of-speech tags
- Dependency relations
- Word shape and character patterns
- Numeric and fraction detection
- Stopword identification
- Previous and next token information
- Sequence boundary indicators (BOS and EOS)

### 6. Class Weighting
Applied a class-weighting strategy to account for differences in entity label frequencies.

The class weights used were:

| Entity | Class Weight |
|---|---:|
| Ingredient | 5.345858 |
| Quantity | 7.259184 |
| Unit | 8.771887 |

### 7. CRF Model Building and Training
Developed and trained a Conditional Random Field model using the following hyperparameters:

| Parameter | Value |
|---|---|
| Algorithm | LBFGS |
| L1 Regularisation (c1) | 0.5 |
| L2 Regularisation (c2) | 1.0 |
| Maximum Iterations | 100 |
| All Possible Transitions | True |

### 8. Model Evaluation
Evaluated the trained model on both training and validation datasets using:

- Precision
- Recall
- F1-score
- Accuracy
- Confusion Matrix
- Flat Classification Report

### 9. Error Analysis
- Identified misclassified tokens in the validation dataset.
- Examined actual and predicted labels.
- Analysed previous and next tokens.
- Investigated classification errors by entity category.
- Evaluated the impact of contextual ambiguity.

## Model Performance

### Training Dataset Results

| Metric | Score |
|---|---:|
| Accuracy | 99.90% |
| Macro F1-score | 99.84% |
| Weighted F1-score | 99.90% |

### Validation Dataset Results

| Metric | Score |
|---|---:|
| Accuracy | 99.79% |
| Macro F1-score | 99.59% |
| Weighted F1-score | 99.79% |

### Validation Performance by Entity

| Entity | Precision | Recall | F1-score |
|---|---:|---:|---:|
| Ingredient | 99.91% | 99.95% | 99.93% |
| Unit | 99.44% | 99.72% | 99.58% |
| Quantity | 99.51% | 99.03% | 99.27% |

### Error Analysis Results

- Total validation tokens: 2,876
- Correctly classified tokens: 2,870
- Misclassified tokens: 6
- Overall validation accuracy: 99.79%

Quantity recognition recorded the highest number of misclassifications, mainly due to contextual ambiguity in expressions such as "few", "a", and "pinch".

## Key Learnings

Through this project, I gained practical experience in:

- Understanding NLP and Named Entity Recognition.
- Working with unstructured text and JSON datasets.
- Performing data cleaning and tokenisation.
- Conducting exploratory data analysis.
- Extracting lexical, linguistic, and contextual features.
- Understanding Conditional Random Fields for sequence labelling.
- Evaluating machine learning models using classification metrics.
- Analysing confusion matrices and misclassified samples.
- Understanding class imbalance and error analysis.

## Future Scope

- Expand the dataset with more diverse recipe examples.
- Improve contextual features for quantity recognition.
- Explore BiLSTM-CRF and transformer-based NER models.
- Develop an application for automatic recipe entity extraction.
- Convert unstructured recipe descriptions into structured ingredient information.

## Conclusion

This project demonstrates the application of NLP and CRF-based sequence labelling for extracting meaningful entities from recipe ingredient data.

The trained model achieved 99.79% validation accuracy, demonstrating excellent performance in identifying ingredients, quantities, and measurement units in the available validation dataset.

The project provided practical exposure to the complete NLP workflow, from data preprocessing and feature engineering to model training, evaluation, and error analysis.

## Author

**Swati J. Nimbolkar**

Postgraduate Program in Artificial Intelligence and Machine Learning

**Areas of Interest:** Artificial Intelligence | Machine Learning | Natural Language Processing | Data Science

## Repository Topics

`python` `nlp` `named-entity-recognition` `ner` `conditional-random-fields` `crf` `machine-learning` `artificial-intelligence` `feature-engineering` `text-processing` `sequence-labeling` `spacy` `scikit-learn`
