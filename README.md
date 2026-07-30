
# NBA Game Outcome Predictor

### What this does
This project uses a logistic regression model to predict the probability 
of either team winning a given NBA matchup, based on each team's recent 
performance leading up to that game.

### Why I built it
As a lifelong basketball fan, I wanted to see if a data-driven model could 
predict game outcomes as well as (or better than) my own instincts, and 
to build real hands-on experience with the machine learning pipeline.

### How it works
- Data source: NBA game data (2015–present) via Kaggle
- Reshaping: Converted the raw game-level data (which split stats into 
  home/away columns) into one row per team per game, making it possible to 
  cleanly calculate each team's individual performance over time
- Feature engineering: For each game, computed each team's rolling 
  average over their previous 10 games (points, rebounds, assists, win %) — 
  explicitly excluding the current game to avoid data leakage (the model 
  should never "see the answer" before predicting)
- Model:Logistic regression, trained on an 80/20 train/test split
- Evaluation: Compared model accuracy against a baseline of "always 
  predict the home team wins," since home-court advantage alone accounts 
  for a meaningful win rate in the NBA

### Results
- Model accuracy:64.80%
- Baseline (always predict home team wins):60.24%

The model outperformed the baseline by about 4.5 percentage points, 
indicating it learned real predictive signal from recent team performance 
beyond simple home-court advantage.

### What I'd improve with more time
- Compare against additional models (e.g. Random Forest) and evaluate 
  feature importance
- Add more features (e.g. rest days, injuries, head-to-head history)
- Build an interactive demo where users can input any two teams and a date

#### Tech stack
Python, pandas, scikit-learn, Google Colab
