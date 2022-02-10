# Finding the Cheat Codes for Game Development
Jessica Conroy <br>
Data 606, Spring 2022 <br>
Data Science Capstone Project <br>

## Project Proposal

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

The data I would like to focus on comes from the game distributor Steam. There are several methods for accessing data from steam, using both Steam’s native API (https://partner.steamgames.com/doc/webapi_overview) or other APIs built to access steam data more easily (SteamSpy for example). I plan to experiment a bit to identify which method provides access to the most robust data (more games) as well as the features I’m interested in, and combining across datasets. <br>
Features of interest inclue:

-	Metacritic rating of the game (target)
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
-	Reviews
-	Game tags
-	Gaming platform
-	When it was released
-	Purchase counts/How many people own the game
-	Potentially image data for the thumbnail (speaks to art style)

This list may change as I explore the available features via the API.<br>
My unit of analysis is at the game level. I am hoping to analyze at least 10,000 games, with a equal sampling across the last 5 years (providing a pre-covid and post-covid time frame)

## Methods:

<i> What kinds of techniques/models do you plan to use (for example, clustering, NLP, ARIMA, etc.)?<br>
How do you plan to develop/apply ML and how you evaluate/compare the performance of the models?<br>
What outcomes do you intend to achieve (better understanding of problems, tools to help solve problems, predictive analytics with practical applications, etc)? </i><br>

This project will include a combination of Natural Language Processing (NLP), and deep learning techniques. I aim to both identify the characteristics of successful games by genre as well as create a model for predicting whether a new game will receive high ratings.  <br>

I plan to use NLP for the analysis of description and review text data, clustering, and identifying common features that can then contribute to a machine learning model for predicting if a game will be successful or not. <br>

Provided the time exists, I would like to combine this with an analysis of the artwork (thumbnail images) associated with the games, to see if art style can predict higher ratings, or higher rates of ownership (judging a book by its cover, so-to-speak).<br>

The practical applications of this project include the ability to provide game developers with a clear outline of what players look for in games, as well as some metrics for making business decisions. For example, investing heavily in artwork may lead to more sales, since gamers may be drawn to try out prettier games.
