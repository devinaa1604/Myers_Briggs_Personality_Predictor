# Myers-Briggs Personality Type Prediction
![](https://excellenceassured.com/wp-content/uploads/2015/09/16-personality-types.png)

## Background
The Myer-Briggs personality test categorizes an individual into 1 of 16 distinct personality types. Myer-Briggs classifies an individual along 4 binary classifications:
* Introvert (I) or Extrovert (E)
* Intuitive (N) or Sensing (S)
* Thinking (T) or Feeling (F)
* Judging (J) or Perceiving (P)

## Data Set
Our data set includes 8,600 rows of data. Each row is an individual person and includes his or her Myer-Briggs personality type and 50 social media posts made by that individual. The data is presented in 2 columns. The first column is the personality type, and the second column includes all 50 social media posts separated by '|||'. The data set can be found [here](https://www.kaggle.com/datasnaek/mbti-type?select=mbti_1.csv).

## Project Purpose

The purpose of this project is to predict personality types as one of the sixteen categories of Myers Briggs personality types (MBTI) based on the correlation between people's writing styles and their psychological personalities. We believe that social media gives people the platform to express themselves freely and openly and hence those posts can be an indicator of their personality type.
We acknowledge the fact that all personality types are equal.

### Project Questions
1. Can you accurately predict an individual's Meyer-Briggs personality type based on their social media activity?
2. Are there certain words that each Meyer-Briggs personality type uses more or less than other personality types?
3. Is post length (i.e., number of words per post) predictive of personality type (e.g, introvert vs. extrovert)?

## Tools & Modules Used
- Machine Learning - Natural Language Processing | Classification Models | Scikit Learn | NLTK | Sentiment Analyzer | Pipeline | Imbalance Learn | TF-IDF
- Data Analysis - Pandas | Numpy | Matplotlib

## Methodology

### Feature Engineering
Following steps were taken to prepare the data for machine learning models:
-  Cleaning the Data
-  Posts were converted into lower case.
-  ||| and punctuations were replaced by spaces.
-  Links and Emails were dropped.
-  MBTI personality types were dropped. 
-  The cleaned data generated after executing above steps was Lemmitized using NLTK Word Net Lemmitizer. Stop Words were also dropped.
-  Sentiment Scoring using Sentiment Intensity Analyzer to calculate compound, positive, negative and neutral sentiment score for each user using the clean posts.
-  NLTK POS tagger was used to tag each word with its part of speech tag. The average number of each of the POS tags was calculated for each user based on the original posts. The POS tags included were – Noun, Verb, Adjective, Prepositions, Interjections and Determiners.
-  Counting per user average counts were taken for number of words, variance, links, images, question marks, exclamations and ellipsis.

### Machine Learning Models
- The data was split into X (input features) and y (target).
- X comprised of clean text, compound sentiment score, pos tag counts, and various other counts.
- Y was set to four target features - is_Extrovert, is_Sensing, is_Thinking, is_Judging
- Preprocessing step was designed to vectorize the clean posts and to select k best features out of the other (non-word) features using column transformer.
- Since the data was imbalanced Imbalance Learn Pipeline was used to create the models. The pipeline was composed of preprocess (from the above step), random under sampler (to handle class imbalance) and the classification model.
- Following models were built, trained and tested on dataset: TF-IDF Logistic Regression Count Vectorized Logistic Regression TF-IDF Logistic Lasso Count Vectorized Logistic Lasso TF-IDF Logistic Ridge Count Vectorized Logistic Ridge TF-IDF Logistic Elasticnet TF-IDF Support Vector Classifier Count Vectorized Support Vector Classifier TF-IDF Naive Bayes Count Vectorized Naive Bayes TF-IDF Random Forest Count Vectorized Random Forest
- Evaluation Metrics – Accuracy, Precision, Recall, ROC-AUC and Average Precison_Recall_Score were used as the measures to evaluate the models and select the one performing the best.
- Final Model – Based on the scores for the evaluation metrics used, TF-IDF Logistic Regression Model was selected as the final model for predicting Myers Briggs personality type.

## Postmortem
- The dataset was heavily imbalanced with most people identifying as introverted (I) and Intuitive (N) rather than extroverted (E) and Sensitive (S). 
- This caused all our models to have a hard time classifying Extroversion vs. Introversion and Sensitivity vs. Intuition. 
- We were able to overcome this problem to some extent by using Imbalance Learn’s Random Under Sampling method. This improved the scores but not significantly. 
- We also added extra words that didn’t seem to be very helpful in classifying a personality trait to the stop words list to make the model predict more efficiently. 
- Our model is able to predict 2 to 4 traits out of a total of 4 traits and we consider this as success because even for human readers it is difficult to accurately predict a person’s Myers Briggs personality type.
- Information lost during data clean-up: E.g., emojis, images, links
- How would outcome change for different forms of social media? I.e., LinkedIn vs. Twitter vs. Facebook

## For Future
- Add more data specifically for the types that have low counts in our current dataset to balance the classes. 
- Implement a neural network based model in an attempt to see if that can outperform our current model in accurately predicting all 4 traits of the Myers Briggs personality type.
