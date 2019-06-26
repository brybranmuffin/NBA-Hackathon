# NBA-Hackathon

Added a high-level workflow.

## Workflow

 1. lineup, game_events, event_lookup
	 - starting tables


 2. substitutions = [`Game_ID`, `Player_ID`, `in/out boolean`, `time`]
	 - use game_events to get when each player was in or out and at what time


 3. player_times = [`Game_ID`, `Player_ID`, `times on court [(start, end), ...]`]
	  - use substitutions to get a list of times each player is on the court


 4. point_times = [`Game_ID`, `Team_ID`, `time`, `number of points`, `scored/allowed boolean`]
	 - use game_events to get when a point is scored. 
     - Each score event in game_events will have 2 rows in point_times
         - one for team scoring
         - one for team allowing


 5. points_per_player = [`Game_ID`, `Player_ID`, `Points scored while on court`, `Points allowed while on court`, `Number of possessions`]
	 - use player_times and point_times to get number of points scored and allowed while that player is on the court
	 - get number of possessions from game_events


 6. player_rating = [`Game_ID`, `Player_ID`, `OffRtg`, `DefRtg`]
	 - use points_per_player to get offensive and defensive rating


let me know if I missed anything

-Brian 6/26 2:55 pm

***

We still need to merge the lineup and game tables so that player 1, player 2, and player 3 will have their teams clearly written out

About the game table: event 12 indicates start of a period game, we will get starting lineups for that period from the lineups table. we can talk about our approach to this problem later, but I outlined one way to do it in the NBA file. 

Haven't started the other problem yet

-Bryant 6/26 12:39 pm

