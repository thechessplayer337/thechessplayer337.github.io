# GeoSpy Changelog

## v1.4 — Cinematic Flow, Voting Discussion, and Endgame Recap

**Release date:** 2026-05-08

GeoSpy v1.4 improves the full game flow from start transition to voting discussion and endgame recap.

### Game Start

- Added a cinematic **Game Started** transition.
- Added a simulated loading bar and short start sound.
- Removed the older top game-start notification.
- Preserved the existing screenshot reveal sequence.

### Voting Discussion

- Added public **Voting Discussion** during the voting phase.
- Players may accuse, defend themselves, question others, or remain silent while voting is open.
- Voting Discussion uses the existing **60-second** voting timer.
- Normal description restrictions still apply.
- Votes still count only after pressing **Confirm Vote**.
- If all living players confirm their votes early, voting still ends immediately.
- Voting discussion messages are recorded in **Game Review**.

### Endgame Transition and Recap

- Added a cinematic victory transition before the recap screen.
- Victory text now fades in gradually.
- **Spies Win** uses a darker suspense theme.
- **Civilians Win** uses a brighter morning/daylight theme.
- Reworked the game over screen into a cleaner recap page.
- Added summary cards for:
  - civilian country
  - spy country
  - spy player / spy players
  - eliminated player / eliminated players
- Removed redundant **Final Result** and **Final Vote** sections.
- Removed the large personal screenshot from the top of the endgame screen.

### Players Revealed and Game Review

- Reworked **Players Revealed** into expandable player cards.
- Each card shows player name, role, country, status, description, screenshot, and full screenshot link.
- Fixed the bug where expanded cards collapsed immediately.
- Fixed expanded card layout so screenshots no longer squeeze role/country text.
- Renamed **Descriptions Recap** to **Game Review**.
- Game Review is collapsed by default.
- Game Review records descriptions, private chats, ready-to-vote choices, voting actions, round results, and game over state.
- Fixed the bug where Game Review collapsed immediately after opening.

### Host Controls and UI Fixes

- Host shortcut controls remain available during active games.
- Top-right host controls are hidden after game over because recap controls appear at the bottom.
- Fixed feedback modal colors during the dark in-game theme.
- Improved secondary button visibility in dark panels.
- Added minor UI polish and countdown feedback improvements.

### Countdown Audio and Timer Feedback

- Added red styling for final countdown seconds.
- Description and active private chat countdowns turn red during the final **5 seconds**.
- Private chat request countdown turns red during the final **3 seconds**.
- Added countdown tick sounds for description turns and active private chat.
- Countdown ticks now play once per second and use a lower, heavier sound.

---

## v1.3 — Gameplay Balance and Expanded Private Chat

**Release date:** 2026-05-07

GeoSpy v1.3 adjusts game pacing and makes private chat more useful in larger rooms.

### Speaking Timer

- Reduced each player's speaking time from **60 seconds** to **45 seconds**.

### Private Chat

- Reduced accepted private chat duration from **90 seconds** to **60 seconds**.
- Changed private chat opportunities from **one per player per game** to:

    Private chat opportunities per player = total player count - 2

| Players | Private chat opportunities per player |
|---:|---:|
| 3 | 1 |
| 4 | 2 |
| 5 | 3 |
| 6 | 4 |

- Private chat opportunities are consumed only when the request is **accepted**.
- Refused or timed-out requests do **not** consume a private chat opportunity.
- Added interface feedback showing remaining private chat opportunities.

---

## v1.2 — Website Integration and Cinematic UI Update

**Release date:** 2026-05-05 to 2026-05-07

GeoSpy v1.2 improves website integration and upgrades the visual presentation of the playable prototype.

### Website Integration

- Added **GeoSpy** to The Chessplayer homepage navigation.
- Added a **Try GeoSpy** button to the homepage hero section.
- Connected the homepage call-to-action directly to `geospy.html`.
- Added a direct **Read rules** link to the public Google Docs rules document.

### Homepage and Landing Page Visual Refresh

- Reworked the homepage visual concept around **From Board Vision to World Vision**.
- Added chessboard-inspired and latitude/longitude visual elements.
- Simplified the slogan area.
- Replaced the Contact card’s old `Back to top` link with a Discord link.
- Added a standalone floating `Back to top` button.
- Centered the GeoSpy Create / Join layout.
- Added a world-map / globe-projection background.
- Removed the old GeoSpy title orbit effect.
- Added subtle moving light points over the map/grid background.

### Cinematic In-game Layout

- Added a darker cinematic layout after the game starts.
- Made the player screenshot the visual focus.
- Added gradual image reveal and subtle golden frame glow.
- Reduced visual clutter during active gameplay.
- Kept description, voting, private chat, result, feedback, and host controls available in cleaner layouts.

---

## v1.1 — Feedback, Rejoin, and Room Control Stability

**Release date:** 2026-05-02 to 2026-05-03

GeoSpy v1.1 improves stability, feedback reporting, rejoin support, notifications, and host room control.

### Feedback System

- Added a bottom-right **Feedback** button.
- Added **Report this image** in the player screenshot panel.
- Added feedback categories for bad images, broken images, wrong country, unfair pairs, bugs, and suggestions.
- Feedback is saved to Firebase under:

    feedback/{feedbackId}

- Feedback automatically records useful context such as room, player, phase, round, screenshot filename, country pair, page URL, and browser info.
- Fixed feedback privacy so hidden role/country information is not displayed in the feedback window during the game.

### Rejoin and Image Stability

- Added support for players rejoining with the same room code and player name.
- Rejoining restores role, country, screenshot, alive/out status, description state, and vote state.
- Prevented new players from joining after a game has started.
- Fixed an issue where screenshots could change between rounds.
- Player screenshots now stay fixed for the whole game.

### Ready-to-vote and Notifications

- Fixed ready-to-vote logic so the stage no longer ends too early.
- Voting begins once confirmed Agree votes reach the threshold.
- A new description round begins only when reaching the Agree threshold becomes impossible.
- Added a game-start notification with a **View image** button.
- Fixed cases where non-host players could miss the game-start notification.
- Added a short notification sound.

### Room Management

- Added host-only **Restart game** after game over.
- Added host-only **Back to Lobby** after game over.
- Added host-only **Restart game** during active rounds.
- Restart game keeps the same room and players but assigns new roles, countries, and screenshots.
- Back to Lobby fully resets the current room.

---

## v1.0 — Official Playable Release

**Release date:** 2026-05-02

GeoSpy v1.0 is the first complete playable release of the project: a multiplayer social deduction game using real GeoGuessr-style screenshot data.

### Core Gameplay

- Added complete multiplayer room flow.
- Supported **3–6 player** rooms.
- Added role assignment:
  - 3 players: 2 civilians, 1 spy
  - 4 players: 3 civilians, 1 spy
  - 5 players: 4 civilians, 1 spy
  - 6 players: 4 civilians, 2 spies
- Added civilian and spy country assignment using similar country/region pairs.
- Added random speaking order, description rounds, ready-to-vote stage, voting stage, tie handling, eliminations, and win conditions.
- Added automatic random vote assignment for missing votes.
- Added `NULL` descriptions when a player fails to submit in time.

### Screenshot Dataset

- Added a cleaned screenshot dataset with **7,891 playable images**.
- Removed detected black/blank screenshots.
- Uploaded the dataset to Cloudflare R2.
- Connected the frontend to R2-hosted screenshots.
- Added screenshot-to-country indexing.
- Added direct in-game screenshot display and **Open full screenshot** links.

### Country and Pair System

- Added **87 countries/regions**.
- Added **100 similar country/region pairs**.
- Published the country/region list and pair table as a rules appendix.

### Private Chat

- Added one private chat opportunity per player per game.
- Private chat can only be requested during the player’s own speaking turn.
- Added accept/refuse window, automatic refusal, private chat timer, timer pause/resume, and private-only messages.

### Post-game Reveal and Room Management

- Added post-game reveal of other players’ images, countries, roles, and descriptions.
- Added room creation, joining by room code, invite link copying, host start control, and room reset.

### Documentation

- Published **GeoSpy Game Rules Version 1.0**.
- Published **GeoSpy Country/Region List and Pair Table Version 1.0**.

### Known Issues

- Some screenshots may still be blurry or low quality.
- Some country/region pairs may need balancing after more testing.
- Future versions may clean, replace, or expand the screenshot dataset.
