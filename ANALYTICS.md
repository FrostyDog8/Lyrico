# Analytics (optional)

The game can send anonymous usage events to **Google Analytics 4** so you can see traffic and outcomes. Nothing runs on your PC; everything is free and handled by Google.

## Setup (one-time)

1. Go to **[analytics.google.com](https://analytics.google.com)** and sign in with your Google account.
2. Create a **GA4 property** for your site (e.g. "Lyrics Puzzle").
3. Get your **Measurement ID** (looks like `G-XXXXXXXXXX`) from Admin → Data Streams → your web stream.
4. In **script.js**, set the constant at the top:
   ```js
   const GA_MEASUREMENT_ID = 'G-XXXXXXXXXX';  // your ID
   ```
5. Leave it empty (`''`) to disable analytics.

## Events sent

- **game_start** – when a song loads (`mode`: `surprise` | `surprise_artist` | `choose_song` | `spotify`, `total_words`, optional `song_year`, optional `playlist` for Spotify)
- **song_complete** – when the player finishes the song (`completion_pct`: 0–100, `hints_used`: count)
- **song_give_up** – when the player gives up (`completion_pct`: 0–100, `hints_used`: count)
- **hint_used** – when the player uses a hint (`words_revealed`: number)
- **next_song** – when the player clicks "Next Song" in surprise mode (`mode`: `surprise` | `surprise_artist`)
- **reveal_title** – when the player reveals the song title (surprise mode)
- **back_to_lobby** – when the player clicks back to leave the game and return to the lobby

## Where to view stats

Open **[analytics.google.com](https://analytics.google.com)** in your browser and use your property. There is **no link or button in the game**; you access the dashboard only via this URL and your Google login.

You can see:

- **Users** – unique visitors (GA4 handles this)
- **Events** – counts of `game_start`, `song_complete`, `song_give_up`
- **Reports** – build custom reports or use "Engagement" → "Events" and filter by event name; use event parameters (`mode`, `completion_pct`) for breakdowns.

### Entries per game mode

To see how many game starts (entries) happened for each mode:

1. In GA4 go to **Report** → **Engagement** → **Events**.
2. Find the **game_start** event and click it (or use the search/filter).
3. Add a breakdown by the **mode** parameter:
   - In the Events table, click **+** (Add dimension) or the column header and add **Event parameter** → **mode**. You'll see counts for `choose_song`, `surprise`, and `surprise_artist`.

Alternatively, use **Explore** (left menu) → **Free form** → add **Event name** = `game_start` and **Dimensions** → **Event parameter** → **mode** to get a table or chart of entries per game mode.

No server or process runs on your computer; the game only loads Google's script and sends events when players use it.
