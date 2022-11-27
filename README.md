# Project 3: Web APIs & NLP

## Introduction

Many fashion retailer launches new collection every season (4-5 times a year). Retailer barely have time to research and react on consumers' reaction and response on current season and another new season is coming. This short time frame, retailer have to analyse sales performance, marketing activation and execution.

## Problem Statement

As part of the commercial analytics team of Nike, we notice that it is a challenge to keep up with consumers conversation with multiple collections launching every season. Our stakeholder, Merchandise Planning department and Marketing department has tasked us to find a solution to help with their planning for the future season. The solution needs to be able to:

- Understand current competitor trend
- Understand current consumer response/comments
- Find out if the merchandise they had planned that would have high demand are accurate based on consumers comments
- Duplicated/reused for every season(dynamic/scalable solution)
- Differentiate Nike posts from competitor posts using a classification model

## Content

- [1. Data Collection](#1-data-collection)
- [2.1 Data Cleaning](#21-data-cleaning)
- [2.2 EDA](#22-eda)
    - [2.2.1 Overview Dataset Analysis](#221-overview-dataset-analysis)
    - [2.2.2 Words Analysis](#222-words-analysis)
        - 2.2.2.1 20 Most Common Words
        - 2.2.2.2 20 Most Common Bigram
        - 2.2.2.3 20 Most Common Trigram
    - [2.2.3 Sentiment Analysis](#223-sentiment-analysis)
- [3.1 Preprocessing](#31-preprocessing)
    - 3.1.1 Tokenize
    - 3.1.2 Lemmatize
    - 3.1.3 Stem
- [Preprocessing and Modeling](#Preprocessing-and-Modeling)
- [Conclusion and Recommendations](#Conclusion-and-Recommendations)


### 3.1 Preprocessing
#### 3.1.1 Tokenize
#### 3.1.2 Lemmatize
####  3.1.3 Stem

### 3.2 Baseline Model
#### 3.2.1 Count Vectorizer
#### 3.2.2 Naive Bayes
- 3.2.2.1 Tokenized words
- 3.2.2.2 Lemmatized words
- 3.2.2.3 Stemmed words
#### 3.2.3 Stopwords
#### 3.2.4 Naive Bayes with Stopwords

### 3.3 Model Tuning
#### 3.3.1 Naive Bayes with TF-IDF
#### 3.3.2 Random Forest

### 3.4 Conclusion and Recommendation


## Executive Summary

### 1. Data Collection

For data collection, we have use Reddit, as it has proper segmentation of different communities in subreddits which help ease our web scraping process.

Data standardisation:
Minimum 20 words in a post (title + selftext)
5000 posts from each brand’s subreddit

Competitor selection: Adidas

#### Data Collection Process

- Create a function to filter post with minimum 20 words count while collecting the data
- Using https://files.pushshift.io to collect post and cut off at 5000
- Nike data was posted between 30 October 2022 and 10 November 2022
- Adidas data was posted between 22 October 2022 and 10 November 2022

#### Data Dictionary

|Features|Description|
|----|----|
|author|The name of the author|
|subreddit|The subreddit community|
|selftext|The title of the post|
|title|The content of the post|
|created_utc|The epoch time|

### 2.1 Data Cleaning
Removing: 
- Everything that comes with http
- Newline: '\n'
- Backslash: '\\'
- Double space: '  '
- Double quote', '\"'

### 2.2 EDA
#### 2.2.1 Overview Dataset Analysis
Average word count
- Nike: 49.52 words
- Adidas: 55.40 words

Top 3 active users
Nike
- Extroe (394 posts)
- Nervous-Matter4576 (198 posts)
- Syranial-Bean (198 posts)
Adidas
- Neonnearvash (167 posts)
- Alternative_Coconut6 (111 posts)
- MClooosey (110 posts)

#### 2.2.2 Word Analysis
##### 2.2.2.1 20 Most Common Words
|Both Subreddit|Nike|Adidas|
|----|----|----|
|shoes|little|shoe|
|like|air|got|
|know|bought|buy|
|just|really|need|
|size|make|black|
|help|leather|confirmed|
|pair|work|app|
|ve|reflective|want|
|does|worn|order|
|time| | |
|don| | |
There are 11 common word from both Nike and Adidas, which is expected as both brands' businesses are driven by Footwear. Some words that stand out from Nike only are 'air', 'leather', 'work' and 'reflective', while for Adidas only are 'black', 'confirmed' and 'app'. We will move on to Bigram to further analyse more commonly used words in each subreddit.

##### 2.2.2.2 20 Most Common Bigram
|Nike|Count|   |Adidas|Count|
|----|----|----|----|----|
|air max|398|   |does know|285|
|nike shoes|299|   |need help|230|
|does know|298|   |pair adidas|227|
|amp x200b|297|   |pair shoes|227|
|basketball shoes|297|   |kanye west|226|
|photon dust|295|   |adidas confirmed|226|
|lace loops|295|   |adidas app|225
|reflective lace|295|   |confirmed app|224|
|loops 95s|295|   |adidas shoes|171|
|dust reflective|295|   |store pickup|171|
|flex experience|294|   |adidas website|169|
|air force|205|   |track jacket|169|
|ve worn|201|   |long term|169|
|hey guys|200|   |don want|168|
|jordan 1s|200|   |nmd r1|116|
|shoes really|198|   |feels like|115|
|13 wide|198|   |money dress|114|
|want know|198|   |boost sole|114|
|tell legit|198|   |shoes boost|114|
|airmax 95|198|   |ve received|114|

We can identify a few words that are related to each brand.
**Nike**
- Style Names/Colourway: 'air max'/'airmax 95', 'air force', 'jordan 1s', 'photon dust'
- Product/Features: 'basketball shoes', 'lace loops', 'flex experience', 'reflective lace'

**Adidas**
- Style Names/Association: 'nmd r1', 'shoes boost', 'kanye west'
- Product/Features: 'track jacket', 'boost sole'
- UX/Service: 'confirmed app', 'store pickup', 'adidas website'


##### 2.2.2.3 20 Most Common Trigram
|Nike|Count|   |Adidas|Count|
|----|----|----|----|----|
|reflective lace loops|295|   |bought adicolor classics|114|
|lace loops 95s|295|   |classics primeblue sst|114|
|photon dust reflective|295|   |adicolor classics primeblue|114|
|guys date tag|198|   |primeblue sst track|114|
|air max 95|198|   |sure age like|113|
|air max plus|198|   |mean know look|113|
|date tag tell|198|   |comfy sure age|113|
|hey guys date|198|   |need sizing help|113|
|tag tell legit|198|   |term usage reviews|113|
|tell legit thank|198|   |boosts durable mean|113|
|colour photon dust|197|   |hella comfy sure|113|
|reflective help pls|196|   |age like long|113|
|dust reflective help|196|   |like long term|113|
|bought jordan 1s|100|   |know look good|113|
|know nike shoes|100|   |22 boosts durable|113|
|air force 1s|100|   |cut ties kanye|113|
|know right subreddit|100|   |zx 22 boosts|113|
|drop follow instagram|99|   |good hella comfy|113|
|mens dunks time|99|   |durable mean know|113|
|mens drop friday|99|   |ties kanye west|113|

Now we can see the combined word make more sense and more distinctive.
**Nike**
- Style Names/Colourway: 'photon dust reflective', 'air max 95', 'air max plus', 'colour photon dust', 'bought jordan 1s', 'air force 1s', 'mens dunks time'
- Product/Features: 'reflective lace loops', 'lace loops 95s'

**Adidas**
- Style Names/Colourway: 'bought adicolor classics', 'classics primeblue sst', 'adicolor classics primeblue', 'primeblue sst track', '22 boosts durable', 'zx 22 boosts'
- Product/Features: 'comfy sure age', 'like long term', 'boosts durable mean'
- Association: 'cut ties kanye', 'ties kanye west', 'adidas website'

#### 2.2.3 Sentiment Analysis
Sentiment analysis is a way to classify text as either having positive or negative sentiment. This will help us to analyse each post according to positive, neutral or negative comments. Overall scoring on 'compound' shows that Adidas is have more positive posts than Nike. 

- Adidas positive posts: reference to previous slide, the community could be expressing positive comments about adidas app or web service. Durability of their ultraboost
- Nike positive posts: most likely talk about likability of the product and design, as we notice alot of product names being mentioned.
