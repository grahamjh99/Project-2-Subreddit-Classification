# Project Title: Determining which Subreddit a Post Belongs To 
Determining if a post belongs to the subreddit wallstreetbets or stocks

# Table of contents
1. [Overview](#overview)
2. [Data](#data)
3. [Requirements](#requirements)
4. [Executive Summary](#executive-summary)
5. [Findings](#findings)
6. [Next Steps](#next-steps)

## Overview:
The stock market where most retirement savings are placed and where most millionaires and all billionaires are made. With about $300 billion on average going through the market daily (google ai) there is a significant opportunity to make money. Certain subreddits are known to be heavily focused on stocks and the market in general. Some have made international news such as the subreddit wallstreetbets during the extreme rise in the stock price of Gamestop. These subreddits thus have a large impact on retail tradding and are useful resources to understand retail sentiment and where retail may be putting it's money. It is therefore useful to be able to determine which subreddit a post belongs to since subreddits like wallstreetbets is primarily a gambling subreddit while the stocks subreddit is mostly about discussing the stock and determining if it is worth the investment.  


---

## Data
The data was scrapped from the subreddits wallstreetbets and stocks. The scraping was done through praw and gathered the time of post in utc, the title of the post, the self_text of the post, and the subreddit of the post. The subreddits were changed to 0 for wallstreetbets and 1 for stocks. The title and the self_text were concatenated and used to train the model.

## Requirements
- Libraries used:
    - praw
    - pandas
    - numpy 
    - matplotlib.pyplot
    - load_dotenv from dotenv
    - os
    - import train_test_split, RandomizedSearchCV from sklearn.model_selection 
    - Pipeline from sklearn.pipeline 
    - CountVectorizer from sklearn.feature_extraction.text
    - RandomForestClassifier from sklearn.ensemble
    - joblib
    - SVC from sklearn.svm
    - confusion_matrix, ConfusionMatrixDisplay, classification_report from sklearn.metrics
    - re
- Data used:
    - Scrapped the subreddits wallstreetbets and stocks for the newsts 100 posts about 2 times a day to get 1100 posts from each subreddit


## Executive Summary
#### Purpose
- The financial world is increasingly influenced by conversations on platforms like Reddit, where communities like wallstreetbets and stocks play a pivotal role in shaping retail trading trends and sentiment. However, the volume of content is overwhelming, and irrelevant or low-quality posts can dilute valuable insights, making it harder for investors and firms to extract actionable intelligence. This model not only classifies posts into relevant subreddits but also serves as a foundation for building an automated content curation system.
#### Methods
- EDA:
    - The subreddits were changed to 0 for wallstreetbets and 1 for stocks.
    - All null values in both subreddits were changed to the string 'Image'
    - Concatenated the DataFrames of both subreddits since they were collected separately

- Modeling:
    - Designed two Random Forest models one using CountVectorizer to remove english stop words and one using CountVectorizer and not removing english stop words
    - The parameters of both random forest models were found using RandomSearchCV and narrowed down from there.
        * The firs model used 50 iterations of RandomSearchCV and the second used 100
    - Designed a Support Vector Machine model (rfb) using RandomSearchCV to find the best paramaters using 500 iterations.
  
#### Findings
- The most common words in the wallstreetbets subreddit were ai, mstr(Micro Strategy), and earnings
- The most common words in the stocks subreddit were growth, revenue, million and billion.
    * Million and billion are likely refering to the amount of revenue a company has made in a quarter or overall. 

#### Next Steps
- Add in scrapping to extract stock tickers
- some form of scrapping to extract the poster's analysis of the stock
- Add sentiment analysis on ticker discussions