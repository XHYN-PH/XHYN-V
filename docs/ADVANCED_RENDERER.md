# Drivers, environment variables and dxvk.conf

[Back to the project](../README.md)

## Driver selection

**Drivers** offers the included **Bundled Turnip R8**, labeled Mesa 26.0.0, and imported compatible drivers. Imported ZIPs must follow the supported AdrenoTools format with `meta.json` and a compatible ARM64 Vulkan library.

The importer validates archive paths, metadata and native library compatibility. An import passing validation does not establish that the driver will correctly render this game on every device. Driver and cache paths are managed by the launcher.

Import through the Android file picker, select the driver, fully close the game and relaunch. To undo a driver experiment, select **Bundled Turnip R8** and restart. An unavailable selected import falls back to the bundled choice; a driver that loads but renders incorrectly can still require manual rollback.

The native libraries in revision 10 match revision 9. This update does not ship a new Turnip or DXVK binary.

## Enable advanced settings

Open **Graphics** or **Settings → Advanced renderer**. Both custom environment variables and custom `dxvk.conf` have independent master switches, initially Off. Saving/importing text does not automatically enable it.

| Editor | Limits |
| --- | --- |
| Environment | Up to 64 literal name/value rows, each with its own switch |
| Environment value | At most 4,096 characters, one line |
| Config import | UTF-8, at most 64 KiB |
| Config text editor | At most 65,536 characters |
| Config syntax | Global `name = value` lines; comments, blank lines and quoted values |

Values are data and are not executed as shell commands. Do not paste `export`, shell scripts or a Windows batch file into the environment editor. Name/value fields should contain only the variable name and its literal value.

Executable-specific `[sections]` in a desktop config are rejected. For this single runtime, supply only the global settings you intend to apply. Unknown options may be ignored by the actual native build.

## How precedence works

1. The launcher produces its graphics/HUD/FPS/worker settings.
2. Enabled global custom config is merged with those settings.
3. **Launcher settings win** is the default for conflicting keys. **Custom config wins** reverses that choice. Nonconflicting custom keys remain in both modes; repeated custom keys use the last value.
4. Some environment variables are interpreted separately by DXVK/Mesa and can override corresponding config behavior. The selected merge preference does not turn those environment variables into ordinary config keys.
5. **Disable diagnostic logging** takes priority over custom logging variables. Reserved driver, cache, log and config-file paths remain launcher-managed.

The result is written to a private config file and applied before native initialization using `DXVK_CONFIG_FILE`. The older inline `DXVK_CONFIG` is cleared. Use **Preview effective settings** to review the next launch's configuration.

Changes require a full restart; there is no hot reload of an active renderer.

## Examples

To express a frame cap through config:

```ini
# Optional custom config example
dxgi.maxFrameRate = 30
```

If the launcher also specifies that key, select the desired precedence or set the cap through the normal FPS UI. A cap of 30 is not a claim that every scene will run at 30 FPS.

An environment row supported by the bundled Turnip binary:

| Name | Value | Purpose |
| --- | --- | --- |
| `MESA_SHADER_CACHE_MAX_SIZE` | `512M` | Set a shader-cache size limit |

A cache-size limit is not an FPS multiplier. Avoid copying large collections of debug flags without checking their meaning and support in the selected build. The supported variable names and their semantics come from the [Mesa environment-variable documentation](https://docs.mesa3d.org/envvars.html#turnip-driver-environment-variables); XHYN V's merge and validation behavior is described above.

Upstream references: [DXVK configuration](https://github.com/doitsujin/dxvk/blob/master/dxvk.conf) and [DXVK debugging/HUD](https://github.com/doitsujin/dxvk#debugging). Upstream documentation can describe options added after this runtime's build, so verify actual behavior.

## Reset and diagnostics

**Reset renderer overrides** clears custom rows/text, disables their master switches and queue tuning, and restores two compiler workers. It keeps selected FPS, VSync, detail, controls and driver choices. Reset is not a full graphics/saves reset.

**Disable diagnostic logging** quiets managed launcher, DXVK and driver diagnostics. It cannot guarantee suppression of every Android system message or native crash report. The explicit local performance recorder remains available when diagnostic logging is disabled.

## DXVK switching and frame interpolation

The app uses native Android DXVK libraries with runtime-specific interfaces. It does not load arbitrary Windows DXVK DLLs, and a DXVK version selector is not implemented. Supporting another binary requires a compatible ARM64 Android build plus integration and device testing.

LSFG-VK/frame interpolation is not installed. The FPS cap and queue experiment control frame delivery; neither generates extra frames.
