# How to Predict the Winner of a Game in the NCAA March Madness Tournament

![March Madness](images/MarchMadness.jfif)

## Overview
The NCAA March Madness tournament is one of the most exciting yet unpredictable sporting events of the year. Every year there are upsets, "cinderella" teams and busted brackets after only the first round. I wanted to look into seeing if there was a way to better predict the winner of games in the March Madness tournamnet to ultimately create a winning bracket. To do this, I used data that was provided for a Kaggle March Madness coding challenge. For my project, I used data on team's seeds in the tournament, NCCA Tournament compact results and data on teams' rankings at the end of the regular season all in hopes of better predicting the winner. For this problem, I ran a logistic regression, first on seed difference between team matchups and second on ranking difference. Both models performed pretty similarly with about a 70-71% accuracy with predictions. After running the regression, I was able to get probabilities of the winner and loser of each game that I then added to the exisiting dataset so now we can see who is more likely to win a game in a March Madness tournamnet. 


## Business Understanding
The NCAA Division 1 Men's Basketball tournament is one of the most exciting sports tournaments of the year. Millions of people, myself included, tune in with the hopes of creating the "perfect bracket" and each year it always seems to be essentially impossible. Personally, it has always been fascinating how rare it is to get a perfect bracket or anything close to it. This year, Northwestern made the NCAA tournament for only the second time in school history so I was more invested this year when it came to my bracket. I joined a bracket with family and friends and tried my best to look at statistics of teams and put in a little more effort than usual only for, once again, my bracket to fail miserably right after the first round. As a data scientist, I wanted to see if there was a way to be able to better predict the winners in March Madness. Therefore, I took a look at historical college basketball data and wanted to see can we better predict the winner of games in the NCAA March Madness tournamnet.

![Empty Bracket](images/EmptyBracket.jfif)

## Data Understanding

* link to data: [NCAA Data](https://www.kaggle.com/competitions/mens-machine-learning-competition-2018/data)

For my dataset, I used data that was provided for a Kaggle March Madness coding challenge in 2018. There was a lot of data provided for this specific project but I focused on 3 main datasets that I use throughout my project:

* NCAATourneySeeds.csv: includes Season, Seed, TeamID
* NCAATourneyCompactResults.csv: includes Season, DayNum (what day the game was played on), WTeamID, LTeamID, LScore, WLoc (H: Home, A: Away, N: neutral), NumOT (number of overtime periods)
* MasseyOrdinalsFinal.csv: includes Season, RankingDayNum, SystemName, TeamID, OrdinalRank (this was a very large dataset that I could not load the whole file into github. Therefore, using Excel I just kept the data on their final rankings each season so just kept data with the maximum RankingDayNum)

For both the seeding dataset and ranking dataset, I wanted to focusing on the difference between the team matchups. Therefore I created a column called SeedDifference for the difference of the winning and losing teams seed and then I created a column for the ranking dataset called RankDifference that, similarly, was the difference of the ranks of the winning and losing team. 

## Model and Evaluation
For my model, I chose a logistic regression model to predict the winner of the NCCA March Madness tournament. I decided to use a logistic regression in this case because I eventually landed on predicting whether a team would win a game or not based on a certain metric. Iactually did two because I thought the first choice - seed based - didn't give conclusive results but it turned out I was messing up my code and the way I split it for regression. So I ended up running a model of seed difference and then, rank difference. Since it is a regression model, I created a column with a binary variable - 1 for win 0 to not and made that the target variable then run a model on it and regression fit perfectly for this case.  I split the data into X and y - y being the WinLoss column. I did a default train test split and set the random state to 0. For the seeding regression model, it had a 70.9% accuracy on the training set and had a slightly higher accuracy on the test set with 72.33%. I looked also at precision, recall, and confusion matrices just as other ways to visualize the performance. For the ranking regression model, it had similar performance results with a 72.3% accuracy for the training set and 70.06% for the testing set. After building, running and evaluating the model, I decided that a model with an average accuracy of about 71% was a decent model. I wanted use the model to create predictions so I created a column WinPred for probability of the higher ranked team to win and and LossPred for the probability of the higher ranked team to lose (so the lower ranked team to win). I decided to use the ranking model as my final model as it performed a tiny tiny bit better than the seeding model. Below is the dataset that includes the predictions. 

![Predictions Dataset](images/PredictionsData.jpeg)

I also created a simple visual to show the regression model. I did a scatter plot of RankDifference and WinPred.

![Regression Graph](images/RankDifferenceGraph.png)

## Conclusion
This model is a good starting point for predicting the winner of games. This dataset can be used to ultimateley create a mock bracket. There are different bracket similuators and packages out there and with more time, I would be able to put the data and run over many iterations to create a bracket that I would have a little more faith in than one I would come up with on my own.
