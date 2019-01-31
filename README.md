# Database Assignment 1
# Abstract
The purpose of this project is to obtain NBA data from internet, clean and audit them, and build a conceptual database based on these information. This database will allow us to search the biography of NBA players from 2017-2018 regular season, also reaching their personal performances, salaries, and team performances.  

# Introduction
### Data were extracted by 3 different approaches:
**1.Data Downloaded**\
The raw data is [NBA Players' Salary of Season17-18](https://www.kaggle.com/koki25ando/nba-season1718-salary). It is downloaded directly from Kaggle.com published by [Koki Ando](https://www.kaggle.com/koki25ando). This dataset include players' names, team abbreviations and salaries.\
It is stored in **Data Downloaded/**

**2.Web Scraper**\
The raw data is [2017-2018 NBA Regular Season Stats](https://basketball.realgm.com/nba/stats/2018/Averages/All/points/All/desc/1/Regular_Season). It is scraped from RealGM.com. The code is in **[NBA2017-2018scraper.ipynb](https://github.com/uttgeorge/Database-Assignment-1/blob/master/Web%20Scraper/NBA2017-2018scraper.ipynb)** file. There are explicit explanations in this file.  This dataset include index, players' names, Teams Abbreviations and 19 attributions of players.\
Both code and csv files are stored in **Web Scraper/**

**3.Web API**\
The API we used were from FantasyData.
[All-Stars](https://developer.fantasydata.com/docs/services/584f728a35491a16a4720f49/operations/5a70c9a135491a0ab00a814f) 
[Player Details](https://developer.fantasydata.com/docs/services/584f728a35491a16a4720f49/operations/584f728a35491a0d440a48e6) 
[Teams Stats](https://developer.fantasydata.com/docs/services/584f728a35491a16a4720f49/operations/584f728a35491a0d440a48f7) \
All-Stars includes attributes: Name, PlayerID, Position, Team(East/West),TeamID\
Player Details inludes attributes: Name, Team, Height, Weight, College, Birth City...\
Teams Stats includes attributes: Team, Points, Field Goal%, Assists, Rebounds...\
We used this API to get 3 these 3 datasets. Both code and csv files are stored in  **Api/**

# Data Clean and Audit
### 1.Audit 2017-2018 Regular Season Players' Statistics
The specific procedures are showed in [Audit 2017-2018 Regular Season Players' Stats Data.ipynb](https://github.com/uttgeorge/Database-Assignment-1/blob/master/Audit%20-%20Clean/Audit%202017-2018%20Regular%20Season%20Players'%20Stats%20Data.ipynb).\
This is scraped from the RealGM.com, and in a very good condition.  \
There are no null value, and data types of each column are correct. We round  ‘FG%’, ‘3P%’ and ‘FT%’ to 3 decimals, because some of these values have 9 decimals.\
The number of players in this dataset match the statistics form NBA.com & ESPN.com.\
When analyzing the distribution of percentage of field goal per game, it shows kind of normal distribution which consist with the common sense.\
There are 77 players in the salary table, but not in this one. That is because of injuries, and this result also match the real life data.\
The final file saved as [2017-2018 Regular Season Players'Stats Revised.csv](https://github.com/uttgeorge/Database-Assignment-1/blob/master/Audit%20-%20Clean/New%20Data/2017-2018%20Regular%20Season%20Players'Stats%20Revised.csv) in **Audit-Clean/New Data**.

### 2. Audited NBA Salary
The specific procedures are showed in [Audit Salary.ipynb](https://github.com/uttgeorge/Database-Assignment-1/blob/master/Audit%20-%20Clean/Audit%20Salary%20.ipynb)\
This dataset is made from two different csv files, one is  2017-2018 NBA Regular Season Players' Salary, and another one is 2017-2018 NBA Regular Season All Star Players List. Because all star players list does not contain many useful information, so we choose to merge it with salary table. What we do is to create a new column in NBA Regular Season Players' Salary table called ‘AllStar’ to show whether each player in salary table is last regular season all star player. Also we change the head to match with statistics file.\
This dataset has no null, and all data types are correct.\
We plot the distribution of salaries. This chart shows a great income gap between NBA players, which meat the reality in real world. We also check the salaries of all star players, and they are correct comparing with NBA.com & ESPN.com & Wikipedia. \
The final file saved as  [NBA_salary.csv](https://github.com/uttgeorge/Database-Assignment-1/blob/master/Audit%20-%20Clean/New%20Data/NBA_salary.csv) in **Audit-Clean/New Data**.

### 3. Audited Regular Season Teams' Stats
The specific procedures are showed in [NewTeamStats.ipynb](https://github.com/uttgeorge/Database-Assignment-1/blob/master/Audit%20-%20Clean/NewTeamStats.ipynb)
This was obtained by using FantasyData API and saved json data to a csv file.
The raw data set was not in good condition because it had many missing values in a few columns.
We don’t need all attributes because we only focus on the basic stats values of teams that match the stats values of players in another players’ stats dataset. Here described our steps in general:
1.	Dropped the columns we didn’t need such as TeamID, AssistPercentage, FantasyPoints and column's which were empty
2.	Ensured that we didn’t have missing values in the remaining columns to make this dataset complete
3.	Revised a few columns’ name and (Team Abbreviation) to make it more readbale and format more consistent
4.	Changed the sequence of columns to make the dataset more readable and valid in structure that resembled the dataset in nba.com
5.	Checked the range of all numerical values to ensure there was no extreme outliers that didn’t make sense, also plotting histogram/boxplots to check the main attributes Points and Field Goal%

The final file was saved as [NewTeamStats.csv](https://github.com/uttgeorge/Database-Assignment-1/blob/master/Audit%20-%20Clean/New%20Data/NewTeamStats.csv) in **Audit-Clean/New Data**
### 4. Audited Players Details
The specific procedures are showed in [NewPlayerDetails.ipynb](https://github.com/uttgeorge/Database-Assignment-1/blob/master/Audit%20-%20Clean/NewPlayerDetails.ipynb)
This was obtained by using FantasyData API and saved json data to a csv file.
The raw data set was not in good condition because it had many missing values in a few columns.
We don’t need all attributes because we only focus on the attributes that give the most direct descriptions of an active player. In another words, we don’t want to include attributes such as Draft Kings Name and Global Team ID that are less relevant to a player. Here described our steps in general:
1.	Checked location of missing values and decided which columns to keep
2.	Revised a few columns’ name and descriptive values (Team Abbreviation) to make it more readable and format more consistent
3.	Dropped columns we didn’t need and kept all columns that had direct information such as Height, Weight, Birth Date, College…
4.	Revised format of Birth Date to increase consistency.
5.	Filled empty values with ‘No record’ in categorical variable such as College and Birth City to increase completeness
6.	Checked the range of all numerical values to ensure there was no extreme outliers that didn’t make sense (For example NBA doesn’t allow 3-digit jersey number), increasing the validity of data. Also plotted histogram/boxplots to check the main attributes such as Height and Weight

The final file was saved as [NewPlayerDetails.csv](https://github.com/uttgeorge/Database-Assignment-1/blob/master/Audit%20-%20Clean/New%20Data/NewPlayerDetails.csv) in **Audit-Clean/New Data**

# Conceptual Model
The conceptual schema are stored in [ConceptualModel_NBA.pdf](https://github.com/uttgeorge/Database-Assignment-1/blob/master/ConceptualModel_NBA.pdf)\
This model includes four tables: players_info, nba_salary,2017-2018 regular season players stats, team stats.\
And there are 2 one to one relationships, and 1 one to many relationships.\
**players_info:** 'Player' is primary key, this table shows the biography of each players.\
**2017-2018 regular season players stats:** 'Player' is primary key, this table shows the stats of each players of last season. This table have one to one relationship with 'Player_info'.\
**nba_salary:** 'Player' is primary key, this table shows the salaries and ?allstar of players. This table have one to one relationship with 'Player_info'.\
**team stats:** 'Team' is primary key, this table shows the stats of each team. It has one to many relationship with 'players_info' table. The foreign key in players_info is 'team'. 
	

# Result
We extracted raw data from Web API, web scraping and directly downloading, followed by cleaning and auditing them to 4 well-organized tables. We built a conceptual database that allow us to search the biography of NBA players from 2017-2018 regular season, also reaching their personal performances, salaries, and team performances through 4 tables.

# Reference
### 1.[NBA Players' Salary of Season17-18](https://www.kaggle.com/koki25ando/nba-season1718-salary)
 from Kaggle.com published by [Koki Ando](https://www.kaggle.com/koki25ando).
### 2.[2017-2018 NBA Regular Season Stats](https://basketball.realgm.com/nba/stats/2018/Averages/All/points/All/desc/1/Regular_Season)
scraped from https://basketball.realgm.com/nba/stats/2018/Averages/All/points/All/desc/1/Regular_Season.
### 3.Web API from FantasyData
All-Star\
https://developer.fantasydata.com/docs/services/584f728a35491a16a4720f49/operations/5a70c9a135491a0ab00a814f \
Teams Stats \
https://developer.fantasydata.com/docs/services/584f728a35491a16a4720f49/operations/584f728a35491a0d440a48f7 \
Players Details \
https://developer.fantasydata.com/docs/services/584f728a35491a16a4720f49/operations/584f728a35491a0d440a48e6
### 4.Ryan Mitchell.April 2018.Web Scraping with Python, 2nd Edition.ISBN: 9781491985571
### 5.Professor Nicholas Brown 
https://github.com/nikbearbrown/INFO_6210/blob/master/Week_2/NBB_Data_cleaning_IMDB.ipynb
https://github.com/nikbearbrown/INFO_6210/blob/master/Week_2/NBB_Data_Munging_Wrangling.ipynb
### 6.TA Raj Sankhe
https://github.com/rajsankhe/python_workshop/blob/6c95fa3f441f42b0526f08f21e2b362671674bbe/Subtopics/9-Pandas.ipynb
### 7.Python Online Tutorials and Forums
https://www.tutorialspoint.com/python \
https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.rename.html \
https://erikrood.com/Python_References/change_order_dataframe_columns_final.html \
https://stackoverflow.com/questions/13682044/remove-unwanted-parts-from-strings-in-a-column \
https://www.geeksforgeeks.org/python-pandas-dataframe-fillna-to-replace-null-values-in-dataframe \
https://chrisalbon.com/python/data_wrangling/pandas_list_unique_values_in_column \
https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.rename.html \
https://stackoverflow.com/questions/33165734/update-index-after-sorting-data-frame


# License
### [LICENSE](https://github.com/uttgeorge/Database-Assignment-1/blob/master/LICENSE)

# Contribution Composition
### Qi Jin
1.Download NBA Players' Salary of Season17-18 from Kaggle;\
2.Scraped 2017-2018 NBA Regular Season Stats from RealGM.com. Scraping methods were leanred from Web Scraping with Python, 2nd Edition by Ryan Mitchell. 50% code were based on the example given in the book;\
3.Audited and Cleaned 2017-2018 Regular Season Players' Statistics;\
4.Audited and Cleaned NBA Salary & All-Star;\
5.Designed the conceptual Model.

### Dongyu Zhang
1.Used API to get 3 datasets from developer.fantasydata.com, including;\
All-star players, old playes' stats and  old players' details;\
2.Audited and cleaned NBA teams stats;\
3.Audiedt and cleaned NBA players details;\
4.Designed the conceptual Model.\
Overall, 50% of the code was written by me. I Wrote the code to clean and audit data after I learnt basic python syntax from
Professor's and other online tutorials and forums. When extracting data from API, I changed a few parameters wihtin the sample
API code and used my API-key for authentication. 


