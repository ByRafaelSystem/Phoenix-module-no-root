# Phoenix — Gaming Performance Optimizer

<div align="center">

```
                    )
                 ) (:
               (   ) )
                `-._.-'

  |--\  |  |  /--\  |--  |\  |  |  \ /
  |--/  |--|  |  |  |--  | \ |  |   X
  |     |  |  \__/  |__  |  \|  |  / \

     Gaming Performance Optimizer
   Auto FPS & Refresh Rate · Non-Root
```

![Version](https://img.shields.io/badge/version-v1.0-red?style=flat-square)
![Android](https://img.shields.io/badge/Android-8.0%2B-green?style=flat-square&logo=android)
![AX Manager](https://img.shields.io/badge/AX%20Manager-supported-blue?style=flat-square)
![Magisk](https://img.shields.io/badge/Magisk-supported-orange?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)

**by [By_Rafael_System](https://github.com/ByRafaelSystem)**

[Telegram](https://t.me/proyect_diablo) · [GitHub](https://github.com/ByRafaelSystem) · [Download](https://github.com/ByRafaelSystem/Phoenix/releases/latest)

</div>

---

## Overview

**Phoenix** is a Magisk/AX Manager module that automatically detects when you launch a game and applies system-level performance tweaks in real time — no root required when used with AX Manager.

When a game from your list is detected in the foreground, Phoenix instantly:
- Boosts your device's refresh rate to peak
- Reduces animation overhead
- Frees up system resources

When you exit the game, everything is restored to normal automatically.

---

## Features

| Feature | Description |
|---|---|
| Auto FPS Boost | Detects active game and sets peak refresh rate |
| Auto Reset | Restores normal settings when game is closed |
| Gamelist Management | Add/remove games from the WebUI |
| Custom Banner | Set your own header image from gallery |
| Device Info | Full hardware and software details |
| System Tweaks | Animations, DNS, NFC, WiFi scan, thermal mode |
| Memory Tools | Kill background apps, trim cache, compact RAM |
| Root & Non-Root | Works with Magisk, KernelSU, APatch and AX Manager |

---

## Requirements

| Requirement | Details |
|---|---|
| Android | 8.0 or higher |
| Non-root | AX Manager v1.4+ |
| Root | Magisk 20+, KernelSU or APatch |

---

## Installation

### Non-Root (AX Manager)
1. Install [AX Manager](https://github.com/axernomy/AXManager) on your device
2. Open AX Manager → **Import Module** → select `Phoenix_v1.0.zip`
3. Enable the module and tap **Start**
4. Open the module's WebUI from AX Manager

### Root (Magisk / KernelSU / APatch)
1. Open your root manager → **Install from storage**
2. Select `Phoenix_v1.0.zip`
3. Reboot your device
4. Access the WebUI from your root manager's module list

---

## WebUI

Phoenix includes a full-featured web interface accessible directly from AX Manager or your root manager.

### Home Tab
- Module status toggle
- Live battery & RAM stats
- Active game detection (updates every 4 seconds)
- Current configuration summary

### Gaming Tab
- Peak refresh rate slider (60–165 Hz)
- Min refresh rate slider
- Check interval (how often to scan for active game)
- Auto boost toggle
- Full gamelist with add/remove support

### Tweaks Tab
- Animation scale (OFF / 0.5x / 1x)
- Kill background apps
- Trim cache
- Compact RAM
- Auto sync toggle
- NFC toggle
- WiFi background scan toggle
- Sustained performance mode
- DNS selector (Cloudflare, Google, Quad9)
- Thermal override
- Reset all to defaults

### Device Tab
- Brand, model, CPU, RAM, battery, Android version, kernel
- Author links (Telegram & GitHub)

---

## Configuration

Settings are stored in `config.prop` inside the module directory:

```
PEAK_RATE=120       # Hz to apply when game is active
MIN_RATE=60         # Hz to restore when game is closed
SLEEP_INTERVAL=5    # Seconds between foreground checks
AUTO_BOOST=1        # 1 = enabled, 0 = paused
BANNER_PATH=        # Optional: path to custom banner image
```

The gamelist is stored in `gamelist.txt`, one package name per line.

---

## Compatibility

Tested and working on:

| Device | Android | Method |
|---|---|---|
| Samsung (tanzanite) | Android 16 | AX Manager |
| Multiple brands | Android 8–16 | Magisk |

The module uses a dual detection method:
1. **Primary** — `dumpsys activity activities` (universal, non-root)
2. **Fallback** — `/proc/[pid]/oom_score_adj` (privileged shell, works with Unity/Vulkan fullscreen games)

---

## Included Games

Phoenix comes pre-configured with 24 popular games including:

PUBG Mobile, Free Fire, Mobile Legends, Genshin Impact, Honkai: Star Rail,
Call of Duty Mobile, Fortnite, Wild Rift, Minecraft, Clash of Clans,
Brawl Stars, Need for Speed, Real Racing 3, and more.

You can add any game via the WebUI's Gaming tab.

---

## How It Works

```
service.sh starts
      │
      ▼
Every N seconds: scan foreground app
      │
      ├── Game detected ──► apply peak refresh rate + animation tweaks
      │                     write state to /data/local/tmp/.phoenix_*
      │
      └── No game ────────► restore normal settings
```

The WebUI polls `/data/local/tmp/.phoenix_game` every 4 seconds to display the active game in real time.

---

## Changelog

### v1.0 — Initial Release
- Auto FPS & refresh rate optimizer
- Dual foreground detection (dumpsys + oom_score_adj)
- Full WebUI with 4 tabs
- Custom banner support (persists across sessions)
- 24 pre-configured games
- AX Manager and Magisk support
- Professional installer ASCII banner

---

## Author

**By_Rafael_System**

[![Telegram](https://img.shields.io/badge/Telegram-proyect__diablo-2CA5E0?style=flat-square&logo=telegram)](https://t.me/proyect_diablo)
[![GitHub](https://img.shields.io/badge/GitHub-ByRafaelSystem-181717?style=flat-square&logo=github)](https://github.com/ByRafaelSystem)

---

## License

This project is released under the MIT License.
Feel free to use, modify and share — credit is appreciated.
