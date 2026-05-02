# GeoSpy Changelog

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
- Fixed ready-to-vote logic so the system does not resolve early while the result can still change.
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
- A future version may add a feedback/report system for bad images and general suggestions.
- A future version may further clean or replace low-quality screenshots.

---

## Planned Next Updates

### v1.1

- Add Suggestions / Report Bad Image system.
- Allow players to report blurry, broken, unfair, or wrong-country images.
- Store feedback records for later dataset maintenance.
- Improve screenshot quality control.

### v1.2

- Possible country-pair balancing updates.
- Possible dataset expansion.
- Possible statistics or admin review tools.
