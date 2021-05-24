# F1FantasyData
Price data from the F1 fantasy game. This data is gathered with the [F1FantasyScraper](https://github.com/EduardoFAFernandes/F1FantasyScraper)

The main file in this repository is [raw_data.csv](raw_data.csv) and **may be subject to changes**.
The changes include but are not limited to: renaming, relocating, adding/removing/renaming columns.
The file is updated everyday at 18:40 GMT+1.

Every row represents an asset (driver/team) in a given moment in time.
The data starts 31/03/2021 00:06:14 so the first days after the first race are not present.
A new full snapshot is taken every 10 minutes but only saved if there are any differences to the previous full snapshot.
This implies that if only one asset changes all other assets will be saved along with the one that changed.
Furthermore there are gaps when no data was recorded, do to some downtime.

Here is a small description of the file:

| Field Name                        | Description   | Format |
| --------------------------------- | ------------- | ------- |
| id                                | ID of the asset   | integer > 0|
| name                              | Name of the asset | string |
| price                             | Price of the asset in millions| float\* > 0 |
| price_delta_season                | Price difference since the first race in millions | float* |
| price_delta_race                  | Price difference since the last race in millions | float |
| probability_price_up_percentage   | How close the driver is to increase 0.1 in price | integer [0, 100] |
| probability_price_down_percentage | How close the driver is to decrease 0.1 in price | integer [0, 100] |
| selection_percentage              | Percentage of players that own the driver | integer [4, 100]\*\* |
| selection_percentage_delta_season | Difference in the percentage of ownership since the start of the season | integer [-100, 100]
| datetime                          | Date and time of the snapshot | YYYY-MM-DD HH:MM:SS |
| timestamp                         | Unix timestamp of the snapshot | integer > 0 |

### Notes:
\* Although the value is a float it's always a float with 1 decimal place. If multiplied by 10 can be seen as an int .

\*\* The developers don't provide further precision beyond 5% ownership, this means that 4 is means less than 5% ownership.

I do not include a continuous sentiment variable because it is easy to calculate that with only the information of one line.
`sentiment = price_delta_start * 10000 + probability_price_up_percentage - probability_price_down_percentage`
