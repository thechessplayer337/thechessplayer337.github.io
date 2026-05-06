# GeoSpy Changelog

## v1.1.8 — Contact section polish

**Release date:** 2026-05-06

- Replaced the Contact card’s `Back to top` link with a Discord link.
- Added a standalone floating `Back to top` button in the bottom-right corner.
- Kept the button style consistent with the navigation button used on Beginner Notes.

## v1.1.7 — Website Integration and Visual Refresh

**Release date:** 2026-05-05

This update improves how GeoSpy appears on The Chessplayer website and makes the playable prototype easier to access from the homepage.

### Homepage Integration

- Added a direct **GeoSpy** item to the main homepage navigation bar.
- Added a **Try GeoSpy** button to the homepage hero section.
- Updated the button layout so **Try GeoSpy** aligns with the two main hero buttons and no longer appears too short.
- Connected the homepage call-to-action directly to `geospy.html`.

### Homepage Visual Refresh

- Reworked the homepage hero illustration around the slogan **“From board vision to world vision.”**
- Added a board-to-world visual concept:
  - left side: chessboard-style grid
  - right side: latitude/longitude globe-style grid
  - center: chess piece bridge between board vision and world vision
- Reduced the feeling of a separate beige illustration block by integrating the board and map elements into one blended visual panel.

### GeoSpy Landing Page Design

- Centered the GeoSpy entry layout and Create / Join card.
- Added a subtle world-map / globe-projection background behind the page.
- Increased background color depth while keeping text readable.
- Adjusted the animated light orbit so it surrounds the **GeoSpy** title without covering the letters.
- Moved **Back to Home** to the far left of the page for clearer navigation.

### Notes

- This is a visual and navigation update only.
- Core gameplay logic, Firebase room flow, screenshot assignment, feedback submission, and voting systems are unchanged.

---

## v1.1.6 — Active Game Restart Hotfix

**Release date:** 2026-05-03

This hotfix improves host control during active games.

### Room Management Fixes

- Added a host-only **Restart game** button during active rounds.
- The host can now restart the current game before it ends.
- Restart game keeps the same room and the same players.
- Restart game immediately assigns new roles, countries/regions, and screenshots.
- This is useful when a game needs to be restarted because of a bad image, a flow issue, or a player-side problem.
- **Back to Lobby** remains available as a full room reset option.

---

## v1.1.5 — Notification Timing and Sound Hotfix

**Release date:** 2026-05-03

This hotfix improves the game start notification experience.

### Start Notification Fixes

- Fixed an issue where non-host players could miss the game start notification.
- The game start notification now appears for all players.
- If a player's page is in the background when the game starts, the notification appears when they return to the tab.
- Reduced the notification duration to **3 seconds**.
- Added a short notification sound when the game starts.
- If the browser blocks autoplay audio, the notification still appears silently.

---

## v1.1.4 — Clean Back to Lobby Hotfix

**Release date:** 2026-05-03

This hotfix clarifies and fixes the post-game room reset flow.

### Room Management Fixes

- Updated **Back to Lobby** so it fully resets the current room.
- Back to Lobby now deletes the active room and returns all players to the clean Create / Join screen.
- Players who want to change room size must now create a new room after returning to lobby.
- This prevents confusion between restarting the same game room and creating a fresh room with a different player count.
- **Restart game** remains available for the host after game over and keeps the same room and same players.

---

## v1.1.3 — Restart Game and Back to Lobby Controls

**Release date:** 2026-05-03

This update improves the post-game host controls.

### Post-game Controls

- Added a host-only **Restart game** button after game over.
- Restart game keeps the same room and the same players.
- Restart game immediately starts a new game with new roles, countries/regions, and screenshots.
- Added a host-only **Back to Lobby** button after game over.
- Separated the meaning of restarting a game from resetting the room flow.

---

## v1.1.2 — Game Start Notification

**Release date:** 2026-05-03

This update adds a clearer notification when a game begins.

### Start Notification

- Added a visible top notification when the game starts.
- The notification tells players that their screenshot is ready.
- Added a **View image** button that scrolls directly to the player’s role and screenshot area.
- Added a **Dismiss** button.
- The notification is shown once per player per game.

---

## v1.1.1 — Feedback Privacy and Storage Hotfix

**Release date:** 2026-05-03

This hotfix improves the feedback system introduced in v1.1.

### Feedback Privacy Fixes

- Fixed an issue where the feedback window could display hidden role and country information during the game.
- The feedback window no longer displays:
  - player role
  - country/region
  - country/region code
- The feedback window now only displays non-secret context, such as:
  - room
  - round
  - phase
  - player name
  - screenshot filename

### Feedback Storage Fixes

- Updated feedback storage so all feedback records are saved under a single root-level Firebase path:

```text
feedback/{feedbackId}
```

- This makes feedback easier to find and review.
- Feedback records still automatically include the relevant room, player, screenshot, country/region, and game context internally for maintenance purposes.

---

## v1.1 — Feedback and Bad Image Reporting

**Release date:** 2026-05-03

GeoSpy v1.1 adds an in-game feedback and issue reporting system for long-term dataset maintenance and gameplay improvement.

### Feedback System

- Added a low-profile **Feedback** button to the bottom-right corner of the page.
- Added a **Report this image** button in the player’s own screenshot panel.
- Added feedback categories:
  - Bad / blurry image
  - Black or broken image
  - Wrong country / wrong screenshot
  - Unfair or questionable country pair
  - Bug in game flow
  - General suggestion
- Feedback is submitted directly to Firebase under:

```text
feedback/{feedbackId}
```

### Automatic Context Attachment

Each feedback submission automatically records relevant game context, including:

- room ID
- player ID
- player name
- current phase
- round number
- player role
- country/region code
- country/region name
- screenshot filename
- screenshot URL
- selected country pair
- civilian country
- spy country
- page URL
- browser user agent
- submission time

### Dataset Maintenance

- Bad image reports now include the exact screenshot filename, making later image removal or replacement possible.
- Reports can be used to identify:
  - blurry screenshots
  - broken screenshots
  - wrong-country images
  - unfair or questionable country pairs
  - game-flow bugs
- This update prepares the project for future screenshot quality control and dataset patch releases.

---

## v1.0.3 — Rejoin Support Hotfix

**Release date:** 2026-05-02

This hotfix adds support for players rejoining an active game after accidentally refreshing, closing the page, or disconnecting.

### Room Rejoin

- Added rejoin support for active games.
- Players can now rejoin an existing room by entering:
  - the same room code
  - the same player name used earlier in the game
- Rejoining restores the original player slot instead of creating a new player.
- Rejoining preserves the player’s:
  - role
  - country/region
  - screenshot
  - alive/out status
  - description state
  - vote state
- New players are still prevented from joining after a game has started.
- Lobby-stage rejoin is also supported for players who disconnect before the game begins.

---

## v1.0.2 — Fixed Images Across Rounds Hotfix

**Release date:** 2026-05-02

This hotfix fixes an important gameplay issue where players could receive new screenshots after a tied vote or a failed vote-to-vote round.

### Gameplay Fixes

- Fixed an issue where player screenshots could change between rounds within the same game.
- Player screenshots now remain fixed for the entire game.
- A new description round no longer reassigns images.
- Tied votes now correctly proceed to the next round while keeping all surviving players’ original screenshots.
- Failed ready-to-vote rounds now correctly proceed to the next description round without changing screenshots.
- Only round-specific state is reset between rounds:
  - descriptions
  - vote intent
  - vote confirmation
  - votes
  - speaking order
  - timers

---

## v1.0.1 — Ready Vote Logic Hotfix

**Release date:** 2026-05-02

This hotfix fixes the ready-to-vote stage so that the system does not resolve the stage before the final outcome is determined.

### Gameplay Fixes

- Fixed an issue where the ready-to-vote stage could end too early.
- The system no longer moves directly to a new description round while remaining unconfirmed players could still change the result.
- Voting now begins immediately if confirmed Agree votes reach the required threshold.
- A new description round begins only if reaching the Agree threshold has become mathematically impossible.
- Unconfirmed players are still treated as Refuse when the ready-to-vote timer expires.

---

## v1.0 — Official Playable Release

**Release date:** 2026-05-02

GeoSpy v1.0 is the first complete playable release of the project. This version turns the original prototype into a fully functional multiplayer social deduction game based on real GeoGuessr-style screenshot data.

### Core Gameplay

- Added complete multiplayer room flow.
- Supported 3–6 player rooms.
- Added role assignment:
  - 3 players: 2 civilians, 1 spy
  - 4 players: 3 civilians, 1 spy
  - 5 players: 4 civilians, 1 spy
  - 6 players: 4 civilians, 2 spies
- Added civilian and spy country assignment based on similar country/region pairs.
- Added automatic random speaking order for each description round.
- Added 60-second speaking timer for each player.
- Added `NULL` display when a player fails to submit a description in time.
- Added ready-to-vote confirmation stage.
- Added player voting stage with confirm/cancel voting.
- Added automatic random vote assignment for players who fail to vote in time.
- Added tie-vote handling.
- Added win condition detection:
  - Civilians win when all spies are eliminated.
  - Spies win when surviving spies are equal to or greater than surviving civilians.

### Screenshot Dataset

- Added a cleaned screenshot dataset with **7,891 playable images**.
- Removed detected black/blank screenshots from the original capture set.
- Uploaded the final screenshot dataset to Cloudflare R2.
- Connected the game frontend to the R2-hosted screenshot dataset.
- Added screenshot-to-country indexing so each image is linked to its correct country/region code.
- Replaced temporary Street View links with direct in-game screenshot display.
- Added “Open full screenshot” link for each player’s own image.

### Country and Pair System

- Added **87 countries/regions** to the playable country pool.
- Added **100 similar country/region pairs**.
- Published a public country/region list and pair table as a rules appendix.
- Made the pair system transparent for players and future balancing.

### Private Chat

- Added one private chat opportunity per player per game.
- Private chat can only be requested during the player’s own speaking turn.
- Added 15-second accept/refuse window for private chat invitations.
- Added automatic refusal if the invited player does not respond in time.
- Added 90-second private chat timer.
- Paused the speaking timer during private chat.
- Resumed the remaining speaking time after private chat ends or is refused.
- Private chat messages are visible only to the two participating players.

### Post-game Reveal

- Added post-game reveal of other players’ images.
- Players can view other players’:
  - image
  - country/region
  - role
  - description
- Added toggle button to show or hide other players’ images after the game ends.

### Room Management

- Added room creation and joining by room code.
- Added invite link copying.
- Added host-only start game control.
- Added host-only room reset.
- Resetting a room returns players to the initial create/join screen.

### Documentation

- Published **GeoSpy Game Rules Version 1.0**.
- Published **GeoSpy Country/Region List and Pair Table Version 1.0**.

### Known Issues

- Some screenshots may be blurry or visually low quality.
- Some country/region pairs may need further balancing after more real-player testing.
- Future versions may further clean, replace, or expand the screenshot dataset.

---

## Planned Next Updates

### v1.2

- Build an admin/review workflow for submitted feedback.
- Add tools for removing or replacing reported bad images.
- Improve screenshot quality control.
- Possible country-pair balancing updates.
- Possible dataset expansion.
- Possible statistics or admin review tools.
