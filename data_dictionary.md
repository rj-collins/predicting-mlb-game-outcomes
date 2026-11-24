# Data Dictionary

| Variable Name | Description | Data Type | Role in Analysis | Origin |
|---|---|---|---|---|
| **home_win** | 1 if the home team's final score is higher than the visitor's, else 0 | Boolean (0/1) | **Target** | Derived (home_final_score > away_final_score) |
| score_v | Visiting team's score at the start of the play | Numeric (integer) | Source of v_after6 and final_v | Located |
| score_h | Home team's score at the start of the play | Numeric (integer) | Source of h_after6 and final_h | Located |
| v_after6, h_after6 | Visitor and home score at the start of the 7th inning | Numeric (integer) | Intermediate inputs to run_diff_6 and total_runs_6 | Derived (first play of inning 7) |
| run_diff_6 | Home score minus visitor score after 6 innings (positive = home team leading) | Numeric (integer) | Predictor | Derived (h_after6 - v_after6) |
| total_runs_6 | Combined runs scored by both teams after 6 innings | Numeric (integer) | Predictor | Derived (h_after6 + v_after6) |
| inning | Inning in which the play occurred | Numeric (integer) | Grouping variable; inning 7 rows give the score after 6 innings | Located |
| vis_home | Team batting: visitor (0) or home (1) | Categorical (0/1) | Assigns runs on the last play to the correct team | Located |
| runs | Runs scored on the play | Numeric (integer) | Added to the last play's score to get the final score | Located |
| gametype | Type of game: regular, wildcard, divisionseries, lcs, worldseries, allstar | Categorical | Filter for regular season games only | Located |
| date | Game date (YYYYMMDD) | Numeric (integer) | Orders plays chronologically | Located |
| gid | Game ID: home team code + date (YYYYMMDD) + game number (0 = single game, 1/2 = doubleheader) | Text | Identifier; grouping key for game-level tables | Located |
| season | Season when the game was played | Numeric (integer) | Grouping | Derived from date |
| pitteam | Pitching (fielding) team code | Categorical | Identifier | Located |
| batteam | Batting team code (32 teams, incl. All-Star squads) | Categorical | Identifier | Located |
| home_team | Team abbreviation for the home team | Text | Identifier | Derived from batteam |
| away_team | Team abbreviation for the visiting team | Text | Identifier | Derived from pitteam |
| home_win_pct, away_win_pct | Home and away team's winning records, respectively, derived from the home_win field as number of wins divided by number of games played calculated up to, but not including, the current game | Numeric (rational) | Predictor | Derived from home_win |
| home_final_score | Final box score for the home team for each game. Taken from the final play of each game accounting for home runs. | Numeric (integer) | Intermediate input to home_win | Derived from final play |
| away_final_score | Final box score for the away team for each game. Taken from the final play of each game accounting for home runs. | Numeric (integer) | Intermediate input to home_win | Derived from final play |
| home_perf_index | Derived from home_win_pct and away_win_pct (home_win_pct / away_win_pct, and if away_win_pct = 0 then number of home team's wins so far during that season. | Numeric (rational) | Predictor | Derived from home_win_pct and away_win_pct |
| home_hits_6, away_hits_6 | Total number of hits that occurred while the home team/away_team is batting through the end of the sixth inning of a given game. Sum of single, double, triple, and hr. | Numeric (integer) | Predictor | Derived |
| home_walks_6, away_walks_6 | Total number of walks (walk) to first base by the home team/away_team while batting through the sixth inning of a given game. | Numeric (integer) | Predictor | Derived |
| home_k_6, away_k_6 | Total number of strikeouts (k) while the home/away team is pitching/fielding through the sixth inning of a given game. | Numeric (integer) | Predictor | Derived |
| home_steals_6, away_steals_6 | Sum of occurrences of stealing second base, stealing third base, and stealing home plate by the home/away team through the sixth inning of a given game. Derived by summing sb2, sb3, and sbh occurrences by the home/away team. | Numeric (integer) | Predictor | Derived |
| home_errors_6, away_errors_6 | Total number of errors committed while the home/away team is fielding through the sixth inning of a given game. Derived by summing e1, e2, e3, e4, e5, e6, e7, e8, and e9 occurrences by the home/away team. | Numeric (integer) | Predictor | Derived |
| home_hits_total | Total hits in games played during the current season up to, but not including, the current game for the home team. | Numeric (integer) | Intermediate to OBP_home | Derived |
| away_hits_total | Total hits in games played during the current season up to, but not including, the current game for the away team. | Numeric (integer) | Intermediate to OBP_away | Derived |
| OBP_home | On-base percentage reflects the percentage of plate appearances that result in the batting team's player getting on base. For OBP_home, the value is an average for the entire home team that is calculated over the course of a given season up to, but not including, the current game. It is calculated as (home_hits_total + walk + hbp) / (ab + walk + hbp + sf), where home_hits_total is an intermediate derived field similar to home_hits_6 but including hits occurring after the sixth inning. | Numeric (rational) | Predictor | Derived |
| OBP_away | Same as OBP_home but for the away team. | Numeric (rational) | Predictor | Derived |
| home_inn7, home_inn8, home_inn9 | Runs scored by the home team in the 7th, 8th, and 9th innings respectively. | Numeric (integer) | Intermediate for home_late_runs_avg | Derived from inn7, inn8, inn9 |
| away_inn7, away_inn8, away_inn9 | Runs scored by the away team in the 7th, 8th, and 9th innings respectively. | Numeric (integer) | Intermediate for away_late_runs_avg | Derived from inn7, inn8, inn9 |
| home_late_runs_avg | Average runs scored in late innings (7, 8, and 9) in previous season games for the home team, not including the current game. | Numeric (rational) | Predictor | Derived from home_inn7, home_inn8, home_inn9 |
| away_late_runs_avg | Same as home_late_runs_avg but for the away team. | Numeric (rational) | Predictor | Derived from away_inn7, away_inn8, away_inn9 |
