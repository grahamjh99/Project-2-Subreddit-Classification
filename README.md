# Project Title: Determining which Subreddit a post belongs to 
Determining if a post belongs to the subreddit wallstreetbets or stocks

# Table of contents
1. [Overview](#overview)
2. [Data](#data)
3. [Requirements](#requirements)
4. [Executive Summary](#executive-summary)
5. [Findings](#findings)
6. [Next Steps](#next-steps)

## Overview:
With increasing building costs it is more important than ever to know what features sell in a home. Using a linear regression model the best features of houses can be determined so they will sell even in locations that would be considered undesriable.

---

## Data
The data was scrapped from the subreddits wallstreetbets and stocks. The scraping was done through praw and gathered the time of post in utc, the title of the post, the self_text of the post, and the subreddit of the post. The subreddits were changed to 0 for wallstreetbets and 1 for stocks. The title and the self_text were concatenated and used to train the model.

## Requirements
- Libraries used:
    - matplotlib.pyplot
    - pandas
    - numpy
    - seaborn
    - train_test_split from sklearn.model_selection
    - LinearRegression from sklearn.linear_model
    - RidgeCV and Ridge from sklearn.linear_model
    - StandardScaler from sklearn.preprocessing
    - metrics from sklearn
- Data used:
    - Ames, Iowa housing data


## Executive Summary
#### Purpose
- The financial world is increasingly influenced by conversations on platforms like Reddit, where communities like wallstreetbets and stocks play a pivotal role in shaping retail trading trends and sentiment. However, the volume of content is overwhelming, and irrelevant or low-quality posts can dilute valuable insights, making it harder for investors and firms to extract actionable intelligence. This model not only classifies posts into relevant subreddits but also serves as a foundation for building an automated content curation system.
#### Methods
- EDA:
    - The subreddits were changed to 0 for wallstreetbets and 1 for stocks.
    - The title and the self_text were concatenated and used to train the model.

- Modeling:
    - designed two Random Forest models 
  
#### Findings
- Through this model it was found that the parameters associated with the Garage of the house had a significant impact on the house's price. The best example is that not having a garage changed the predicted price by about 150%
- Square footage is a good predictor of sales price
- Loaction is a good predictor of sales price
- The type of building is not as great of a predictor of sales price as expected
- The age and the year of remodling had high correlations to sale price but did not change the sale prices overly much

#### Next Steps
- The next steps of this research involve adding loan and intrest rate information to better understand the amount of debt people are willing to take on to purchase a home. There also should be a closer examination of the columns and what they correspond to in order to remove repeats and similar data. Removal of outliers might help the model greatly 