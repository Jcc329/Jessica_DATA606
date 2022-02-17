# Finding the Cheat Codes for Game Development
Jessica Conroy <br>
Data 606, Spring 2022 <br>
Data Science Capstone Project <br>

## Motivation:

<i> What is your issue of interest (provide sufficient background information)?
Why is this issue important to you and/or to others? </i><br>

The game industry is an intensely competitive, multi-billion-dollar industry, with tens of thousands of games being released every year. Both large game producers and small indie game developers are competing in this space, and while many games succeed, many more fail. Steam, a video game distribution service, released more than 10,000 games in 2020 alone (Number of Games Released on Steam 2021, n.d.). Needless to say, the industry does not look like it’s slowing down any time soon (Video Game Market Value Worldwide 2015, n.d.). Not only are the number of games produced growing every year, but so are the types of games and the number of players. As more powerful graphics cards and gaming architecture is being developed, as well as a global pandemic to contend with, the uses of gaming are evolving as well, with more and more players turning to games as a social outlet (Global Insights Report - Google for Games, n.d.). In their 2021 Global Insights Report, Google found an increase of 45% in the number of gamers playing new games since the start of the pandemic (Global Insights Report - Google for Games, n.d.). One approach that the report highlighted as successful is a player-first strategy, stating that ‘the best game developers deeply understand their players’ (Global Insights Report - Google for Games, n.d.).  But how does a game developer understand their players? <br>

With so many games and game related metadata available, and so much competition, it seems a small step to use machine learning techniques to try to better understand players and their behavior as well as to predict the success of game concepts before even starting game development. This project aims to solve some of the ambiguity around what game elements lead to high ratings by genre, and how that may have changed as a result of the pandemic. <br>

Sources: <br>
Global Frontier Report—Google for Games. (n.d.). Retrieved February 6, 2022, from https://games.withgoogle.com/reports/<br>
Global Insights Report—Google for Games. (n.d.). Retrieved February 6, 2022, from https://games.withgoogle.com/reports/insightsreport/<br>
Number of games released on Steam 2021. (n.d.). Statista. Retrieved February 6, 2022, from https://www.statista.com/statistics/552623/number-games-released-steam/<br>
Video game market value worldwide 2015. (n.d.). Statista. Retrieved February 6, 2022, from https://www.statista.com/statistics/292056/video-game-market-value-worldwide/

## Research Questions

<i> What questions do you have in mind and would like to answer? </i><br>

•	What game characteristics are predictive of a high game rating? <br>
•	Are these characteristics different across different genres of game?<br>
•	Have these characteristics changed as a result of the covid pandemic?<br>
(for example, are multi-player games more likely to have a high game rating than single player due to the increase in gaming as a social activity)

## Data

<i> Where do you get the data to analyze and help answer your questions (creditability of source, quality of data, size of data, attributes of data. etc.)?
What will be your unit of analysis (for example, patient, organization, or country)? Roughly how many units (observations) do you expect to analyze?
What variables/measures do you plan to use in your analysis (variables should be tied to the questions in #3)? </i><br>

The data I would like to focus on comes from the game distributor Steam. There are several methods for accessing data from steam, using both Steam’s native API (https://partner.steamgames.com/doc/webapi_overview) or other APIs built to access steam data more easily (SteamSpy for example). Additionally, I plan to use steamapis.com to get market data on game sales (units/games sold at what price). I plan to experiment a bit to identify which method provides access to the most robust data (more games) as well as the features I’m interested in, and combining across datasets. <br>

Features of interest include:

-	Metacritic rating of the game (target)
-	Review Score
-	Name
-	App ID
-	Detailed description 
-	Categories (contains information like whether or not the game is multiplayer or single player, PvP, has split screen, etc.)
-	Whether or not it’s a demo, beta, etc.
-	Required age to play
-	Genre
-	Developer
-	Average/median Playtime
-	Price
-	Reviews (Top 20 per game sorted on Up Votes, decending) 
-	Game tags
-	Gaming platform
-	When it was released
-	Purchase counts/How many people own the game
-	How many games where sold at what prices
-	Potentially image data for the thumbnail

#### Target Variable (s)
The metacritic score ranges from 0-100 with higher scores representing better reviews. The score itself is calculated using a weighted average of published critic reviews. Details on how this is calculated can be found here (https://www.metacritic.com/about-metascores)

There is also an aggregate review score based on weighted steam user scores associated with review text. I will collect this data as well. During exploritory analysis, I will compare how metacritic scores and user scores correlate to success metrics like how many times the game was purchased, how much time is spent playing (median playtime), and game sales. I will then be able to determine which is a better metric for identifying characteristics that lead to practical success in the game industry. 

This list may change as I explore the available features via the API.<br>
My unit of analysis is at the game level. I am hoping to analyze at least 10,000 games split between two years, 2019 and 2021 to represent the before covid time period and the during covid time period. 

## Methods:
<i> What kinds of techniques/models do you plan to use (for example, clustering, NLP, ARIMA, etc.)?</i><br>

This project will include a combination of Natural Language Processing (NLP), and deep learning techniques. I aim to both identify the characteristics of successful games by genre as well as create a model for predicting whether a new game will receive high ratings.  <br>

<b> Text Analysis and Natural Language Processing </b>

Initial exploratory data analysis will include several natural language processing techniques applied to the text data fields (Description and Review data) <br>
Review data has an associated sentiment and user score already, so I will be able to use that to evaluate the relationship between user reviews and metacritic scores. The core of the natural language processing will be in the form of keyword extraction and topic modeling of the text, both descriptions and reviews, to identify clusters of themes and in the text and how they relate to metacritic/user scores. The goal of this analysis is to identify features described in the text that are related to more successful games. <br>
Methods for topic modeling will include testing a few different models against eachother to identify the best performing model for this dataset. I will vectorize the text using TF-IDF unless I’m able to find a good model for transfer learning to apply to this dataset (I have used BERT in the past to vectorize articles, but it is ill suited for raw review data due to the training data it’s based on). I will then experiment with the use of Latent Dirichlet Allocation (LDA) and Non-negative Matrix Factorization (NMF) for performing the topic modeling. LDA is a generative probabilistic model for identifying topics in a text copora, while NMF factorizes the document term matrix into two smaller matrices which contain weights and variables for each topic in the corpus (Blei et al., 2003; Lee & Seung, 1999). I expect that NMF will be the better performer, based on both personal experience and the work of Carbonetto, et al. (2021). <br>

Once topic modeling is complete, I can visualize and cluster those topic vectors using some dimensionality reduction and DBSCAN. Then I’ll be able to look at aggregate success measures for each cluster (such as user and metacritic scores, sales, and purchase counts) in order to identify features that relate to higher success. Further, I can do this process for both the pre- and during-COVID time frames in order to identify any potential impact that the pandemic has had on gamer behaviors and what characteristics make a game successful. The result will inform whether or not I train my machine learning model on all the collected data or on only data collected from a time frame after the pandemic began. <br>

Blei, D. M., Ng, A. Y., & Jordan, M. I. (2003). Latent Dirichlet Allocation. Journal of Machine Learning Research, 3(Jan), 993–1022. <br>

Carbonetto, P., Sarkar, A., Wang, Z., & Stephens, M. (2021). Non-negative matrix factorization algorithms greatly improve topic model fits. https://arxiv.org/abs/2105.13440v2 <br>

Lee, D. D., & Seung, H. S. (1999). Learning the parts of objects by non-negative matrix factorization. Nature, 401(6755), 788–791. https://doi.org/10.1038/44565 <br>

<b> Machine Learning Techniques </b>

For the machine learning portion of the project the goal is to build a model that, given characteristics of a game, will predict the success metric of that game. The specific target metric is yet to be decided as are the methods used to build the predictive model. There are several potential models I could use to predict an outcome. I will likely attempt using a classic neural network (multi-layer perceptron) as my primary method, but test against other models to make sure a simpler model wouldn’t perform better.   
Additionally if I do end up having time to work with the image thumbnails for each game, I would like to use the methods described in the link below, to convert the image data into color palates, which can then be added to the model discussed above.  Future work might entail clustering images and then building a CNN to identify if image style can predict success of a game, but this is currently outside the scope of a single semester capstone. <br>

<i>How do you plan to develop/apply ML and how you evaluate/compare the performance of the models? </i><br>

The metric I use to show success of the model will depend on the target variable I choose to attempt to predict. if I end up using a classification via score, I will use accuracy, but if I end up using sales or products sold, I will use root mean squared error (RMSE). <br>

<i> What outcomes do you intend to achieve (better understanding of problems, tools to help solve problems, predictive analytics with practical applications, etc)?  </i><br>

The practical applications of this project include the ability to provide game developers with a clear outline of what players look for in games, as well as some metrics for making business decisions. For example, investing a game that supports multi-player capabilities may be more important to the success of a game than game length. Further, I aim to identify any significant changes in what makes a successful game as a result of the COVID 19 pandemic, and to incorporate those findings into the process of building this model. <br>

In terms of personal goals and outcomes. I hope to gain more practical experience in the use of text analysis techniques and tuning deep learning models. 

