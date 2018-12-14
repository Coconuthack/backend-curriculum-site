---
layout: page
title: Team Statistics
---

Each of the methods below take a team id as an argument. Using that team id, your instance of StatTracker will provide statistics for a specific team.

| Method | Description | Return Value |
| ------ | ----------- | ------------ |
| `team_info` | A hash with key/value pairs for each of the attributes of a team. | Hash |
| `best_season` | Season with the highest win percentage for a team. | Integer |
| `worst_season` | Season with the lowest win percentage for a team. | Integer |
| `average_win_percentage` | Average of all of the seasons win percentages for a team. | Decimal |
| `most_goals_scored` | Highest number of goals a particular team has scored in a single game. | Integer |
| `fewest_goals_scored` | Lowest numer of goals a particular team has scored in a single game. | Integer |
| `favorite_opponent` | Name of the opponent that has the lowest win percentage against the given team. | String |
| `rival` | Name of the opponent that has the highest win percentage against the given team. | String |
| `biggest_team_blowout` | Biggest difference between team goals and opponent goals for a win for the given team. | Integer |
| `worst_loss` | Biggest difference between team goals and opponent goals for a loss for the given team. | Integer |
| `head_to_head` | Record (as a hash - win/loss/tie) against a specific opponent  | Hash |
| `seasonal_summary`| For each season that the team has played, a hash that has two keys (`:preseason`, and `:regular_season`), that each point to a hash with the following keys: `:win_percentage`, `:total_goals_scored`, `:total_goals_against`, `:average_goals_scored`, `:average_goals_against` | Hash |
