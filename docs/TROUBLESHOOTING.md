# Troubleshooting

[Back to the project](../README.md)

## Black screen, intro audio or device loss

Earlier startup failures in this project involved graphics pipeline errors, graphics-device loss and stalled rendering. The original compatibility changes and bundled driver path helped XHYN_PH reach gameplay. That history does not prove that every later black screen has the same cause.

1. Fully close the game. Return to **Bundled Turnip R8** if an imported driver was selected.
2. Turn off custom environment/config overrides and the optional frame-queue experiment, then restart.
3. Restore the last known working graphics profile. Confirm that data matches the runtime and folder access remains granted.
4. If it still fails, enable diagnostic logging for a short reproduction and report the new logs, build version and driver.

`VK_ERROR_DEVICE_LOST` describes a rendering-device failure; it is not a complete native backtrace or proof of one particular bad setting. Useful files can include `gtav_tty*.log`, driver/pipeline logs, shader dumps and the newest `gtav_exit_trace_*.bin`, when the runtime produces them.

Do not upload the game directory, account information or signing credentials. Attach only the files needed for the report.

## Graphics stay low after turning the preset off

Detail and resolution are separate. Fully close the game, turn **Lower graphics detail** off, check **Individual graphics controls**, and check both custom scale and the selected resolution preset. Enabled individual choices can still override the original settings.

Also check custom `dxvk.conf` precedence. If all detail overrides are off, the launcher should restore its saved original-detail values on the next launch. Use the full settings backup only when you intend to restore that broader snapshot. Preserve a copy of current settings before investigating a damaged or missing backup.

## Settings file is missing

The runtime may need an initial launch to create `save/settings.xml` or `save/Settings.xml`. Choose current resolution/settings for that initial launch. Confirm the game-data location and permissions before applying XML graphics changes.

## Camera movement feels slow

Choose a keyboard/mouse touch mode and adjust horizontal/vertical sensitivity. Check aiming sensitivity and the aim binding if the slowdown happens only while aiming. Use a floating movement stick or gallery starter if the current layout interferes with swipes.

Native-controller stick movement and direct mouse swipe look have different behavior. Physical-controller dead zones change the center response rather than the maximum turn speed.

## A button sticks or a profile cannot be imported

Open and close the in-game menu to release synthetic input. Record the mode, active page, bindings and exact touch sequence if the problem repeats.

Profiles must be valid `.xhyn-controls.json`, at most 512 KiB. Winlator `.icp` files use a different format. Large collections of buttons and pages can reach the file-size limit. Save/export a smaller profile and avoid hand-editing native target geometry.

## HUD values look wrong

App CPU is normalized across processors; RAM is app PSS. Android thermal status is not a temperature reading. The app HUD and DXVK HUD are separate. Restart after native DXVK counter changes.

The performance report contains app CPU/RAM/thermal measurements; it does not contain actual game FPS, frame times or GPU utilization. A recording must be stopped and saved before export, and a crash can lose its unfinished samples.

## Driver import fails or makes rendering worse

Use a compatible ARM64 AdrenoTools ZIP containing valid metadata, not a Windows DLL or arbitrary library archive. Read the import error. Select the bundled driver and fully restart to roll back a rendering regression. Record the exact driver version in your report.

## Menu changed language but the game did not

**Menu language** affects the launcher and control tools only. Game-language launch configuration and game text are separate. Custom button labels and technical variable/key names are not translated automatically.

## APK update fails

Compare the package, version and signing certificate with [Installation](INSTALLATION.md). An independently signed fork or older Test branch may not be compatible with an in-place update. Keep backups before any uninstall or app-data reset.

## Share a useful report

Open a bug or compatibility issue in the repository. Include device/Android/RAM, XHYN V version, driver version, graphics and renderer overrides, reproduction steps, and what happened. Note whether the same configuration worked on an earlier build. For lag, state whether it occurs during startup/shader compilation or sustained gameplay, with actual render dimensions and session length.
