# Retention of NBA players in the team for the next year 
- **Author**: Lavanya Telapudi
- Prepared for UMBC Data Science Master Degree Capstone(Fall 2023) by Dr Chaojie (Jay) Wang
- **GitHub**: https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya
- **LinkedIn**: https://www.linkedin.com/in/lavanya-t-5b7666214/
- **Link to PowerPoint presentation file**: https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/documents/Capstone_presentation.pptx
- **Link to Youtube Video**: https://www.youtube.com/watch?v=LWwEpobl6HA


## 2. Background

The National Basketball Association (NBA) is one of the premier basketball leagues globally, known for its high level of competition and talented players. Each year, NBA teams undergo various changes, including player transfers, drafts, and retirements. Retaining key players from the previous season is often considered a critical factor in a team's success. Championship-winning teams typically have higher player retention rates, suggesting a correlation between team stability and success. In the beginning of the NBA season, the cavalcade of predictions, projections and presumptions will push their way through the door, and they play an important role throughout the tournament. They blindside us with the innumerable stray ideas that looking at a new roster amidst new rosters brings. 


## Player retention in the NBA matters for several reasons

Team Cohesion: Keeping key players together allows teams to build better chemistry and understanding on the court, which can lead to improved performance.

Fan Engagement: Fans often develop strong connections with their favorite players. High player turnover can affect fan engagement and loyalty to a team.

Financial Implications: Contracts and salaries of NBA players are significant financial investments for teams. Effective player retention strategies can help teams manage their budgets efficiently.

Competitive Advantage: Retaining star players or key contributors can give a team a competitive edge, making them more likely to contend for championships.

## Research questions
1. I'm analyzing performance of every player from 1997 to 2022 based on the points they scored.
2. I'm trying to draft the best players for the team for next year by correlating with the points they scored in the past seasons.



## 3. Data: 
[Link to Dataset](https://data.world/etocco/nba-player-stats/workspace/file?filename=NBA_Player_Stats_2.csv)

This dataset is from data.world. The Dataset being used is 2 MB and it has 14574 rows and 31 columns

### Workorder Table Columns:
- Name(object) -Name of the player
- G(int64) -Games played
- MP(float64) -Minutes played
- PTS(float64) -Average points made per game
- FG(float64) -Field goals
- FGA(float64) -Field goals attempted
- %FG(float64) -Percentage of field goals
- 2P(float64) -2-Point Field Goal
- 3P(float64) -Three-pointers made
- 3PA(float64) -Three-pointers attempted
- FT(float64) -Free throw
- FTA(float64) -Free throws attempted
- FT%(float64) -Free throw percentage
- ORB(float64) -Offensive rebounds
- DRB(float64) -Defensive rebounds
- AST(float64) -Assists
- STL(float64) -Steals
- BLK(float64) -Blocks
- TOV(float64) -Turnovers

I have five potential features which are continuous,
MP= Minutes Played, FG=Field Goal, 2P= 2-Point Field Goal, FT=Free Throw, TOV=Turnovers

I did both regression and classification on my dataset
For the Classification problem, I added one more column to my dataframe as 'Threshold PTS' giving 1 if PTS is greater than 7 and 0 if it is less than 7 making this a classification problem and Threshold PTS as the target variable.

## 4. Exploratory Data Analysis(EDA)
### 4.1 Data Summary Statistics
For each of the dataset's numerical columns, we computed summary statistics. 
Here are some significant figures:
1.   Age: Mean of 26, with a minimum of 18 and a maximum of 44.
2.   Games: Mean of 45, with a minimum of 1 and a maximum of 85.
3.   Minutes Played: Mean of 19, with a minimum of 0 and a maximum of 43.
4.   Points: Mean of 7, with a minimum of 0 and a maximum of 36.
5.   Assists: Mean of 1.7, with a minimum of 0 and a maximum of 12.8

**we have 25 different NBA seasons from 1997 - 2022 in my project**

### 4.2 Data Cleaning
#### 4.2.1 Analysing null values: 
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_17_0.png)

Evidently, out of 32 columns 5 columns contains missing values.
Above plot shows 3P% and FT% has maximum number of null values
- Treatment: Becuase these columns are associated with number of goals made or attempted, it is safe to replace these missing values with zero.

### 4.3 Data Analysis
#### 4.3.1 Count of players per season
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_27_0.png)
- we can see that 2002-03 season has least number of players and 2021-22 got more number of players.

#### 4.3.2 Distribution of Players Age
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_29_0.png)

#### 4.3.3 Top 10 Players and Number of Games played
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_42_0.png)

#### 4.3.4 Age vs Efficiency
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_47_0.png)

- we can observe that overall as the age of the player increases to 40 both offensive and defensive rebounds decreases but after 40 it increased and decreased this could be an outlier

#### 4.3.5 Age vs Turnovers
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_48_0.png)

- Here we can observe that between 23 to 28 players commit more turnovers and then the turnovers decreased gradually over the age

#### 4.3.6 Age vs Fouls
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_49_0.png)

- There is a decreasing trend in Foul Per 100 possssions as player ages however there is a sharp increase in after the age 44. This could be an outlier.

#### 4.3.7 Distribution of Points
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_34_0.png)

- Data is Right skewed.
- To treat skewed data, we will be using "Square root transformation" to normalize the feature PTS
  
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_38_0.png)


### 4.4 Heatmap showing the correlation between the columns
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_58_0.png)

- we can observe that **MP= Minutes Played, FG=Field Goal, 2P= 2-Point Field Goal, FT=Free Throw, TOV=Turnovers** are highly related to the POINTS from the above heatmap
- So my features are MP, FG, 2P, FT, TOV and my target variable is PTS_sqrt after square root transformatio.


- Before splitting data as train and test data I wanted to plot pairplot
  
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_66_1.png)
- From the above pairplot I observed that my features are skewed, so I will treat them using sqrt transformation again

### 5. Data Modeling
- Now, I'm going to apply various Machine Learning Algorithms on the above
### Regression Problem
Predicting the points(PTS_sqrt) based on 'MP', 'FG', '2P', 'FT', 'TOV' features after transformation.

## 5.1 Models Used for Machine Learning
1.	Linear Regression
2.	Ridge Regression
3.	Lasso Regtression
4.	Decision Tree
5.	Gradient Boosting Regressor
6.	Random Forest Regressor
   
#### 5.1. Linear Regression
- Split the data set into 70% train data set and 30% test data set.  
- Fit the data into the model
- Calculated R2 score for train and test data, is 98 percent approximately 
- And predicted the first 10 target values for the test dataset

#### 5.2. Ridge regression
- We used the same features and target for this too
- Fit the data
- R2 score is 96.3 percent for this regression 

#### 5.3. Lasso regression 
- R2 score for this regression is 97 percent 
- Printed coefficients of regression and found two of them to be 0. So, this regression can be used as a feature selection tool
- And observed that this regression is in agreement with the results of spearman correlation analysis

#### 5.4. DecisionTreeRegressor
- We used the same features and target and calculated the 
- Feature importance and found that ‘FG_sqrt’ is the most important feature than others
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_93_0.png)

- For the rest of the models we took only ‘FG_sqrt’  as our feature  

- Found the predictions of the tree regressor for train and test subsets and calculated R2 score

- Used GridSearchCV to find the best hyperparameters

- Retrained the regressor with the best hyperparameters and calculated the R2 score again and compared with the previous ones. We were successful in curing some variance by tuning the hyperparameters.

#### Plot predictions vs true values for ‘PTS_sqrt’
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_105_0.png)

#### 5.5. Gradient Boosting Regressor
- 98.18 percent R2 score and no overfitting

#### 5.6. Random Forest Regressor
- 98 percent accuracy and no overfitting for this model

#### Conclusion for Regression Analysis
Best ML Models: Decision Tree, Gradient Boosting Regressor, Random Forest Regressor produces good results.


### 6. Player will retain or not?

- Here we added one more column to our dataframe as 'Threshold PTS' giving 1 if PTS is greater than 7 and 0 if it is less than 7
- We took our features as ‘FG_sqrt’ and ‘FT_sqrt’ and target as ‘Threshold PTS’ 


- Balanced dataset
Size of class 0: 7938
Size of class 1: 6635

#### 6.1 Logistic regression
- Accuracy of 97%
- No sign of overfitting

#### Decision Region for logistic regression
![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_131_0.png)

#### 6.3 Linear Discriminant Analysis
- Accuracy of 92%
- No sign of overfitting

#### 6.3 Quadratic Discriminant Analysis
- Accuracy of 95%
- No sign of overfitting
  
#### Decision Region for Discriminant Analysis
  ![image](https://github.com/DATA-606-2023-FALL-THURSDAY/telapudi_lavanya/blob/main/assets/output_141_0.png)

#### Conclusion for the Classification Analysis
From the above we can say that Logistic regression and random forest classifier are the best to model our classification problem.

#### Future Analysis
**1. KMeans Clustering**
- A cluster refers to a collection of data points aggregated together because of certain similarities

- Can make 5 clusters of players using this ML model to show which players are most similar to each other

- By doing KMeans clustering we can see which players are in the same cluster and know some interesting facts from this

  ### Thank you



