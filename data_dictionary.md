# Data Dictionary
## A1: Variables used in initial EDA models
The models use one row per game, the score after six innings. Predictors are the run differential and total runs after 6 innings. The target is home_win. "Located" variables come straight from the 2025 play-by-play file from Retrosheet. "Derived" variables are built from them in code.

| Variable name | Description | Data type | Role in the analysis | Status |
|---|---|---|---|---|
| **home_win** | 1 if the home team's final score is higher than the visitor's, else 0 | Boolean (0/1) | **Target** | Derived (`final_h > final_v`) |
| run_diff | Home score minus visitor score after 6 innings (positive = home team leading) | Numeric (integer) | Predictor (all three models) | Derived (`h_after6 - v_after6`) |
| total_runs | Combined runs scored by both teams after 6 innings | Numeric (integer) | Predictor (k-means, logistic regression) | Derived (`h_after6 + v_after6`) |
| gid | Game ID: home team code + date (YYYYMMDD) + game number (0 = single game, 1/2 = doubleheader) | Text | Identifier; grouping key for game-level tables | Located |
| inning | Inning in which the play occurred | Numeric (integer) | Grouping variable; inning 7 rows give the score after 6 innings | Located |
| score_v | Visiting team's score at the start of the play | Numeric (integer) | Source of `v_after6` and `final_v` | Located |
| score_h | Home team's score at the start of the play | Numeric (integer) | Source of `h_after6` and `final_h` | Located |
| vis_home | Team batting: visitor (0) or home (1) | Categorical (0/1) | Assigns runs on the last play to the correct team | Located |
| runs | Runs scored on the play | Numeric (integer) | Added to the last play's score to get the final score | Located |
| gametype | Type of game: regular, wildcard, divisionseries, lcs, worldseries, allstar | Categorical | Filter (All-Star game excluded) | Located |
| date | Game date (YYYYMMDD) | Date | Orders plays chronologically | Located |
| v_after6, h_after6 | Visitor and home score at the start of the 7th inning | Numeric (integer) | Intermediate inputs to `run_diff` and `total_runs` | Derived (first play of inning 7) |
| final_v, final_h | Final visitor and home score | Numeric (integer) | Intermediate inputs to `home_win` | Derived (last play's score + runs) |
| cluster | K-means cluster assignment (0–2) for each game state | Categorical | Model output; each cluster's home-win rate is its prediction | Derived (k-means) |
| p_home_win | Predicted probability the home team wins | Numeric (0–1) | Model output; predicted winner = home if ≥ 0.5 | Derived (each model) |

## A2: Full Data Dictionary
All 75 columns below were located in the baseline 2025 play-by-play dataset. Each row of the file is one play. Flag columns are 1 if the play included that event, else 0. Role marks whether a column was used in the initial EDA or is a candidate for later analysis.

| Variable name | Description | Data type | Role in the analysis | % missing |
|---|---|---|---|---|
| gid | Game ID: home team code + date + game number (0 = single game, 1/2 = doubleheader) | Text | Identifier (used) | 0 |
| event | The play as written in Retrosheet's event file (e.g., K, W, 63/G6) | Text | Descriptive | 0 |
| inning | Inning of the play (1–18 in 2025) | Numeric (integer) | Grouping variable (used) | 0 |
| top_bot | Half-inning: top (0) or bottom (1) | Categorical (0/1) | Grouping variable | 0 |
| vis_home | Team batting: visitor (0) or home (1) | Categorical (0/1) | Used to compute final score | 0 |
| site | Ballpark code where the play occurred (33 parks) | Categorical | Candidate predictor | 0 |
| batteam | Batting team code (32 teams, incl. All-Star squads) | Categorical | Candidate predictor | 0 |
| pitteam | Pitching (fielding) team code | Categorical | Candidate predictor | 0 |
| score_v | Visiting team score at the start of the play | Numeric (integer) | Predictor source (used) | 0 |
| score_h | Home team score at the start of the play | Numeric (integer) | Predictor source (used) | 0 |
| lp | Batter's lineup position (1–9) | Numeric (integer) | Descriptive | 0 |
| bat_f | Batter's fielding position (1–9 by position, 10 = designated hitter, 11 = pinch hitter) | Categorical (stored as number) | Descriptive | <0.01 (9 rows) |
| bathand | Batter handedness: L, R or B (switch) | Categorical | Candidate predictor | 0 |
| pithand | Pitcher handedness: L or R | Categorical | Candidate predictor | 0 |
| balls | Balls in the count before the final pitch of the play (0–3) | Numeric (integer) | Descriptive | 0 |
| strikes | Strikes in the count before the final pitch of the play (0–2) | Numeric (integer) | Descriptive | 0 |
| count | Balls and strikes combined as one code (e.g., 12 = 1 ball, 2 strikes; 2 = 0–2) | Categorical (stored as number) | Descriptive | 0 |
| nump | Number of pitches in the plate appearance, if known | Numeric (integer) | Descriptive | 0.29 |
| pa | Play was a plate appearance | Boolean (0/1) | Descriptive | 0 |
| ab | Play was an official at-bat | Boolean (0/1) | Descriptive | 0 |
| single | Single | Boolean (0/1) | Descriptive | 0 |
| double | Double | Boolean (0/1) | Descriptive | 0 |
| triple | Triple | Boolean (0/1) | Descriptive | 0 |
| hr | Home run | Boolean (0/1) | Descriptive | 0 |
| sh | Sacrifice hit (bunt) | Boolean (0/1) | Descriptive | 0 |
| sf | Sacrifice fly | Boolean (0/1) | Descriptive | 0 |
| hbp | Hit by pitch | Boolean (0/1) | Descriptive | 0 |
| walk | Walk (includes intentional walks) | Boolean (0/1) | Descriptive | 0 |
| k | Strikeout | Boolean (0/1) | Descriptive | 0 |
| bip | Ball put in play | Boolean (0/1) | Descriptive | 0 |
| bunt | Ball in play was a bunt | Boolean (0/1) | Descriptive | 0 |
| ground | Ball in play was a ground ball | Boolean (0/1) | Descriptive | 0 |
| fly | Ball in play was a fly ball | Boolean (0/1) | Descriptive | 0 |
| line | Ball in play was a line drive | Boolean (0/1) | Descriptive | 0 |
| gdp | Batter grounded into a double play | Boolean (0/1) | Descriptive | 0 |
| othdp | Other (non-ground-ball) double play | Boolean (0/1) | Descriptive | 0 |
| tp | Triple play | Boolean (0/1) | Descriptive | 0 |
| fle | Error on a dropped foul ball; batter stays at bat | Boolean (0/1) | Descriptive | 0 |
| wp | Wild pitch | Boolean (0/1) | Descriptive | 0 |
| pb | Passed ball | Boolean (0/1) | Descriptive | 0 |
| bk | Balk | Boolean (0/1) | Descriptive | 0 |
| sb2 | Stolen base of second | Boolean (0/1) | Descriptive | 0 |
| sb3 | Stolen base of third | Boolean (0/1) | Descriptive | 0 |
| sbh | Stolen base of home | Boolean (0/1) | Descriptive | 0 |
| cs2 | Caught stealing second | Boolean (0/1) | Descriptive | 0 |
| cs3 | Caught stealing third | Boolean (0/1) | Descriptive | 0 |
| csh | Caught stealing home | Boolean (0/1) | Descriptive | 0 |
| pko1 | Runner picked off first | Boolean (0/1) | Descriptive | 0 |
| pko2 | Runner picked off second | Boolean (0/1) | Descriptive | 0 |
| pko3 | Runner picked off third | Boolean (0/1) | Descriptive | 0 |
| k_safe | Strikeout where the batter reached base safely (subset of k) | Boolean (0/1) | Descriptive | 0 |
| e1 | Errors by the pitcher on the play | Numeric (count, 0–2) | Descriptive | 0 |
| e2 | Errors by the catcher on the play | Numeric (count, 0–1) | Descriptive | 0 |
| e3 | Errors by the first baseman on the play | Numeric (count, 0–2) | Descriptive | 0 |
| e4 | Errors by the second baseman on the play | Numeric (count, 0–2) | Descriptive | 0 |
| e5 | Errors by the third baseman on the play | Numeric (count, 0–2) | Descriptive | 0 |
| e6 | Errors by the shortstop on the play | Numeric (count, 0–2) | Descriptive | 0 |
| e7 | Errors by the left fielder on the play | Numeric (count, 0–1) | Descriptive | 0 |
| e8 | Errors by the center fielder on the play | Numeric (count, 0–1) | Descriptive | 0 |
| e9 | Errors by the right fielder on the play | Numeric (count, 0–2) | Descriptive | 0 |
| outs_pre | Outs before the play (0–2; 3 on rare plays recorded after the third out) | Numeric (integer) | Candidate predictor | 0 |
| outs_post | Outs after the play (0–3) | Numeric (integer) | Descriptive | 0 |
| rbi_b | RBI credited for the batter scoring | Boolean (0/1) | Descriptive | 0 |
| rbi1 | RBI credited for the runner from first scoring | Boolean (0/1) | Descriptive | 0 |
| rbi2 | RBI credited for the runner from second scoring | Boolean (0/1) | Descriptive | 0 |
| rbi3 | RBI credited for the runner from third scoring | Boolean (0/1) | Descriptive | 0 |
| runs | Total runs scored on the play (0–4) | Numeric (integer) | Used to compute final score | 0 |
| rbi | Total RBIs credited on the play (0–4) | Numeric (integer) | Descriptive | 0 |
| er | Earned runs charged on the play (0–4) | Numeric (integer) | Descriptive | 0 |
| tur | Team unearned runs on the play (0–3) | Numeric (integer) | Descriptive | 0 |
| hittype | Type of ball in play: G, F, L, P (ground, fly, line, pop-up); BG, BP, BL = bunt versions | Categorical | Descriptive | 34.22 (blank when no ball in play) |
| pn | Play number, in sequence within the game | Numeric (integer) | Ordering key | 0 |
| date | Game date (YYYYMMDD); converted to a date in preprocessing | Date | Ordering key (used) | 0 |
| gametype | Type of game: regular, wildcard, divisionseries, lcs, worldseries, allstar | Categorical | Filter (used) | 0 |
| pbp | Whether the play-by-play is full or deduced (all rows are "full" in 2025) | Categorical | Data-quality flag | 0 |
