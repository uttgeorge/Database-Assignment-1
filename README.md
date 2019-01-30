# Database Assignment 1
# Abstract
The purpose of this project is to obtain NBA data from internet, clean and audit them, and build a conceptual database based on these information. This database will allow us to search the biography of NBA players from 2017-2018 regular season, whilst reaching their personal performances, salaries, and team performances.  

# Introduction
### Data are from three different sources:
**1.Data Downloaded**\
The raw data is [NBA Players' Salary of Season17-18](https://www.kaggle.com/koki25ando/nba-season1718-salary). It is downloaded directly from Kaggle.com published by [Koki Ando](https://www.kaggle.com/koki25ando). This dataset include players' names, team abbreviations and salaries.\
It is stored in **Data Downloaded/**

**2.Web Scraper**\
The raw data is [2017-2018 NBA Regular Season Stats](https://basketball.realgm.com/nba/stats/2018/Averages/All/points/All/desc/1/Regular_Season). It is scraped from RealGM.com. The code is in **[NBA2017-2018scraper.ipynb](https://github.com/INFO6210-Spring19-02/assignment-1-group-qi-jin-dongyu-zhang/blob/master/Web%20Scraper/NBA2017-2018scraper.ipynb)** file. There are explicit explanations in this file.  This dataset include index, players' names, Teams Abbreviations and 19 attributions of players.\
Both code and csv files are stored in **Web Scraper/**

**3.Api**

# Audit and Clean Data
### 1.Audit 2017-2018 Regular Season Players' Statistics
The specific procedures are showed in [Audit 2017-2018 Regular Season Players' Stats Data.ipynb](https://github.com/INFO6210-Spring19-02/assignment-1-group-qi-jin-dongyu-zhang/blob/master/Audit%20-%20Clean/Audit%202017-2018%20Regular%20Season%20Players'%20Stats%20Data.ipynb).\
This is scraped from the RealGM.com, and in a very good condition.  \
There are no null value, and data types of each column are correct. We round  ‘FG%’, ‘3P%’ and ‘FT%’ to 3 decimals, because some of these values have 9 decimals.\
The number of players in this dataset match the statistics form NBA.com & ESPN.com.\
When analyzing the distribution of percentage of field goal per game, it shows kind of normal distribution which consist with the common sense.\
There are 77 players in the salary table, but not in this one. That is because of injuries, and this result also match the real life data.\
The final file saved as [2017-2018 Regular Season Players'Stats Revised.csv](https://github.com/INFO6210-Spring19-02/assignment-1-group-qi-jin-dongyu-zhang/blob/master/Audit%20-%20Clean/New%20Data/2017-2018%20Regular%20Season%20Players'Stats%20Revised.csv) in Audit - Clean/New Data.

### 2. Audit NBA Salary
The specific procedures are showed in [Audit Salary.ipynb](https://github.com/uttgeorge/Database-Assignment-1/blob/master/Audit%20-%20Clean/Audit%20Salary%20.ipynb)\
This dataset is made from two different csv files, one is  2017-2018 NBA Regular Season Players' Salary, and another one is 2017-2018 NBA Regular Season All Star Players List. Because all star players list does not contain many useful information, so we choose to merge it with salary table. What we do is to create a new column in NBA Regular Season Players' Salary table called ‘AllStar’ to show whether each player in salary table is last regular season all star player. Also we change the head to match with statistics file.\
This dataset has no null, and all data types are correct.\
We plot the distribution of salaries. This chart shows a great income gap between NBA players, which meat the reality in real world. We also check the salaries of all star players, and they are correct comparing with NBA.com & ESPN.com & Wikipedia. \
The final file saved as  [NBA_salary.csv](https://github.com/uttgeorge/Database-Assignment-1/blob/master/Audit%20-%20Clean/New%20Data/NBA_salary.csv) in Audit - Clean/New Data.


Audit validity/ accuracy ( You must  reformat the data to fit your database schema i.e. Use python to check whether there are any null or duplicates and delete the row with those values, describe about the same in the report.)
Audit completeness (Check if the given data makes sense for your assignment i.e check with real world, describe about the same in the report )
- Audit consistency/uniformity (Compare your dataset with another dataset from a similar domain and note whether the values in your dataset covers the entire possible range when compared to the other dataset or is your dataset limited to a certain columns/range of values, for example : Data of score contains no invalid value, in another word, there is no negative scores, describe about the same in the report.)

# Build Conceptual Model
The conceptual schema are stored in [ConceptualModel_NBA.pdf](https://github.com/INFO6210-Spring19-02/assignment-1-group-qi-jin-dongyu-zhang/blob/master/ConceptualModel_NBA.pdf)\
What we build is 

# conclusion and inference

# citations and reference

# text license ( Creative Commons) and percentage contribution in assignment



