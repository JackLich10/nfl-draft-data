
## Note

If you attempt to read in the .csv files in R with the commonly used `readr::read_csv` function, please use the parameter `guess_max = 13000` to avoid parsing errors (this has to do with how `readr` guesses column types using only the first 1000 rows). Alternatively, use the `read.csv` function which will handle this without intervention.

## Data Dictionaries

`nfl_draft_prospects.csv`

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
