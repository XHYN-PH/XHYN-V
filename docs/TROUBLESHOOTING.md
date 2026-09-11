# Quick fixes

[Back to XHYN V](../README.md)

## Black screen or crash

Fully close the game. Select **DXVK 3.1+** and your working driver, or Bundled Turnip R8. Turn off custom config/environment and optional renderer/native experiments, then relaunch. Check game-data compatibility and folder access.

If it still fails, enable diagnostic logging and reproduce once. Export a fresh support ZIP.

## Detail will not return to normal

Turn lower detail off, then check individual graphics overrides, resolution/custom scale and texture LOD bias. Restart. These settings are independent.

## Camera feels slow

Choose a keyboard/mouse touch mode. Adjust horizontal/vertical and aim sensitivity. Try Linear mouse response and check whether buttons or enlarged touch areas cover your swipe space.

## DXVK did not change

A settings dialog does not restart the engine. Save, use **MENU → Launcher home**, choose DXVK and launch again. Enable its version HUD counter to check the actual renderer.

## Profile or driver import fails

Use the correct XHYN V profile format or a compatible ARM64 AdrenoTools driver ZIP. Winlator profiles and Windows DXVK DLLs are not directly supported. Install a setup's required driver before applying it.

## Menu option is missing

Switch from Simple to Advanced menus. If Creator mode hid your controls, tap its restore handle.

## Still need help?

Share phone/Android/RAM, XHYN V version, DXVK, driver, settings and clear reproduction steps. Preview exported logs before posting.

[Report an issue](https://github.com/XHYN-PH/XHYN-V/issues) · [Telegram](https://t.me/xhynv)

<details>
<summary><strong>Technical details and full reference (optional)</strong></summary>

## Black screen, intro sound, crash or device loss

Earlier startup work addressed graphics compatibility and stalled rendering, and the user subsequently reached gameplay. That history does not establish that every new black screen has the same cause.

1. Fully close the game and reopen the launcher.
2. Select **DXVK 3.1+** and the last working driver, or **Bundled Turnip R8** for the original bundled path.
3. Turn off custom environment/config overrides, queue/tiler/texture-bias experiments, Swappy and performance hints for a baseline.
4. Restore a known working graphics configuration. Confirm compatible game data and folder permission.
5. If it still fails, enable diagnostic logging, restart and reproduce once. Export relevant fresh diagnostics and record the selected/loaded renderer and driver.

Library-load recovery chooses the original DXVK for the next restart. It cannot recover every later driver crash or device loss. `VK_ERROR_DEVICE_LOST` identifies a graphics-device failure, not its complete cause. Useful files may include engine/driver/pipeline logs, shader dumps and the newest `gtav_exit_trace_*.bin` if the runtime creates it.

## A selected DXVK version did not take effect

DXVK cannot switch inside a running game process. Save, use **MENU → Launcher home → Close game and return**, choose the version and launch again. Enable the DXVK version HUD counter and inspect the session's loaded-pair report.

A failed alternate-library load may select 3.1+ for recovery. Re-entering a settings dialog alone does not restart the engine. Windows DLLs and loose renderer ZIPs are not supported imports.

## GPLAsync causes late or missing objects

Disable **Asynchronous shaders** in the GPLAsync selector and restart, or return to 3.1+. If the async switch appears ineffective, inspect custom config priority and an enabled `DXVK_ASYNC` environment row. `DXVK_ASYNC=0` forces async off. Config explanations show supplied values; they cannot confirm every renderer option is supported.

## Graphics stay low after turning the preset off

Fully close gameplay. Turn **Lower graphics detail** off and check **Individual graphics controls**, population/distance, resolution preset, custom scale and texture LOD bias. An enabled independent override can still change the picture.

The next launch should restore saved baseline detail when the managed detail overrides are off. Custom config may still override renderer settings. **Restore full graphics backup** restores a broader snapshot including resolution; it does not reconstruct unknown settings if that backup was already low quality. Preserve current settings/recovery files when investigating a damaged baseline.

## Settings file or world controls are missing

Use current game settings for the first launch if `save/settings.xml` or `save/Settings.xml` has not been created. Confirm the folder and permission. Population/distance choices are disabled when the expected unique numeric XML fields do not exist; the launcher does not invent unsupported engine settings.

## Camera is slow or difficult to control

Choose a keyboard/mouse touch mode, then check horizontal/vertical sensitivity and the aiming multiplier/binding. Start with the Linear response curve before evaluating Precision or Acceleration. Physical-controller dead zones do not increase maximum turning speed.

If movement interferes with camera swipes, inspect floating-stick and handedness settings and the button positions. Enlarged touch areas can intercept intended swipes; transparent faded buttons can still receive input. On-foot/driving mode switches are manual.

## A button sticks or behaves differently after a mode change

Opening MENU cancels synthetic inputs. Check toggle, double-tap, long-press, modifier and swipe actions, along with the active mode/page. Record the exact touch sequence and binding if the problem repeats. Use **Controls → Test inputs** to inspect layout actions without starting the engine.

## Profile/setup import fails

Use the correct XHYN V format: `.xhyn-controls.json` up to 512 KiB, or `.xhyn-setup.json` up to 3 MiB. Winlator `.icp` is not supported. Limits for pages, controls and saved-profile counts still apply.

Import saves a profile; it does not apply it automatically. A complete setup that references an imported driver needs that exact driver installed before **Use setup** succeeds. A setup does not contain driver binaries, game data or saves. See [Profiles and backups](PROFILES_AND_BACKUPS.md).

## Driver import fails or makes rendering worse

Use a compatible ARM64 AdrenoTools ZIP with `meta.json`. Read the import error for format, API or alignment problems. A valid archive is not proof of GPU compatibility. Select Bundled Turnip or the previously working driver and fully restart to roll back rendering problems.

## Swappy or performance hints remain Waiting/Unavailable

These are optional experiments. Restart after changing their switches. Swappy needs an eligible presentation path; hints need API support and suitable same-thread work samples. Waiting/Unavailable can mean the integration cannot use that path and ordinary rendering remains active. Keep frame caps aligned and compare each experiment separately.

## HUD, reports or logging seem inconsistent

The app HUD and native DXVK HUD are separate. App CPU is normalized, RAM is app PSS, and thermal status is severity rather than degrees. The legacy renderer filters some unsupported native counters while keeping their preferences for other versions. Native HUD changes need restart.

Performance recording must be stopped and saved before export. It does not contain game FPS or 1% lows. Disabling diagnostics does not stop explicit recording, erase old logs or guarantee silence from Android/native crash reporting. A support ZIP may contain older logs; check timestamps.

## Language, hidden options and Creator mode

Menu language changes launcher/control text, not game text or custom labels. If a tool is missing, check Simple/Advanced mode. Hidden advanced choices can remain enabled. Creator mode hides app controls/HUD/cursor; use its restore handle to recover them. The native DXVK HUD is configured separately.

## Returning home, saves and APK updates

**Launcher home** intentionally closes gameplay and does not autosave. If the handoff fails, close/reopen the app manually. Save backup tools operate on files already written to disk and require gameplay closed.

If updating fails, compare package/version/signing identity before uninstalling. App-private profiles, drivers and backup snapshots can be lost by uninstall or clear-storage. See [Installation](INSTALLATION.md).

## Share a useful report

Include phone/SoC/GPU/RAM/Android, XHYN V version, DXVK, driver, graphics dimensions, advanced overrides, reproduction steps and whether an earlier build worked. For lag, distinguish startup/compilation from sustained play and state scene, session length and measurement method.

Use the selective support export and review its preview. Share only relevant diagnostics, not the game directory or private saves. Open an [issue](https://github.com/XHYN-PH/XHYN-V/issues) or post your reviewed report in the [community](https://t.me/xhynv).

</details>
