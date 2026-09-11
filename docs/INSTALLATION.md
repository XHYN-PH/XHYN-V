# Getting started

[Back to XHYN V](../README.md)

## Install or update

1. **Save and close the game.** Keep an external backup of important saves and profiles.
2. Get the APK from the maintainer's [Releases page](https://github.com/XHYN-PH/XHYN-V/releases) and check its version.
3. Install it, open XHYN V and allow access to the game folder.
4. Use compatible game data in **Internal storage → Games → GTAV**. Game data is not included here.
5. Start with **DXVK 3.1+** and **Bundled Turnip R8**, or keep the configuration that already works for you.

Revision 13 can update the matching signed revision 12 app without uninstalling. If Android reports a conflict, check the build first: uninstalling can remove app-private profiles, drivers and backups.

## First launch

If the launcher says the graphics settings file is missing, choose **current game settings** for the initial launch. Close the game afterward, then adjust graphics.

## Change the language

Open **Settings → Menu language** for launcher text. The game itself retains the earlier English setting; changing menu language does not change game text.

**Returning home:** save in-game, then open **MENU → Launcher home → Close game and return**. This closes gameplay rather than saving it for you.

[Controls](CONTROLS.md) · [Graphics](GRAPHICS.md) · [Phone compatibility](COMPATIBILITY.md)

<details>
<summary><strong>Technical details and full reference (optional)</strong></summary>

## Before installing

Check [system requirements and compatibility](COMPATIBILITY.md). Use the APK supplied by the maintainer and check its version against the [release notes](releases/v0.13.md). The guides describe revision 13; older APKs may have fewer options. Available public downloads are listed under [Releases](https://github.com/XHYN-PH/XHYN-V/releases).

Compatible local game data is required and is not supplied by this documentation repository. There is no universal conversion procedure here for arbitrary current Steam, Epic or Rockstar data.

## Install or update

1. Save progress and fully close any running game. Export any app-private profiles/backups you need to keep.
2. Open the APK with Android's installer. If requested, allow that browser/file-manager source to install apps.
3. Open XHYN V and grant the game-folder access it requests.
4. Place compatible data in the expected `Internal storage/Games/GTAV` location, corresponding to `/storage/emulated/0/Games/GTAV/`.
5. Start with the original **DXVK 3.1+** and **Bundled Turnip R8**, or retain your already-working driver/settings. Keep optional advanced overrides off for an initial baseline.

Matching package/signature updates retain app-private settings, imported drivers and profiles. An old Test branch or independently signed APK may use a different identity.

If Android reports a signature/version conflict, check the build line before taking further action. Uninstalling or clearing storage removes app-private settings, drivers, profiles and local backup copies. External game saves and exported files are separate, but keep your own backup before changing installations.

## First launch and graphics files

The launcher edits compatible XML graphics settings under `Games/GTAV/save`. If `settings.xml` / `Settings.xml` does not exist yet, use current resolution/settings for the first launch so the runtime can create it, then close the game before applying file-based graphics choices.

Graphics detail, resolution and advanced renderer settings are independent. The launcher preserves detail-recovery state and a separate full settings backup. See [Graphics](GRAPHICS.md) before using a full restore.

## Menu and game language

**Settings → Menu language** selects English, Filipino, Spanish, Indonesian, Brazilian Portuguese, Russian or French for the launcher and control tools.

The game-language change introduced earlier is retained: the runtime uses `-uilanguage=american` for English. This is separate from the launcher's language menu. If a different build still reports `chinesesimp`, confirm the APK/version and actual launch arguments before changing files. The menu selector does not translate game assets or custom button captions.

## Apply a different renderer

Use **Drivers → Choose DXVK version** before launching. Both DXVK and Vulkan-driver changes need a fresh process. During gameplay, save first, then use **MENU → Launcher home → Close game and return**. Read [Advanced renderer](ADVANCED_RENDERER.md) for version limits and rollback.

</details>
