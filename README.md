# NFL Playcalling and Aggressiveness Over Time
This project analyzes NFL play-by-play data for the 2022–2024 seasons, focusing on how teams call plays (pass vs. run) by down and distance, and measures trends in playcalling aggressiveness, play success, and conversion rates. It automatically generates team-level visualizations and CSV summaries for transparency and onward research.

## Features
Download and Process 2022–2024 NFL Play-by-Play Data: Uses nfl_data_py

Playcalling Profile Charts: Saves team-level PDF bar charts of pass/run tendency by down and distance bucket (short, medium, long, very long), per season

Pass/Run Rate Trends: Exports CSV with each team’s pass/run percentage by down/distance/play type and year-over-year changes

Success & Conversion Analysis: Breaks down third/fourth down conversion rates and play “success” (per NFL analytics definition), with year-to-year deltas

EPA Summaries: Optional (user can adapt) average EPA (Expected Points Added) per play for offense/defense, by team and situation

## Dependencies
This notebook requires:

Python 3.8+

nfl_data_py>=0.3.3

pandas>=1.5

matplotlib>=3.10

seaborn>=0.13

numpy

All requirements can be installed with:

```
pip install nfl_data_py pandas matplotlib seaborn numpy
```

### Data Sourcing
All NFL play-by-play data is loaded using the nfl_data_py package. Data is sourced directly from the NFLverse repository, which is routinely updated for recent seasons.

## Generated Outputs
### 1. Team Playcalling Frequency Charts (PDFs)
Bar chart PDF for each team (one file per team) in:

```
NFL_Team_play_type_frequency_charts/<TEAM>/<TEAM>_2022_2024_pass_run_by_down_and_distance.pdf
```

Each bar (horizontal) is labeled by down, distance bucket, and play type, e.g., “D1-short-pass”.

## 2. Team Playcalling Trends (CSV)

CSV summarizing the pass/run percentage split (and year-to-year change) by team, down, distance, and play type:

```
NFL_Team_play_type_frequency_charts/team_playcalling_rate_trends.csv
```

## 3. Success & Conversion Summary (CSV)

Aggregates play “success” rate and actual third/fourth down “conversion” rate by team, down, distance, and play type, with year-on-year deltas, plus team totals:

```
NFL_Team_play_type_frequency_charts/team_playcalling_conversion_success_trends.csv
```

## Analysis Steps
Column Listing: The notebook first lists all available play-by-play column names for reference.

Data Download: Loads and filters play records for 2022, 2023, and 2024 with required columns via nfl_data_py.import_pbp_data.

Down/Distance Buckets: Buckets plays by standard down (1–4) and distance (“short” 1–3, “medium” 4–7, “long” 8–10, “very long” 11+).

Aggregation: Calculates counts and percentages for pass/run plays for every [team, down, distance, season] slice.

Chart Output: Produces and saves horizontal bar charts of play type frequency for all teams.

CSV Output: Exports all calculated split percentages and year-over-year changes.

Play Success & Conversion: Aggregates and outputs team and situation “success rate” and “conversion rate” by play type and distance, with deltas.

EPA Analysis (Optional, Example): Displays top teams by EPA per play, per season, and situational breakdowns.

## Customizing
Years: Modify the years = [2022, 2023,[2024] list as desired.

Extra Situations: Expand distance buckets or chart types as needed.

Visualization tweaks: Change color schemes or plot layouts in the matplotlib code.

Further stats: Add more advanced stats (EPA, win probability, rush/pass EPA splits, etc.) using additional columns from the play-by-play data.

## Example Usage
Run the notebook in a Jupyter environment or as a standalone. Once run, output PDFs and CSVs are ready for further analysis.

## Notes
This analysis only considers regular play types (passes and runs) and standard down/distance situations.

For small fourth down sample sizes, interpret conversion percentages with caution.

EPA and team success rankings can be added/adapted as shown in the notebook.
