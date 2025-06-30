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

Most important feature: MIN_avg_3 (minutes played average over last 3 games)


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
