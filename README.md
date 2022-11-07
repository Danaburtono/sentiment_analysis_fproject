# **Final Project: Twitter Sentiment Analysis**

<br><br>

## Project Overview

### Executive Summary

Our team has decided to utilize Machine Learning to conduct a Sentiment Analysis on Gun Control using Natural Language Processing (NLP) and Machine Learning (ML) libraries and tools. Our team has opted to find and review tweets that contain a number of predetermined relevant keywords and focus on the 2022 Midterm Elections timeframe.
The team has conducted a few team sessions to align on classification criteria on a set of 100 tweets. This will allow us to more closely agree on tweet classification to train our ML models. Once trained and tested, we will decide on the most accurate ML model and proceed to analyze at least 400,000 tweets to understand sentiment on gun-control during pre- and post-election dates. Ultimately, the team will use the metadata to make appropriate data visualization tools and provide summaries and opinions on the data.

The data results will be discussed in the "Results" section. A summary section will contain the teams' findings, reporting, considerations and any recommendations for future studies.

<br>

### Topic Selection

Our team had been considering doing a Sentiment Analysis prior to the introduction of the Big Data module (in September 2022). After going through the Big Data and subsequent ML modules, we agreed we would do use NLP and ML to conduct an analysis of people's pro-gun and anti-gun sentiments expressed on Twitter on the days leading to the 2022 Mid-Term Elections held on November 8, 2022.
Once the ML model is trained to an acceptable accuracy range, the analysis should allow to present sentiment percentages across the population of tweets gathered. The tweet population will be limited to the United States. Ultimately, the team aims to present the variation of sentiment across various dates leading up to and post the election. If our premium-access-tier request is approved, the team aims to include an analysis of sentiment variation throughout various regions of the country to better understand how the pro- and anti-gun sentiment is distributed across the country through the time period described herein.

<br>

### Data Sources

-	Twitter API v2

    - Search Tweets endpoint
      - [Developer Documentation](https://developer.twitter.com/en/docs/twitter-api/tweets/search/api-reference/get-tweets-search-recent)
<br>

### Software Used

- Python 3.7.13
- Jupyter Notebook:
  - IPython : 7.31.1
  - ipykernel : 6.9.1
  - ipywidgets : 7.6.5
  - jupyter_client : 6.1.12
  - jupyter_core : 4.9.2
  - jupyter_server : 1.13.5
  - jupyterlab : 3.3.2
  - nbclient : 0.5.13
  - nbconvert : 6.4.4
  - nbformat : 5.3.0
  - notebook : 6.4.8
  - qtconsole : 5.3.0
  - traitlets : 5.1.1
- ML Methods: `<TBD>`

<br><br><br>

## Methodology

The following section contains details about the project and how the team derived results from the analysis.

### Documentation

The following documentation is captured as part of this repository:

- Group 6 Final Project Proposal
- Final Project Process Overview

### Branching

The team agreed to use the following branching strategy:

_More details on [this Google document](https://docs.google.com/document/d/1R5ymXR9j9KWXxl4_9Ug5ayz2Q5TtuGFOi0grzYWA0bA/view)._

### Data Extraction

To retrieve the necessary natural language text data for processing and analysis, our team chose to utilize the Twitter API. The Twitter API is the Application Programming Interface of the company Twitter, a popular microblogging and social networking service platform. The Twitter API has a few available versions and access tiers with various endpoints. We used the Search Tweets endpoint of the Twitter API v2 service on the Essential access tier to procure 100 tweets as a sample text dataset for classification and prediction model prototyping.

Our project protocols rely heavily on the Python programming language, therefore, we chose to use the Tweepy 4.11.0 ([Developer Documentation](https://docs.tweepy.org/en/stable/client.html#search-tweets)) Python library to authenticate and interact with Twitter’s interface endpoints. Through use of Python and Tweepy in a Jupyter Notebook with our project environment kernel, we were able to utilize the Search Tweets query parameter to select the most recent tweets (within the last 7 days) for the hashtags #uvalde and #guncontrol. The query also filtered for tweets that are not retweets, as well as only tweets in the English language. Tweepy’s Paginator was also used to perform pagination through Twitter’s API in order to select 10 tweets before selecting the next page and selecting another 10 tweets. This pagination was repeated until 100 tweets (50 tweets for each hashtag) were fetched and received in the API responses. Once the fetching process was complete, the tweets were aggregated in an array using a Python for loop. After containing the tweets in a list format, the tweets were combined into a Pandas dataframe and then exported as a CSV file for portability and further wrangling of the acquired dataset.

The next phase for our project will feature a refined query for a greater variety of tweets on our subject matter: sentiment about guns and gun control. Our results will also include more fields from the Search Tweets endpoint for additional features to the data including Tweet IDs and ISO formatted Timestamps. Since our project will focus on sentiment regarding gun control near and around the 2022 US midterm elections, we will also make use of endpoint parameters to pull 40,000 tweets for each day for a range of dates around election day, November 8, 2022.


### Data Preprocessing

#### Training the Trainers

2 team members were assigned a set of 50 tweets that were extracted through the Twitter API which contained one of two hashtags: #uvalde or #gun-control.
In total, 100 tweets were used (50 per each 2 team members) to classify the dataset.
After each member submitted their respective sentiment classification, the results were combined into one single csv file. This file was further processed using pandas DataFrames to create a new column identifying conflicts in classification. Using this file, the team held a couple of meetings to ensure alignment on the methodology for classifying tweet sentiment. During this review, we still ended with 6% of tweets that we could not fully agree on classification. These will be reviewed more in depth with the TAs and/or instructor(s) to try and reduce ambiguity.

#### Preprocessing

The aforementioned classified dataset (100 tweets) will be fed into a few ML models to understand what model may be best suited for our analysis.
**\*NOTE:** This initial analysis has two intentions: (1) understand which models may be most beneficial for our use-case and (2) meet the criteria in the Segment 1 rubric. This is not the final training dataset.\*

The final training data will contain at least 1000 rows of classified tweets. The team will aim for using the following classifications and percentages to train the ML models and decide which model provides the best accuracy:

- Pro-gun - 40%
- Anti-gun - 40%
- Neutral - 20%

### Database

A traditional entity relational diagram (ERD) is a representation of “entities” such as people, places, or dates as they relate to each other usually expressed in several data frames. However, this method of visualization is not typically used in natural language processing. However, ERDs are still used to create conceptual models to map relationships between attributes, objects, and classes based on relationships with words. The structure of the ERD usually follows similar requirements however not all models are the same. Typically, NLP models conduct a series of processing such as segmentation, tokenization, tagging as part-of-speech, chucking, and parsing. Due to the heuristic approach to NLP, the ERD stands as a conceptual model that will likely change through the course of the project.

![ERD_image](res/images/ERD_v1.png)

### Proposed ML Models

We are using supervised learning for twitter sentiment analysis to classify tweets as pro-gun, anti-gun or neutral. Since, we have a small dataset of 1000 tweets (400 pro-gun, 400 anti-gun and 200 neutral), to overcome the problem of overfitting we are considering to use the following Machine Learning models:

- Naive Bayes: These are a set of supervised learning algorithms based on applying Bayes’ theorem with the “naive” assumption of conditional independence between every pair of features given the value of the class variable. In Naive Bayes, probabilities are assigned to words or phrases, segregating them into different labels.

- Support Vector Machine: An SVM model is basically a representation of different classes in a hyperplane in multidimensional space. The hyperplane will be generated in an iterative manner by SVM so that the error can be minimized. The goal of SVM is to divide the datasets into classes to find a maximum marginal hyperplane (MMH).

- Random Forest: A random forest algorithm samples the data and builds several smaller, simpler decision trees. Each tree is simpler because it is built from a random subset of features. They are robust against overfitting.

- Adaptive Boosting: The idea behind Adaptive Boosting, called AdaBoost, in which a model is trained then evaluated. After evaluating the errors of the first model, another model is trained. This time, however, the model gives extra weight to the errors from the previous model. The purpose of this weighting is to minimize similar errors in subsequent models. Then, the errors from the second model are given extra weight for the third model. This process is repeated until the error rate is minimized.

- XGBoost

Division of Training And Testing dataset- 70:30.

### Training the Model(s)

TBD

### Testing the Model(s)

TBD

### Dataset Analysis

TBD

<br><br><br>

## Results

### Results1

### Results2

### Results3

### Results4

### Results5

### Results Summary & Recommendations

<br><br><br>

## Appendix

Templates:

|     ![Figure1]()      |
| :-------------------: |
| **Figure 1.** Example |
