# Installation and updates

[Back to the project](../README.md)

## Before installation

Check [compatibility](COMPATIBILITY.md), back up saves and close the game. Obtain an APK from a release announced by XHYN_PH. GitHub's automatically generated repository ZIP contains these documents, not an installable Android application.

This repository does not supply game data. Use data you legally own that is compatible with the supplied Android runtime. No universal Steam/Epic/Rockstar installation conversion procedure has been verified for this build.

## Install or update

1. Copy/download `XHYN-V.apk` to the phone and open it through Android's installer. Allow that file-manager/browser source to install apps if Android requests it.
2. When updating revision 9, install over the existing XHYN V application. Revision 10 keeps package `com.xhynph.v` and the same update certificate.
3. Open XHYN V and grant the game-folder access requested by the launcher.
4. The runtime expects its data under `Internal storage/Games/GTAV`, corresponding to `/storage/emulated/0/Games/GTAV/`.
5. Start with **Bundled Turnip R8** and your known working graphics settings. Keep optional advanced overrides off for the first launch.

Updating the same package with the same signing identity is intended to retain app settings, imported drivers, profiles and saves. Keep your own backup; clearing app storage or uninstalling can remove app-private settings and profiles.

If Android reports a signing conflict, verify that both APKs belong to the same package/build line. Do not uninstall the working app merely to bypass the conflict. Older **GTAV Test** branches used separate identities and are not automatically equivalent to an XHYN V update.

## First-run graphics settings

Graphics options edit the compatible runtime's XML settings under `Games/GTAV/save`. If the settings file does not exist yet, use **current resolution/settings** for the initial launch so the runtime can create it. Close the game before applying file-based graphics changes.

The launcher keeps an original-detail snapshot for reversible detail overrides and a separate full settings backup. Resolution, individual detail choices, the lower-detail preset and renderer overrides are separate settings; see [Graphics](GRAPHICS.md).

## Menu language and game language

Use **Settings → Menu language** for English, Filipino, Spanish, Indonesian or Brazilian Portuguese launcher text. This choice applies to the launcher and control tools. It does not change the game's language or rewrite user-created button names.

The runtime's game-language launch configuration is separate. If the game itself appears in the wrong language, include the actual launch arguments and build version in a support report; do not assume that changing the menu language will change game text.

## Verify revision 10

| Field | Expected value |
| --- | --- |
| Version name / code | `0.10` / `10` |
| Package | `com.xhynph.v` |
| APK size | `196224106` bytes |
| APK SHA-256 | `56a640334e7efbae808b14d4ba3834ec187720695d0f6864176948ca5564169c` |
| Signing certificate SHA-256 | `189414552fdb5910780d432e3d16401c4c6a09786cefa427e73526fa48220455` |

With the APK and the downloaded [checksum file](releases/v0.10-SHA256SUMS.txt) in the same directory:

```bash
sha256sum -c v0.10-SHA256SUMS.txt
```

On PowerShell:

```powershell
Get-FileHash .\XHYN-V.apk -Algorithm SHA256
```

With Android SDK Build Tools installed, inspect the signing certificate:

```bash
apksigner verify --verbose --print-certs XHYN-V.apk
```

Compare the digest with the expected value above. These values describe the prepared revision 10 APK, not a newly compiled fork or later release. See the [release notes](releases/v0.10.md) for the corresponding release summary.
