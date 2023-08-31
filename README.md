# Analyzing Product Sentiment with Natural Language Processing (NLP)
Using Natural Language Processing (NLP) to interpret, manipulate, and comprehend consumer attitudes towards major brands.

<img width="983" alt="Screen Shot 2023-08-29 at 2 11 49 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/001302ad-0f34-4e4a-b751-d26cc71ba7d0">

## Overview and Problem Statement
This project focuses on building a Natural Language Processing (NLP) tool as part of a classification task to analyze sentiment about Apple, Google, and Android (developed by Google). Using machine learning models, we can assign emotion labels to thousands of tweets about the three brands. Performing sentiment analysis on the Twitter dataset helps us determine whether a given tweet is positive, negative, or neutral, and our findings can be used to aid these businesses in monitoring perceptions about their brand and specific products.

## The Data
The file `tweet_data.csv` is a dataset containing tweets posted by contributors at a SXSW festival about Google, Apple, or Android. There are 9,093 rows and 3 columns. The columns in the original spreadsheet are as follows:
* `tweet_text`: the original tweet
* `emotion_in_tweet_is_directed_at`: the product the tweet is referring to
* `is_there_an_emotion_directed_at_a_brand_or_product`: the emotion (or lack of emotion) expressed in the tweet

The column `is_there_an_emotion_directed_at_a_brand_or_product` will serve as the target variable in our analysis. The target variable's unique values are:
* Negative emotion
* Positive emotion
* No emotion toward brand or product
* I can't tell

We assign a number to each target variable value for our analysis so the data can be modeled. Through performing a process called tokenizing on the `tweet_text` column and analyzing consumer sentiment by brand, we can deliver actionable insights to each brand so they can better understand their strengths and address pain points.

Below is a preview of the raw data table:
<img width="856" alt="Screen Shot 2023-08-29 at 12 56 50 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/c46bda30-8aae-4cdb-929d-836438cc40a7">

## Methods
This project deals with a classification problem, as we're building a model to predict labels for each tweet. We start by preprocessing and cleaning the original dataset, and the procedure consists of:
* Removing duplicate rows
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

A Multinomial Naïve Bayes algorithm is used for this project, as the algorithm is best suited for categorizing text. Since the dataset we're dealing with isn't entirely numerical, many other algorithms, such as regressions, are less valuable. Moreover, the Multinomial Naïve Bayes model can be scaled to tackle large quantities of data, and our original table has over 9000 rows.

In tuning our hyperparameters, we choose to specify "f1_weighted" as the scoring method since our dataset has a class imbalance, and we're dealing with a multiclass target. "f1_weighted" takes the mean score of each class' f1-score and accounts for each class' support. For reference, the f1-score calculates the harmonic mean between precision and recall (number of true positives over total elements), and an f1-score returns the model's overall accuracy.

## Results
### Binary Classification
The best version of our Multinomial Naïve Bayes algorithm for our binary classifier includes tokenization, stopword removal, random oversampling, and hyperparameter tuning. We got a test score of 0.88 and a weighted f1-score of 0.87. We've created a confusion matrix to visualize the performance of the classification algorithm with normalized (proportion) values. The two dimensions are "True label" and "Predicted label".

<img width="384" alt="Screen Shot 2023-08-30 at 8 32 06 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/1a024c4b-ea28-4d2a-ad29-6d95fb6ccbee">

### Multiclass Classification
The Multinomial Naïve Bayes algorithm that returns the best results for our multiclass classifier includes tokenization, stopword removal, and hyperparameter tuning. We got a test score of 0.69 and a weighted f1-score of 0.67. We've created a confusion matrix to visualize the performance of the classification algorithm with normalized (proportion) values. The two dimensions are "True label" and "Predicted label". For this confusion matrix, an additional variable represents the tweets labeled "none" (also known as no sentiment tweets).

<img width="378" alt="Screen Shot 2023-08-30 at 8 34 19 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/8b1c91fb-803c-4808-a0dc-c87b57b50784">

### Sentiment Analysis for Google, Apple, and Android Brands
We created bar graphs displaying the top bigrams associated with negative and positive sentiment tweets for Google, Apple, and Android brands. A bigram refers to a pair of two consecutive words. A detailed explanation of the graphs and corresponding word cloud graphics can be found in the [Jupyter Notebook](https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/blob/main/Tweet%20Sentiment%20Analysis%20Notebook.ipynb), and a summary of recommendations can be found under the "Recommendation" portion of this README.

#### Google
<img width="920" alt="Screen Shot 2023-08-30 at 8 55 45 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/9e3870e3-e03b-4690-a271-4fcd8b1a5658">
<img width="912" alt="Screen Shot 2023-08-30 at 8 56 05 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/03729c18-714d-4a80-bac7-111fa1933fa1">

#### Android
<img width="912" alt="Screen Shot 2023-08-30 at 8 58 01 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/d143567f-5938-4edc-9605-02a572d34edb">
<img width="909" alt="Screen Shot 2023-08-30 at 8 56 42 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/79476edc-909b-489d-b2a9-34853875a8ec">

#### Apple
<img width="918" alt="Screen Shot 2023-08-30 at 8 56 49 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/372e090d-de4b-4cf6-8f60-8991190be26b">
<img width="908" alt="Screen Shot 2023-08-30 at 8 56 53 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/269f5c0b-4b1f-41de-a486-e07b479ff5ef">

## Conclusion

The optimal MNB model for a binary classifier has the following parameters and results:

`Pipeline([('vect', TfidfVectorizer(tokenizer = tk.tokenize, stop_words = stopwords_list, ngram_range = (1,3))), ('mnb', MultinomialNB(alpha = 0.001))])`

<img width="474" alt="Screen Shot 2023-08-30 at 7 36 40 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/74a1cebc-25e1-4fea-8766-c2cc21cc465f">

The optimal MNB model for a multiclass classifier has the following parameters and results:

`Pipeline([('vect', TfidfVectorizer(tokenizer = tk.tokenize, stop_words = stopwords_list, ngram_range = (1, 2))), ('mnb_multi', MultinomialNB(alpha = 0.1))])`

<img width="470" alt="Screen Shot 2023-08-30 at 7 36 27 PM" src="https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/assets/111642763/eb8420df-be52-4daf-94d5-0149af268eca">

## Recommendation
By building an NLP tool and conducting a sentiment analysis, we recommend the following:

Google / Android
* Google Maps garners lots of positive attention, and continued investment in the app is critical to success
* Launches and party events with famous figures like Marissa Mayer garner excitement from contributors
* Pain points addressed by customers include problems with Android compatibility and uncertainty surrounding product launches

Apple
* Frequently have popup stores and booths as consumers enjoy visiting new locations
* Concentrate marketing efforts on product launches as they garner enthusiasm (shown through iPad 2's launch)
* Increase product testing to address design headaches and iPhone battery issues
* Work towards improved corporate social responsibility efforts to ease negative perspectives on the company as a whole

## Future Analyses
* Gather more data from different sources such as Google Reviews, stores like Best Buy, or tech articles
* Find more negative sentiment data to improve the analysis of what consumers dislike about each brand
* Add processes such as stemming to tokenization and stopword removal to see if better models can be built

## Additional Information
More details can be found in this [Jupyter Notebook](https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/blob/main/Tweet%20Sentiment%20Analysis%20Notebook.ipynb). A deliverable summarizing the project can also be found [here](https://github.com/keziasetokusumo/product_sentiment_analysis_nlp_project/blob/main/p4_project_deliverable.pdf).

## Repository Structure
```
├── data
├── images
├── .gitignore                         
├── README.md                                      
├── Tweet Sentiment Analysis Notebook.ipynb 
├── p4_project_deliverable.pdf
└──
```
