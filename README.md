# ⚽ Football League Database Management System 🏟️

Welcome to the **Football League Database Management System**! This project is designed to simulate the data management operations of a football league. From teams and players to matches and stadiums, this database captures all the essential information for running a football league, complete with match results, player statistics, team stats, and official roles.

## 🎯 **Project Overview**

This project demonstrates the structure of a football league by creating and managing data for:
- **Teams** 🏆
- **Players** 👥
- **Matches** ⚔️
- **Stadiums** 🏟️
- **Officials** 🧑‍⚖️
- **Seasons** 📅
- **Team Stats** 📊
- **Player Stats** ⚡

### 🚀 Features

- **Team Management**: Store and manage team details including name, city, coach, captain, and foundation year.
- **Player Management**: Track player details such as nationality, position, date of birth, and team associations.
- **Match Scheduling**: Record match results, venues, teams involved, and match outcomes.
- **Official Roles**: Assign referees, assistant referees, and other officials to matches.
- **Seasonal Tracking**: Manage seasons with team and player performance stats.
- **Data Relationships**: Ensure proper foreign key relationships between teams, players, stadiums, matches, and officials.

## 🏗️ **Database Schema**

This database consists of **8 main tables** and their relationships.

### 1. `Teams` Table 🏆
Stores the teams competing in the league.

| Column       | Description                            |
|--------------|----------------------------------------|
| `team_id`    | Unique team identifier (PK)            |
| `team_name`  | Name of the team                       |
| `city`       | City where the team is based           |
| `coach_name` | Team coach's name                      |
| `captain_name`| Team captain's name                   |
| `founded_year`| Year the team was founded             |

### 2. `Players` Table 👥
Manages player details, their position, and association with a team.

| Column         | Description                            |
|----------------|----------------------------------------|
| `player_id`    | Unique player identifier (PK)          |
| `player_name`  | Name of the player                     |
| `nationality`  | Player's nationality                   |
| `position`     | Playing position (Forward, Midfielder) |
| `date_of_birth`| Player's date of birth                 |
| `team_id`      | Foreign key linking to `Teams`         |

### 3. `Matches` Table ⚔️
Records match results, venue, and the teams involved.

| Column           | Description                            |
|------------------|----------------------------------------|
| `match_id`       | Unique match identifier (PK)           |
| `date`           | Date of the match                      |
| `venue`          | Venue of the match                     |
| `result`         | Match result (goals for each team)     |
| `winning_team_id`| Team ID of the winning team            |
| `losing_team_id` | Team ID of the losing team             |
| `stadium_id`     | Foreign key linking to `Stadiums`      |
| `season_id`      | Foreign key linking to `Seasons`       |

### 4. `Stadiums` Table 🏟️
Stores information about the stadiums used for the matches.

| Column         | Description                            |
|----------------|----------------------------------------|
| `stadium_id`   | Unique stadium identifier (PK)         |
| `stadium_name` | Name of the stadium                    |
| `city`         | City where the stadium is located      |
| `capacity`     | Seating capacity of the stadium        |

### 5. `Seasons` Table 📅
Tracks the different seasons in the football league.

| Column      | Description                            |
|-------------|----------------------------------------|
| `season_id` | Unique season identifier (PK)          |
| `start_year`| Start year of the season               |
| `end_year`  | End year of the season                 |

### 6. `Officials` Table 🧑‍⚖️
Tracks the match officials, their roles, and nationality.

| Column        | Description                            |
|---------------|----------------------------------------|
| `official_id` | Unique official identifier (PK)        |
| `official_name`| Name of the official                  |
| `roles`       | Role of the official (e.g., Referee)   |
| `nationality` | Official's nationality                 |
| `match_id`    | Foreign key linking to `Matches`       |

### 7. `Teams_Stats` Table 📊
Stores seasonal statistics for each team.

| Column           | Description                            |
|------------------|----------------------------------------|
| `team_stats_id`   | Unique stats identifier (PK)           |
| `team_id`         | Foreign key linking to `Teams`         |
| `season_id`       | Foreign key linking to `Seasons`       |
| `wins`            | Number of wins for the team            |
| `losses`          | Number of losses for the team          |
| `draws`           | Number of draws for the team           |
| `goals_for`       | Goals scored by the team               |
| `goals_against`   | Goals conceded by the team             |

### 8. `Players_Stats` Table ⚡
Tracks the individual performance of each player during the season.

| Column           | Description                            |
|------------------|----------------------------------------|
| `player_stats_id` | Unique stats identifier (PK)           |
| `player_id`       | Foreign key linking to `Players`       |
| `season_id`       | Foreign key linking to `Seasons`       |
| `appearances`     | Number of appearances in matches       |
| `goals_scored`    | Number of goals scored by the player   |
| `assists`         | Number of assists by the player        |
| `yellow_cards`    | Number of yellow cards                 |
| `red_cards`       | Number of red cards                    |

## 📊 **Sample Queries**

### 1. **View All Player Stats** ⚡
```sql
SELECT * FROM Players_Stats;
```

### 2. **Find Match Results for a Specific Team** ⚔️
Retrieve all the matches where `Manchester United` was involved:
```sql
SELECT * FROM Matches WHERE winning_team_id = 1 OR losing_team_id = 1;
```

### 3. **Get All Team Stats for a Specific Season** 📊
```sql
SELECT * FROM Teams_Stats WHERE season_id = 1;
```

### 4. **List Players by Team** 👥
Find all players in `Liverpool FC`:
```sql
SELECT * FROM Players WHERE team_id = 2;
```

### 5. **Official Roles for a Specific Match** 🧑‍⚖️
Find officials for match `1`:
```sql
SELECT * FROM Officials WHERE match_id = 1;
```

## 📂 **How to Run the Project**

1. **Set up MySQL Database**: Install MySQL on your system and create a database using the provided SQL script.
2. **Run the SQL Script**: Use a MySQL client or command line to run the SQL script and generate all the tables, relationships, and sample data.
3. **Query the Data**: Use the provided SQL queries or create your own to interact with the data.

## 🚀 **Future Enhancements**

- Add more seasons and expand team rosters.
- Create triggers for automatic updates on player stats when match results are recorded.
- Implement stored procedures for more complex operations like calculating league standings dynamically.
  
## 📝 **License**
This project is free to use for educational, personal, or commercial purposes.

Enjoy managing the **Football League Database**! ⚽👨‍💻

--- 
Hope you have an exciting time using and expanding this football league database! 🎉
