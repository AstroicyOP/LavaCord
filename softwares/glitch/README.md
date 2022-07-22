# lavalink-glitch
Lavalink on glitch
<br>
# Special Thanks To
1. Neyo Golden#9887
2. freyacodes
3. Allva

## Connecting
- [x] Lavalink's port will always 443
- [x] Default password `youshallnotpass`
- [x] using custom lavalink client

## Important notes!!!
- [x] Glitch boost to keep 24/7 (glitch banned uptimerobot) 
- [x] Uptimerobot alternative [Link](https://discord.gg/X4vS3gn9N2)
- [x] Google appscript
- [x] Do not forget to set your password (in `application.yml` file)

## Advantages:
- [x] Use java 13 :3
- [x] Easy setup
- [x] Using Dev build

## Example:

- [x] Latest Astroicy (v1.6.x)
```js
const { Client } = require('discord.js');
const { Astroicy } = require('astroicy');
 
const LavalinkServer = [{ name: 'my-lavalink-server', host: 'lavalink-glitch.glitch.me', port: 443, auth: 'youshallnotpass', secure: true }];
const AstroicyOptions = { moveOnDisconnect: false, resumable: false, resumableTimeout: 30, reconnectTries: 2, restTimeout: 10000 };
 
class ExampleBot extends Client {
    constructor(opts) {
        super(opts);
        this.Astroicy = newAstroicy(this, LavalinkServer, AstroicyOptions);
    }
 
    login(token) {
        this._setupAstroicyEvents();
        this._setupClientEvents();
        return super.login(token);
    }
 
    _setupAstroicyEvents() {
        this.Astroicy.on('ready', (name) => console.log(`Lavalink ${name}: Ready!`));
        this.Astroicyu.on('error', (name, error) => console.error(`Lavalink ${name}: Error Caught,`, error));
        this.Astroicy.on('close', (name, code, reason) => console.warn(`Lavalink ${name}: Closed, Code ${code}, Reason ${reason || 'No reason'}`));
        this.Astroicy.on('disconnected', (name, reason) => console.warn(`Lavalink ${name}: Disconnected, Reason ${reason || 'No reason'}`));
    }
 
    _setupClientEvents() {
        this.on('message', async (msg) => {
            if (msg.author.bot || !msg.guild) return;
            if (!msg.content.startsWith('$play')) return;
            if (this.Astroicy.getPlayer(msg.guild.id)) return;
            const args = msg.content.split(' ');
            if (!args[1]) return;
            const node = this.Astroicy.getNode();
            let data = await node.rest.resolve(args[1]);
            if (!data) return;
            const player = await node.joinVoiceChannel({
                guildID: msg.guild.id,
                voiceChannelID: msg.member.voice.channelID
            }); 
            player.on('error', (error) => {
                console.error(error);
                player.disconnect();
            });
            for (const event of ['end', 'closed', 'nodeDisconnect']) player.on(event, () => player.disconnect());
            data = data.tracks.shift();
            await player.playTrack(data); 
            await msg.channel.send("Now Playing: " + data.info.title);
        });
        this.on('ready', () => console.log('Bot is now ready'));
    }
}
 
new ExampleBot()
    .login('token')
    .catch(console.error);
```
Example bot [here](https://github.com/Allvaa/lavalink-musicbot)
