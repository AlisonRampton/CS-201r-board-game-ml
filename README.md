# CS-201r-board-game-ml

## Problem Description

For many, being able to accurately predict how well a new item will be received by the public is a necessity in being able to create valuable products. For this project, our group is concerned with creating a machine learning model capable of accurately predicting the review rating (a score from 0 to 10) based on board game data from BoardGameGeeks. The project seeks to answer questions such as: if you are shown a board game that you have never seen before, how likely are you to enjoy that game? What rating will you most probably give it? What rating is the game likely to receive overall from all BoardGameGeek users? Answering these little questions can have a big impact in the success of any board game. Depending on a number of factors, such as how hard the data is to gather and how accurate the machine is, we will then proceed to implement a user personalized recommendation algorithm, similar to Netflix, but on a slightly smaller scope. This would be in addition to our machine learning model being able to predict an overall rating for a particular board game.

## Gathering Data

We plan to create a model trained on data that is gathered from the BoardGameGeeks API (https://boardgamegeek.com/wiki/page/BGG_XML_API2). Using this API, we can obtain information on all the board games currently stored within BoardGameGeek’s database. This includes a lot of feature information about these board games as well as an overall rating between 0 and 10 that comes from the average review score left by users. Because score ratings can be fractional numbers, we may end up rounding these values to prevent having too many output classes. Although there is a lot of data returned from the API, our team is planning on using data that would be most helpful for our classifier.

## Data Description

Board game instance features:
-ID (identifier)
-Name (identifier)
-Year Published (discrete)
-Min Players (discrete)
-Max Players (discrete)
-Playing Time (continuous)
-Average Rating (continuous)
-Bayes Average Rating (continuous)
-Average Complexity/Weight (continuous)

Example API response: https://api.geekdo.com/xmlapi/boardgame/822?stats=1
Also available through the API are attributes like game mechanics (nominal), genre (nominal), and recommended minimum age (discrete).
User rating instance features:
-Username (identifier)
-Game Rated ID (identifier)
-Rating Given (discrete)
-Average Rating (continuous)

Example API response: https://api.geekdo.com/xmlapi/collection/ripplegylf

If necessary, we can also get user specific attributes like whether or not they own the game rated, their country / state of residence, when they joined the site, and when they last updated their profile. These attributes are dependent on user discretion, so they are not universally available across all users.

## Models

Initially, we believe that using a multilayer perceptron (MLP) will provide us with a robust and accurate model for predicting board game ratings. Due to the high dimensionality of the data that we are working with, the data is not going to be linearly separable. Because of this, we need to use a perceptron with multiple layers in and some nonlinear activation function to properly calibrate its weights using gradient descent. This activation function will most likely be a sigmoid activation function, but we are open to experimenting to see if another function will provide a higher test accuracy and minimize the model’s error.
We have also considered implementing a k-nearest neighbors model (KNN) in order to predict a board game’s rating. This type of model lends itself well to this type of data classification, especially in the context of a recommendation algorithm because it will be attempting to group users into categories or clusters based on some criteria. In this case, it could place users into groups depending on the genre of boardgame to which they have given the highest ratings.
Due to overfitting issues and the immense number of features that our data instances contain, we have decided to avoid using any sort of decision trees, at least initially. Decisions trees would most likely prove too large and cumbersome to work with efficiently.

## Future Plans

Using a group discord chat as well as a shared code repository, we plan on continuing to work as a group to gather data, train different learning models, and test those models to identify one that achieves our accuracy standards. We are also going to meet together in person before our group oral presentation in order to discuss and plan how we are going to share our findings with the rest of the class. This way, we will be able to most effectively work together to finish the project and produce a machine learning model capable of accurately classifying a board game’s rating.

Data in Kaggle_data from https://www.kaggle.com/datasets/threnjen/board-games-database-from-boardgamegeek/data
