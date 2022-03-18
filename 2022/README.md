# 2022 F1FantasyData

Price data from the F1 fantasy game. This data is gathered with the
[F1FantasyScraper](https://github.com/EduardoFAFernandes/F1FantasyScraper)
with some help from GitHub actions.

The file [prices.csv](prices.csv) has the price information.

Every row represents an asset (driver/team) in a given moment in time. A new
full snapshot is taken every hour, roughly, it depends on GitHub actions 
availability.

Here is a small description of the file:

| Field Name           | Description   								| Format 				|
| -------------------- | -------------------------------------------| --------------------- |
| id                   | ID of the asset   							| integer > 0 			|
| name                 | Name of the asset 							| string 				|
| price                | Price of the asset in millions				| float\* > 0 			|
| sentiment			   | How close the driver is to change price 	| integer [-100, 100]	|
| selection_percentage | Percentage of players that own the driver 	| integer [4, 100]\*\* 	|
| datetime             | Date and time of the snapshot 				| YYYY-MM-DD HH:MM:SS 	|
| timestamp            | Unix timestamp of the snapshot 			| integer > 0 			|

### Notes:
\* Although the value is a float it's always a float with 1 decimal place. If
multiplied by 10 can be seen as an int .

\*\* The developers don't provide further precision beyond 5% ownership, this
means that 4 is means less than 5% ownership.


