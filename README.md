# Analyzing Product Sentiment with Natural Language Processing (NLP)
Using Natural Language Processing (NLP) to interpret, manipulate, and comprehend consumer attitudes towards major brands.

<img width="983" alt="Screen Shot 2023-08-29 at 2 11 49 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/001302ad-0f34-4e4a-b751-d26cc71ba7d0">

## Overview and Problem Statement
This project focuses on building a Natural Language Processing (NLP) tool as part of a classification task to analyze sentiment about products released by Apple, Google, and Android. Using machine learning models, we can assign emotion labels to thousands of tweets regarding the three companies and their products. Performing sentiment analysis on the Twitter dataset helps us determine whether a given tweet is positive, negative, or neutral, and our findings can be used to aid these businesses in monitoring perceptions about their brand and specific products.

## The Data
The file `tweet_data.csv` is a dataset containing tweets users posted about Google, Apple, or Android products. The columns in the original spreadsheet are as follows:
* `tweet_text`: the original tweet
* `emotion_in_tweet_is_directed_at`: the product the tweet is referring to
* `is_there_an_emotion_directed_at_a_brand_or_product`: the emotion (or lack of emotion) expressed in the tweet

The column `is_there_an_emotion_directed_at_a_brand_or_product` will serve as the target variable in our analysis. The target variable's unique values are:
* Negative emotion
* Positive emotion
* No emotion toward brand or product
* I can't tell

We assign a number to each target variable value for our analysis so the data can be modeled. Through performing a process called tokenizing on the `tweet_text` column and analyzing consumer sentiment by product and company, we can deliver actionable insights to each brand so they can better understand their strengths and address pain points.

Below is a preview of the raw data table:
<img width="856" alt="Screen Shot 2023-08-29 at 12 56 50 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/c46bda30-8aae-4cdb-929d-836438cc40a7">

## Methods
This project deals with a classification problem, as we're building a model to predict labels for each tweet. We start by preprocessing and cleaning the original dataset, and the procedure consists of:
* Removing or replacing rows that contain null values
* Renaming values and columns so they are less ambiguous
* Tokenizing (the process of splitting into smaller pieces) strings of tweets
* Assigning numerical values to the target (sentiment/emotion) variable

Our analysis begins with a deep dive into each brand and its respective positive or negative tweets. We use the FreqDist() method during this stage to determine which words and products are associated with each brand and emotion. The results are visualized as a pie chart and bar graph. After gaining insight into what evokes positive and negative emotions towards each brand, we continue with the modeling portion of our analysis.

We performed an iterative modeling process by looping through several runs of a Multinomial Naïve Bayes classifier algorithm. We start by testing the model for binary classification before moving on to a multi-classification version. Our model is used on several conditions, as outlined below:
* Baseline version
* Stopword removal to omit words that frequently occur
* Hyperparameter tuning to identify the best parameters to specify
* Random oversampling to handle data imbalances

A Multinomial Naïve Bayes algorithm is used for this project, as the algorithm is best suited for categorizing text. Since the dataset we're dealing with isn't entirely numerical, many other algorithms, such as regressions, are less useful. Moreover, the Multinomial Naïve Bayes model can be scaled to tackle large quantities of data, and our original table has over 9000 rows.

## Results
