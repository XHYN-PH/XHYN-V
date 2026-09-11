# Will it work on my phone?

[Back to XHYN V](../README.md)

**Reported working:** Snapdragon 6 Gen 1 / Adreno 710, 8 GB RAM.

| You need | What to know |
| --- | --- |
| Android 11 or newer and ARM64 | Meets the APK's installation requirements; gameplay is not guaranteed |
| A compatible Vulkan GPU/driver | The bundled Turnip route is intended for supported Adreno hardware |
| Compatible game data | Must match this Android runtime |
| Enough storage | APK is about 200.0 MiB; game data, installed files and caches need additional space |

There is no confirmed minimum RAM/GPU specification beyond the reported setup. Older Snapdragon phones, 6/8 GB devices and other GPU families are not confirmed.

## Help others check compatibility

Share your phone model, Android/RAM, app version, DXVK, driver and whether gameplay works. If reporting FPS, include resolution, scene and how you measured it.

[Installation](INSTALLATION.md) · [Report a result](https://github.com/XHYN-PH/XHYN-V/issues)

<details>
<summary><strong>Technical details and full reference (optional)</strong></summary>

 A minimum Android version in a manifest is not a minimum specification for playable GTA V.

## Package requirements and known working target

| Item | Prepared revision 13 package | Current device evidence |
| --- | --- | --- |
| Android | Minimum API 30 / Android 11; target API 36 / Android 16 | Android 15 in the stated working setup |
| CPU architecture | ARM64 (`arm64-v8a`) native libraries | Snapdragon 6 Gen 1 |
| GPU | Compatible Vulkan rendering/driver path; bundled Turnip is Adreno-oriented | Adreno 710 |
| RAM | No tested minimum established | 8 GB in the stated working setup |
| Native memory pages | Original libraries and alternate DXVK libraries checked for 16 KiB ELF alignment; APK native library placement checked | Package validation, not coverage of all Android/OEM combinations |
| Download size | Approximately 200.0 MiB | Excludes installed/extracted files, game data and caches |
| Storage total | Depends on compatible data, installation, drivers, caches and backups | No measured whole-installation minimum |
    
An older DXVK option does not, by itself, establish support for older GPUs.

## Data and access

The runtime expects compatible local game data under `Internal storage/Games/GTAV`, or `/storage/emulated/0/Games/GTAV/`. The examined runtime identifies as `2699-dev_ng_Live`. This identifier is not a promise that arbitrary retail files with a similar version number will work.

No universal conversion process from a current Steam, Epic or Rockstar installation is provided here. Game ownership and data-format compatibility are separate questions. The documentation repository supplies no game data.

The launcher and app-local driver importer do not require root. Android must permit access to the expected game folder. Optional gyro requires a suitable sensor; physical-controller tools require compatible hardware and their own testing.

## Other devices and renderers

- Older/newer Snapdragon devices and 6 GB/8 GB RAM configurations do not have a verified minimum or complete test matrix here.
- Mali, Xclipse, PowerVR and other GPU families have no established supported driver path or gameplay result in this project. An Adreno Turnip ZIP does not add support for those GPUs.
- Installing the APK successfully or advertising a Vulkan version does not prove the runtime's required features and workarounds function correctly.
- A driver ZIP passing import checks confirms its format and basic binary eligibility, not shader correctness or sustained gameplay.
- All alternate DXVK pairs have packaging/interface checks. Independent phone results are still required for each renderer/driver combination.
- GTA Online and arbitrary PC mod/launcher compatibility are outside the supported scope. This build is not a general Windows compatibility environment.

## Share a compatibility result

Use [Issues](https://github.com/XHYN-PH/XHYN-V/issues) or the [Telegram community](https://t.me/xhynv). Include:

1. Phone model, SoC/GPU, RAM and Android version.
2. XHYN V version, selected DXVK and actual renderer version if visible, plus driver name/version.
3. Separate outcomes for installation, launch, menu rendering and gameplay.
4. Render dimensions, graphics profile, cap/VSync, advanced overrides and native experiments.
5. Scene/mission, session duration, visual problems and how any FPS measurement was taken.
6. A small reviewed [support report](PROFILES_AND_BACKUPS.md), when useful.

Keep successful and failed results together. A result for one phone/configuration should not be generalized to every device with the same chipset.

</details>
