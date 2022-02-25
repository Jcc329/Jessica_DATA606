# Finding the Cheat Codes for Game Development
By <a href="https://github.com/Jcc329">Jessica Conroy Styer</a><br>
Data 606, Spring 2022 <br>
Data Science Capstone Project <br>

## Table of Contents

<ul>
  <li><b>Data</b> - The small sample data files for this project</li>
  <ul>
    <li><a href="https://github.com/Jcc329/Jessica_DATA606/blob/main/Data/RawSteamGameData.zip">Raw Data</a> - The xip file with a sample of raw, pre-processed game data on which to replicate methods demonstrated in this project.</li>
    <li><a href="https://github.com/Jcc329/Jessica_DATA606/tree/main/Cleaned_Data">Clean Data</a> - The zip file with a sample of the cleaned game data on which to replicate methods demonstrated in this project.</li>
  </ul>
  <li><b>Notebooks</b> - Project Notebooks</li>
  <ul>
    <li><a href="https://github.com/Jcc329/Jessica_DATA606/blob/main/Notebooks/1.Accessing_Steam_APIs.ipynb">1. Data Acquisition</a></li> - Notebook for accessing the steam APIs and collecting raw data
    <li><a href="https://github.com/Jcc329/Jessica_DATA606/blob/main/Notebooks/2.Steam_Data_Cleaning.ipynb">2. Data Cleaning</a></li> - Notebook for applying basic data cleaning techniques
    <li><a href="https://github.com/Jcc329/Jessica_DATA606/blob/main/Notebooks/3.%20EDA%20with%20Pandas%20Profiling.ipynb">3. Preliminary Exploratory Analysis</a></li> - Notebook for generating a pandas profile widget and exploring the data features
    <li><a href="">4. Topic Modeling and Text EDA</a> - Notebook containing text exploratory analysis </li>
  </ul>
  <li><a href="https://github.com/Jcc329/Jessica_DATA606/blob/main/README.md">README.md</a> - An overview of the project and results</li> 
  <li><a href="https://github.com/Jcc329/Jessica_DATA606/blob/main/Proposal.md">Project Proposal</a> - The .py file containing functions called in the notebooks</li
  <li><b>Supplemental Files</b> - Files containing supporting python functions for this analysis</li>
  <li><b>Report and Presentations</b> - File containing Project Presentations and the Final Report</li>
</ul>

## Introduction

The game industry is an intensely competitive, multi-billion-dollar industry, with tens of thousands of games being released every year. Both large game producers and small indie game developers are competing in this space, and while many games succeed, many more fail. Steam, a video game distribution service, released more than 10,000 games in 2020 alone (Number of Games Released on Steam 2021, n.d.). Needless to say, the industry does not look like it’s slowing down any time soon (Video Game Market Value Worldwide 2015, n.d.). Not only are the number of games produced growing every year, but so are the types of games and the number of players. As more powerful graphics cards and gaming architecture is being developed, as well as a global pandemic to contend with, the uses of gaming are evolving as well, with more and more players turning to games as a social outlet (Global Insights Report - Google for Games, n.d.). In their 2021 Global Insights Report, Google found an increase of 45% in the number of gamers playing new games since the start of the pandemic (Global Insights Report - Google for Games, n.d.). One approach that the report highlighted as successful is a player-first strategy, stating that ‘the best game developers deeply understand their players’ (Global Insights Report - Google for Games, n.d.).  But how does a game developer understand their players? <br>

With so many games and game related metadata available, and so much competition, it seems a small step to use machine learning techniques to try to better understand players and their behavior as well as to predict the success of game concepts before even starting game development. This project aims to solve some of the ambiguity around what game elements lead to high ratings by genre, and how that may have changed as a result of the pandemic. <br>

Sources: <br>
Global Frontier Report—Google for Games. (n.d.). Retrieved February 6, 2022, from https://games.withgoogle.com/reports/<br>
Global Insights Report—Google for Games. (n.d.). Retrieved February 6, 2022, from https://games.withgoogle.com/reports/insightsreport/<br>
Number of games released on Steam 2021. (n.d.). Statista. Retrieved February 6, 2022, from https://www.statista.com/statistics/552623/number-games-released-steam/<br>
Video game market value worldwide 2015. (n.d.). Statista. Retrieved February 6, 2022, from https://www.statista.com/statistics/292056/video-game-market-value-worldwide/

## Research Questions

•	What game characteristics are predictive of a high game rating? <br>
•	Are these characteristics different across different genres of game?<br>
•	Have these characteristics changed as a result of the covid pandemic?<br>
(for example, are multi-player games more likely to have a high game rating than single player due to the increase in gaming as a social activity)

## Data

<b> Data Collection </b><br>

Data for this project came from a total of 4 API calls. The first call was to obtain the complete list of Steam Game IDs https://api.steampowered.com/ISteamApps/GetAppList/v2/. Documentation for this API call can be found at the following URL: https://partner.steamgames.com/doc/webapi/ISteamApps <br>
After retreiving the App IDs I use them to make 3 additional API calls:
    Steam API 1: primary game data
    Steam API 2: Review data (https://partner.steamgames.com/doc/store/getreviews)
    Steamspy API: Supplemental usage and cost data (https://steamspy.com/api.php)
Due to time and space constraints, a random sample of games were selected. The initial data pull was run for 6 hours and resulted in 7,309 games. Raw and Clean versions of that data are available in this repository. 

<a href="https://github.com/Jcc329/Jessica_DATA606/blob/main/Cleaned_Data/CleanSteamGameData%20(1).zip">Cleaned Data</a>
<a href="https://github.com/Jcc329/Jessica_DATA606/blob/main/Raw_data/RawSteamGameData.zip">Raw Data</a>

The descriptive statistics and Pandas Profile can be viewed by running the following notebook: <a href="url">Pandas Profiling of Steam Data</a>

A larger dataset was used for the remainder of this project. This was run for 18 hours and resulted in 18,424 games. This data could not be stored on Github due to a large file size (152 MB unzipped, about 35 MB zipped), but is available upon request. 

Features of interest include:
(This list has been updated based on the finalized fields pulled from the API).
- Game Type ('type')
- Game Name ('name')
- app ID ('steam_appid') 
- Required Age to Play ('required_age') 
- Is the Game Free ('is_free')
- Detailed Game Description ('detailed_description')
- About Game text ('about_the_game') 
- Short Game Description ('short_description')
- Supported languages ('supported_languages' - field will be broken into columns for each language) 
- Developer ('developers') 
- Publisher ('publishers')
- Supported Platforms ('platforms' - will be broken out into columns for each, ex. mac, windows, linux)
- Category Tags ('categories' broken out into columns, ex. Single-Player, PvP, Downloadable Content, etc.)
- Game Genre Tags ('genres' - will be broken into columns, ex. action, RPG, Indie)
- Release Date ('release_date')
- Notes on game content such as age suitability ('content_descriptors')
- Weighted average review score on steam ('Review Score')
- Description of review score ('Review Score Description', ex. Overwhelmingly positive)
- Text from up to 20 top reviews based on upvotes ('Top Reviews by Upvotes')
- Number of positive reviews ('positive')
- Number of negative reviews ('negative')
- Average user scores collected by metacritic ('userscore')
- Range representing the number of people owning a game on steam ('owners')
- Average playtime since March 2009, minutes ('average_forever')
- Average playtime in the last two weeks, minutes ('average_2weeks')
- Median playtime since March 2009, minutes ('median_forever')
- Median playtime in the last two weeks, minutes ('median_2weeks') 
- Game price now ('price') 
- Game price at release ('initialprice') 
- Current game discount in percent ('discount')
- Peak count of concurrent users worldwide in the last day('ccu')
- Game tags on content ('tags')

<b> Exploratory Analysis Results </b>

Pandas Profiling Key Findings:

With so many data fields it is difficult to summarize the findings sucinctly. Therefore, I will focus on key features and findings.

1. My target variables are missing a lot of data:
    Review Score: 74% zeros, <.01% missing
    User Score: 99.9% zeros
    Owners: Categorical with heavy right skew. This can be seen in the figure below, however there is very little missint data.
    Metacritic Score: 96.4% Missing
    
Despite there being so many games with a zero review score (essentially indicating that there were not reviews) there are still 4788 games with scores. That is sufficient to work with for training my machine learning model. I also have the categorical owner's field, which despite being skewed, is a strong target for measuring game success.

<b> Figure 1. Top 10 Bins for Number of People who Own Each Game, range </b>
   <p align="center">
      <img src="https://github.com/Jcc329/Jessica_DATA606/blob/main/Supplemental%20Files/Top%2010%20Owner%20Categories.png" width="350" title="Bar Chart showing the Top 10 bins for people who own each game." alt="The bar chart is heavily skewed to the right, with the majority of games having 0 to 20,000 owners and decreasing from there.">
    
2. Correlation: 
    Most features don't appear to have strong correlations with anything else. 
    Unsuprisingly, the categorical features (things like Action, RPG, etc) are more correlated with eachother, likely because when the data was present it was likely to include multiple features. 
    Additionally amount played was correlated with itself in all it's forms (median, average, forever, last 2 weeks, etc.)
    
    <b> Figure 2. Spearman's Correlation Matrix </b>
   <p align="center">
      <img src="https://github.com/Jcc329/Jessica_DATA606/blob/main/Supplemental%20Files/Variable%20Correlation%20Matrix.png" width="700" title="Spearman's Correlation Matrix" alt="A correlation matrix showing how the features relate to eachother using the Spearman's coefficient. The Figure demonstrates that few of the features have correlate with eachother.">
  </p>

3. Missing Data:
    Several features were missing significant chunks of data. 
    44% of games had no reviews.

4. Text data analyses
    The frequencies of words in the text fields reveal that several stopwords are still a problem. 

5. One duplicate game was identified

<b> Next Steps </b>

Next steps will include: 
- identifying and dropping fields with high numbers of missing data
- performing topic modeling on text in the complete dataset (description and tag text)
- filtering a subset of the data that contains review score and assessing the completeness of that data. 

## Methods:

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

The metric I use to show success of the model will depend on the target variable I choose to attempt to predict. if I end up using a classification via score, I will use accuracy, but if I end up using sales or products sold, I will use root mean squared error (RMSE). <br>

The practical applications of this project include the ability to provide game developers with a clear outline of what players look for in games, as well as some metrics for making business decisions. For example, investing a game that supports multi-player capabilities may be more important to the success of a game than game length. Further, I aim to identify any significant changes in what makes a successful game as a result of the COVID 19 pandemic, and to incorporate those findings into the process of building this model. <br>

In terms of personal goals and outcomes. I hope to gain more practical experience in the use of text analysis techniques and tuning deep learning models. 

