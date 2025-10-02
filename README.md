# Covasify v1.0.0

Voice-controlled Spotify integration for COVAS NEXT. Play music, control playback, and bind tracks to custom voice commands.

## What It Does

- Play tracks, albums, artists, and playlists by voice
- Control playback (pause, skip, seek, volume, shuffle, repeat)
- Save tracks to your Liked Songs
- **Bind tracks to custom phrases** - Say "workout intro" to instantly play your bound track
- Get current track info

## Installation

### 1. Get Spotify API Credentials

1. Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
2. Create an app with these settings:
   - **Redirect URI**: `http://127.0.0.1:8888/callback`
3. Copy your **Client ID** and **Client Secret**

### 2. Install Plugin

1. Place the `Covasify` folder in: `%appdata%\com.covas-next.ui\plugins\`

2. Create `spotify_credentials.txt` in the plugin folder:
   ```
   CLIENT_ID=your_client_id_here
   CLIENT_SECRET=your_client_secret_here
   ```

3. Restart COVAS NEXT

4. First use will open browser for Spotify authorization (one-time setup)

**Requirements**: Spotify Premium account and an active device (desktop app, mobile, web player)

## Voice Commands

### Playing Music

```
"Play Bohemian Rhapsody on Spotify"
"Play the album Abbey Road"
"Play Queen on Spotify"
"Play Queen's top tracks"
"Play my liked songs"
```

### Playback Control

```
"Pause" / "Resume" / "Stop"
"Next song" / "Previous song"
"Restart this track"
"Skip to 2:30"
"Volume up" / "Set volume to 50%"
"Shuffle on" / "Repeat this track"
```

### Library

```
"What's playing?"
"Add this to my library"
"Remove this from my library"
```

### Binding System

**Create a binding:**
1. Play any track
2. Say: "Bind this to [phrase]"
   - Example: "Bind this to workout intro"

**Play bound track:**
- Just say the phrase: "Workout intro"

**Manage bindings:**
```
"List my bindings"
"Unbind workout intro"
"Clear all bindings"
```

Bindings are stored in `spotify_bindings.json` and work with punctuation/case variations.

## Troubleshooting

**"No active Spotify devices found"**
- Open Spotify on any device and start playing something first

**"Not connected to Spotify"**
- Check `spotify_credentials.txt` has valid credentials
- Delete `.spotify_cache` and restart COVAS to re-authenticate
- Test with: "Test Covasify"

**Binding doesn't play immediately**
- Say the phrase again if needed (plugin overrides COVAS safety protocols but may need retry on first attempt)

**Need to re-authorize**
- Delete `.spotify_cache` from plugin folder
- Restart COVAS - browser will open for re-auth on first command

## What's NOT Possible

Due to Spotify API restrictions (November 2024):
- True radio/recommendations (API deprecated for new apps)
- Endless queue (API limitation - use artist/playlist playback instead)
- Related artists suggestions (API blocked)

## Files

```
Covasify/
├── Covasify.py              # Main plugin
├── manifest.json            # Plugin metadata
├── spotify_credentials.txt  # Your credentials (create this)
├── spotify_bindings.json    # Your bindings (auto-created)
├── .spotify_cache          # OAuth tokens (auto-created)
└── deps/                   # Bundled dependencies
```

## Credits

**Author**: D. Trintignant  
**COVAS NEXT**: https://ratherrude.github.io/Elite-Dangerous-AI-Integration/  
**Spotify API**: Spotipy library
