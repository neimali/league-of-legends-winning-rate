# League of Legends winning rate: Project Overview
+ Created a tool to predict the match result to help League of Legends coaches and players develop strategies
+ Performed EDA to check the relationship between features and matches results and select features for futher analysis and prediction
+ optimized a Logistical Regression model and a XGboost Random Forest model using gridsearchCV to get the best estimator
+ Ultilizing the coefficient and feature importance of trained models to quantify and analyze the influence of each element on match result
+ Provide suggestions according to the analysis

## Resources Used
+ **Package:** Pandas, Numpy, sklearn, matplotlib, seaborn, pickle
+ **Data:**  [Kaggle "League of Legends Diamond Ranked Games (10 min)"](https://www.kaggle.com/datasets/bobbyscience/league-of-legends-diamond-ranked-games-10-min)

## Features(Element)
### Element explaination
+ Ward: An item that players can place on the map to reveal the nearby area. Very useful for map/objectives control.
+ Assist: Awards partial gold and experience points when damage is done to contribute to an enemy's death.
+ Elite Monsters: Monsters with high hp/damage that give a massive bonus (gold/XP/stats) when killed by a team.
+ Dragon: AKA Drake. This powerful neutral monster grants various permanent effects and buffs when when killed by a team.
+ Herald: A monster that spawns on the eigth minute. Grants a buff that allows the user to spawn the Herald for your team to help push towers and lanes.
+ Tower: A structure that blocks the enemy’s path to the base. They take high damage and fire at opponents within a certain radius.
+ Gold: Currency awarded for killing monsters or enemy players as well as for completing objectives.
+ Level: Champion level. Start at 1. Max is 18
+ Minions: Non-player characters (NPCs) that spawn from each team’s base.
+ Jungle Minions: NPC that belong to NO TEAM. They give gold and temporary buffs when killed by players.

### Feature selection

#### some pictures of EDA

![alt text](https://github.com/neimali/league-of-legends-winning-rate/blob/main/pictures/heatmap_select.png?raw=true)
![alt text](https://github.com/neimali/league-of-legends-winning-rate/blob/main/pictures/assists.png?raw=true)

+ **TotalGold, AvgLevel, TotalExperience, GoldDiff, ExperienceDiff, CSPerMin** were firstly removed because they are not independent feature or they are liner combination of other features

+ Remove **redKills, redDeaths, redFirstBlood** due to the high multicolinearity

## Model
I tried two models Logistical regression and XGboost Random Forest. To comprehensively evaluate the models I used marco recall and ROR curve(AUC).

### I tried two models:
+ **Logistical Regression with selected features** : Baseline model recall=0.72, AUC=0.81
+ **Logistical Regression with all features**: recall=0.71, Auc=0.80
+ **XGBoost Random Forest**: recall=0.73, AUC=0.81
