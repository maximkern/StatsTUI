# StatsTUI

StatsTUI is a terminal-based user interface for viewing your Spotify listening statistics. It provides an elegant way to explore your top tracks, artists, genres, and recent listening history through an interactive terminal interface. View a showcase [here](https://youtu.be/8riIn9S8ELk).

## Features

- View your top tracks, artists, and genres across different time periods
- Track detailed statistics for each time range (4 weeks, 6 months, all time)
- See recently played tracks with relative timestamps
- Detailed views for songs, artists, and genres including:
  - Song view: Album art (ASCII), track details, and popularity metrics
  - Artist view: Top tracks, popular albums, and genre information
  - Genre view: Related artists, genre trends, and associated tracks
- Customizable color schemes
- Keyboard-driven navigation
- Spotify integration for opening items directly in Spotify

## Prerequisites

Before running StatsTUI, you'll need:

1. Go 1.16 or higher installed on your system 
2. A Spotify Developer account and application credentials
3. The following Go packages (will be installed automatically with go mod):
   - github.com/zmb3/spotify/v2
   - github.com/charmbracelet/bubbletea
   - github.com/charmbracelet/lipgloss
   - github.com/charmbracelet/bubbles
   - golang.org/x/oauth2

NOTE: This is only needed if you are planning to build the program yourself, otherwise resort to running the prebuilt binaries in build.

## Path requirments

This program doesnt currently come with an installer and an automatic way to add itself to path, instead you must run the add.bat in the build folder to add it to path. If you wish to later remove it simply remove the program or run remove.bat. Otherwise its acceptable to run the program by double clicking it or by running run.bat in the project folder. 

## Installation

1. Clone the repository: (Currently unavailable)
```bash
git clone <repository-url>
cd statstui
```

2. Install dependencies:
```bash
go mod download
```

3. Build the application: // or alternatively using build.bat
```bash
go build 
```


## First-Time Setup

When you first run StatsTUI, you'll need to configure your Spotify credentials:

1. Go to the [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
2. Create a new application
3. Add `http://localhost:8080/callback` to the Redirect URIs in your Spotify application settings
4. Launch via cmd:
```bash
stats
```
5. Enter your Spotify Client ID and Client Secret when prompted
6. Complete the OAuth flow in your browser when it opens automatically

## Navigation

### Main View Controls
- `Tab`/`Shift+Tab` or `←`/`→`: Switch between views (Tracks/Artists/Genres/Recent)
- `↑`/`↓` or `k`/`j`: Navigate through items
- `Enter`: View detailed information for the selected item
- `Space`: Open the selected item in Spotify
- `1`/`2`/`3`: Switch time ranges (4 weeks/6 months/all time)
- `s`: Toggle settings view
- `q`: Quit

### Detail View Controls
- `ESC`: Return to main view
- `Space`: Open in Spotify

### Settings View
- `↑`/`↓`: Navigate settings
- `Enter`: Change selected setting
- `s`: Return to main view

## Configuration

StatsTUI stores its configuration in your system's user configuration directory:
- Linux: `~/.config/StatsTUI/config.json`
- macOS: `~/Library/Application Support/StatsTUI/config.json`
- Windows: `%AppData%\StatsTUI\config.json`

The configuration file includes:
- Spotify credentials
- Default time range
- Color schemes

## Color Schemes

StatsTUI comes with several built-in color schemes:
- Spotify (Default)
- Purple
- Blue
- Coral
- Mint
- Gold
- Pink
- Monochrome

You can switch between color schemes in the settings menu and add your own using the config file. 

## Troubleshooting

1. **Authentication Errors**
   - Verify your Client ID and Client Secret are correct
   - Check that your redirect URI matches exactly: `http://localhost:8080/callback`
   - Ensure your Spotify application has the correct permissions 

2. **Display Issues**
   - Ensure your terminal supports Unicode characters
   - Use a terminal with true color support for best results
   - Make sure your terminal window is large enough (minimum 80x24 recommended)

3. **Performance Issues**
   - The application caches data to minimize API calls
   - If experiencing slowdown, try restarting the application
   - If freezes when getting song details restart the program (happens due to spotify api being slow).

## Error Messages

Common error messages and their solutions:

- "Error checking setup status": Verify your configuration file permissions
- "Failed to initialize Spotify auth": Check your internet connection and credentials
- "Invalid credentials": Re-enter your Spotify Client ID and Secret
- "HTTP server error": Ensure port 8080 is available for the OAuth callback

## Credits

Built with:
- [Bubble Tea](https://github.com/charmbracelet/bubbletea) - Terminal UI framework
- [Lip Gloss](https://github.com/charmbracelet/lipgloss) - Style definitions
- [zmb3/spotify](https://github.com/zmb3/spotify) - Spotify API client