<p align="center">
  <img src="docs/assets/icon.png" alt="XHYN V purple V logo" width="144">
</p>

<h1 align="center">XHYN V</h1>
<p align="center"><strong>By XHYN_PH 🇵🇭</strong><br>Android controls, graphics tuning and a personalized launcher for a compatible GTA V runtime.</p>
<p align="center">
  <a href="https://youtube.com/@xhyn_ph">YouTube</a> ·
  <a href="https://t.me/xhynv">Telegram community</a> ·
  <a href="docs/INSTALLATION.md">Installation</a> ·
  <a href="docs/CONTROLS.md">Controls guide</a> ·
  <a href="CHANGELOG.md">Changelog</a>
</p>

## What is XHYN V?

XHYN V is a community Android launcher, customizable input overlay and compatibility/tuning layer around an existing ARM64 GTA V Android runtime. It brings touch keyboard and mouse controls, portable control profiles, graphics settings, Adreno driver selection and performance tools together in one interface.

The runtime uses an Android native build of **DXVK** for graphics translation and supports a bundled **Mesa Turnip** driver. XHYN V adds the launcher experience and controls around that runtime. This documentation repository contains the project overview, user guides, compatibility information, changelog, release notes and credits.

**Compatible game data must be supplied separately.** This is an independent community project, not an official Rockstar Games Android release. Application source code, build tools, APKs and GTA V game data are not included in this documentation package.

## Current status

| Item | Status |
| --- | --- |
| Current prepared build | **0.10 / revision 10** |
| Android package | `com.xhynph.v` |
| Gameplay report | XHYN_PH reached gameplay on Snapdragon 8 Gen 3 / Adreno 750, Android 16, 12 GB RAM; reports cover earlier builds through revision 9 |
| Revision 10 validation | 17,473 host assertions plus signature, package and native-library preservation checks passed |
| Revision 10 phone testing | Pending confirmation; host checks do not establish gameplay performance |

See the [validation record](docs/VALIDATION.md) for the evidence and its scope. Performance and compatibility depend on the device, driver, settings and supplied runtime/data combination.

## Features

### Touch controls that fit your play style

- Four modes: native controller, mobile on foot, mobile driving, and keyboard/mouse touch. The three mouse modes use keyboard/mouse input with swipe camera control.
- Add, duplicate, remove, move and resize buttons. Customize labels, key or mouse bindings, hold/toggle behavior, opacity and five button shapes.
- Up to **256 controls per layout**, with undo/redo, multi-select, snapping, alignment and group resizing.
- Up to **eight named control pages per mode**, with an in-game page switch.
- Save, rename, duplicate, import and export profiles using `.xhyn-controls.json`.
- Profile gallery with two-finger, four-finger and left-handed starter layouts.
- Optional floating movement stick and eight-slot keyboard/mouse shortcut wheel.
- Separate horizontal/vertical camera sensitivity, aiming sensitivity, vertical inversion and optional gyro aiming.
- Optional mouse cursor, physical-controller button remapping, stick dead zones and automatic hiding of touch controls.

Profile limits and mode behavior are explained in the [controls guide](docs/CONTROLS.md). XHYN profiles use their own format; Winlator `.icp` import is not implemented.

### Graphics and performance tuning

- Resolution presets and custom **0–100% rendering scale**, with actual pixel dimensions shown. The minimum is clamped to a drawable size; 0% does not mean zero pixels.
- Reversible lower-detail preset and individual texture, shadow, reflection, grass and antialiasing controls.
- FPS presets, custom limits of **10–240 FPS** or no added limit, and VSync choices.
- Shader compiler worker selection and an optional DXVK frame-queue experiment.
- Built-in and custom graphics profiles.
- Individual HUD counter checkboxes: app CPU/RAM/thermal status and supported DXVK FPS, estimated GPU load, frame time, memory and rendering counters.
- Moveable app statistics panel with opacity and orientation settings.
- User-started local performance reports with real app CPU, RAM and Android thermal samples.

FPS settings are caps, not promised frame rates. The performance recorder does not export game FPS, GPU usage or 1% lows. See [Graphics and HUD](docs/GRAPHICS.md).

### Drivers and advanced renderer settings

- Bundled Turnip R8 and import of compatible ARM64 AdrenoTools driver ZIPs.
- Custom environment editor with a master switch and individual row switches.
- Editable/importable global `dxvk.conf` with an independent on/off switch.
- Choose whether launcher settings or custom config wins when keys conflict.
- Preview the effective renderer settings and reset custom overrides.
- Diagnostic logging toggle, with opt-in performance reports kept separate.

Driver and renderer changes apply on a full game restart. See [Drivers and advanced configuration](docs/ADVANCED_RENDERER.md).

### Launcher and accessibility

- Dark purple interface, XHYN V logo, large toggle rows and compact in-game tools.
- Menu languages: **English, Filipino, Spanish, Indonesian and Brazilian Portuguese**.
- Sliders snap in steps of 10 while retaining endpoints and untouched older values.
- Community links and XHYN_PH credits in About.

## System requirements

| Component | Requirement or known status |
| --- | --- |
| Android | **Android 11 / API 30** is the APK installation floor; Android 16 is the reported gameplay environment |
| Architecture | **64-bit ARM Android (`arm64-v8a`)** |
| GPU/driver | Compatible Vulkan driver; current bundled path targets Adreno/Turnip. Adreno 750 is the reported working GPU |
| RAM | **12 GB reported working** on the tested device; minimum RAM has not been established |
| Storage | APK is approximately **187.1 MiB**, plus installation space, compatible game data, saves and caches |
| Game data | Separately supplied data compatible with this specific Android runtime |
| Optional hardware | Gyroscope for gyro aiming; compatible USB/Bluetooth controller for physical input |

The closest known working configuration is **Snapdragon 8 Gen 3 / Adreno 750 / Android 16 / 12 GB RAM**. Other devices are unverified, and installation eligibility alone does not guarantee gameplay. [Full compatibility details](docs/COMPATIBILITY.md).

## Getting started

1. Use the APK attached to a release announced by XHYN_PH. The repository ZIP contains documentation and is not an installable app.
2. Back up saves and close the running game before installing or updating.
3. Install the APK and grant the requested game-folder access.
4. Provide the compatible data expected under `Internal storage/Games/GTAV`.
5. Start with the bundled driver and your existing working graphics settings. Select a control mode and save a profile before experimenting.

Read [Installation and updates](docs/INSTALLATION.md) for update signatures, first-run settings and APK verification. APK publication is separate from this documentation repository; a release may not have an attached APK yet.

## Guides

| I want to… | Read |
| --- | --- |
| Install, update or verify an APK | [Installation](docs/INSTALLATION.md) |
| Check my device or report compatibility | [Compatibility](docs/COMPATIBILITY.md) |
| Customize buttons, pages, gyro or profiles | [Controls](docs/CONTROLS.md) |
| Tune resolution, details, FPS or HUD | [Graphics](docs/GRAPHICS.md) |
| Import drivers or configure DXVK/Turnip | [Advanced renderer](docs/ADVANCED_RENDERER.md) |
| Investigate crashes, black screens or settings | [Troubleshooting](docs/TROUBLESHOOTING.md) |
| Read the prepared app's validation summary | [Validation record](docs/VALIDATION.md) |
| Review current changes | [Changelog](CHANGELOG.md) and [0.10 release notes](docs/releases/v0.10.md) |
| Maintain or publish the repository | [Maintainer guide](docs/MAINTAINER.md) |

## Current limits

Arbitrary DXVK version switching, Windows DXVK DLL loading, LSFG-VK/frame interpolation and Winlator profile import are not implemented. This project does not establish GTA Online support or universal GPU compatibility. New native renderer versions would need a compatible Android ABI and integration work.

## Community and credits

**Community release, customization direction, branding and device testing: XHYN_PH 🇵🇭**

[YouTube](https://youtube.com/@xhyn_ph) · [Telegram group](https://t.me/xhynv)

GTA V, the supplied Android runtime and third-party components belong to their respective creators. See [Credits](CREDITS.md), [license status](LICENSES.md) and [contribution guidelines](CONTRIBUTING.md).

> XHYN_PH does not condone or support piracy. Use only game files you legally own, and respect the rights and licenses of the original creators.

XHYN V is not affiliated with or endorsed by Rockstar Games or Take-Two Interactive.
