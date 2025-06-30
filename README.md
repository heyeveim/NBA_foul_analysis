<h1>The Foul Factor 🏀: Can We Predict When an NBA Player Will Foul Out?</h1>



<h2>Description</h2>
This project analyzes NBA player performance using box score data (2004–2020) to predict the probability of <b>fouling out</b> (committing 6+ fouls in a game). By applying machine learning models, we aimed to uncover relationships between key statistics like <b>minutes played</b>, <b>rebounds</b>, and foul patterns to assist coaches and teams with strategic player management. <br><br>

While the models were tested using advanced classification techniques like <b>Random Forest</b> and <b>Gradient Boosting</b>, the analysis revealed significant limitations in using box score data alone, highlighting opportunities for <b>future improvements</b> using richer datasets.
<br />

This project explores whether we can predict when an NBA player will foul out (commit 6 or more personal fouls in a game) using traditional box score data from 2004–2020. While this data is rich in player stats like minutes, rebounds, and turnovers, it lacks spatial or contextual insight.

Through a series of regression and classification models—including Decision Trees, Random Forest, and Gradient Boosting—we investigated whether patterns in past performance could signal foul-outs.

Despite extensive modeling efforts, results showed poor predictive power (best F1-score: 0.06), highlighting the limitations of box score data for such granular predictions.

**Our takeaway?** Predicting fouling out is more complex than it seems—and the current data doesn't tell the full story.



<h2>Languages and Tools Used</h2>

- <b>Python</b> (Data Analysis, Machine Learning)
- <b>SQL</b> (Data Preparation)
- <b>Pandas</b>, <b>Scikit-Learn</b> (Libraries for modeling and feature engineering)
- <b>Matplotlib/Seaborn</b> (Visualizations)
- <b>Jupyter Notebook</b>


<h2>Dataset </h2>

- <b>Source: NBA Box Score Data (2004–2020) from Kaggle</b>

  [Visit NBA Data Source](https://www.kaggle.com/datasets/nathanlauga/nba-games)

- <b>Main Attributes:</b>
  - MIN: Minutes played
  - PF: Personal fouls
  - OREB: Offensive rebounds
  - REB, AST, STL, BLK, TO, PTS
    
- <b>Target Variable:</b>
    - Binary Fouled_Out: 1 if PF ≥ 6, else 0
    - Rolling averages for 3 games were created to enhance predictions
 
<h2>Key Steps </h2>

<h3>1. Data Preparation:</h3>

- Merged games_details.csv and games.csv using GAME_ID
- Cleaned missing values and filtered out inactive players (MIN = 0)
- Engineered rolling averages (e.g., MIN_avg_3) for historical context

<h3>2. Exploratory Data Analysis (EDA):</h3>

- Analyzed foul distributions, box plots by positions, and correlations between stats
- Visualized key insights: centers commit the most fouls; higher minutes → higher fouls

<h3>3. Modeling:</h3>

- <b>Regression Models:</b> Predicted continuous PF values.
- <b>Classification Models:</b>
  - <b>Decision Tree</b>
  - <b>Random Forest</b>
  - <b>Gradient Boosting</b>
  - Addressed class imbalance using <b>SMOTE</b> and hyperparameter tuning
    
<h3>4. Evaluation:</h3>

- Metrics: <b>Accuracy, Precision, Recall, F1-Score</b>
- <b>Best Result</b>: Random Forest with an F1-Score of <b>0.06</b> (highlighting limitations)

<h2>Challenges and Insights</h2>

- <b>Data Limitations:</b>
    - Box score data alone is insufficient for foul prediction
    - Significant class imbalance: players fouling out (PF ≥ 6) represent only 0.42% of the dataset
      
- <b>Key Insights</b>:
  - Minutes played is the most significant factor for foul prediction
  - Ensemble models like Random Forest and Gradient Boosting were ineffective due to weak relationships in the data



<h2>Visualizations:</h2>

<p align="center">
Foul Distribution Among Players: <br/>
<img src="https://i.imgur.com/ltPgUxf.png" alt="Foul Distribution" height="80%" width="80%"/>
<br />
</p>
</p>
<p align="center">
Box Plot of Fouls by Position: <br/>
<img src="https://i.imgur.com/X7KhgYv.png" alt="Box Plot of Fouls by Position" height="80%" width="80%"/>
<br />
</p>
<p align="center">
Model Performance Comparison: <br/>
<img src="https://i.imgur.com/gQJdnHN.png" alt="Launch Utility" height="80%" width="80%"/>
<br />
</p>

<h2>Future Recommendation</h2>

<h3>1. Data Enhancements:</h3>

- Integrate spatial data (e.g., foul location maps)
- Include player characteristics like height and wingspan
- Add substitution and game-context data.

<h3>2. Feature Engineering:</h3>

- Combine variables to create advanced features (e.g., offensive vs defensive fouls)

<h3>3. Refine Research Focus:</h3>

- Narrow to specific fouls: "How do offensive fouls impact player performance?"

<h2>Conclusion</h2>

While current models showed limited success, the analysis emphasizes the importance of <b>better datasets</b> and contextual features to accurately predict foul behavior. This project lays the foundation for future research into player performance management.

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
