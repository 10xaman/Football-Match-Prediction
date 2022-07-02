## Table of Contents

<!--ts-->
* [Aims and Objectives](#Aims-and-Objectives)
* [Dataset](#Dataset)
* [Data Cleaning and Preparation](#Data-Cleaning-and-Preparation)
* [Feature Engineering and Data Visualisation](#Feature-and-Data-Visualisation)
* [Model Selection and Training](#Model-Selection-and-Training)
* [Evaluation](#Evaluation)
* [Further Work and Improvements](#Further-Work-and-Improvements)
<!--te-->


## Aims and Objectives

The aim was to build a model that could accurately predict the outcome of future league football matches.

- Achieve a test accuracy of greater than 50% and further normalizing the features for improvement.
- Output probabilities that appear sensible/realistic, that are comparable to odds offered on popular betting websites.


## Dataset

The data was collected directly from :<a href="https://www.kaggle.com/datasets/hugomathien/soccer" target="_blank"> Kaggle </a>. 
(This dataset was used to perform exploratory data analysis.)

The data was collected directly from :<a href="http://football-data.co.uk/data.php" target="_blank"> Football Data </a>. 

This was preferred because it has following:

- This dataset contains information of all the game statistics like fulltime goals, halftime goals, corners, half time away goal, free kicks, fouls, yellow cards, red cards, total shots, shots on target etc.


## Data Cleaning and Preparation

Data was initially collected from the 2000-2021 Premier League season, and further merged in the form of a single csv file per fixture containing a range of stats (e.g. number of shots, corners etc.)  


## Feature and Data Visualisation

In order to utilise as much previous match data as possible, whilst minimising the number of features, match data was averaged over the previous 10 games to predict an upcoming fixture. Eighteen features were chosen:

- FTHG - Full Time Home Goal
- FTAG - Half Time Away Goal
- FTR - Full Time Result
- HTHG - Half Time Home Goal
- HTAG - Half Time Away Goal
- HTR - Half Time Result
- HS - Home Shots
- AS - Away Shots
- HST - Home Shots on Target
- AST - Away Shots on Target
- HF - Home Team Foul
- AF - Away Team Foul
- HC - Home Team Corner
- AC - Away Team Corner
- HY - Home Team Yellow Card
- Ay - Away Team Yellow Card
- HR - Home Team Red Card
- Ar - Away Team Red Card

The above describes the features for a single team. Like-for-like features were visualised in figure 1, and demonstrate that the chosen features have some influence on the outcome of a match.

<img src="https://github.com/10xaman/Football-Match-Prediction/blob/main/images/1.png" alt="Figure 1">

<em>Figure 1. Green dots indicate a 'team' win and blue dots indicate an opponent win. Dots in the bottom left quadrant indicate a poor quality team and opponent, top left: low quality team and high quality opponent, top right: high quality team and opponent, bottom right: high quality team and low quality opponent.</em>


## Model Selection and Training

These algorithms were selected and tested from the library: scikit-learn.

- Multinomial Naive Bayes
- Support Vector Machine
- Logistic Regression


## Evaluation

Along with accuracy, graph plotting were initially used to evaluate model performance, displayed in figure 2 below.

<img src="https://github.com/10xaman/Football-Match-Prediction/blob/main/images/2.png" alt="Figure 2">

<em>Figure 2. (a) Naive Bayes - 57.2% accuracy (b) SVM model - 61.2% accuracy (c) Logistic regression - 59.1% accuracy</em>

Immediate inspection of these matrices shows all three models are performing poorly when predicting a draw.

- After normalization

<img src="https://github.com/10xaman/Football-Match-Prediction/blob/main/images/3.png" alt="Figure 3">

<em>Figure 2. (a)  - 48.4% accuracy (b) SVM model - 59.3% accuracy (c) Logistic regression - 60.9% accuracy</em>


Immediate inspection of these matrices shows all three models are performing poorly when predicting a draw.

## Further Work and Improvements

Several areas of further work are suggested to improve the predictions made in this study. These include:

- Collect additional data: <a href="http://football-data.co.uk/data.php" target="_blank"> Football Data </a> can supply numerous seasons of data prior to that collected in this study. It is postulated additional data collected will result in better clustering, especially those fixtures counted as a draw.

- Currently the model is built on short term data, and specific in game statistics - like number of shots. More generic features regarding a club’s size and quality could also be added such as: average points per game, current league position, past season(s) league positions etc. This may add some context to the heavily form driven model. 

- Gradient boosting applied to decision trees should be tested as an additional algorithm for consideration.


