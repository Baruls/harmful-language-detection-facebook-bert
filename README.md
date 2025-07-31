# Detecting and Classifying Harmful Language in Facebook Comments Using BERT

## Overview
This repository contains the code and resources for a project focused on detecting and classifying harmful language in Facebook comments. Utilizing a pre-trained BERT model, this project addresses the growing challenge of online toxicity by developing an automated moderation system capable of understanding nuanced informal language.

## Problem Statement
The proliferation of harmful language (such as hate speech, offensive language, and toxic comments) on social media platforms like Facebook poses significant threats to individuals and communities. Manual moderation is impractical due to the immense volume of user-generated content. This project aims to build an effective automated solution for binary text classification: identifying comments as either "Not Harmful" (0) or "Harmful" (1).

## Methodology
The project employs a robust methodology centered on fine-tuning a BERT-based Transformer model.

### 1. Data Collection & Preprocessing
-   A custom dataset of **1030 Facebook comments** (in English and Indonesian) was collected via scraping and manually labeled.
-   Initial data cleaning involved removing irrelevant columns and handling missing values.
-   The dataset exhibits an **imbalanced label distribution** (744 Not Harmful, 286 Harmful).
-   To address this, data splitting for training (824 comments) and testing (206 comments) was performed using a **stratified sampling** strategy to maintain label proportions.
-   Text tokenization was performed using `BertTokenizer` for the `bert-base-multilingual-cased` model.

### 2. Model Architecture & Training
-   The core model is `bert-base-multilingual-cased`, fine-tuned for binary sequence classification (\texttt{TFBertForSequenceClassification}).
-   **Class weighting** was applied during training to mitigate the effects of dataset imbalance, giving more attention to the minority class.
-   Training was conducted for a maximum of 10 epochs, with a learning rate of `3e-5`, `max_length` 128, and a batch size of 16.
-   **Early Stopping** (patience=2 on validation loss) was implemented to prevent overfitting and ensure the use of optimal model weights.

## Results
The model demonstrated promising performance in classifying harmful language.

-   **Overall Accuracy**: 81.07%.
-   **Minority Class (Harmful) Performance**:
    -   Precision: 0.74
    -   Recall: 0.49
    -   F1-score: 0.59
-   **Confusion Matrix**:
    -   True Negatives: 139
    -   False Positives: 10
    -   False Negatives: 29
    -   True Positives: 28
-   These results highlight a trade-off between minimizing false positives and maximizing recall for the harmful class, indicating areas for future improvement.

## Files in this Repository
-   `BERT_Train_Facebook_Post.ipynb`: The main Google Colab Jupyter Notebook containing all the code for data preprocessing, model training, and evaluation. (Make sure you replace this with your actual notebook file name).
-   `fb-posts.csv`: The dataset used for this project.
-   `README.md`: This file.
-   `images/`: A folder containing figures such as ROC curves, confusion matrix heatmap, and training performance plots. (Highly recommended to upload your plots here).

## Future Work
-   Improve recall for the minority class through more advanced imbalanced dataset handling strategies (e.g., oversampling, undersampling).
-   Conduct in-depth error analysis on false negatives to understand specific failure cases (e.g., sarcasm, implicit language).
-   Explore other Transformer model variants or more complex ensemble learning approaches.
-   Collect larger and more diverse datasets to improve model generalization.

## List of Facebook Group Scraped
- https://www.facebook.com/groups/486352819054396
- https://www.facebook.com/groups/560229822983601
- https://www.facebook.com/groups/635199913774100
- https://www.facebook.com/groups/640264044716845
- https://www.facebook.com/groups/771918063464559
- https://www.facebook.com/groups/985626342743662
- https://www.facebook.com/groups/1178001026167846
- https://www.facebook.com/groups/3250318435200916
- https://www.facebook.com/groups/sukimemes
- https://www.facebook.com/groups/tahubulatdigorengdadakan
