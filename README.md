# Monte Carlo Simulations of NBA Match-Ups
<p align="center">
<img src="https://user-images.githubusercontent.com/110261952/182031204-acd0016e-466a-4931-ae8e-be0f6aeac74a.png" />
</p>
  <br />
 Simulating NBA matchups with Monte Carlo to predict odds and predicted winning team. 

## Table of Contents
- [**Introduction**](https://github.com/ACM40960/project-eileenkhoury#introduction)
- [**Getting Started**](https://github.com/ACM40960/project-eileenkhoury#getting-started)
  - [Software Installation](https://github.com/ACM40960/project-eileenkhouryt#software-installation)
  - [Data Collection](https://github.com/ACM40960/project-eileenkhouryt#data-collection)
- [**Included Code**](https://github.com/ACM40960/project-eileenkhouryt#included-code)
  - [R/R Studio](https://github.com/ACM40960/project-eileenkhouryt#r/r-studio)

## Introduction
 This project aims to empircally model the odds a team winning in a specific team match up in the NBA using R and R studio. The model is then extended to predict which team will win the proposed match up. This model is in the spirit of academic curiousity rather than a direct monetary application. 
<br />
<br />
The four models included use team and players statistics to propose a mehtodology of simualting NBA mactchup results. The first model, considered the 'simple model', looks only at a team's scored points distribution in a particualre season to replicate game results. The second model utlizes the 'Four Factors' technique, initally proposed by Dean Oliver, aggregated by team to simualte mactchup results. The third model builds on the second, but allows the user to pick 8 players from each team to pick the matchup to build the simualtion off of, and for this reason the statistics feeding the four factors are on a player aggregated level. The final fourth model automates the third model by selecting the top 8 players, by average minutes played in each game during the 2019, 2020 and 2021 seasos, for each team. 
<br />
<br />
This README file will guide interested parties in reproducing the results of the paper included in the repositry, from collecting the data set to running the included R scripts. 
 
 ## Getting Started
 
 ### R/R Studio
R                          |  RStudio
:-------------------------:|:-------------------------:
![R_resize](https://user-images.githubusercontent.com/110261952/182035430-c2ca75d5-0553-41cc-812b-ff2ee51146c3.png) |![RStudio_resize](https://user-images.githubusercontent.com/110261952/182035438-912e4851-2e4e-43f6-b574-170cb6d49328.png)

The R markdown files were created using **RStudio 2022.02.3+492** using the **R 4.2.1** as a sub-skeleton, as you must download R before you can download RStudio. RStudio is the integrated development envoronment, IDE, of R which allows a more user friendly interface to code, test and debug. It is critical you download **R** before you download **R Studio**. 

Your computer complier (UNIX, Windows, MacOS, etc) dictates which version of **R** and **R Studio** you will download. You can follow this [tutorial](https://www.projectpro.io/recipes/download-and-install-r-and-rstudio) for a step by step guide on how to dowload R and R studio is accordance with the specfifications of your computer. 

You can download [R](https://www.r-project.org/) here and [RStudio](https://www.rstudio.com/products/rstudio/download/). 

 
