# Save, share and back up

[Back to XHYN V](../README.md)

## Which profile should I use?

| Profile | What it saves |
| --- | --- |
| **Control profile** | One touch mode, its pages and related control preferences |
| **Graphics profile** | Graphics and frame-rate selections |
| **Complete setup** | All four touch modes, graphics, DXVK/driver choices and custom renderer settings |

Use **Controls → Manage profiles** for layouts, or **Graphics / Settings → Complete setup profiles** for a broader setup.

Importing stores a profile; choose **Use** to apply it. A complete setup contains a driver reference, not its files—install that driver first. Profiles do not contain game data or saves.

## Back up saves

1. Save inside the game and close gameplay.
2. Open **Settings → Save backup manager**.
3. Choose **Back up saves now**.
4. Use **Export ZIP** to keep an external copy.

Local backups can be lost when uninstalling or clearing app storage. Restore preview shows what will be restored. Backups capture files already saved, not live gameplay.

## Share a problem report

Open **Settings / MENU → Export support ZIP**. Preview the entries, choose what to include and save the file. Nothing is sent automatically.

Review logs and custom settings before sharing them. The separate performance recorder contains app CPU/RAM/thermal data, not an FPS benchmark.

The optional reference explains profile limits and exactly which settings each export includes.

<details>
<summary><strong>Technical details and full reference (optional)</strong></summary>

## Choose the right kind of profile

| Type | Captures | Limit / sharing |
| --- | --- | --- |
| Control profile | One touch mode, its pages, geometry/styles/actions, movement and applicable look/appearance options | 128 saved profiles; `.xhyn-controls.json`; 512 KiB per file |
| Graphics profile | Resolution, detail/world settings, cap/VSync, workers, queue and supported renderer experiments | 32 custom saved profiles plus built-in presets; managed locally |
| Complete setup | Graphics, driver reference, all four touch modes, renderer/config choices and native experiment switches | 32 saved setups; `.xhyn-setup.json`; 3 MiB per file |

A profile is configuration, not a copy of the game or a saved gameplay state. Keep a named working setup before applying someone else's choices.

## Control profiles

Open **Controls → Manage profiles** to save, use, update, rename, duplicate, delete, import or export. Import creates a saved profile; applying it deliberately changes the working mode/layout. It can also change shared look, opacity, vibration, fading, floating-stick, handedness and shortcut-wheel preferences included in that snapshot.

One mode can have up to eight pages, each with up to 256 controls. The total file-size limit still applies. Older version-1 profiles remain readable with defaults for missing optional fields. Unsupported/malformed imports are rejected. These are not Winlator `.icp` files.

## Complete setup profiles

Open **Graphics** or **Settings → Complete setup profiles**. Save current setup, use, update, rename, export, import or delete a saved entry. Import stores a new setup without applying it immediately.

Revision 13 includes:

- Resolution, lower/individual detail, population/distance, FPS, VSync, compiler workers, frame queue, tiler and texture-bias selections.
- DXVK version and GPLAsync preference, plus the selected driver's package reference.
- All four touch modes and their pages: layout, bindings, gestures, groups, locks, larger hit areas, styles, movement, mouse/gyro preferences, fading, overall opacity, floating/left-handed choices and shortcut wheel.
- Custom environment rows, global `dxvk.conf`, their master switches and conflict preference.
- Swappy and Android performance-hint switches.

The file **does not include driver binaries, game files, saves, shader caches, app menu language/appearance, HUD choices or physical-controller mappings**. It is a defined set of gameplay configuration, not a complete app-data backup. Quick-toolbar and Creator-mode preferences are not part of the setup either.

If a setup refers to an imported driver, install that exact supported package locally before using the setup. The app validates the required driver and setup before applying preferences. A missing driver causes an error; importing a setup does not install it or silently substitute another. Older setup files without DXVK fields select the original renderer.

Control changes apply through their usual tools; graphics/renderer/driver changes need a fresh game launch. The application confirmation shows the intended replacement, so save your current setup first if it matters.

## Save backup manager

Close gameplay, then open **Settings → Save backup manager**. It copies `Games/GTAV/save`, including settings and recovery sidecars present in that folder, to timestamped app-private ZIPs.

- **Back up saves now** captures files already written to storage. It does not trigger an in-game save or capture live process state.
- Retain 2, 5, 10 or 20 backups; the default is 5. Retention runs after creating a backup or completing a restore.
- **Restore preview** lists the selected backup's files and sizes. Restore verifies checksums, stages the result and creates a protective backup first.
- Files absent from the selected backup are preserved. Interrupted replacement is recovered before normal launch; failed recovery is shown instead of ignored.
- Limits are 4,096 files and 512 MiB of uncompressed data, with bounded directory depth and archive validation.
- **Export ZIP** writes a copy through Android's file picker. App-private backups can be removed by uninstalling or clearing app storage, so keep external copies when needed.

External backup ZIP import is not implemented in the app. An exported ZIP contains a `save/` folder for manual restoration to `Games/GTAV/save` while XHYN V is closed. Back up the destination before doing that, retain settings/recovery files together, and use saves compatible with this runtime. A save backup is not a control-profile export.

## Selective support ZIP

Use **Settings / MENU → Export support ZIP**. Review the available entries and select what to include. Device/driver information and graphics selections start selected; logs, custom renderer/environment text and the last saved performance report are optional.

The preview is the same captured text written to the export. Up to 32 matching logs can be included, with at most the latest 256 KiB of each. Existing logs may describe an earlier launch when logging has been disabled. Check timestamps and the selected/loaded renderer fields.

The device-information entry does not collect serial numbers or account identifiers. The export does not automatically include game data, saves or signing credentials. Selected logs/config text are not automatically redacted and may contain paths or personal values, so inspect the preview before sharing.

Nothing is uploaded or messaged automatically. The picker saves the ZIP; you decide where to share it.

## Performance reports are a different export

The performance recorder saves app CPU/RAM/thermal samples plus configuration/context. It is not a game-FPS capture or support-log collector. Stop and save the recording before export; a crash can lose unfinished samples. See [Graphics](GRAPHICS.md) for measurement scope and [Performance](PERFORMANCE.md) for comparisons.

</details>
