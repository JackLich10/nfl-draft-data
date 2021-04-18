
## Notes

Please read the data dictionaries for descriptions of each dataset and descriptions of the variables present.

If you attempt to read in the .csv files in R with the commonly used `readr::read_csv` function, please use the parameter `guess_max = 13000` to avoid parsing errors (this has to do with how `readr` guesses column types using only the first 1000 rows). Alternatively, use the `read.csv` function which will handle this without intervention.

If you are joining the datasets together, the value `player_id` is uniquely identified across all data. Be wary of `pos_abbr`, as the abbreviations sometimes (though rarely) differ across datasets. I have had no issues with `school`, `school_name`, and `school_abbr`, but `player_id` will always join the data correctly.

If you are joining in ESPN college QBR statistics from `college_qbr.csv`, join by `guid` and `player_name`.

## Data Dictionaries


`nfl_draft_prospects.csv`


Information on previous NFL draft prospects dating back to 1967 (first year of the common draft). If the player has `NA` values for `pick`, `overall`, and `round`, it means he went undrafted or the draft has not occurred yet (for current year prospects).

|variable       |class     |description              |
|:--------------|:---------|:------------------------|
|year           |integer   |year of draft            |
|player_id      |character |unique player ID         |
|guid           |character |guid                     |
|player_name    |character |name of player           |
|position       |character |position                 |
|pos_abbr       |character |position abbreviation    |
|school         |character |school                   |
|school_name    |character |school name              |
|school_abbr    |character |school abbreviation      |
|weight         |double    |weight (lbs)             |
|height         |double    |height (inches)          |
|link           |character |player link              |
|pick           |integer   |pick in round            |
|overall        |integer   |overall pick in draft    |
|round          |integer   |round in draft           |
|traded         |logical   |pick traded?             |
|trade_note     |character |trade note               |
|team           |character |NFL team                 |
|team_abbr      |character |NFL team abbreviation    |
|team_logo_espn |character |NFL team logo            |
|pos_rk         |double    |ESPN position rank       |
|ovr_rk         |double    |ESPN overall rank        |
|grade          |double    |ESPN player grade        |
|player_image   |character |player image             |


`nfl_draft_profiles.csv`


Information on NFL draft prospects including pre-draft text analysis in columns `text*` for * in 1, 2, 3, 4.

|variable     |class     |description  
|:------------|:---------|:--------------------------|
|player_id    |character |unique player ID           |
|guid         |character |guid                       |
|player_name  |character |player name                |
|position     |character |position                   |
|pos_abbr     |character |position abbreviation      |
|weight       |double    |weight (lbs)               |
|height       |double    |height (inches)            |
|player_image |character |player image               |
|link         |character |player link                |
|school_logo  |character |school logo                |
|school       |character |school                     |
|school_abbr  |character |school abbreviation        |
|school_name  |character |school name                |
|pos_rk       |double    |ESPN position rank         |
|ovr_rk       |double    |ESPN overall rank          |
|grade        |double    |ESPN player grade          |
|text1        |character |prospect analysis 1        |
|text2        |character |prospect analysis 2        |
|text3        |character |prospect analysis 3        |
|text4        |character |prospect analysis 4        |


`college_qbr.csv`


ESPN college QB QBR metrics for every quarterback in college football since 2004. Please join in this dataset using `guid` and `player_name`.

|variable     |class     |description                                                                                                                            |
|:------------|:---------|:--------------------------------------------------------------------------------------------------------------------------------------|
|season       |integer   |college season                                                                                                                         |
|guid         |character |guid                                                                                                                                   |
|player_name  |character |player name                                                                                                                            |
|age          |double    |current age                                                                                                                            |
|total_qbr    |double    |Adjusted Total QB Rating, which values the QB on all play types on a 0-100 scale adjusted for the strength of opposing defenses faced. |
|points_added |double    |Number of points contributed by a QB, accounting for QBR and how much he plays, above the level of an average quarterback.             |
|qb_plays     |double    |Plays on which the QB has a non-zero expected points contribution. Includes most plays that are not handoffs.                          |
|total_epa    |double    |Total expected points added with low leverage plays, according to ESPN Win Probability model, down-weighted.                           |
|pass         |double    |Expected points added on pass attempts with low leverage plays down-weighted.                                                          |
|run          |double    |Clutch-weighted expected points added through rushes                                                                                   |
|exp_sack     |double    |Clutch-weighted expected points added (lost) from sacks (not fumbles that may occur because of sacks)                                  |
|penalty      |double    |Expected points added on penalties with low leverage plays down-weighted.                                                              |
|raw_qbr      |double    |Raw Total QB Rating, which values QB on all play types on a 0-100 scale (not adjusted for opposing defenses faced)                     |
|sack         |double    |Expected points added on sacks with low leverage plays down-weighted.                                                                  |


`ids.csv`


Information for joining a player's ESPN ID (commonly referred to as `player_id` in many datasets) with their ID in the `nflfastR` package. At this time, it only has data for QB's. Might add in receivers and running backs later.

|variable             |class     |description                  |
|:--------------------|:---------|:----------------------------|
|espn_id              |character |unique player ID from ESPN   |
|player_name          |character |player name                  |
|nflfastR_id          |character |unique player ID in nflfastR |


`college_stats.csv`


NFL draft prospect counting statistics in college. Includes counting statistics like interceptions, tackles, receiving touchdowns, passing touchdowns, etc. by a player's college season.

|variable             |class     |description                |
|:--------------------|:---------|:--------------------------|
|player_id            |character |unique player ID           |
|alt_player_id        |character |alternate player ID        |
|player_name          |character |player name                |
|pos_abbr             |character |position abbreviation      |
|school               |character |school                     |
|school_abbr          |character |school abbreviation        |
|school_primary_color |character |school primary color       |
|school_alt_color     |character |school alternate color     |
|season               |integer   |college season             |
|statistic            |character |statistic                  |
|value                |double    |statistic value            |
|active               |logical   |active player?             |
|all_star             |logical   |all star in college?       |
