# Project 2 - Myers-Briggs Personality Type
![](https://excellenceassured.com/wp-content/uploads/2015/09/16-personality-types.png)

## Background
The Meyer-Briggs personality test categorizes an individual into 1 of 16 distinct personality types. Myer-Briggs classifies an individual along 4 binary classifications:
* Introvert (I) or Extrovert (E)
* Intuitive (N) or Sensing (S)
* Thinking (T) or Feeling (F)
* Judging (J) or Perceiving (P)

## Data Set
Our data set includes 8,600 rows of data. Each row is an individual person and includes his or her Meyer-Briggs personality type and 50 social media posts made by that individual. The data is presented in 2 columns. The first column is the personality type, and the second column includes all 50 social media posts separated by '|||'. The data set can be found [here](https://www.kaggle.com/datasnaek/mbti-type?select=mbti_1.csv).

## Project Questions
1. Can you accurately predict an individual's Meyer-Briggs personality type based on their social media activity?
2. Are there certain words that each Meyer-Briggs personality type uses more or less than other personality types?
3. Is post length (i.e., number of words per post) predictive of personality type (e.g, introvert vs. extrovert)?

## Packages
- NLTK
- Spacey
- Wordcloud
- Tensor Flow

## Methods
1. Visualize the frequency of words used in social media posts by each Meyer-Briggs personality type.
2. Use NLP to analyze the words used by different personality types and train the model to classify them into 1 of 16 distinct personality types. We will use Random Forest and RNN for classification.
3. Test training data set to predict the personality type.
4. Apply model to celebrity example by scraping data from selected celebrity's social media page.
