<h1>The Foul Factor 🏀: Can We Predict When an NBA Player Will Foul Out?</h1>



<h2> Project Summary </h2>

This project explores whether NBA players are likely to foul out (commit ≥6 personal fouls in a single game) using traditional box score statistics from 2004–2020. We applied multiple machine learning techniques, including regression and classification models, to analyze patterns related to fouling behavior.

Despite leveraging models like Decision Trees, Random Forest, and Gradient Boosting, our models performed poorly, with the highest F1 score reaching just 0.06. The findings highlight the limitations of box score data alone and the need for more contextual data to improve predictive accuracy.


<h2>Languages and Tools Used</h2>

- <b>Python</b> (Data Analysis, Machine Learning)
- <b>SQL</b> (Data Preparation)
- <b>Pandas</b>, <b>Scikit-Learn</b> (Libraries for modeling and feature engineering)
- <b>Matplotlib/Seaborn</b> (Visualizations)
- <b>Jupyter Notebook</b>


<h2>Dataset </h2>

- <b>Source: NBA Box Score Data (2004–2020) from Kaggle</b> : [Visit NBA Data Source](https://www.kaggle.com/datasets/nathanlauga/nba-games)

- <b>Merged Files</b>: `games_details.csv` and `games.csv` using `GAME_ID`
 
- <b>Features Used</b>:
  - Player stats: `MIN`, `OREB`, `REB`, `AST`, `STL`, `BLK`, `TO`, `PTS`
    - MIN: Minutes played
    - PF: Personal fouls
    - OREB: Offensive rebounds
   - Rolling averages: 'MIN_avg_3', 'OREB_avg_3', etc.
    
- <b>Target Variable:</b>
    - `Fouled_Out` (Binary: 1 if `PF` ≥ 6, else 0)
    - Rolling averages for 3 games were created to enhance predictions

 
<h2>Key Steps </h2>

<h3>1. Data Preparation:</h3>

- Cleaned missing values and filtered out inactive players (`MIN = 0`)
- Engineered rolling averages (e.g., MIN_avg_3) for historical context

<h3>2. Exploratory Data Analysis (EDA):</h3>

- Most players commit 3 fouls or less per game

- <b>Centers</b> commit more fouls than <b>guards</b> on average

- Strong correlation found between <b>minutes played</b> and <b>personal</b> fouls

<h3>3. Modeling Approach:</h3>

<b>Regression Models:</b> 

- Predicted number of fouls (`PF`) directly
- Used Decision Tree Regressor
  
<b>Classification Models:</b>
- Predicted `Fouled_Out` (binary)
- Models used:
  - Decision Tree
  - Random Forest
  - Gradient Boosting
    
- Applied <b>SMOTE</b> to handle extreme class imbalance (0.42% foul-out rate)

<h3> 🔽Result Summary </h3>

<p align="center">
  <img width="458" alt="Image" src="https://github.com/user-attachments/assets/435cb68d-a80c-47a7-9049-89a0546317ac" />
  <br />
</p>

<b> Most important feature </b>: `MIN_avg_3` (minutes played average over last 3 games)


<h3>4. Evaluation:</h3>

- Metrics: <b>Accuracy, Precision, Recall, F1-Score</b>
- <b>Best Result</b>: Random Forest with an F1-Score of <b>0.06</b> (highlighting limitations)

<h2>Challenges and Insights</h2>

- <b>Key Challenges:</b>
   - <b>Severe class imbalance</b>: only 0.42% players fouled out
   - <b>Box score data lacks context</b>: no spatial, player bio, or foul type data
   - <b>Overfitting risk</b> due to low variation in data
   - Ensemble models did not significantly improve results
      
- <b>Key Insights</b>:
   - <b>Minutes played</b> is the strongest predictor of fouls
   - <b>Centers</b> are more prone to fouling out
   - Players who foul out often show similar patterns (high activity, high rebounds)
   - Regression and classification both fail without richer context



<h2> Future Work: </h2>

<h3>Data Enhancements:</h3>

 - Include player characteristics (height, wingspan, etc.)
 - Add spatial data (e.g., foul location maps)
 - Use play-by-play data for context (game pressure, score gap, substitution timing)

<h3> Feature Engineering:</h3>

 - Differentiate foul types (offensive vs defensive)
 - Apply PCA, log transforms, interaction features

<h3> New Problem Framing: </h3>

 - Instead of "Will a player foul out?", ask:
   - What types of fouls are most common by position/time?
   - How do fouls impact player performance?


<h2>Visualizations:</h2>

### Foul Distribution Histogram

<p align="center">
  <img width="398" alt="Image" src="https://github.com/user-attachments/assets/638ce184-5ca7-4d97-972c-34f5334c45de" />
  <br />
</p>

> Most players commit 3 or fewer fouls per game, but a small portion consistently exceeds 4+, indicating foul-out risk.

### Box Plot of PF by Position

<p align="center">
  <img width="371" alt="Image" src="https://github.com/user-attachments/assets/4dc8206a-d2d8-4247-a1fd-0af124e48d7a" />
  <br />
</p>

> Centers show a higher median of personal fouls compared to guards, aligning with their defensive role.

### Feature Importance (Random Forest)

<p align="center">
  <img width="271" alt="Image" src="https://github.com/user-attachments/assets/eab13969-5c03-4b40-bca5-acbedfe4227b" />
  <br />
</p>

> `MIN_avg_3` (average minutes played over past 3 games) is by far the most influential predictor of foul-outs.

### Confusion Matrix (Random Forest)
<p align="center">
  <img width="449" alt="Image" src="https://github.com/user-attachments/assets/32f63ad8-300f-41b3-bd04-16fd41d70188" />
  <br />
</p>

> Despite adjustments, models struggled with false positives—many players were misclassified as likely to foul out.


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
