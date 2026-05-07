# GeoSpy Changelog

## v1.3 — Gameplay Balance and Expanded Private Chat

**Release date:** 2026-05-07

GeoSpy v1.3 is a gameplay balance update focused on making discussion faster, private chat more meaningful, and larger rooms more strategically interesting.

### Speaking Timer Balance

- Reduced each player's speaking time from **60 seconds** to **45 seconds**.
- Updated related description-phase text so the interface and rules remain consistent.
- This change is intended to keep description rounds faster and reduce downtime between turns.

### Private Chat Balance

- Reduced accepted private chat duration from **90 seconds** to **60 seconds** total.
- Changed private chat opportunities from **one per player per game** to:

    Private chat opportunities per player = total player count - 2

| Players | Private chat opportunities per player |
|---:|---:|
| 3 | 1 |
| 4 | 2 |
| 5 | 3 |
| 6 | 4 |

- A private chat opportunity is consumed only when the request is **accepted**.
- If the invited player refuses or does not respond before the request timer ends, the opportunity is **not** consumed.
- Private chat remains available only during the requesting player's own speaking turn.
- Added interface feedback showing remaining private chat opportunities, such as:

    Remaining: 2 / 3

### Design Goal

- Make private chat more useful in larger rooms.
- Encourage more social deduction, alliance-building, and targeted questioning.
- Prevent private chat from becoming too slow by shortening each accepted chat to 60 seconds.
- Keep smaller 3-player rooms balanced by preserving the original one-chat limit.

---

## v1.2 — Website Integration and Cinematic UI Update

**Release date:** 2026-05-05 to 2026-05-07

GeoSpy v1.2 is a major visual and presentation update. It improves how GeoSpy appears on The Chessplayer website and makes the in-game experience feel less like a functional webpage and more like a cinematic social deduction game.

### Website Integration

- Added a direct **GeoSpy** item to The Chessplayer homepage navigation.
- Added a **Try GeoSpy** button to the homepage hero section.
- Connected the homepage call-to-action directly to `geospy.html`.
- Adjusted the homepage button layout so **Try GeoSpy** aligns cleanly with the other hero buttons.
- Added a direct **Read rules** link from the GeoSpy landing page to the public Google Docs rules document.

### Homepage Visual Refresh

- Reworked the homepage hero concept around the slogan **From Board Vision to World Vision**.
- Added a board-to-world visual direction:
  - chessboard-inspired background structure
  - latitude/longitude map-grid atmosphere
  - stronger connection between chess pattern recognition and GeoGuessr-style world recognition
- Simplified the right-side homepage slogan area so it feels cleaner and less crowded.
- Replaced the Contact card's old `Back to top` link with a Discord link.
- Added a standalone floating `Back to top` button in the bottom-right corner.
- Kept the floating button style consistent with the lightweight navigation buttons used on note pages such as Beginner Notes.

### GeoSpy Landing Page Visual Refresh

- Centered the GeoSpy entry layout and Create / Join card.
- Added a subtle world-map / globe-projection background behind the page.
- Increased background color depth while keeping text readable.
- Removed the old title orbit effect from the GeoSpy landing section.
- Added subtle moving light points over the existing map/grid background.
- Moved **Back to Home** to the far left of the page for clearer navigation.

### Cinematic In-game Layout

- Introduced a darker cinematic in-game layout after the game starts.
- Made the player's screenshot the visual focus of the game screen.
- Added a gradual image reveal effect when the screenshot appears.
- Added a subtle golden frame glow around the screenshot area.
- Reduced visual clutter during active gameplay.
- Kept description, voting, private chat, result, and feedback controls available below or around the main image.
- Kept host controls available in a compact in-game control area.
- Preserved the host-only **Restart game** and **Back to Lobby** controls during active games.

### Design Goal

- Make the landing page feel more polished and game-like.
- Make the transition into an active game feel more dramatic.
- Reduce the feeling of a plain functional webpage.
- Focus the player's attention on the screenshot, description, voting, and deduction flow.

---

## v1.1 — Feedback, Rejoin, and Room Control Stability Update

**Release date:** 2026-05-02 to 2026-05-03

GeoSpy v1.1 improves the first playable release with feedback reporting, rejoin support, better room controls, notification fixes, and several important gameplay stability hotfixes.

### Feedback and Bad Image Reporting

- Added a low-profile **Feedback** button to the bottom-right corner of the page.
- Added a **Report this image** button in the player's own screenshot panel.
- Added feedback categories:
  - Bad / blurry image
  - Black or broken image
  - Wrong country / wrong screenshot
  - Unfair or questionable country pair
  - Bug in game flow
  - General suggestion
- Feedback is submitted directly to Firebase under:

    feedback/{feedbackId}

### Automatic Feedback Context

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
- Feedback records still store relevant internal context for maintenance purposes.

### Dataset Maintenance Support

- Bad image reports now include the exact screenshot filename.
- This makes later image removal or replacement possible.
- Reports can be used to identify:
  - blurry screenshots
  - broken screenshots
  - wrong-country images
  - unfair or questionable country pairs
  - game-flow bugs
- This update prepares the project for future screenshot quality control and dataset patch releases.

### Rejoin Support

- Added support for players rejoining an active game after accidentally refreshing, closing the page, or disconnecting.
- Players can rejoin an existing room by entering:
  - the same room code
  - the same player name used earlier in the game
- Rejoining restores the original player slot instead of creating a new player.
- Rejoining preserves the player's:
  - role
  - country/region
  - screenshot
  - alive/out status
  - description state
  - vote state
- New players are still prevented from joining after a game has started.
- Lobby-stage rejoin is also supported for players who disconnect before the game begins.

### Fixed Images Across Rounds

- Fixed an issue where player screenshots could change between rounds within the same game.
- Player screenshots now remain fixed for the entire game.
- A new description round no longer reassigns images.
- Tied votes now correctly proceed to the next round while keeping all surviving players' original screenshots.
- Failed ready-to-vote rounds now correctly proceed to the next description round without changing screenshots.
- Only round-specific state is reset between rounds:
  - descriptions
  - vote intent
  - vote confirmation
  - votes
  - speaking order
  - timers

### Ready-to-vote Logic Fixes

- Fixed an issue where the ready-to-vote stage could end too early.
- The system no longer moves directly to a new description round while remaining unconfirmed players could still change the result.
- Voting begins immediately if confirmed Agree votes reach the required threshold.
- A new description round begins only if reaching the Agree threshold has become mathematically impossible.
- Unconfirmed players are still treated as Refuse when the ready-to-vote timer expires.

### Game Start Notification

- Added a visible top notification when a game begins.
- The notification tells players that their screenshot is ready.
- Added a **View image** button that scrolls directly to the player's role and screenshot area.
- Added a **Dismiss** button.
- The notification is shown once per player per game.
- Fixed an issue where non-host players could miss the game start notification.
- If a player's page is in the background when the game starts, the notification appears when they return to the tab.
- Reduced the notification duration to **3 seconds**.
- Added a short notification sound when the game starts.
- If the browser blocks autoplay audio, the notification still appears silently.

### Room Management Improvements

- Added a host-only **Restart game** button after game over.
- Restart game keeps the same room and the same players.
- Restart game immediately starts a new game with new roles, countries/regions, and screenshots.
- Added a host-only **Back to Lobby** button after game over.
- Separated the meaning of restarting a game from resetting the room flow.
- Updated **Back to Lobby** so it fully resets the current room.
- Back to Lobby now deletes the active room and returns all players to the clean Create / Join screen.
- Players who want to change room size must create a new room after returning to lobby.
- Added a host-only **Restart game** button during active rounds.
- The host can restart the current game before it ends.
- Restart game keeps the same room and the same players.
- Restart game immediately assigns new roles, countries/regions, and screenshots.
- **Back to Lobby** remains available as a full room reset option.

### Design Goal

- Make the first playable version more stable.
- Make disconnects and accidental refreshes less damaging.
- Improve host control over broken or awkward rooms.
- Prepare the game for larger-scale testing and dataset cleanup.

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
- Added **Open full screenshot** link for each player's own image.

### Country and Pair System

- Added **87 countries/regions** to the playable country pool.
- Added **100 similar country/region pairs**.
- Published a public country/region list and pair table as a rules appendix.
- Made the pair system transparent for players and future balancing.

### Private Chat

- Added one private chat opportunity per player per game.
- Private chat can only be requested during the player's own speaking turn.
- Added 15-second accept/refuse window for private chat invitations.
- Added automatic refusal if the invited player does not respond in time.
- Added 90-second private chat timer.
- Paused the speaking timer during private chat.
- Resumed the remaining speaking time after private chat ends or is refused.
- Private chat messages are visible only to the two participating players.

### Post-game Reveal

- Added post-game reveal of other players' images.
- Players can view other players':
  - image
  - country/region
  - role
  - description
- Added toggle button to show or hide other players' images after the game ends.

### Room Management

- Added room creation and joining by room code.
- Added invite link copying.
- Added host-only start game control.
- Added host-only room reset.
- Resetting a room returns players to the initial Create / Join screen.

### Documentation

- Published **GeoSpy Game Rules Version 1.0**.
- Published **GeoSpy Country/Region List and Pair Table Version 1.0**.

### Known Issues

- Some screenshots may be blurry or visually low quality.
- Some country/region pairs may need further balancing after more real-player testing.
- Future versions may further clean, replace, or expand the screenshot dataset.
