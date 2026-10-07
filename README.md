<div align="center">

# Hyper Island for Windows

**An iOS 26 "Liquid Glass" Dynamic Island for Windows, built as a [Windhawk](https://windhawk.net) mod.**
---
![Hyper Island](https://github.com/Tanmay-Tiwaricyber/HyperLand/blob/main/banner.png?raw=true)
Swipeable pages · Full-screen Focus timer · Per-app volume mixer · Any-player media · Tasks & expenses · Clipboard history · File Shelf · Wellness tracking
---

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-0078D4.svg)
![Language](https://img.shields.io/badge/language-C%2B%2B-00599C.svg)
![Windhawk](https://img.shields.io/badge/Windhawk-tool%20mod-orange.svg)
![Version](https://img.shields.io/badge/version-2.6.0-brightgreen.svg)

</div>

---

## Overview

**Hyper Island** turns the top of your Windows desktop into an interactive, iPhone-style Dynamic Island. It is a single unified surface for the things you normally reach for in the taskbar and tray: volume, brightness, media, notifications, calendar, tasks, focus sessions, and more.

It is a Windhawk **tool mod**: it runs in its own `windhawk.exe` process and draws a layered, click-through overlay. **It does not inject into or modify Explorer.**

> Hover the pill to peek, click to open the panel, swipe left/right to change pages, click outside to dismiss.

## Features

### Look and motion
- **Liquid Glass material:** real blur-behind with boosted saturation, top-lit sheen, caustic highlights, inner edge glow, a specular rim, a cursor-following light, and a soft floating shadow.
- **iPhone-style spring animation:** bouncy expand with slight overshoot, firmer collapse, content scales and fades in as the island morphs.
- **Vector icons (SF Symbols style):** crisp on Windows 10 and 11, no icon font required.
- **Apple system palette** with the "SF Pro" font when installed, falling back to Segoe UI Variable.
- **Backdrop styles:** `Translucent`, `Glass`, `Frosted`, `Acrylic`, `Liquid`, or `None`, fully tweakable with inline `Key=Value` overrides.
- **Themes:** Auto (follows Windows), Dark, Light, or Adaptive (follows the background).

### Pages (swipe, trackpad swipe, Shift + wheel, or click the dots)

| Page | What it does |
|---|---|
| **Home** | Media controls with live waveform, volume, brightness, battery, and quick actions (Lock, Screenshot, Settings, Task Manager, Mic mute) |
| **Alerts** | Full notification center: tap to open the app, dismiss, or clear all |
| **Sound** | Per-app volume mixer with per-app mute; audible apps float to the top and glow |
| **Calendar** | Month view backed by your Outlook published `.ics` feed, with task and expense markers |
| **Plan** | Per-day tasks and expenses with glass "New Task" / "New Expense" popups |
| **Notes** | Quick notes with add, edit, one-tap copy, and delete |
| **Shelf** | Drag files or folders onto the island to hold them; open, reveal in Explorer, copy, or remove. Files are referenced, never moved |
| **Wellness** | Daily water tracker (goal, last-7-days bars, optional reminders) and a habit tracker with streaks |
| **Focus** | Pomodoro (25/5 or 50/10) and stopwatch with daily history |
| **Tools** | Clipboard history, system info, and a live Bluetooth / Wi-Fi connections card |

### Highlights
- **Any player, not just Spotify:** media from Spotify, Chrome / Edge / Firefox, Apple Music, and anything exposed via Windows media controls. Players without media controls (VLC, many games) are detected from live audio output and controlled via media keys. The active app is tinted with its brand color.
- **Full-screen Focus timer:** a large ring timer takes over the screen. `Space` pauses, `Esc` (or switching away) minimizes it back to the island while the session keeps running.
- **Notification showcase:** new Windows notifications pop out of the island as a two-line banner.
- **Smart popups:** battery plug/unplug and low-battery, Bluetooth connect and low-battery (with battery %), Wi-Fi / Ethernet connect and disconnect, and water reminders.
- **Volume OSD replacement:** optionally captures the hardware volume keys so the island shows its own volume popup instead of the native flyout.
- **Multi-monitor aware:** pin to a monitor by number, by name (EDID), or to the laptop's built-in panel.

## Requirements

- Windows 10 or Windows 11
- [Windhawk](https://windhawk.net) (v1.4 or newer recommended)
- Optional: a monitor that supports DDC/CI (for the brightness slider; it hides itself automatically when unsupported)

## Installation

1. Install [Windhawk](https://windhawk.net/).
2. Open Windhawk and click **Create a new Mod** (the pencil icon).
3. Replace the template contents with the contents of [`HyperLand-v2.cpp`](./HyperLand-v2.cpp).
4. Click **Compile Mod** (or press `Ctrl+B`), then enable the mod.
5. The island appears at the top-center of your primary monitor.

To hide the duplicate native taskbar items, pair it with Windhawk's **Taskbar tray system icon tweaks** mod (bell, volume, battery, network) and a clock mod or the Taskbar Styler.

## Usage

| Action | Result |
|---|---|
| Hover the pill | Peek / highlight |
| Click the pill | Open the panel |
| Drag, two-finger swipe, or `Shift` + wheel | Change page |
| Click the page dots | Jump to a page |
| Click outside | Dismiss |
| Drag a file onto the island | Open the Shelf and hold the item |
| Click a calendar date | Select the day; add tasks or expenses |
| Type `250 lunch` in a new expense | Logs 250 with the note "lunch" (amount first or last) |
| `Space` / `Esc` in full-screen Focus | Pause or resume / minimize to the island |

## Configuration

All options are available in the Windhawk mod settings panel.

| Setting | Default | Description |
|---|---|---|
| `Position` | `top-center` | `top-center`, `top-left`, `top-right`, `bottom-center` |
| `TargetMonitor` | `0` | `0` primary, `1-8` by number, `-1` follow the mouse, or a name such as `internal`, `laptop`, `Dell` |
| `OffsetX` / `OffsetY` | `0` | Pixel offsets |
| `SizeScale` | `1.0` | Overall island scale |
| `AutoDpiScale` | `true` | Scale with monitor DPI |
| `AlwaysOnTop` | `true` | Keep the island above other windows |
| `PillOpacity` | `1.0` | Fades the whole island (0.35 to 1.0) |
| `Theme` | `auto` | `auto`, `dark`, `light`, `adaptive` |
| `BackdropStyle` | `$Liquid FocusOpacity=0.36` | Inline style string (see below) |
| `LiquidGlass` | `true` | Specular rim, caustics, edge glow, cursor light |
| `SpringBounce` | `true` | iPhone-style bouncy motion |
| `FocusFullscreen` | `true` | Full-screen Pomodoro timer |
| `ClipboardHistory` | `true` | In-memory clipboard history (turn off if you copy secrets) |
| `AudioFallback` | `true` | Show apps without media controls (VLC, games) |
| `ExpenseCurrency` | *(rupee sign)* | Up to 3 characters, e.g. `$`, `EUR`, `Rs` |
| `CalendarIcsUrl` | *(empty)* | Your Outlook published-calendar `.ics` URL |
| `CalendarRefreshMinutes` | `20` | Calendar refresh interval |
| `BrightnessEnabled` | `true` | Brightness slider via DDC/CI |
| `WeatherCity` | *(auto by IP)* | e.g. `Colorado Springs, CO` |
| `WeatherFahrenheit` | `true` | Off = Celsius |
| `CaptureVolumeKeys` | `true` | Replace the native volume flyout |
| `NotificationPopups` | `true` | Banner for new Windows notifications |
| `BluetoothPopups` | `true` | Device connect and low-battery popups |
| `WifiPopups` | `true` | Wi-Fi / Ethernet connect and drop popups |
| `WaterGoal` | `8` | Daily water goal (glasses) |
| `WaterReminderMinutes` | `90` | Reminder interval, `0` = off (08:00 to 22:00) |

### Backdrop style syntax

```
[$Name] [Key=Value ...]
```

**Names:** `None`, `Translucent` (blur 15), `Glass` (blur 5), `Frosted` (blur 20), `Acrylic` (blur 30), `Liquid` (blur 28, strong saturation).

**Keys:** `BlurAmount`, `TintSaturation`, `TintColor` (`theme`, `accent`, `#RRGGBB`, or `#AARRGGBB`), `TintOpacity`, `FallbackColor`, `FallbackOpacity`, `FocusOpacity`.

```text
$Liquid FocusOpacity=0.36                      # default
$Glass TintColor=#3388CC TintOpacity=0.5       # custom blue glass
$Frosted TintColor=accent FallbackColor=#1A1A1A
BlurAmount=22 TintSaturation=1.1               # fully custom
None                                           # no backdrop
```

## Privacy and data

- **Local first.** There is no telemetry and no account.
- User data is stored as UTF-8 text files (Hindi and other scripts work) in `%LOCALAPPDATA%\IslandCommandCenter\`: `tasks.txt`, `expenses.txt`, `notes.txt`, `shelf.txt`, `water.txt`, `habits.txt`, `study-history.txt`.
- **Clipboard history is kept in memory only** and never written to disk.
- **File Shelf** only stores references to your files; nothing is moved or copied.
- **Network use:** the calendar `.ics` feed you configure (treated as private) and weather lookups. Nothing else is sent anywhere.
- **Volume key capture** uses a low-level keyboard hook, and only to intercept volume up/down/mute. You can disable it with `CaptureVolumeKeys`.

## Versions

| File | Mod name | Version | Notes |
|---|---|---|---|
| [`HyperLand-v2.cpp`](./HyperLand-v2.cpp) | Hyper Island | 2.6.0 | **Current.** Swipe pages, Focus timer, Shelf, Notes, Wellness, Bluetooth/Wi-Fi popups, notification showcase |
| [`HyperLand-v1.cpp`](./HyperLand-v1.cpp) | Dynamic Island for Windows | 2.4.0 | Previous release: single-panel layout, per-app mixer, any-player media, per-day tasks and expenses |

<details>
<summary><b>Changelog</b></summary>

### v2.6
- Notification showcase banner and a dedicated **Alerts** page
- **File Shelf** (drag and drop)
- **Quick Notes** page
- **Wellness** page: water tracker and habit streaks
- Bluetooth and Wi-Fi popups, plus a live Connections card on Tools
- Ten swipeable pages in total

### v2.5
- Swipeable pages: Home, Sound, Calendar, Plan, Focus, Tools
- Full-screen Focus timer
- Glass popups for New Task / New Expense
- Clipboard history (in memory)

### v2.4
- Per-day tasks and expenses with calendar markers
- Any-player media with audio-output fallback and brand colors
- Per-app volume mixer
- Battery row, plug/unplug and low-battery popups, Quick Actions row

### v2.3
- iOS 26 Liquid Glass rendering and spring motion

### v2.2
- SF Symbols-style vector icons, Apple palette, SF Pro font support

</details>

## Troubleshooting

| Problem | Try this |
|---|---|
| No blur or glass effect | Enable **Transparency effects** in Windows Settings > Personalization > Colors. Without it the mod falls back to a denser tint |
| Brightness slider missing | Your monitor does not support DDC/CI; this is expected, and the slider hides itself |
| Island on the wrong monitor | Set `TargetMonitor` to a name (`internal`, `Dell`) instead of a number, since numbers can shift after sleep or docking |
| Native volume popup still shows | Make sure `CaptureVolumeKeys` is enabled |
| Compile errors in Windhawk | Update Windhawk to the latest version and make sure the mod's compiler options were kept when pasting |

## Contributing

Contributions are welcome.

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Commit your changes: `git commit -m "Add my feature"`
4. Push the branch and open a Pull Request.

Please open an issue first for large changes. When reporting a bug, include your Windows version, Windhawk version, mod version, monitor setup, and steps to reproduce.

## License

Released under the **MIT License**. This project is a modified derivative of an original MIT-licensed work, and the original license notice is retained as the license requires. See [`LICENSE`](./LICENSE) for details.

## Author

**Tanmay Tiwari**

- GitHub: [@Tanmay-Tiwaricyber](https://github.com/Tanmay-Tiwaricyber)
- Instagram: [@iamt4nm4y](https://instagram.com/iamt4nm4y)

## Acknowledgements

- [Windhawk](https://windhawk.net) by m417z, the platform this mod runs on
- The author of the original MIT-licensed Dynamic Island mod this project builds on
- Apple's iOS design language, which inspired the visuals (this project is not affiliated with Apple)

---

<div align="center">

If you find this project useful, consider giving it a ⭐

</div>
