# Menu and in-game tools

[Back to XHYN V](../README.md)

## Keep the menu simple

Open **Settings → Menu appearance** to choose Simple or Advanced menus, accent color and text size. **Simple hides expert tools but keeps their saved settings active.**

## Choose a language

Under **Settings → Menu language**, choose English, Filipino, Spanish, Indonesian, Brazilian Portuguese, Russian or French. This changes launcher/control text, not game text or your custom button labels.

## Edit while playing

Open **MENU** for controls, layouts and app tools. The editor panel can be dragged or hidden. **Quick toolbar** lets you rearrange shortcuts and collapse them when they cover the screen.

Use **Settings status** to check whether a change applies now or after the next launch.

## Return to the launcher

**Save your game first**, then open **MENU → Launcher home → Close game and return**. Gameplay closes; the app does not autosave or keep that live session suspended.

## Creator mode and logging

**Creator mode** hides the app's touch controls, statistics and cursor, with an optional XHYN_PH watermark. Tap its small handle to restore them. The DXVK HUD is separate.

**Disable diagnostic logging** reduces managed logs after restart. Old logs and some Android/native crash reports may remain. Turn logging back on when collecting a fresh bug report.

[Controls](CONTROLS.md) · [Profiles and backups](PROFILES_AND_BACKUPS.md)

<details>
<summary><strong>Technical details and full reference (optional)</strong></summary>

## Launcher

The landscape launcher provides **Graphics, Controls, Drivers, Settings and About** pages, a persistent Launch game button, selected renderer/driver information and setting status.

Settings use larger ON/OFF controls and tappable rows. The dark interface supports accent choices and text sizing under **Settings → Menu appearance**. **Simple** mode hides selected advanced tools; **Advanced** exposes them. Hiding a setting does not disable its saved value.

If an imported setup appears to affect a hidden option, switch to Advanced mode and inspect **Settings status** and **Explain active overrides**.

## Languages

Choose **Settings → Menu language**:

| Language | Menu label |
| --- | --- |
| English | English |
| Filipino | Filipino |
| Spanish | Español |
| Indonesian | Bahasa Indonesia |
| Brazilian Portuguese | Português (Brasil) |
| Russian | Русский |
| French | Français |

Revision 13 includes 675 menu dictionary entries across these seven languages. The selection affects the launcher and control tools. User-written profile/group names, button captions, technical keys and raw errors may remain in their original language.

Game language is separate. The English runtime change from revision 3 is retained; this menu selector does not replace it with another game-language selection. See [Installation](INSTALLATION.md).

## Compact in-game MENU and toolbar

**MENU** opens compact, scrollable tools for layout editing, graphics, input modes, profiles, pages, mouse/cursor settings, HUD, reports and other app options. The layout editor's floating panel can be moved or hidden to expose more of the canvas.

**Quick toolbar** controls which shortcuts appear and their order: MENU, mode, pages, wheel, edit layout and Creator mode. MENU cannot be removed. Page/wheel tools appear when the corresponding feature is active. A small handle collapses or expands the toolbar; start-collapsed is optional.

## Return to launcher home

While playing:

1. Save progress using the game's own save system.
2. Open **MENU → Launcher home**.
3. Choose **Close game and return**.

This closes the game process and opens a fresh launcher. It does not autosave, pause indefinitely or resume the same live game session. If Android cannot complete the handoff, close and reopen XHYN V manually as prompted. This fresh start also lets a different DXVK pair or driver load cleanly.

## Creator mode

**Settings / MENU → Creator mode** temporarily hides touch controls, app statistics and the app cursor. A small restore handle stays available. An optional **XHYN_PH** watermark is Off by default.

Creator mode does not record/stream video or replace saved layouts. A manually started performance recording can continue while its panel is hidden. The native DXVK HUD is independent: uncheck its counters and restart if those must also be hidden in a recording.

## Applied versus pending settings

Open the footer status or **Settings / MENU → Settings status**. It compares launch selections with the stored startup snapshot for graphics, renderer, driver, native HUD and diagnostics. New native experiment/DXVK selections are tracked too.

Controls and app appearance apply through their normal live tools. Renderer libraries, drivers and file-based graphics choices require a fresh launch. “Applied at launch” records what the launcher supplied; it cannot verify every driver's interpretation of a setting. Unknown state is shown as saved/next launch rather than guessed success.

## Logging and About

**Settings → Disable diagnostic logging** quiets managed diagnostics on the next launch. It keeps old logs and cannot suppress every Android/native crash report. Turn diagnostic logging back on for a short reproduction when fresh logs are needed. Explicit local report recording/export remains available.

**About** contains the community description, original/third-party attribution, anti-piracy notice and links to [YouTube](https://youtube.com/@xhyn_ph) and [Telegram](https://t.me/xhynv). Current release history is available in the [Changelog](../CHANGELOG.md).

</details>
