# F1FantasyData
Price data from the f1 fantasy game. This data is gatherd with the [F1FantasyScraper](https://github.com/EduardoFAFernandes/F1FantasyScraper)

The main file in this repository is [raw_data.csv](raw_data.csv) and **may be subject to changes**.
The changes include but are not limited to: renaming, relocating, adding/removing/renaming columns.

Every row represents an asset (driver/team) in a given moment in time.
The data starts 31/03/2021 00:06:14 so the first days after the first race are not present.
Furthermore tere are gaps when no data was recorded.

Here is a small description of the file:

| Field Name                        | Description   | Format |
| --------------------------------- | ------------- | ------- |
| id                                | ID of the asset   | integer > 0|
| name                              | Name of the asset | string |
| price                             | Price of the asset in millions| float\* > 0 |
| price_delta                       | Price diference since the first race in milions | float* |
| probability_price_up_percentage   | How close the driver is to increase 0.1 in price | integer [0, 100] |
| probability_price_down_percentage | How close the driver is to decrease 0.1 in price | integer [0, 100] |
| current_selection_percentage      | Percentage of players that own the driver | integer [0, 100] |
| datetime                          | Date and time of the snapshot | YYYY-MM-DD HH:MM:SS[.ffff] |

\* Altho the value is a float it's always a float with 1 decimal place. If multiplied by 10 can be seen as an int .
