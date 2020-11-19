# Top 20 European Soccer Leagues Player Data - Project Overview:
* Scraped over 10000 players data from http://transfermarkt.us/ using python and BeautifulSoup.
* Cleaned, transformed and organized the data for EDA.
* Attempt to build a prediction model using Linear Regression and Random Forest. 

## Code and Resources Used 
**Python Version:** 3.8  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, BeautifulSoup, pickle   
**Project's inspiration:** https://github.com/PlayingNumbers/ds_salary_proj  
**Source of the data:** https://transfermarkt.us/

## Web Scraping
Used BeautifulSoup to scrape over 10000 player's data from transfermarkt.us. Here's some of the main columns gathered from the scraping:
*	Short_name
*	Age
*	Height
*	Citizenship
* 	Position
*	Foot
*	Player agent
*	Current club	
*	appearances
*	goals
*	yellow
*	second_yellow
*	red
*	goals_conceded
*	clean_sheets
*	minutes_played
*	league
*	latest_market_value
*	highest_market_value
*	assists

## Data Cleaning
After scraping the data, I needed to clean it so that it was possible to make an useful EDA and a prediction model. Here's some of the changes applied to the data:

* Renamed all columns so that they would have lower case letters and wouldn't have spaces between words.
* Simplified our data selecting only columns that I thought may be useful to our project.
* Converted the appropriate columns to numeric.
* Separated citizenship column into main and second nationality.
* Removed all string from currency data and converted to numeric.
* Filled NAs as needed.
* Renamed leagues that had the same name but were from different countries.


	
## EDA

Looked data distribution, created new columns, and used and group by to analyze and understand better the data.

![alt text](https://github.com/Caldass/europe_players_data/blob/main/goalsperleague.png "Goals per game by League")
![alt text](https://github.com/Caldass/europe_players_data/blob/main/goalsperplayer.png "Goals per game by player")
![alt text](https://github.com/Caldass/europe_players_data/blob/main/league_marketvalue.png "Players Market Value by League")
![alt text](https://github.com/Caldass/europe_players_data/blob/main/cmap.png "Correlations")


## Model Building 

At first I thought it wouldn't be too much trouble to create a prediction of a player's market value using this data, but I ended up trying 3 different approaches to creating the model based on player's positions.

My model used the following algorithms:
*	**Multiple Linear Regression** – Baseline for the model.
*	**Random Forest** – There weren't many categorical variables specially when using all the player positions, but I thought I'd still try Random Forest.

## Model scoring:
I thought I'd use a simple concept as R-Squared to evaluate my model since it's easy to interpret and its efficient to tell how related things are.

## Model attempts

First I used all the data with no position restrictions for the players:
*	**Linear Regression**: R² = 0.4
*	**Random Forest** : R² = 0.5

Then I thought I might get a better result restricting the player's positions to forwards only:
*	**Linear Regression**: R² = 0.39
*	**Random Forest** : R² = 0.17

At last I tryied using only keepers:
*	**Linear Regression**: R² = 0.12
*	**Random Forest** : R² = -0.0

## Model Conclusion
Unfortunately the best result I managed to get using these 2 algorithms explained around 0.4 and 0.5 per cent of the data at best, which is not good enough for a prediction model. In my perspective, there isn't enough stats in this dataset so that one could actually predict player prices since football is way too complex to sum up its valuable stats in goals, assists, appearances, age, etc. Football takes into account many other factors that will hardly be found in any football stats website. Not to mention that these stats are way too general. For example, center-backs and defensive midfielders should have tackles and ball recovery stats to be taken into account too. Keepers should have a saves stat and so on. 

