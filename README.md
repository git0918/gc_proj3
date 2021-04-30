# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & NLP

### Problem Statement

How can we use predictive modeling to best predict which subreddit a post came from?  Which words will most differentiate our two chosen subreddits - vegan and nutrition?

The goal of the project is to train the classifier on which subreddit a given post came from - Vegan and Nutrition to solve a binary classification problem by showcase on WebScraping | APIs | Natural Language Processing on Reddit Vegan and Nutrition posts

### Executive Summary

This project documents the process of downloading large amounts of Reddit submissions and comments using the Pushshift API to get interesting insights for vegan and nutrition.  
The project is divided in 3 main parts: collect data, perform EDA, and find the best score for the models (performance comparison) by using confusion matrix and pipeline, etc.

### Data Collection

I collected 17266 posts in total, 12098 nutrition and 5168 vegan, from 120 days before until the day of the data collection
Collection methods is pushshift.io
Vegan Data:
Vegan Data collected with 120 days period from Reddit to satisfy the requirements:
base_v_url = 'https://api.pushshift.io/reddit/search/submission/?subreddit=vegan&size=200&before={}d'
vegan_urls = [base_v_url.format(i) for i in range(120,-1,-1)]

Nutrition Data:
Nutrition Data collected with 120 days period from Reddit to satisfy the requirements:
base_n_url = 'https://api.pushshift.io/reddit/search/submission/?subreddit=nutrition&size=200&before={}d'
nutrit_urls = [base_n_url.format(i) for i in range(120,-1,-1)]

### EDA

I removed "deleted" text or ' ' string from posts for selftext of my dataset.  I checked the classes count, essential first step in any classification problem, and verify data and checked the baseline.  Now my data is ready to go modeling.

### Pre-Processing

Pre-processing includes custom stop word and vectorizing with Count Vectorizer and TF-IDF (Term Frequency-Inverse Document Frequency) to enhance modeling response.

### Model selection

Using a GridSearchCV hyperparameter optimization, we selected models to build and examine:
-	Multinomial Naive-Bayes
-	Random Forest
- Logistic Regression

### Model Optimization

I use a Pipeline to batch our pre-processing and model fitting into a single process, which GridSearch can iterate through.

### Conclusions and Recommendations

- The best score of TFDIF with Logistic Regression is: 0.9414
- The best score of CountVectorizer with Logistic Regression is: 0.9352
- The best score of TFDIF with naive multinomial Bayes is: 0.9187
- The best score of random foresets is:  0.919

Based on the conclusions, the winning model was the TFDIF with Logistic Regression that has a 94% accuracy score.  We recommend to go for it.
