# DarkMP-DiscordBot

A NodeJS Discord bot for getting some informations from your DarkMP Kerbal Space Program multiplayer server (and even some administration commands)

## Installation

### Requirements

As it can handle admin commands, each server must be running into a named screen session (https://linux.die.net/man/1/screen)

Example:
```bash
screen -S DMPServer_stock-1.7.0 -d -m mono ~/DMPServer/stock-1.7.0/DMPServer.exe
```
where 'DMPServer_stock-1.7.0' is the screen name (will be used in hosts.json config file later)

### Steps

Use npm to install required modules
```bash
npm install discord.js winston sync-request shelljs --save
```

You can also install 'supervisor' module if you want to run your bot infinitly
```bash
npm install supervisor -g
```

Follow this guide to create your Discord application/bot:
https://github.com/reactiflux/discord-irc/wiki/Creating-a-discord-bot-&-getting-a-token

Create configuration files
- auth.json
```json
{
    "token": "YOUR_DISCORD_BOT_TOKEN"
}
```
- hosts.json
```json
[
    {
        "address": "SERVER1_ADDRESS",
        "port": "SERVER1_PORT",
        "screen_name": "SERVER1_SCREEN_SESSION_NAME"
    },
    {
        "address": "SERVER2_ADDRESS",
        "port": "SERVER2_PORT",
        "screen_name": "SCREEN2_SCREEN_SESSION_NAME"
    }
]
```
- admins.json
```json
[
    "ADMIN1_DISCORD_PSEUDO",
    "ADMIN2_DISCORD_PSEUDO"
]
```

## Usage

```bash
node bot.js
```

with supervisor
```bash
supervisor bot.js
```

### Available commands

```
- !help     => print this help
- !ping     => should respond 'Pong!' if alive
- !server   => give informations about DarkMP server

- !server help      => print this help
- !server print     => print infos about all servers
- !server dump <id> => dump all informations about specified server
- !server players   => list players currently on servers

- !server admin help                => print this help
- !server admin restart <id>        => restart specified server
- !server admin say <id> <message>  => send message to all players on specified server
```
