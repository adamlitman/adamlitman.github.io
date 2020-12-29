---
title: "NBA Draft Classification Project"
date: December 15, 2020
#tags: [data wrangling, data science, messy data]
header:
  image: "/images/basketball.png"
excerpt: "Web Scraper, Data Cleaning, Data Visualization, Model Building"
mathjax: "true"
---

## Project Overview
Link to full python code: [Github Repository](https://github.com/adamlitman/nbadraft_project)

- Created a classifier for determining whether an NBA player was drafted too high, too low, or accurately
- Scraped data for over 2900 draft picks from basketballreference.com from 1981 through 2010
- Added ranking features to determine the optimal draft order for each year based on player success
- Explored and visualized the data using multiple plot types in seaborn and matplotlib
- Built and tested multiple classification techniques to find the optimal model (K-nearest neighbors, Naive Bayes, Logistic Regression, Decision Tree)

## Sources and Code Used
- Data Source: [Basketball Reference](https://www.basketball-reference.com/)
- Article for building scraper: [Full Article](https://medium.com/hardwood-convergence/intro-to-virtual-environments-and-scraping-nba-data-with-beautifulsoup-6ce745f8c26e)
- Python Packages Used: pandas, BeautifulSoup, requests, matplotlib, numpy, seaborn, sklearn

## Web Scraping
Modified the scraper in the article above to pull 30 years of NBA Draft data. For each draft selection, I scraped the following columns:
- Pick Number
- Player
- Team
- College
- Years Played
- Games Played
- Minutes Played
- 14 additional player statistics such as points per game, total rebounds, WinShares, Box Plus/Minus, etc.

## Data Cleaning and Modifications
- Made column for draft year
- Converted relevant columns to numeric type
- Filled all null values
- Created a key to standardize team acronyms for teams that changed locations 
- Standardized the data by including only top 60 picks for each draft year
- Added columns to rank players in each draft by WinShares, VORP, and BPM
- Added columns to identify lottery picks and superstar players
- Added columns to identify if players were picked too high or too low based on ranking features

## Exploratory Data Analysis
Highlights from EDA

![scatter]({{ site.url }}{{ site.baseurl }}/images/scatterplot_nba.png)

![box]({{ site.url }}{{ site.baseurl }}/images/boxplot.png)

![bar1]({{ site.url }}{{ site.baseurl }}/images/bar_teams.png)

![bar2]({{ site.url }}{{ site.baseurl }}/images/bar_college.png)

## Model Building and Scoring
The goal of model building was to design a classifier that designates players as 'overdrafted', 'underdrafted', or 'even' based on their draft position and subsequent success in the NBA.

Started by creating dummy variables and splitting the data into training and test sets with a test size of 20%.

Tested 4 different categorical models and used a scaler to improve the 2 most accurate ones. Used a simple accuracy score to determine the success of a model. 

- K-nearest neighbors: accuracy = 0.67
- Naive Bayes: accuracy = 0.55
- Logistic Regression: accuracy = 0.86
- Decision Tree: accuracy = 0.85

The Logistic Regression and Decision Tree models clearly performed best, with Logistic Regression achieving the slight edge. 

