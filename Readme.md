# Toxic Comments Filter

A multi-label text classification project for automatic detection of toxic content in online comments.

## Project Overview

The project uses a recurrent neural network to classify comments into six categories:

- `toxic`
- `severe_toxic`
- `obscene`
- `threat`
- `insult`
- `identity_hate`

This is a **multi-label classification task**, meaning that a comment can belong to multiple categories simultaneously. The main challenges are the strong class imbalance and the high co-occurrence between labels.

## Dataset

The dataset contains **159,571 comments** with six binary labels. The strong imbalance, particularly for rare categories such as `threat` and `severe_toxic`, is addressed through a weighted sampling strategy during training.

## Preprocessing

The text is cleaned, tokenized into integer sequences, and padded/truncated to a fixed length. The vocabulary is limited to the **10,000 most frequent tokens**, with the tokenizer fitted only on the training data to avoid data leakage.

The dataset is split into training, validation, and test sets using **multi-label stratification** to preserve the distribution of the six categories.

## Model Architecture

The classifier is based on an **LSTM recurrent neural network**:
It is evaluated using **precision, recall and F1-score** for each category, together with aggregate multi-label metrics.

The model achieves **over 80% precision and recall across all six categories**, while performance on individual classes is analyzed separately to account for the strong class imbalance.