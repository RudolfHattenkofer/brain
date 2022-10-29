[Source](https://alvinalexander.com/mac-os-x/mac-osx-startup-crontab-launchd-jobs/)

```other
$HOME/Library/LaunchAgents
```

1. **/Library/LaunchDaemons** - Put your plist scripts in this folder if your job needs to run even when no users are logged in.
2. **/Library/LaunchAgents** - Put your plist scripts in this folder if the job is only useful when users are logged in. (Note: I learned that this has the side-effect of your job being run as 'root' after a system reboot.)
3. **$HOME/Library/LaunchAgents** - Put your plist files in this folder if the job is only useful when users are logged in. (When your plist configuration file is placed here, your job will be run under your username.)

```other
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>Label</key>
  <string>com.rudolfhattenkofer.notes</string>

  <key>ProgramArguments</key>
  <array>
    <string>/Users/rudolfhattenkofer/Library/Mobile Documents/27N4MQEA55~pro~writer/Documents/sync</string>
  </array>

  <key>Nice</key>
  <integer>1</integer>
    
  <key>RunAtLoad</key>
  <true/>

  <key>StartInterval</key>
  <integer>60</integer>

  <key>StandardErrorPath</key>
  <string>/Users/rudolfhattenkofer/Downloads/notes-sync-error.log</string>

  <key>StandardOutPath</key>
  <string>/tmp/notes-sync.log</string>
</dict>
</plist>
```

Don't wait for reboot, load now:

```other
launchctl load com.rudolfhattenkofer.notes.plist
```



