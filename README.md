<p align="center"><img src="docs/assets/icon.png" alt="XHYN V logo" width="128"></p>
<h1 align="center">XHYN V</h1>
<p align="center"><strong>Based on the China Android Launcher of GTA V.</strong></p>
<p align="center">
<a href="https://github.com/XHYN-PH/XHYN-V/releases">Downloads</a> ·
<a href="docs/INSTALLATION.md">Getting started</a> ·
<a href="https://youtube.com/@xhyn_ph">YouTube</a> ·
<a href="https://t.me/xhynv">Telegram</a>
</p>

## What is it?

(This is a Native Launcher not a literal andoird port. Its better to wait for mojs0's literal andoird port + The chinese port itself is built upon AI and so this build too.)

XHYN V is a modified community build based on the **China Android Launcher of GTA V**. It adds an easier launcher, customizable touch controls, graphics options and compatibility improvements. Credit for the original game and Android launcher belongs to their respective developers.

## What can you do?

- **Make your own controls:** add buttons, change shapes and bindings, use mouse swipes, and save or share layouts.
- **Adjust graphics:** choose resolution, lower detail, FPS limits and other quality settings. Turning lower detail off restores the saved original detail.
- **Choose DXVK and drivers:** four included DXVK versions, bundled Turnip and compatible custom driver imports.
- **Watch performance:** select individual FPS, GPU, app CPU/RAM and thermal HUD counters.
- **Save your setup:** export profiles, back up saves and create support reports.
- **Make the menu yours:** seven languages, appearance options, compact tools and Creator mode.
- **Return home:** open MENU to close the game and return to the launcher. Save in-game first—it does not autosave.

## Will it work on my phone?

**Reported lowest configuration working so far:** Snapdragon 6 Gen 1 / Adreno 710, 8GB RAM.

The APK requires Android 11 or newer and ARM64, but gameplay also needs a compatible Vulkan GPU/driver and matching game data. Other devices are not yet confirmed. The APK is about 200 MiB; game data and installed files need additional storage.

[Check compatibility](docs/COMPATIBILITY.md) before installing. Game files are not included in this repository.

## Start here

1. [Install or update XHYN V](docs/INSTALLATION.md).
2. Start with **DXVK 3.1+** and **Bundled Turnip R8**, or keep your working setup.
3. [Adjust your controls](docs/CONTROLS.md) and [graphics](docs/GRAPHICS.md).

For problems, open the [troubleshooting guide](docs/TROUBLESHOOTING.md).

## Is it native? Is it faster than a Windows emulator?

The engine runs as Android ARM64 code. DXVK translates its graphics to Vulkan, and Turnip handles the GPU. This avoids the CPU translation used by a typical Windows-game setup, but higher FPS is not guaranteed. It supports this particular runtime, not arbitrary Windows games or mods.

[Read the simple explanation and limitations](docs/ARCHITECTURE.md).

<details>
<summary><strong>More guides and release notes</strong></summary>

- [DXVK versions and custom drivers](docs/ADVANCED_RENDERER.md)
- [Profiles, backups and sharing](docs/PROFILES_AND_BACKUPS.md)
- [Menu, languages and in-game tools](docs/INTERFACE.md)
- [Performance tips](docs/PERFORMANCE.md)
- [What's changed](CHANGELOG.md) · [Revision 13 notes](docs/releases/v0.13.md)
- [Credits](CREDITS.md) · [Notices](LICENSES.md) · [Contributing](CONTRIBUTING.md)

</details>



[YouTube](https://youtube.com/@xhyn_ph) · [Telegram](https://t.me/xhynv) · [Report a problem](https://github.com/XHYN-PH/XHYN-V/issues)

XHYN_PH does not condone or support piracy. Use only game files you legally own and respect the original creators' rights and licenses. XHYN V is unofficial and is not affiliated with Rockstar Games or Take-Two Interactive.
