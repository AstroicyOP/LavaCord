# lavalink-repl
Lavalink on replit
<br>
<a href="https://replit.com/github/kagchi/lavalink-repl"><img src="https://img.shields.io/badge/REPL-FORK-green"></a>
## Connecting
- [x] Lavalink's port will always 443 
- [x] Default password `youshallnotpass`
- [x] using custom lavalink client if your client doesnt support secure options


## Important notes:
- [x] Do not change port in `application.yml`
- [x] To keep this 24/7 you need to make an account on UptimeRobot service, and make HTTP request to your app every 5 minutes. For example, if your app is named `lavalink-repl` and your repl username is `ahmasa` then make HTTP request to `https://lavalink-repl.ahmasa.repl.co`
- [x] Do not forget to set your password (in `application.yml` file)
- [x] Connection to node must be secured E.g https/wss\
- [x] Does not automatically update, you must specify `AUTO_UPDATE` true in environtment variables 
## Advantages:
- [x] Use java 13 :3
- [x] Easy setup
- [x] Using Dev build
## Glitch
- for glitch user here [Repo](https://github.com/KagChi/lavalink-glitch)

## Example
- [x] Latest Astroicy (v1.6.x)
```js
const { Client } = require('discord.js');
const { Astroicy, Libraries } = require('Astroicy');

const LavalinkServer = [{ name: 'my-lavalink-server', url: 'lavalink-repl.ahmasa.repl.co:443', auth: 'youshallnotpass', secure: true }];
const AstroictOptions = { moveOnDisconnect: false, resumable: false, resumableTimeout: 30, reconnectTries: 2, restTimeout: 10000 };

class ExampleBot extends Client {
    constructor(opts) {