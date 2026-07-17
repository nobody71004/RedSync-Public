<pre align="center">
╔══════════════════════════════════════════════════════════════════╗
║                                                                  ║
║   ██████╗ ███████╗██████╗ ███████╗██╗   ██╗███╗   ██╗ ██████╗    ║
║   ██╔══██╗██╔════╝██╔══██╗██╔════╝╚██╗ ██╔╝████╗  ██║██╔════╝    ║
║   ██████╔╝█████╗  ██║  ██║███████╗ ╚████╔╝ ██╔██╗ ██║██║         ║
║   ██╔══██╗██╔══╝  ██║  ██║╚════██║  ╚██╔╝  ██║╚██╗██║██║         ║
║   ██║  ██║███████╗██████╔╝███████║   ██║   ██║ ╚████║╚██████╗    ║
║   ╚═╝  ╚═╝╚══════╝╚═════╝ ╚══════╝   ╚═╝   ╚═╝  ╚═══╝ ╚═════╝    ║
║                                                                  ║
║          NIGHT CITY MULTIPLAYER  ·  CYBERPUNK 2077 v2.31         ║
║                     PROTOCOL 0x7  ·  NET 9                       ║
╚══════════════════════════════════════════════════════════════════╝
</pre>

<p align="center">
  <img alt="status" src="https://img.shields.io/badge/STATUS-ONLINE-ff2a32?style=for-the-badge&labelColor=050203" />
  <img alt="game" src="https://img.shields.io/badge/CP2077-2.31-c4141c?style=for-the-badge&labelColor=050203" />
  <img alt="launcher" src="https://img.shields.io/badge/LAUNCHER-BLACKWALL-ff2a32?style=for-the-badge&labelColor=050203" />
  <img alt="region" src="https://img.shields.io/badge/RELAY-USA-9a2028?style=for-the-badge&labelColor=050203" />
  <img alt="events" src="https://img.shields.io/badge/EVENTS-SMASHER_%2B_CERBERUS-b81820?style=for-the-badge&labelColor=050203" />
  <img alt="license" src="https://img.shields.io/badge/LICENSE-MIT-6a0c12?style=for-the-badge&labelColor=050203" />
</p>

<p align="center">
  <b>Client plugin · Redscript layer · .NET game server · C++ networking core</b><br/>
  Jack in with <code>RedSyncLauncher.exe</code> ·
  <a href="https://xbuniverse.duckdns.org/api/media/RedSync-Tester-Client.zip">Download package</a> ·
  <a href="#04-quick-start">Quick start</a>
</p>

---


> [!IMPORTANT]
> **This repository is the public showcase face.** It mirrors the private RedSync README.  
> **No source code, binaries, configs, or credentials are published here.** Implementation lives in the private repository.

## `00` SYSTEM MATRIX

> Status bars show **live capability**. Launcher + in-game chat are **ONLINE**.

### Online systems

| Subsystem | Link | Status |
| --- | --- | --- |
| Connection & auth | `████████████` | **ONLINE** — UDP (GameNetworkingSockets), username auth + admin secrets |
| HUD overlay | `████████████` | **ONLINE** — ping, player count, connection state |
| **In-game chat** | `████████████` | **ONLINE** — **F6** player chat, history, `CHAT\|` markers, screen broadcasts |
| Server console | `████████████` | **ONLINE** — **F10** `help` / `who` / events / admin cmds |
| Admin panel | `████████████` | **ONLINE** — **F7** kick · ban · teleport · spectate · events |
| Player menu | `████████████` | **ONLINE** — **\`** online list, click-name teleport (all players) |
| RedSync Launcher | `████████████` | **ONLINE** — `RedSyncLauncher.exe` Blackwall UI: install, matchmaker list, JACK IN |
| Matchmaker list | `████████████` | **ONLINE** — server / relay browser in the launcher |
| Join / leave | `████████████` | **ONLINE** — puppets spawn & despawn with players |
| Movement sync | `████████████` | **ONLINE** — ~10 Hz position stream |
| Animation / locomotion | `████████████` | **ONLINE** — remote puppets play walk / run |
| Player puppets | `████████████` | **ONLINE** — Jackie/Judy stand-ins + nametags |
| Weapons / PvP | `████████████` | **ONLINE** — equip, shot relay, server hitscan damage |
| **PROJECT SMASHER** | `████████████` | **ONLINE** — admin co-op Adam Smasher wave |
| **CERBERUS EVENT** | `████████████` | **ONLINE** — city-wide Cerberus hunt (Phantom Liberty) |
| World tools | `████████████` | **ONLINE** — `force open door` / `fod` |
| Server self-heal | `████████████` | **ONLINE** — prune · event timeout · empty cleanup |
| Anticheat / security | `████████████` | **ONLINE** — server validator · **admins always exempt** |
| Vehicles | `██████████░░` | **IMPROVED** — driver stand-in hidden while car syncs; faster vehicle pose |
| Proximity voice | `████████░░░░` | **ONLINE** — press **.** to toggle mic (~45m, CET + UDP 2078) |

---

## `01` CONTROL DECK

| Input | System |
| --- | --- |
| **\`** | Player menu |
| **F6** | **Chat** (live) |
| **F10** | Console |
| **F11** | Stop/resume world (cars + NPCs) |
| **.** (period) | Toggle proximity voice chat |
| **F7** | Admin panel |
| `stopworld` / `freeze` | Same as F11 (console/chat) |
| `projectsmasher` / `smasherevent` | PROJECT SMASHER (admin) |
| `cerberusevent` / `cerebus` | CERBERUS EVENT (admin) |
| `endevent` | Clear active event NPCs |
| `force open door` / `fod` | Open + despawn looked-at door |
| `broadcast <msg>` | On-screen announce (admin) |
| `chat <msg>` / `say <msg>` | Send chat |
| `health` | Self-heal snapshot (admin) |
| `security` / `sec` | Anticheat snapshot (admin) |

---

## `02` COMMS — CHAT LIVE

Press **F6**. Messages fan out to every connected player. History lives in the F6 panel and the player menu.

| Input | Behavior |
| --- | --- |
| Normal text | Chat → all players |
| `say <msg>` / `chat <msg>` | Explicit chat send |
| Server commands | Type in F6 **without** wrapping as `chat …` (e.g. `who`, `projectsmasher`, `cerberusevent`) |
| `broadcast <msg>` | Admin toast on every screen + chat line |

Wire markers: `CHAT|name|text` · admin screens: `SCREEN|…`

---

## `03` COMBAT EVENTS

One combat event at a time. New event clears the previous. Event NPCs use **shared server HP**; death despawns for everyone. `endevent` / F7 **End event** clears the wave. Leftovers: `purge` / `gc`.

### PROJECT SMASHER

Co-op wave: **5–10** Adam Smashers (`Character.Smasher`) in a ring at the commanding player.

| Start | Stop |
| --- | --- |
| F7 → **PROJECT SMASHER** | F7 → **End event** |
| F10 / F6: `projectsmasher` or `smasherevent [5-10]` | `endevent` |

Aliases: `smasher`, `adamevent`, `project smasher`.

### CERBERUS EVENT

City-wide hunt: **8–50** Cerberus bots (default **28**) — rings around players + Night City landmarks. Record: `Character.q305_cerberus` (**Phantom Liberty**). Proximity refresh streams bots as you approach.

| Start | Stop |
| --- | --- |
| F7 → **CERBERUS EVENT** | F7 → **End event** |
| F10 / F6: `cerberusevent [8-50]` | `endevent` / `purge` |

Aliases: `cerebus`, `cerebusevent`, `cerberus`, `cerberus event`, `cerebus event`.

After script updates, clear `r6/cache` so redscript recompiles.

---

## `04` QUICK START

1. Download the slim launcher package:
   - CDN: [RedSyncLauncher.zip](https://xbuniverse.duckdns.org/api/media/RedSyncLauncher.zip)
   - Page: [RedSync.html](https://xbuniverse.duckdns.org/api/media/RedSync.html) (Blackwall download)
2. Unzip and run **`RedSyncLauncher.exe`** (no Python required).
3. First run offers **Install / Repair** (RED4ext, redscript, Codeware, RedSync + voice).
4. Enter a callsign, select the **USA** official relay (`88.214.59.166:2077`), click **JACK IN**.
5. Load into Night City — HUD shows ping + online players.

After script updates: **Install / Repair** in the launcher (or `Install-All.bat`).

Launcher docs ship inside the download package (`START-HERE.txt` · `RedSyncLauncher/README.txt`).

```
--redsync-server-address=<ip> --redsync-server-port=2077 --launcher-skip
```

Use `127.0.0.1` only on the machine running the server. Remote clients need LAN IP or public/VPS address.

Do **not** copy `game-path.cfg`, `launch-args.cfg`, or `server-address.cfg` between PCs — they are created locally.

---

## `05` REQUIREMENTS

| Dependency | Version | Role |
| --- | --- | --- |
| [Cyberpunk 2077](https://store.steampowered.com/app/1091500/) | **2.31** | Other patches unsupported |
| [RED4ext](https://github.com/WopsS/RED4ext) | 1.30.0+ | Plugin loader |
| [redscript](https://github.com/jac3km4/redscript) | 0.5.31+ | Script compiler |
| [Codeware](https://github.com/psiberx/cp2077-codeware) | 1.18.0+ | Entity spawning |
| [Cyber Engine Tweaks](https://github.com/maximegmd/CyberEngineTweaks) | 1.37.0+ | Required by AMM |
| [Appearance Menu Mod](https://www.nexusmods.com/cyberpunk2077/mods/790) | 2.4+ | Remote player appearance as V |

Server from source: **.NET 9**. Tester package notes cover the packaged host runtime.

---

## `06` ARCHITECTURE

```
┌──────────── CLIENT ────────────┐          ┌──────────── SERVER ────────────┐
│  Redscript  →  RED4ext C++     │ ── UDP ─ │  Native C++ sockets/framing    │
│  UI · puppets · Codeware       │          │  → .NET 9 logic · entities     │
└────────────────────────────────┘          └────────────────────────────────┘
                    shared/protocol  ·  revision must match  ·  0x7
```

| Component | Role |
| --- | --- |
| `client/red4ext` | Networking, clientbound spawn/teleport/destroy, serverbound actions |
| `client/RedscriptModule` | Game events, UI, puppet spawn/teleport via Codeware |
| `server/Native` | Low-level sockets and serialization |
| `server/Managed` | Players, entities, admin, events, chat fan-out, self-heal, security |

---

## `07` SELF-HEAL

Long-uptime safeguards (no extra config):

| Behavior | Default |
| --- | --- |
| Prune stale entity tracking / send-state | every **30s** |
| Auto-clear active combat event | after **45 min** |
| Empty-server cleanup | after **3 min** empty |
| Health snapshot in logs | every **5 min** |
| Event NPC damage cooldown | **180ms** per player→NPC |
| Graceful `stop` | clears events then exits |

Admin: `health` / `status` · `gc` / `selfheal` / `purge`  
Logs: `logs/log.txt` · Discord: `REDSYNC_DISCORD_WEBHOOK=off` to disable.

---

## `08` SECURITY

Server-side validator (not client AC). Config next to the binary: **`security.json`** (auto-created on first run).

**Admins are always exempt** from rate limits, movement checks, combat correlation, entity caps, and auto kick/ban. Cannot be disabled.

| Option | Default | Mitigation |
| --- | --- | --- |
| `enabled` | `true` | Master switch |
| `mode` | `enforce` | `observe` = log only; `enforce` = reject + punish |
| `adminExempt` | `true` (forced) | Allowlisted admins bypass all checks |
| `maxSpeedMetersPerSecond` | `48` | Speed / teleport spike detection |
| `maxTeleportMeters` | `90` | Hard position jump cap |
| `snapBackOnTeleport` | `true` | Reject + snap to last good position |
| `shootMinIntervalMs` / `hitMinIntervalMs` | `75` | Packet flood / rapid-fire |
| `allowClientPvpHit` | `true` | Client OnHit assists hitscan (debounced to avoid double damage) |
| `playerHitRequiresRecentShootMs` | `900` | Event hits need recent `PlayerShoot` |
| `eventHitMaxRangeMeters` / `eventHitMaxDamage` | `90` / `120` | Spoofed event-NPC damage |
| `maxOwnedVehicles` / `maxOwnedItems` | `1` / `16` | Entity spam |
| `restrictTptoToAdmin` | `false` | Any player can teleport to players via the ` menu |
| `autoKick` / `autoBan` | `true` / `false` | warn 8 / kick 20 / ban 45 |
| `violationDecayPerMinute` | `4` | Score cools down |

Commands: `security` / `sec` / `flags` · process console: `security reload`.

### Threat map

| Threat | Mitigation |
| --- | --- |
| Teleport / speed hack | Movement sanity + snap-back |
| Spoofed `PlayerHit` | Hitscan-only PvP; event hits need shoot + range + clamp |
| Shoot / hit floods | Per-type rate limits + violation score |
| Vehicle / item spam | Caps + spawn/equip intervals |
| Unauthenticated world packets | Dropped if not connected |
| Free `tpto` | Admin-only by default |
| Repeat offenders | Warn → kick → optional auto-ban |

Does **not** claim to stop a determined local cheater forever — makes abuse noisy, limited, and kickable.

---

## `09` RUN SERVER

**Docker** (after copying protocol into the server tree):

```bash
cp -r shared/protocol server/protocol
cd server
docker build -t redsync-server .
docker run -d --name redsync-server --restart unless-stopped \
  -p 2077:2077/tcp -p 2077:2077/udp redsync-server
```

**Local / release:** `RedSync - Start Server.bat` or `server/Start-Server.bat` (UDP/TCP **2077**).

From source: `dotnet publish -c Release` on `server/Managed`, then run `RedSync.Server` (.NET 9).

---

## `10` BUILD CLIENT

Visual Studio 2022, CMake, vcpkg:

```powershell
$env:VCPKG_ROOT = "C:\path\to\vcpkg"
cmake -S client/red4ext -B client/red4ext/build/vs-vcpkg `
  -DCMAKE_TOOLCHAIN_FILE="$env:VCPKG_ROOT\scripts\buildsystems\vcpkg.cmake" `
  -DCMAKE_BUILD_TYPE=Release -G "Visual Studio 17 2022" -A x64
cmake --build client/red4ext/build/vs-vcpkg --config Release
```

Output: `client/red4ext/build/vs-vcpkg/src/Release/RedSync.Red4Ext.dll`

### Manual install

| Source | Destination |
| --- | --- |
| `RedSync.Red4Ext.dll` | `red4ext/plugins/` |
| Runtime DLLs (`GameNetworkingSockets`, protobuf, abseil, OpenSSL) | `bin/x64/` |
| `client/RedscriptModule/src/` → `RedSync/` | `r6/scripts/RedSync/` |

Delete `r6/cache` (or `final.redscripts.modded`) after install / script updates.

Healthy log (`%LOCALAPPDATA%\RED4ext\RedSync.log` or `red4ext/logs/`): connect → login accepted → `PlayerJoinWorld`.

---

## `11` ADMIN

Allowlisted usernames open **F7** and run admin commands (server-enforced).

Next to `RedSync.Server.exe` (restart after edits):

```json
[
  { "name": "YourUsername", "secret": "optional-join-secret" }
]
```

File: `admins.json` (or `admins.txt`, one name per line). Names match join name / `username.cfg` (case-insensitive). Reserved admin names can require `username~secret` at join. Process console always has full access.

---

## `FF` LICENSE & CREDITS

[MIT](LICENSE) — Copyright (c) 2023–2026 **XEROX710**.

Originally based on earlier open multiplayer work for Cyberpunk 2077. RedSync continues that work under MIT with copyright held by XEROX710.

<pre align="center">
┌─────────────────────────────────────────┐
│  REDSYNC  ·  STAY FROSTY, CHOOM         │
│  PUBLIC FACE  ·  SOURCE STAYS DARK      │
└─────────────────────────────────────────┘
</pre>
