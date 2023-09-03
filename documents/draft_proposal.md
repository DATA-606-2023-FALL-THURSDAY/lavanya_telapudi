# Retention of NBA players in the team for the next year 
*September 03, 2023*

## Background

The National Basketball Association (NBA) is one of the premier basketball leagues globally, known for its high level of competition and talented players. Each year, NBA teams undergo various changes, including player transfers, drafts, and retirements. Retaining key players from the previous season is often considered a critical factor in a team's success. Championship-winning teams typically have higher player retention rates, suggesting a correlation between team stability and success. In the beginning of the NBA season, the cavalcade of predictions, projections and presumptions will push their way through the door, and they play an important role throughout the tournament. They blindside us with the innumerable stray ideas that looking at a new roster amidst new rosters brings. 


## Player retention in the NBA matters for several reasons

Team Cohesion: Keeping key players together allows teams to build better chemistry and understanding on the court, which can lead to improved performance.

Fan Engagement: Fans often develop strong connections with their favorite players. High player turnover can affect fan engagement and loyalty to a team.

Financial Implications: Contracts and salaries of NBA players are significant financial investments for teams. Effective player retention strategies can help teams manage their budgets efficiently.

Competitive Advantage: Retaining star players or key contributors can give a team a competitive edge, making them more likely to contend for championships.

## Research questions
1. I'm analyzing performance of every player from 1997 to 2022 based on the points they scored.
2. I'm trying to draft the best players for the team for next year by correlating with the points they scored in the past seasons.



## Data: 
[Link to Dataset](https://data.world/etocco/nba-player-stats/workspace/file?filename=NBA_Player_Stats_2.csv)

This dataset is from data.world. The Dataset being used is 2 MB and it has 14574 rows and 31 columns

### Workorder Table Columns:
- Name(object) -Name of the player
- G(int64) -Games played
- MP(float64) -Minutes played
- PTS(float64) -Average points made per game
- FGM(float64) - Field goals made
- FGA(float64) -Field goals attempted
- %FG(float64) -Percentage of field goals
- 3P(float64) - Three-pointers made
- 3PA(float64) - Three-pointers attempted
- FTM(float64) -Free throws made
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

I deleted all the categorical variables and used only continuous variables

Here I added one more column to my dataframe as 'Threshold PTS' giving 1 if PTS is greater than 7 and 0 if it is less than 7 making this a classification problem and Threshold PTS as the target variable.





