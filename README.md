# How to Predict the Winner of a Game in the NCAA March Madness Tournament

![March Madness](MarchMadness.jfif)

## Overview
The NCAA March Madness tournament is one of the most exciting yet unpredictable sporting events of the year. Every year there are upsets, "cinderella" teams and busted brackets after only the first round. I wanted to look into seeing if there was a way to better predict the winner of games in the March Madness tournamnet. To do this, I used data that was provided for a Kaggle March Madness coding challenge. For my project, I used data on team's seeds in the tournament, NCCA Tournament compact results and data on teams' rankings at the end of the regular season all in hopes of better predicting the winner. For this problem, I ran a logistic regression, first on seed difference between team matchups and second on ranking difference. After running the regression, I was able to get probabilities of the winner and loser of each game that I then added to the exisiting dataset so now we can see who is more likely to win. 


## Business Understanding
The NCAA Division 1 Men's Basketball tournament is one of the most exciting sports tournaments of the year. Millions of people, myself included, tune in with the hopes of creating the "perfect bracket" and each year it always seems to be essentially impossible. Personally, it has always been fascinating how rare it is to get a perfect bracket or anything close to it. This year, Northwestern made the NCAA tournament for only the second time in school history so I was more invested this year when it came to my bracket. I joined a bracket with family and friends and tried my best to look at statistics of teams and put in a little more effort than usual only for, once again, my bracket to fail miserably right after the first round. As a data scientist, I wanted to see if there was a way to be able to better predict the winners in March Madness. Therefore, I took a look at historical college basketball data and wanted to see can we better predict the winner of games in the NCAA March Madness tournamnet.


## Data Understanding
For my dataset, I used data that was provided for a Kaggle March Madness coding challenge in 2018. There was a lot of data provided for this specific project but I focused on 3 main datasets that I use throughout my project:

* NCAATourneySeeds.csv: includes Season, Seed, TeamID
* NCAATourneyCompactResults.csv: includes Season, DayNum (what day the game was played on), WTeamID, LTeamID, LScore, WLoc (H: Home, A: Away, N: neutral), NumOT (number of overtime periods)
* MasseyOrdinalsFinal.csv: includes Season, RankingDayNum, SystemName, TeamID, OrdinalRank (this was a very large dataset that I could not load the whole file into github. Therefore, using Excel I just kept the data on their final rankings each season so just kept data with the maximum RankingDayNum)

For both the seeding dataset and ranking dataset, I wanted to focusing on the difference between the team matchups. Therefore I created a column called SeedDifference for the difference of the winning and losing teams seed and then I created a column for the ranking dataset called RankDifference that, similarly, was the difference of the ranks of the winning and losing team. 

## Model and Evaluation
For my model, I chose a logistic regression model to predict the winner of the NCCA March Madness tournament. I decided to use a logistic regression in this case because I eventually landed on predicting whether a team would win a game or not based on a certain metric. Iactually did two because I thought I the first choice - seed based - didn't give conclusive results but it turned out I was messing up my code and the way I split it for regression.  Therefore, I can create a column with a binary variable - 1 for win 0 to not and made that the target variable then run a model on it and regression fit perfectly for this case. 
