# LavaCord
An Lavalink documentation version made for replit and glitch users to make discord music bots.

Being used in production by Alpha Esports bots, Aleztro, Lava Music bot.

A [basic example bot](Testbot) is available.

[![JDA guild](https://discordapp.com/api/guilds/125227483518861312/embed.png?style=banner2)](https://discord.gg/jtAWrzU)

## Features
* Powered by Lavaplayer
* Minimal CPU/memory footprint
* Twitch/YouTube stream support
* Event system
* Seeking
* Volume control
* REST API for resolving lavaplayer tracks (used for non-JVM clients)
* Statistics (good for load balancing)
* Basic authentication
* Prometheus metrics
* Docker images

## Requirements

* Need a Replit/Glitch account.
* Know how to use lavalink.
* Need to know how to make a discord bot.
* At least you need have knowladge of Java Script



## Installation + Setup

```shell
# Clone the repository:
git clone https://github.com/AstroicyOP/Lavacord.git

# Run the code:
language = "nodejs"
run = "bash start.sh"

```




## Changelog

Please see [here](CHANGELOG.md)

## Versioning policy

- The public API ("API" in a very broad sense) of Lavalink can be categorized into two main domains:
  - **Client Domain:** The API exposed to clients, consisting of both the WebSocket protocol and any public HTTP endpoints
  - **Server Domain:** The server application with its runtime environment, its configuration, etc.

- A change that is breaking to one domain might not be breaking at all to another.

  *Examples:*
  - Removing an endpoint: This is a breaking change for the client domain but is not for running the server itself.
  - Upgrading the minimum Java version: This is a breaking change for the server domain, but client implementations couldn't care less about it.

**Given the above, the following versioning pattern lends itself well to the Lavalink project:**

_**api.major.minor.patch**_

- **API**: Bumped when breaking changes are committed to the client domain of Lavalink

  *Examples:* Removing an endpoint, altering the output of an endpoint in a non-backward-compatible manner
- **Major**: Bumped when breaking changes are committed to the Lavalink server domain

  *Examples:* Bumping the required Java version, altering the configuration in a non-backward-compatible manner
- **Minor**: New features in any domain

  *Examples:* New optional endpoint or opcode, additional configuration options, change of large subsystems or dependencies
- **Patch**: Bug fixes in any domain

Examples: Fixing a race condition, fixing unexpected exceptions, fixing output that is not according to specs, etc.

While major, minor and patch will do an optimum effort to adhere to [Semantic Versioning](https://semver.org/), prepending it with an additional API version makes life easier for developers in two ways: It is a clear way for the Lavalink project to communicate the relevant breaking changes to client developers, and in return, client developers can use the API version to communicate to their users about the compatibility of their clients to the Lavalink server.


## Credits

**We don't own any files all files are from orginal owner, this is an own doc for future use**
