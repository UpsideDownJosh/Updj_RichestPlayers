# Updj_RichestPlayers
A lightweight FiveM resource that ranks the richest players on your server by cash + bank and posts a clean Discord embed on a configurable interval. ESX &amp; QBCore compatible, with online-only or full-database modes.


![Framework](https://img.shields.io/badge/framework-ESX%20%7C%20QBCore-blue)

---

## ✨ Features

- 🏆 **Top X leaderboard** — ranks players by total wealth (cash + bank)
- 🤖 **Auto-detects framework** — works with ESX or QBCore out of the box
- 💬 **Discord webhook integration** — posts a polished embed with medals for the top 3
- 🗄️ **Two ranking modes** — pull from the database (all characters) or live (online only)
- ⏱️ **Configurable interval** — auto-posts every X minutes
- 🛡️ **Admin command** — manually trigger the leaderboard with ACE permissions
- 🎨 **Fully customizable embed** — title, color, bot name, avatar, footer

---

## 📦 Installation

1. Download or clone this repo into your `resources` directory:
```bash
   cd resources
   git clone https://github.com/YOUR_USERNAME/updj_richRichestPlayers.git
```

2. Add to your `server.cfg` **after** your framework and `oxmysql`:
```cfg
   ensure oxmysql
   ensure es_extended      # or qb-core
   ensure updj_richRichestPlayers
```

3. Open `config.lua` and paste your Discord webhook URL:
```lua
   Config.Webhook = 'https://discord.com/api/webhooks/...'
```

4. (Optional) Grant the admin command permission:
```cfg
   add_ace group.admin updj.leaderboard allow
```

5. Restart your server.

---

## ⚙️ Configuration

All settings live in `config.lua`:

| Setting | Type | Description |
|---|---|---|
| `Config.Framework` | string | `'esx'`, `'qbcore'`, or `'auto'` |
| `Config.Webhook` | string | Your Discord webhook URL |
| `Config.Interval` | number | How often the leaderboard auto-posts, in minutes |
| `Config.TopCount` | number | How many players to display (e.g. 10) |
| `Config.Mode` | string | `'database'` (all characters) or `'online'` (connected only) |
| `Config.Command` | string | Command name to manually trigger the leaderboard |
| `Config.Embed` | table | Title, color, bot name, avatar, footer |

---

## 🎮 Usage

The leaderboard posts automatically every `Config.Interval` minutes once the server starts.

To trigger it manually in-game (requires `updj.leaderboard` ACE permission):
```
/richlist
```

Or from the server console:
```
richlist
```

---

## 📋 Requirements

- [oxmysql](https://github.com/overextended/oxmysql)
- ESX (`es_extended`) **or** QBCore (`qb-core`)

---

## 🗃️ Database Notes

- **ESX** — expects the default `users` table with an `accounts` JSON column containing `money` and `bank` keys. If your server uses split columns, edit the query in `server.lua`.
- **QBCore** — uses the standard `players` table with the `money` and `charinfo` JSON columns. No changes required.

---

## 🖼️ Preview

> *(Add a screenshot of the Discord embed here once you've got one — drop it in a `/preview` folder and link it like `![Preview](preview/leaderboard.png)`)*

---

## 🛠️ Roadmap

- [ ] Top earners mode (income deltas between runs)
- [ ] Include dirty money / crypto in totals
- [ ] Job-filtered leaderboards (richest cops, criminals, etc.)
- [ ] Persistent message edit (update one embed instead of spamming)

---

## 📜 License

MIT © UPDJ Developmentz

---

## 💬 Support

For other UPDJ Developmentz resources, check out the [storefront](https://updjdevelopmentz.netlify.app) or get in touch on Discord.
