# GeoSpy Game Rules

**Version:** 1.0  
**Language:** English  
**Status:** Official rules document

## 1. Game Overview

GeoSpy is a screenshot-based social deduction game. Each player receives a hidden geography screenshot and must describe it, reason from other players' descriptions, and vote to identify the player or players whose screenshots come from a different country or region.

Most players are **Civilians**. Civilians receive screenshots from the same country or region. A smaller number of players are **Spies**. Spies receive screenshots from a similar but different country or region.

## 2. Player Count and Roles

GeoSpy supports **3–6 players**.

| Players | Civilians | Spies |
|---:|---:|---:|
| 3 | 2 | 1 |
| 4 | 3 | 1 |
| 5 | 4 | 1 |
| 6 | 4 | 2 |

Roles are assigned automatically when the game starts.

## 3. Screenshots and Country/Region Assignment

1. Each player receives one hidden screenshot.
2. Civilians receive screenshots from the same country or region.
3. Spies receive screenshots from a similar but different country or region.
4. Players cannot view other players' screenshots during the game.
5. Other players' screenshots may be viewed only after the game ends.

## 4. Game Flow

Each round proceeds in the following order:

1. Description phase
2. Ready-to-vote confirmation phase
3. Voting phase
4. Result phase
5. Next round or game over

## 5. Description Phase

### 5.1 Speaking Order

At the beginning of each description round, the system randomly generates a speaking order.

Players must speak in the assigned order. A player may submit a description only during their own speaking turn.

### 5.2 Speaking Timer

Each player has **60 seconds** to submit a description.

If a player does not submit a description within 60 seconds, the system records that player's description as:

```text
NULL
```

`NULL` is displayed in a visually muted style and counts as that player's completed description for the round.

### 5.3 Description Restrictions

Players should describe geographic, environmental, road, architectural, vegetation, climate, or visual features shown in their screenshot.

Players should not directly state:

- the country or region name
- the city name
- the language name
- a flag, emblem, or explicit national symbol
- exact text that directly reveals the country or region

Descriptions should be indirect and should support deduction without directly revealing the answer.

## 6. Private Chat

Each player has **one private chat opportunity per game**.

### 6.1 Requesting Private Chat

A player may request private chat only during their own speaking turn. The player must choose one living player as the private chat target.

### 6.2 Accepting or Refusing

The invited player has **15 seconds** to accept or refuse the private chat request.

If the invited player refuses, or does not respond within 15 seconds, the request is treated as refused.

### 6.3 Private Chat Duration

If accepted, the two players receive **90 seconds** of private chat time.

The speaking timer is paused during private chat. After private chat ends, the original speaker's remaining speaking time resumes.

### 6.4 Visibility

Private chat messages are visible only to the two participating players.

## 7. Ready-to-Vote Confirmation Phase

After all living players have completed their descriptions, the game enters the ready-to-vote confirmation phase.

Each living player may choose:

- **Agree to Vote**
- **Refuse to Vote**

A choice counts only after the player presses **Confirm**. A player may cancel an unconfirmed choice.

### 7.1 Resolution Rule

The game enters the voting phase if confirmed Agree votes reach at least half of the living players.

The system does not resolve the phase early while the result can still change.

If it becomes mathematically impossible for Agree votes to reach the required threshold, the game proceeds to a new description round.

If the timer expires, all unconfirmed players are treated as Refuse.

## 8. Voting Phase

During the voting phase, each living player votes for one living player to be eliminated.

### 8.1 Voting Timer

The voting phase lasts **60 seconds**.

### 8.2 Confirmed Votes

A vote counts only after the player presses **Confirm Vote**.

### 8.3 Missing Votes

If a player does not confirm a vote before the timer expires, the system randomly assigns that player's vote to another living player.

### 8.4 Tied Votes

If the highest vote total is tied, no player is eliminated.

The game proceeds to the next description round, and all surviving players keep their original screenshots.

### 8.5 Elimination

If one player receives the highest number of votes, that player is eliminated and cannot participate in later speaking or voting phases.

## 9. Win Conditions

### 9.1 Civilian Victory

Civilians win when all Spies have been eliminated.

### 9.2 Spy Victory

Spies win when the number of living Spies is greater than or equal to the number of living Civilians.

## 10. Game Over and Information Reveal

When the game ends, the system reveals:

1. each player's role
2. each player's country or region
3. the final result
4. other players' screenshots, if the player chooses to view them

Before the game ends, other players' screenshots and roles remain hidden.

## 11. Room Management

1. The player who creates the room is the host.
2. The host selects the room size before the game begins.
3. The host may start the game once the room is full.
4. The host may reset the room.
5. Resetting the room returns players to the initial create/join screen.

## 12. Rejoining a Game

If a player disconnects, refreshes, or accidentally closes the page, they may rejoin the game by entering:

1. the same room code
2. the same player name used earlier in the game

Rejoining restores the original player slot and preserves the player's role, country or region, screenshot, alive/out status, description state, and vote state.

New players may not join a game after it has started.

## 13. Feedback and Issue Reporting

Players may use the in-game feedback system to report:

- blurry or low-quality screenshots
- black or broken screenshots
- wrong-country screenshots
- unfair or questionable country pairs
- game-flow bugs
- general suggestions

When feedback is submitted during a game, the system automatically attaches relevant context, including the room code, round number, player name, country or region code, screenshot filename, and screenshot URL.

## 14. Supplementary Notes

1. The game uses a fixed screenshot dataset and a predefined country/region pair table.
2. The game only selects from country/region pairs that are currently available in the dataset.
3. The country/region list and pair table are public and are provided as a rules appendix.
