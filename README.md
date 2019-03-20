# Discord Google Assistant Bot

> A bot that hangs out in Discord and sometimes talks to Google Assistant. 

<br />
<br />
<p align="center">
	<img src="https://discordapp.com/assets/f8389ca1a741a115313bede9ac02e2c0.svg" width=75px /> 
	<img src="https://ak3.picdn.net/shutterstock/videos/15154723/thumb/9.jpg" width=125px/>
	<img src="https://upload.wikimedia.org/wikipedia/commons/5/5a/Google_Assistant_logo.png" width=75px/>
</p>

<br />

## Features
### Bot
- Hangs out in the voice chat, plays music from YouTube, SoundCloud, etc. through [youtube-dl](https://github.com/rg3/youtube-dl/commit/f7560859a3e25ccaa74123428d42f821299a2bed).
- Responds to guild messages with custom user-defined responses, available through an easily-accessible Google Sheets link.

### Google Assistant Action
- Google Assistant intent for asking which members of a Discord guild are online.

<p align="center">
	<img src="https://github.com/pg8wood/discord-voice-assistant-bot/blob/master/docs/discord-screenshot.jpeg" width=200px />
	<img src="https://github.com/pg8wood/discord-voice-assistant-bot/blob/master/docs/google-assistant-screenshot.PNG" width=200px />
</p>

## Installation
- [Create a Discord bot account and invite it to your server](https://discordpy.readthedocs.io/en/rewrite/discord.html).
- `cd` to the project directory, and run the installer script `python3 install.py` (Mac users should run 'install.sh').
- Note: The bot's dependencies require that you use Python 3.6!
- The bot's command prefix defaults to `.`. This can be configured to suit your guild's needs.
- Note: Some low-level dependencies such as `ffmpeg` may not be pip-able on your system. You'll need to install these dependencies yourself. 

### Google Assistant Setup
If you want to use Google Assistant features, [follow the Dialogflow setup instructions](https://developers.google.com/actions/dialogflow/project-agent). Set the fulfillment URL to point to your hosted `index.py`. 
	
- If you need free web hosting, you host your web service locally and expose a port to the web using a tool like [Serveo](https://serveo.net/).

### Custom Bot Responses
The bot uses Google Sheets as a shared database of custom responses. This Sheet can be edited on-the-fly to setup custom bot text or audio responses to text typed in the Discord channels. 

Create a new Sheet and configure a service account for the bot [following this tutorial](https://youtu.be/vISRn5qFrkM). If you wish, share the link with your guild's members to allow them to add their own flavor to the bot. 

Note: The video tutorial states to use the Google Drive API; use the Google Sheets API instead. All other steps are the same.

<br />

## Usage 

### Vanilla bot
Run `python3 bot/bot_service.py` (Mac users should run `bot/bot_service.sh`) to run the Discord bot without any fancy Google Assistant functionality.

### Google Assistant mode
Run the Sanic server with `python3 bot/index.py`. This will run the web server at http://localhost:8000. 

If you're hosting the bot elsewhere, run the server the way you're used to. You may need to edit the configuration in `index.py`. 

Type `<command_prefix> help` to see what the bot can do!

## Roadmap
- More bot features. Got an idea? Open an issue! 

## Credit
- Some of the code in bot/bot.py was taken from [discord.py](https://github.com/Rapptz/discord.py), as some modifications to the default help message required that the default methods be overridden, and as the original code was quite close to what was required already it made sense to copy said code and modify it as necessary in the overridden methods.
