Customer Support Message Classification (Billing / Technical / Account)
📌 Project Overview

This project implements a multi-class text classification system that categorizes short customer support messages into three categories:

Billing

Technical

Account

The goal is to automatically classify customer support tweets using traditional NLP techniques such as TF-IDF and Logistic Regression.

📂 Dataset

The dataset used is from Kaggle:

Customer Support on Twitter
https://www.kaggle.com/datasets/thoughtvector/customer-support-on-twitter

The dataset contains customer support conversations between customers and company support accounts.

Files Used

twcs.csv → used for training

sample.csv → used for testing predictions

Important Note

The dataset does not provide labels such as Billing, Technical, or Account.
Therefore, labels were generated automatically using keyword-based weak supervision.

⚙️ Approach Used
1. Data Filtering

Only customer messages were used for training by selecting:

inbound = True

This ensures we train on messages written by customers (support requests), not company replies.

2. Automatic Labeling (Weak Supervision)

Since no category column exists, we automatically created labels using keywords:

Billing keywords: charge, payment, refund, invoice, bill, subscription...

Technical keywords: error, crash, bug, not working, slow, failed...

Account keywords: login, password, reset, account, email, locked...

Messages not matching any category were ignored.

3. Text Feature Extraction (TF-IDF)

We used TF-IDF Vectorization to convert text into numerical vectors.

Settings used:

Stopwords removal: stop_words="english"

N-grams: (1,2) (unigrams + bigrams)

4. Classification Model

We trained a Logistic Regression classifier:

Efficient for sparse TF-IDF features

Common baseline model for text classification

🧪 Model Training and Testing
Training

The model was trained using labeled tweets from twcs.csv.

Validation

The training data was split into:

80% training

20% validation

Evaluation metrics:

Accuracy

Precision / Recall / F1-score

Testing

After training, the model was used to predict categories for messages in sample.csv.

The output contains a new column:

predicted_category

📊 Output

The final predictions are saved into:

predictions.csv

Columns:

tweet_id

text

predicted_category

🚀 Technologies Used

Python

Pandas

Scikit-learn

TF-IDF Vectorizer

Logistic Regression

✅ Conclusion

This project demonstrates a complete NLP pipeline using traditional machine learning methods:

Data cleaning

Weak supervision labeling

Feature extraction with TF-IDF

Multi-class classification with Logistic Regression

Testing on unseen dataset

This approach can be improved further using:

Manual labeling (better ground truth)

Deep learning models (BERT, LSTM)

More advanced preprocessing
