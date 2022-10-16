## Base

- 1Password
- Set up Google inside of MacOS
- Things
- Install Chrome
   - Log in to Google
      - Private
      - S&P
- ​File Stream
   - [https://support.google.com/drive/answer/7329379](https://support.google.com/drive/answer/7329379)
- ​Keyboard settings
   - Modifier keys -> Caps lock to Ctrl
   - Disable autocorrect
   - key repeat to max
   - Disable smart quotes
   - Shortcuts -> Display -> Turn off all
- ​Touchpad: Tap vs click
- Mouse: Right click
- Finder
   - New window opens home folder
   - Sidebar home
   - Desktop right click -> View options -> Sort By -> Snap to grid
   - Any folder: View options -> sort by -> name
- Turn on Dock hiding

```swift
launchctl disable gui/$UID/com.apple.photoanalysisd
launchctl kill -TERM gui/$UID/com.apple.photoanalysisd
```

## Opsec

- LittleSnitch

## Works

- Office + Teams
- Slack
- Tableau
- Docker
- VS Code
- Notion

## Tools

- Set up brew [The Missing Package Manager for macOS (or Linux) — Homebrew](https://brew.sh/)
- Install

```other
brew install git wget yarn npm vim pre-commit
```

- Set up git

[Creating a personal access token - GitHub Docs](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)

```other
echo .DS_Store > ~/.gitignore_global
git config --global core.excludesfile ~/.gitignore_global
git config --global pull.rebase true
git config --global credential.helper cache
git config --global user.name "Rudolf Hattenkofer"
git config --global user.email "rudolf@geardev.de"
```

- ​Install fonts
- [Hack | A typeface designed for source code](https://sourcefoundry.org/hack/)

```other
mkdir ~/code;
mkdir ~/client
```

- Google cloud [https://cloud.google.com/sdk/](https://cloud.google.com/sdk/)
- ​Firebase

`npm install -g firebase-tools`

## Tools

- ​BetterSnapTool
- Timery
- Toggl
- Fantastical
- Keyboard Maestro
- Spotify
- SetApp
   - Cleanshot X
   - Paw
   - Archiver
   - TablePlus
   - Transmit

