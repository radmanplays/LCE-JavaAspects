![LCE Revelations Banner](.github/LCE-Revelations-banner.png)
# Legacy Console Edition Java Aspects

This project is based on Legacy Console Edition v1.6.0560.0 (TU19) with LCE-Revelations's fixes and improvements applied.

The current goal of LCE-JavaAspects is to port java 1.6.1's ui to Legacy Console edition as its the closest equivalent to TU19. On top of that, we're working to make this a quality experience on Desktop with or without a controller while (long-term) retaining console support.

See our our [Contributor's Guide](./CONTRIBUTING.md) for more information on the goals of this project.

## Download
### Client
Windows users can download our [Nightly Build](https://github.com/radmanplays/LCE-JavaAspects/releases/tag/Nightly)! Simply download the `.zip` file and extract it to a folder where you'd like to keep the game. You can set your username in `username.txt` (you'll have to make this file)

## Platform Support

- **Windows**: Supported for building and running the project
- **macOS / Linux**: The Windows nightly build will run through Wine or CrossOver based on community reports, but this is unofficial and not currently tested by the maintainers when pushing updates
- **Android**: VIA x86 EMULATORS (like GameNative) ONLY! The Windows nightly build does run but has stability / frametime pacing issues frequently reported
- **iOS**: No current support
- **All Consoles**: Console support remains in the code, but maintainers are not currently verifying console functionality / porting UI Changes to the console builds at this time.

## Features

- Dedicated Server Software (`Minecraft.Server.exe`)
- Fixed compilation and execution in both Debug and Release mode on Windows using Visual Studio 2022
- Added support for keyboard and mouse input
- Added fullscreen mode support (toggle using F11)
- (WIP) Disabled V-Sync for better performance
- Added a high-resolution timer path on Windows for smoother high-FPS gameplay timing
- Device's screen resolution will be used as the game resolution instead of using a fixed resolution (1920x1080)
- LAN Multiplayer & Discovery
- Added persistent username system via `username.txt`
- Decoupled usernames and UIDs to allow username changes
- Fixed various security issues present in the original codebase
- Splitscreen Multiplayer support (connect to dedicated servers, etc)
- In-game server management (Add Server button, etc)


## Controls (Keyboard & Mouse)

- **Movement**: `W` `A` `S` `D`
- **Jump / Fly (Up)**: `Space`
- **Sneak / Fly (Down)**: `Shift` (Hold)
- **Sprint**: `Ctrl` (Hold) or Double-tap `W`
- **Inventory**: `E`
- **Chat**: `T`
- **Drop Item**: `Q`
- **Crafting**: `C` Use `Q` and `E` to move through tabs (cycles Left/Right)
- **Toggle View (FPS/TPS)**: `F5`
- **Fullscreen**: `F11`
- **Pause Menu**: `Esc`
- **Attack / Destroy**: `Left Click`
- **Use / Place**: `Right Click`
- **Select Item**: `Mouse Wheel` or keys `1` to `9`
- **Accept or Decline Tutorial hints**: `Enter` to accept and `B` to decline
- **Game Info (Player list and Host Options)**: `TAB`
- **Toggle HUD**: `F1`
- **Toggle Debug Info**: `F3`
- **Open Debug Overlay**: `F4`
- **Toggle Debug Console**: `F6`

## Contributors
Would you like to contribute to this project? Please read our [Contributor's Guide](CONTRIBUTING.md) before doing so! This document includes our current goals, standards for inclusions, rules, and more.

## Client Launch Arguments

| Argument           | Description                                                                                         |
|--------------------|-----------------------------------------------------------------------------------------------------|
| `-name <username>` | Overrides your in-game username.                                                                    |
| `-fullscreen`      | Launches the game in Fullscreen mode                                                                |

Example:
```
Minecraft.Client.exe -name Steve -fullscreen
```

## LAN Multiplayer
LAN multiplayer is available on the Windows build

- Hosting a multiplayer world automatically advertises it on the local network
- Other players on the same LAN can discover the session from the in-game Join Game menu
- Game connections use TCP port `25565` by default
- LAN discovery uses UDP port `25566`
- Add servers to your server list with the in-game Add Server button (temp)
- Rename yourself without losing data by keeping your `uid.dat`
- Split-screen players can join in, even in Multiplayer

## Build & Run

1. Install [Visual Studio 2022](https://aka.ms/vs/17/release/vs_community.exe) or [newer](https://visualstudio.microsoft.com/downloads/).
2. Clone the repository.
3. Open the project folder from Visual Studio.
4. Set the build configuration to **Windows64 - Debug** (Release is also ok but missing some debug features), then build and run.

### CMake (Windows x64)

```powershell
cmake --preset windows64
cmake --build --preset windows64-debug --target Minecraft.Client
```

For more information, see [COMPILE.md](COMPILE.md).
