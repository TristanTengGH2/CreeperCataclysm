<div align="center">

# 💥 Creeper Cataclysm

**A team-based Minecraft minigame where one side hunts the creeper and the other side guards it.**

![Minecraft](https://img.shields.io/badge/Minecraft-1.21.5-62B47A?style=for-the-badge&logo=minecraft&logoColor=white)
![Spigot](https://img.shields.io/badge/Spigot%20%2F%20Paper-Plugin-ED8106?style=for-the-badge)
![Java](https://img.shields.io/badge/Java-17-007396?style=for-the-badge&logo=openjdk&logoColor=white)
![License](https://img.shields.io/badge/License-GPLv3-blue?style=for-the-badge)

</div>

---

## 🎮 How It Works

Players queue up, get shuffled onto two teams, and are dropped into a map for a timed match.

| Team | Goal |
| --- | --- |
| 🔴 **Attackers** | Kill the defenders' creeper before time runs out |
| 🔵 **Defenders** | Keep the creeper alive until the clock hits zero |

Kills earn **gold**, and gold buys gear from the in-game shop. Defenders get an alarm whenever the creeper is under attack, and a comeback buff gives the losing side extra gold per kill so matches stay close.

## ✨ Features

- 🧭 **Queue and matchmaking** with random team assignment
- 🗺️ **Multiple maps** defined entirely in `config.yml`
- 💰 **Gold economy** with a team-specific shop
- 🛒 **Shop items** such as swords, shields, golden apples, fire charges, goat horns, wind charges, maces, and eggs
- 🪝 **Grappling hook** for fast movement around the map
- 🗿 **Team statues** and zone particles that show who controls what
- 📈 **Comeback buffs** that kick in when one team falls behind
- 🛠️ **Admin and debug commands** for building maps and testing matches

## 📦 Requirements

- Java 17 or newer
- A Spigot or Paper server on **Minecraft 1.21.5**
- [ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/)
- [WorldEdit](https://enginehub.org/worldedit)

## 🚀 Installation

1. Download `CreeperCataclysm.jar` from the [Releases](../../releases) page, or build it yourself (see below).
2. Drop the jar into your server's `plugins/` folder along with ProtocolLib and WorldEdit.
3. Start the server once so the default `config.yml` is generated.
4. Set up your lobby and maps (see [Setting Up a Map](#-setting-up-a-map)).
5. Run `/reloadconfig` and have players use `/play`.

## 🔨 Building

```bash
git clone https://github.com/TristanTengGH2/CreeperCataclysm.git
cd CreeperCataclysm
mvn clean package
```

The shaded jar ends up in `target/`.

## ⌨️ Commands

### Player commands

| Command | Aliases | Description |
| --- | --- | --- |
| `/play` | `/join`, `/p`, `/j` | Join the queue for a game |
| `/queue` | `/q` | List the players in the queue |
| `/leave` | `/l`, `/quit` | Leave the queue |
| `/creepercommands` | `/cc`, `/helpcreeper` | List all commands |
| `/grapplinghook` | `/hook` | Give yourself a grappling hook |

### Admin and debug commands

| Command | Aliases | Description |
| --- | --- | --- |
| `/forcestart` | `/fs`, `/start` | Force a game to start |
| `/abort` | `/a` | Abort the current game |
| `/setplayers <n>` | | Set the number of players in a game |
| `/settime <n>` | `/st` | Set the match time |
| `/addgold <player> <amount>` | `/ag` | Give gold to a player |
| `/switchteam` | | Switch teams |
| `/resetdeaths` | `/rd` | Reset all player deaths |
| `/captureprogress <int>` | `/progress` | Set the capture progress |
| `/statue <red/white/blue>` | | Set the statues to a team color |
| `/tplobby` | | Teleport to the lobby |
| `/tpsnow` | | Teleport to the snow map |
| `/reloadconfig` | | Reload `config.yml` |

## 🗺️ Setting Up a Map

Maps live under the `maps:` section of `config.yml`. Each map needs these locations, each with `world`, `x`, `y`, `z`, `yaw`, and `pitch`:

```yaml
maps:
  mymap:
    attackerspawn:     # where attackers start
    attackervillager:  # attacker shop villager
    defenderspawn:     # where defenders start
    defendervillager:  # defender shop villager
    creeper:           # the creeper to protect
```

The lobby is set with the top level `lobby:` section. You can use `/zonelobby`, `/zonemap <map>`, and `/cancelzone` to select regions in game, and `/setspecial` to mark special blocks.

## 🗂️ Project Layout

```
src/main/java/com/skle/creepercataclysm/
├── commands/     player and admin commands
│   └── debug/    testing helpers
├── listeners/    damage, death, explosions, items, chat, respawn
├── managers/     game, gold, queue, shop, statue, and zone logic
├── packets/      ProtocolLib packet wrappers
└── api/          plugin interface
```

## 🤝 Contributing

Issues and pull requests are welcome. Please open an issue first for larger changes so we can talk it through.

## 📄 License

Released under the [GNU General Public License v3.0](LICENSE).
