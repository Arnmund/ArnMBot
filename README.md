# ArnMBot
 
----------------------------------------------------------------
1. WHAT IS ARN M BOT
----------------------------------------------------------------
 
Arn M Bot is a program that monitors your Twitch channel chat
and automatically reloads a specified browser tab when a
moderator sends a command. Perfect for refreshing stream
overlays without manually pressing F5.
 
The bot connects to Twitch anonymously — no token required —
and can listen to up to 5 different channels simultaneously,
each in its own tab within the interface.
 
 
----------------------------------------------------------------
2. INSTALLATION — EXTRACTING THE ARCHIVE
----------------------------------------------------------------
 
The bot is distributed as a ZIP archive. You must extract it
before running.
 
  ! IMPORTANT: Do not run the bot directly from the ZIP archive
    — it will not save settings and may behave incorrectly.
 
How to extract:
 
  1. Locate the downloaded ArnMBot.zip file in your Downloads.
  2. Right-click on it.
  3. Select "Extract All..." or "Extract Here".
  4. Wait for the extraction to complete.
  5. Open the extracted ArnMBot folder.
 
Contents of the folder after extraction:
 
  ArnMBot.exe  — the bot executable
  icon.png     — program icon
  guide.txt    — this guide
 
You can place the folder anywhere convenient: Desktop,
Documents, drive D:, etc. Just don't delete any files from it.
 
 
----------------------------------------------------------------
3. BROWSER SETUP
----------------------------------------------------------------
 
The bot controls the browser via the CDP protocol
(Chrome DevTools Protocol). To enable this, the browser must
be launched with a special flag that opens a debugging port.
 
Supported browsers:
Google Chrome, Vivaldi, Microsoft Edge, Opera, Brave.
 
 
3.1 Creating a shortcut with the debug flag
---------------------------------------------
 
  1. Find the browser shortcut on your Desktop or Start Menu.
  2. Right-click → "Properties".
  3. In the "Target" field, find the path to the browser.
  4. Append the required flags to the end of the line
     (after the closing quote — see section 3.2 below).
  5. Click "Apply" and "OK".
  6. Always launch the browser using this shortcut from now on.
 
  ! IMPORTANT: If you launch the browser the normal way
    (without the flag), the bot will not be able to connect.
 
 
3.2 Flags for each browser
----------------------------
 
  Vivaldi:
    --remote-debugging-port=9222 --user-data-dir="C:\VivaldiDebug"
 
  Google Chrome:
    --remote-debugging-port=9222 --user-data-dir="C:\ChromeDebug"
 
  Microsoft Edge:
    --remote-debugging-port=9222 --user-data-dir="C:\EdgeDebug"
 
  Opera / Brave:
    --remote-debugging-port=9222 --user-data-dir="C:\BrowserDebug"
 
Example of a complete Target field for Vivaldi:
 
  "C:\Program Files\Vivaldi\Application\vivaldi.exe"
  --remote-debugging-port=9222 --user-data-dir="C:\VivaldiDebug"
 
  * Note: --user-data-dir creates a separate browser profile
    specifically for use with the bot. Your main bookmarks
    and personal data are not affected.
 
 
3.3 Opening the overlay
-------------------------
 
  1. Launch the browser using the shortcut you just created.
  2. Open the overlay or page you want the bot to reload.
  3. Copy the URL from the address bar — you will need it
     when configuring the bot.
 
 
----------------------------------------------------------------
4. LAUNCHING AND CONFIGURING THE BOT
----------------------------------------------------------------
 
4.1 First launch
------------------
 
  1. Open the ArnMBot folder.
  2. Double-click ArnMBot.exe.
  3. If Windows shows a "Windows Defender" warning — click
     "More info" → "Run anyway".
 
  * This is a standard warning for programs without a digital
    signature. The bot is safe to run.
 
 
4.2 Interface overview
------------------------
 
The bot window has tabs at the top — one for each channel.
Switch between them by clicking "Tab 1" … "Tab 5".
 
The symbol and color on each tab button shows the bot status:
 
  ○  grey    — Offline (bot is not running)
  ◌  yellow  — Connecting...
  ●  green   — Online (bot is listening to chat)
  ✕  red     — Connection error
 
 
4.3 Settings — TWITCH section
--------------------------------
 
  Channel   — the streamer's Twitch username (no @ or spaces).
             
  Prefix    — the symbol before the command. Default: !
 
  Command   — the command word without the prefix.
               Default: reload
               The resulting chat command will be: !reload
 
  Mods only — if checked, only moderators and the streamer
               can trigger the command. Recommended: keep on.
 
 
4.4 Settings — BROWSER (CDP) section
---------------------------------------
 
  CDP address  — the debugging port address.
                 Default: http://localhost:9222
                 No need to change if you used port 9222.
 
  Overlay URL  — the full URL of the tab to reload.
                 Example: https://overlay.example.com/scene1
 
 
4.5 Testing the browser connection (Test CDP)
-----------------------------------------------
 
Before starting the bot, make sure the browser is running and
the overlay tab is open. Click the "Test CDP" button.
 
The log will show one of the following:
 
  CDP available. Tabs: N          — browser found, ready to go
  Tab found: [title]              — overlay tab found
  CDP unavailable                 — browser not running or
                                    launched without the flag
  Tab with URL '...' not found    — check your overlay URL
 
 
4.6 Starting and stopping
---------------------------
 
  - Click START — the status will change to "Online".
  - Click STOP to disconnect the bot.
 
  * Settings are saved automatically when the bot starts
    and restored the next time you open the program.
 
 
----------------------------------------------------------------
5. WORKING WITH MULTIPLE CHANNELS
----------------------------------------------------------------
 
The bot supports up to 5 independent configurations. Each tab
(Tab 1 … Tab 5) is a separate bot instance with its own
settings.
 
  1. Switch to the desired tab (e.g., Tab 2).
  2. Fill in the fields: a different channel, a different
     overlay URL.
  3. Click START on that tab.
 
Each tab starts and stops independently.
All 5 bots can run at the same time.
 
Example:
  Tab 1 — command !reload, channel stream1, overlay #1
  Tab 2 — command !refresh, channel stream2, overlay #2
 
 
----------------------------------------------------------------
6. TROUBLESHOOTING
----------------------------------------------------------------
 
Bot won't connect to chat
  - Make sure the channel name has no @ symbol or spaces.
  - Check that you have an active internet connection.
  - Try stopping and restarting the bot.
 
CDP unavailable
  - Make sure the browser was launched using the shortcut with
    the --remote-debugging-port=9222 flag.
  - There should be no other browser windows open without
    the flag.
  - Check that port 9222 is not blocked by your antivirus
    or firewall.
 
Overlay tab not found
  - Copy the URL directly from the browser address bar.
  - The URL must match exactly, including https:// at the start.
  - Make sure the overlay tab is currently open in the browser.
 
Command not triggering
  - Check that the command is typed correctly in chat
    (case-insensitive).
  - If "Mods only" is enabled, only a moderator or the streamer
    can send the command.
  - Make sure the bot is online (● green status).
 
Error when launching .exe
  - Make sure the folder has been extracted from the ZIP.
    Running directly from the archive is not supported.
  - Try running as administrator:
    Right-click ArnMBot.exe → "Run as administrator".
