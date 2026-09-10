# System requirements and compatibility

[Back to the project](../README.md)

## Installation requirements versus tested hardware

The APK manifest sets a minimum Android version. It does not establish a minimum GPU or amount of RAM capable of running the game.

| Item | Verified from package or source | Device evidence |
| --- | --- | --- |
| Android | Minimum API 33 / Android 13; target API 36 / Android 16 | Successful gameplay reported on Android 16 with 8 Gen 3 |
| CPU architecture | ARM64 native libraries (`arm64-v8a`) | Atleast Snapdragon 8 Gen 1 or equivalent |
| GPU | Vulkan graphics path with bundled Adreno-oriented Turnip driver | Atleast Adreno 730 with Vulkan 1.3 support or equivalent |
| RAM | Atleast 12GB | I don't know if it will launch in 8GB ram |
| Native memory-page compatibility | Nine native libraries retain 16 KiB ELF and APK ZIP alignment | Package check; not a guarantee for every Android/device combination |
| Storage | Approximately 200.0 MiB | Total installed size and data size not measured but its approximately more than 100GB or less|

**Closest known working setup:** Snapdragon 8 Gen 3, Adreno 750, Android 16, 12 GB RAM.

## What else is required?

- Game data that matches this Android runtime's expectations. Owning a PC copy alone does not prove that copying its current installation will produce compatible data.
- Enough free storage for installation, data, extracted libraries, saves and caches. There is no verified fixed storage minimum for the whole installation.
- Android permission to access the game folder. The launcher and driver importer do not require root.
- A usable gyroscope for optional gyro aiming. All other touch controls can be used without gyro.
- A compatible Bluetooth or USB controller if using physical-controller features.

## Other devices

No tested minimum has been established for older Snapdragon devices or for 6 GB/8 GB configurations. **Mali, Xclipse, PowerVR and other GPU families** are not supported. A working Vulkan implementation or a successful APK install is not sufficient evidence of game compatibility.

The DXVK build in this runtime has Android-specific integration and compatibility fallbacks.

## Reporting compatibility

Open a device compatibility issue in the repository, or share a report in the [Telegram community](https://t.me/xhynv). Include:

- Device model, SoC, GPU, RAM and Android version.
- XHYN V version and driver name/version.
- Whether installation, launch, menu rendering and gameplay each work.
- Render dimensions, detail settings, FPS cap and custom renderer overrides.
- Approximate session duration and how performance was measured.

A report for one configuration should not be generalized to every device using the same SoC. Record crashes or visual problems alongside successful launches. Attach only relevant, reviewed diagnostics; no game data or private saves are needed.
