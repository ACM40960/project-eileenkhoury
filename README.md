# Monte Carlo Simulations of NBA Match-Ups
<p align="center">
<img src="https://user-images.githubusercontent.com/110261952/182031204-acd0016e-466a-4931-ae8e-be0f6aeac74a.png" />
</p>
  <br />
 Simulating NBA matchups with Monte Carlo to predict odds and predicted winning team. 

## Table of Contents
- [**Introduction**](https://github.com/ACM40960/project-eileenkhoury#introduction)
- [**Getting Started**](https://github.com/ACM40960/project-eileenkhoury#getting-started)
  - [Software Installation](https://github.com/ACM40960/project-eileenkhoury#software-installation)
  - [Data Collection](https://github.com/ACM40960/project-eileenkhoury#data-collection)
- [**Included Code**](https://github.com/ACM40960/project-eileenkhoury#included-code)
  - [Models](https://github.com/ACM40960/project-eileenkhoury#models)
  - [Evaluation and Accuracy](https://github.com/ACM40960/project-eileenkhoury#evaluation-and-accuracy)
- [**Miscellaneous**](https://github.com/ACM40960/project-eileenkhoury/blob/main/README.md#miscellaneous) 

## Introduction
 This project aims to empircally model the odds a team winning in a specific team match up in the NBA using R and R studio. The model is then extended to predict which team will win the proposed match up. This model is in the spirit of academic curiousity rather than a direct monetary application. 
<br />
<br />
The four main models included use team and players statistics to propose a mehtodology of simualting NBA mactchup results. The first model, considered the 'simple model', looks only at a team's scored points distribution in a particualre season to replicate game results. The second model utlizes the 'Four Factors' technique, initally proposed by Dean Oliver, aggregated by team to simualte mactchup results. The third model builds on the second, but allows the user to pick 8 players from each team to pick the matchup to build the simualtion off of, and for this reason the statistics feeding the four factors are on a player aggregated level. The final fourth model automates the third model by selecting the top 8 players, by average minutes played in each game during the 2019, 2020 and 2021 seasos, for each team. 
<br />
The last three models have a variable 'Home Advantage' factor, in which different values for modeling this advantage are plugged in. The accuracy of these home advantge values are assesed in model validation files. The first model is built on scoring distributions based on the home team's scoring distribution when home and away, as well as for the away team; essentailly this imbeds the home advantge in the model considering the differnt point distributions for each team in the matchup. 
<br />
<br />
This README file will guide interested parties in reproducing the results of the paper included in the repositry, from collecting the data set to running the included R scripts. 
 
 ## Getting Started
 
 ### Software Installation
R                          |  RStudio
:-------------------------:|:-------------------------:
![R_resize](https://user-images.githubusercontent.com/110261952/182035430-c2ca75d5-0553-41cc-812b-ff2ee51146c3.png) |![RStudio_resize](https://user-images.githubusercontent.com/110261952/182035438-912e4851-2e4e-43f6-b574-170cb6d49328.png)

The R markdown files were created using **RStudio 2022.02.3+492** using the **R 4.2.1** as a sub-skeleton, as you must download R before you can download RStudio. RStudio is the integrated development envoronment, IDE, of R which allows a more user friendly interface to code, test and debug. It is critical you download **R** before you download **R Studio**. 

Your computer complier (UNIX, Windows, MacOS, etc) dictates which version of **R** and **R Studio** you will download. You can follow this [tutorial](https://www.projectpro.io/recipes/download-and-install-r-and-rstudio) for a step by step guide on how to dowload R and R studio is accordance with the specfifications of your computer. 

You can download [R](https://www.r-project.org/) here and [RStudio](https://www.rstudio.com/products/rstudio/download/). 

 ### Data Collection
 This project utilizes four data sets, sourced  from [kaggle](https://www.kaggle.com/), [Basketball Reference](https://www.basketball-reference.com/), and 
 [NBA.com](https://www.basketball-reference.com/). They are listed data sets are located in the "Data" folder:
 - games_details.csv 
 - games.csv 
 
These two data sets were taken from a [kaggle data repository](https://www.kaggle.com/datasets/nathanlauga/nba-games), in which Nathan uses a python web scraper on the [NBA Stats](https://www.nba.com/stats/) website to collect player level and team level statistics for each NBA game from the 2004 season to the 2021 season. Nathan includes several datasets but we are only interested in downloading 'games.csv' and 'games_details.csv'. You can select the data files of interest by left clicking on the file of interest (shown in the Green and Red boxes below), and then right clicking the download button circled in blue. 
![kaggle instructions_resize](https://user-images.githubusercontent.com/110261952/182036976-53aa30a7-e147-45db-a3be-665dd62eecd4.png)
<br />
<br />
- Team Totals.csv

This data set was taken from a [kaggle data repository](https://www.kaggle.com/datasets/sumitrodatta/nba-aba-baa-stats?select=Team+Totals.csv), in which Sumitro used the IMPORTHTML function from Google Sheets repeatedly on [Basketball Reference](https://www.basketball-reference.com/). Nathan includes several datasets but we are only interested in downloading 'Total_Teams.csv'. You can select the data files of interest by left clicking on the file of interest (shown in the Green and Red boxes below), and then right clicking the download button circled in blue. 

![kaggle_2_resize](https://user-images.githubusercontent.com/110261952/182037287-0e7c9e16-d12b-44c5-b296-ed6884847766.png)
<br />
<br />
- 2021_2022 Team Box Scores.csv

This data set was tediously created by repeated copy and pasting the boxscores of every game from the [NBA Stats boxscore listings](https://www.nba.com/stats/teams/boxscores/?sort=gdate&dir=1&Season=2021-22&SeasonType=Regular%20Season) for the 2021/2022 season. The offial NBA stats site suspended  dowloading  official box score files some time after the regular 2021/2022 season wrapped, and after  ma ny failed attempts at webscraping the data I resorted to old and faithful. I performed many validation checks in Excel so ensure no errors were made when copy adn pasting. 
![boxscore_resize](https://user-images.githubusercontent.com/110261952/182038020-95646365-a2f0-45a2-a56b-f6f6259f2d59.png)


 ## Included Code
There are several **.Rmd** files included in the 'Code' folder. The first folder, 'Models', includes the models and a data exploration, while 'Accuracy Evaluation' includes the files that test and evaluate said models. 
 ### Models
 
 - **EDA.Rmd**

This file performs an intial data exploration as it pertains to points scored by team, players and positions. Statistical factors and point distributions of 'home teams'  opposed to 'away teams' are compared to determine validity of the home team advantage. Season over season scoring trends are also included. 
<br />
<br />
 - **Simple Model.Rmd**
 
This file has the code for the most basic MC simulation- looking at just points scored distributions of the two teams matched up. There is also an exploration and justification of a tie breaker included.
<br />
<br />
 - **Team Factor Model.Rmd**

This file has the code for a team level MC simulation using [Dean Oliver's Four Factor's](http://www.basketballonpaper.com/index.html) approach. There is an exploration and justification of a tie breaker, as well as home court advantage. The wieght of the factors are evaluated to create similliar model with different justified weights for each factor. 
<br />
<br />
 - **Player Factor Model.Rmd**
 
 This file has the code for a player level MC simulation using [Dean Oliver's Four Factor's](http://www.basketballonpaper.com/index.html) approach. There is an exploration and justification of a tie breaker, as well as home court advantage. The wieght of the factors are evaluated to create similliar model with different justified weights for each factor. There are two approaches in this model- one in which the user can enter manually 8 players on the home and away team, and the other which automatically chooses the players for each team according to those with the highest average game play, in minutes, across the 2019, 2020 and 2021 season. 
 
 ### Evaluation and Accuracy
 The .Rmd files in this subfolder evaluate the accuracy of the proposed models above using training and testing data. 
 - **Simple_Model_Accuracy.Rmd**
 
 This file performs an accuracy test with training data and testing data to get an overall accuracy rate of the  model included in the **Simple Model.Rmd** file. We perform two types of testing, one randomly selcting the matchups for training and testing, and the other using the first 80% of matches to train, while testing on the last 20%. 
 <br />
<br />
- **Team_Factor_Accuracy.Rmd**
 
This file performs an accuracy test with training data and testing data to get an overall accuracy rate of the  model included in the **Team Factor Model.Rmd** file. We perform two types of testing, one randomly selcting the matchups for training and testing, and the other using the first 80% of matches to train, while testing on the last 20% . Within those two types of testing there is also variation among the factor wieghts and home court advatage values. Morover, we pass the model through a sequence of home advantage factors to see which value is optimal and again test the accuracy again using the standard and adjusted weights. There are many accuracy while() loops in the files, so it takes quite a bit of time to run. 
 <br />
<br />
- **Player_Factor_Accuracy.Rmd**
 
This file performs an accuracy test with training data and testing data to get an overall accuracy rate of the  model included in the **Player Factor Model.Rmd** file. We perform two types of testing, one randomly selcting the matchups for training and testing, and the other using the first 80% of matches to train, while testing on the last 20% . Within those two types of testing there is also variation among the factor wieghts and home court advatage values. Morover, we pass the model through a sequence of home advantage factors to see which value is optimal and again test the accuracy again using the standard and adjusted weights. There are many accuracy while() loops in the files, so it takes quite a bit of time to run. 
 <br />
<br />

## Miscellaneous

Included in this projecct's repository is a a pdf of my final paper and a 'Graphics' folder, which includes all graphics, mostly generated from the .Rmd files, used in the paper. 
