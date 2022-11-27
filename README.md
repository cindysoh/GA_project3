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

### 1. Data Collection

### 2.1 Data Cleaning
#### 2.1.1 Nike
#### 2.1.2 Adidas

### 2.2 EDA
#### 2.2.1 Overview Dataset Analysis
#### 2.2.2 Words Analysis
- 2.2.2.1 20 Most Common Words
- 2.2.2.2 20 Most Common Bigram
- 2.2.2.3 20 Most Common Trigram
- 2.2.2.4 20 Most Common Words using TF-IDF
#### 2.2.3 Sentiment Analysis

### 2.3 Saving Data

### 3.1 Preprocessing
#### 3.1.1 Tokenize
#### 3.1.2 Lemmatize
#### 3.1.3 Stem

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
-Everything that comes with http
-Newline: '\n'
-Backslash: '\\'
-Double space: '  '
-Double quote', '\"'

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

#### 2.2.1 Word Analysis
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

##### 2.2.2.2 20 Most Common Bigram
 Nike
Count
air max
398
nike shoes
299
does know
298
amp x200b
297
basketball shoes
297
photon dust
295
lace loops
295
reflective lace
295
loops 95s
295
dust reflective
295
flex experience
294
|air force|205|
|ve worn|201|
|hey guys|200|
|jordan 1s|200|
|shoes really|198|
|13 wide|198|
|want know|198|
|tell legit|198|
|airmax 95|198|







Pushshift's API is fairly straightforward. For example, if I want the posts from [`/r/boardgames`](https://www.reddit.com/r/boardgames), all I have to do is use the following url: https://api.pushshift.io/reddit/search/submission?subreddit=boardgames

To help you get started, we have a primer video on how to use the API: https://youtu.be/AcrjEWsMi_E

**NOTE:** Pushshift now limits you to 100 posts per request (no longer the 500 in the screencast).

---

### Requirements

- Gather and prepare your data using the `requests` library.
- **Create and compare two models**. One of these must be a Random Forest classifier, however the other can be a classifier of your choosing: logistic regression, KNN, SVM, etc.
- A Jupyter Notebook with your analysis for a peer audience of data scientists.
- An executive summary of your results.
- A short presentation outlining your process and findings for a semi-technical audience.

**Pro Tip:** You can find a good example executive summary [here](https://www.proposify.biz/blog/executive-summary).

---

### Necessary Deliverables / Submission

- Code must be in at least one clearly commented Jupyter Notebook.
- A readme/executive summary in markdown.
- You must submit your slide deck as a PDF.
- Materials must be submitted before **26 Nov 2022 12 pm** through your GitHub account repo shared with the Teaching Team.

---

## Presentation Structure

- **Presentation Time: 10 minutes**
- Use Google Slides or some other visual aid (Keynote, Powerpoint, etc).
- Consider the audience. Assume you are presenting to a non-technical audience.
- Start with the **data science problem**.
- Use visuals that are appropriately scaled and interpretable.
- Talk about your procedure/methodology (high level, **CODE IS ALWAYS INAPPROPRIATE FOR A NON-TECHNICAL AUDIENCE**).
- Talk about your primary findings.
- Make sure you provide **clear recommendations** that follow logically from your analyses and narrative and answer your data science problem.

Be sure to rehearse and time your presentation before class.

---

## Rubric
Teaching team will evaluate your project using the following criteria.  You should make sure that you consider and/or follow most if not all of the considerations/recommendations outlined below **while** working through your project.

**Note:** Presentation will be done as a group while codes will be prepared and submitted by each student.

For Project 3 the evaluation categories are as follows:<br>
**The Data Science Process**
- Problem Statement
- Data Collection
- Data Cleaning & EDA
- Preprocessing & Modeling
- Evaluation and Conceptual Understanding
- Conclusion and Recommendations

**Organization and Professionalism**
- Organization
- Visualizations
- Python Syntax and Control Flow
- Presentation

**Scores will be out of 30 points based on the 10 categories in the rubric.** <br>
*3 points per section*<br>

| Score | Interpretation |
| --- | --- |
| **0** | *Project fails to meet the minimum requirements for this item.* |
| **1** | *Project meets the minimum requirements for this item, but falls significantly short of portfolio-ready expectations.* |
| **2** | *Project exceeds the minimum requirements for this item, but falls short of portfolio-ready expectations.* |
| **3** | *Project meets or exceeds portfolio-ready expectations; demonstrates a thorough understanding of every outlined consideration.* |


### The Data Science Process

**Problem Statement**
- Is it clear what the goal of the project is?
- What type of model will be developed?
- How will success be evaluated?
- Is the scope of the project appropriate?
- Is it clear who cares about this or why this is important to investigate?
- Does the student consider the audience and the primary and secondary stakeholders?

**Data Collection**
- Was enough data gathered to generate a significant result?
- Was data collected that was useful and relevant to the project?
- Was data collection and storage optimized through custom functions, pipelines, and/or automation?
- Was thought given to the server receiving the requests such as considering number of requests per second?

**Data Cleaning and EDA**
- Are missing values imputed/handled appropriately?
- Are distributions examined and described?
- Are outliers identified and addressed?
- Are appropriate summary statistics provided?
- Are steps taken during data cleaning and EDA framed appropriately?
- Does the student address whether or not they are likely to be able to answer their problem statement with the provided data given what they've discovered during EDA?

**Preprocessing and Modeling**
- Is text data successfully converted to a matrix representation?
- Are methods such as stop words, stemming, and lemmatization explored?
- Does the student properly split and/or sample the data for validation/training purposes?
- Does the student test and evaluate a variety of models to identify a production algorithm (**AT MINIMUM:** Random Forest and one other model)?
- Does the student defend their choice of production model relevant to the data at hand and the problem?
- Does the student explain how the model works and evaluate its performance successes/downfalls?

**Evaluation and Conceptual Understanding**
- Does the student accurately identify and explain the baseline score?
- Does the student select and use metrics relevant to the problem objective?
- Does the student interpret the results of their model for purposes of inference?
- Is domain knowledge demonstrated when interpreting results?
- Does the student provide appropriate interpretation with regards to descriptive and inferential statistics?

**Conclusion and Recommendations**
- Does the student provide appropriate context to connect individual steps back to the overall project?
- Is it clear how the final recommendations were reached?
- Are the conclusions/recommendations clearly stated?
- Does the conclusion answer the original problem statement?
- Does the student address how findings of this research can be applied for the benefit of stakeholders?
- Are future steps to move the project forward identified?


### Organization and Professionalism

**Project Organization**
- Are modules imported correctly (using appropriate aliases)?
- Are data imported/saved using relative paths?
- Does the README provide a good executive summary of the project?
- Is markdown formatting used appropriately to structure notebooks?
- Are there an appropriate amount of comments to support the code?
- Are files & directories organized correctly?
- Are there unnecessary files included?
- Do files and directories have well-structured, appropriate, consistent names?

**Visualizations**
- Are sufficient visualizations provided?
- Do plots accurately demonstrate valid relationships?
- Are plots labeled properly?
- Are plots interpreted appropriately?
- Are plots formatted and scaled appropriately for inclusion in a notebook-based technical report?

**Python Syntax and Control Flow**
- Is care taken to write human readable code?
- Is the code syntactically correct (no runtime errors)?
- Does the code generate desired results (logically correct)?
- Does the code follows general best practices and style guidelines?
- Are Pandas functions used appropriately?
- Are `sklearn` and `NLTK` methods used appropriately?

**Presentation**
- Is the problem statement clearly presented?
- Does a strong narrative run through the presentation building toward a final conclusion?
- Are the conclusions/recommendations clearly stated?
- Is the level of technicality appropriate for the intended audience?
- Is the student substantially over or under time?
- Does the student appropriately pace their presentation?
- Does the student deliver their message with clarity and volume?
- Are appropriate visualizations generated for the intended audience?
- Are visualizations necessary and useful for supporting conclusions/explaining findings?


---

### Why did we choose this project for you?
This project covers three of the biggest concepts we cover in the class: Classification Modeling, Natural Language Processing and Data Wrangling/Acquisition.

Part 1 of the project focuses on **Data wrangling/gathering/acquisition**. This is a very important skill as not all the data you will need will be in clean CSVs or a single table in SQL.  There is a good chance that wherever you land you will have to gather some data from some unstructured/semi-structured sources; when possible, requesting information from an API, but often scraping it because they don't have an API (or it's terribly documented).

Part 2 of the project focuses on **Natural Language Processing** and converting standard text data (like Titles and Comments) into a format that allows us to analyze it and use it in modeling.

Part 3 of the project focuses on **Classification Modeling**.  Given that project 2 was a regression focused problem, we needed to give you a classification focused problem to practice the various models, means of assessment and preprocessing associated with classification.   
