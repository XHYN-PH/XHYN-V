# Revision 10 validation record

[Back to the project](../README.md)

The prepared **XHYN V 0.10** APK passed the following checks. These are build/host results and do not replace running the app on a phone.

| Check | Result |
| --- | --- |
| Host model assertions | 17,473 passed |
| Revision 7 regression suite | 3,014 assertions; 349 generated SDL input events |
| Revision 8 regression suite | 4,683 assertions; current 432-entry translation dictionary |
| Revision 9 regression suite | 801 assertions |
| Revision 10 suite | 8,975 assertions |
| APK ZIP integrity and duplicate entries | Passed |
| Package/version | `com.xhynph.v`, `0.10`, code `10` |
| Signature | Verified with established update certificate, including v3 verification |
| Native libraries | Nine ARM64 libraries byte-identical to revision 9 |
| Native alignment | 16 KiB ELF segments and APK ZIP placement verified |
| Modified APK payloads | `AndroidManifest.xml` and `classes.dex` |
| DEX classes | 369 |
| Preserved original classes checked | 66 |
| Unresolved project method references | None found |
| Permissions | No additions from revision 9 |
| Icon | Existing supplied bitmap resources retained |

The older packaged prose notes had a stale **368** class count. The final package validator records **369**, which is the value used here. This is a documentation correction; the APK bytes have not changed.

## Documentation scope

This page summarizes the checks recorded during preparation of the revision 10 app. The documentation repository does not contain test implementations, build scripts, source manifests or raw build reports. Updating these documents does not rerun those app checks.

The [installation guide](INSTALLATION.md) and [checksum file](releases/v0.10-SHA256SUMS.txt) retain the prepared APK's public verification values. The [release notes](releases/v0.10.md) describe that version's changes.

## Scope

Host checks cover pure input/config/profile/graphics/report models. Package checks inspect the signed artifact and its relationships to the baseline. Neither executes Android widgets, document providers, touch/gyro hardware, Bluetooth input, Vulkan drivers or actual game rendering.

Earlier builds through revision 9 have user-reported gameplay on Snapdragon 8 Gen 3 / Adreno 750, Android 16, 12 GB RAM. Revision 10 still needs a current phone report. No universal compatibility, sustained frame rate, thermal stability or measured FPS gain is claimed.
