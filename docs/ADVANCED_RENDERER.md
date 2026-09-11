# DXVK versions and custom drivers

[Back to XHYN V](../README.md)

**DXVK and Turnip do different jobs:** DXVK translates graphics calls; Turnip is the GPU driver. Change one at a time when comparing performance.

## Choose DXVK

Open **Drivers → Choose DXVK version**.

| Choice | Use it for |
| --- | --- |
| **3.1+** | The default and your first rollback option |
| **2.7.1+** | Trying the included compatibility build |
| **2.7.1 GPLAsync** ``[UNSTABLE]`` | Testing asynchronous shaders; some objects may appear late |
| **1.10.3 Native** ``[UNSTABLE]`` | Testing the older Android build; fewer supported options |

**Fully restart after switching.** Save in-game, then use MENU → Launcher home if needed. These are four integrated Android versions; arbitrary Windows DXVK DLLs cannot be imported.

If an alternative crashes or renders incorrectly, return to **3.1+** and your working driver.

## Add a driver

Open **Drivers → Import & use driver ZIP** and choose a compatible ARM64 AdrenoTools package. The bundled choice is **Turnip R8**.

Driver imports affect XHYN V only and do not require root. Passing import checks does not guarantee the driver works with your phone.

## Advanced settings are optional

**Advanced renderer** has separate switches for custom environment variables and global **dxvk.conf**. Keep them off unless you want to tune specific options.

Use **Preview effective settings** or **Explain active overrides** to see what will be supplied at launch. Custom settings can conflict with launcher choices, so check priority.

The cache manager can clear a selected driver's managed caches. Expect temporary compilation stutter afterward.

[Fix rendering problems](TROUBLESHOOTING.md) · [Graphics guide](GRAPHICS.md)

<details>
<summary><strong>Technical details and full reference (optional)</strong></summary>

**DXVK and the Vulkan driver are separate selections.** DXVK translates the engine's graphics API; the driver implements Vulkan for the GPU. Keep the driver that already works when first comparing DXVK versions.

## Switch between the included DXVK pairs

Open **Drivers → Choose DXVK version**, or the same selector under **Graphics → Advanced renderer**. Choose a version, close the selector and start the game in a fresh process.

| Choice | Origin | What to expect |
| --- | --- | --- |
| **DXVK 3.1+** | The original bundled Android pair, unchanged from r12 | Default on upgrade and the first rollback option |
| **DXVK 2.7.1+** | Alternative | Compatibility experiment |
| **DXVK 2.7.1 GPLAsync** ``[UNSTABLE]`` | Upstream 2.7.1 with the pinned Ph42oN GPLAsync patch, built for Android ARM64 | Optional asynchronous shaders; can trade compilation stalls for temporarily missing/late objects |
| **DXVK 1.10.3 Native** ``[UNSTABLE]`` | Upstream 1.10.3 with DXVK Native platform work and Android/ARM64 adaptations | Experimental legacy option with fewer features; not an official upstream Android release |

The two source-built alternatives are modified Android builds, so desktop version numbers alone do not describe their compatibility.

Every choice loads matching DXGI and D3D11 libraries before the engine. A library-load failure selects 3.1+ for the **next restart**, rather than mixing two versions in a partly initialized process.

This recovery cannot catch every later black screen, native crash, shader failure or Vulkan device loss. If rendering fails, fully close the app, select the original renderer, and restart. **MENU → Launcher home → Close game and return** provides a fresh launcher process after closing gameplay. Save first; this is not a suspend/resume feature.

The selector is limited to the four included pairs. Arbitrary Windows `dxgi.dll`/`d3d11.dll`, loose native libraries and desktop DXVK ZIPs are not importable renderer packages. There is no hot swap or in-app build/download of additional DXVK versions.

## GPLAsync and version-specific settings

**Asynchronous shaders** appears for the GPLAsync choice and defaults On for that build. It controls `dxvk.enableAsync`; normal custom-config precedence still applies. An enabled custom `DXVK_ASYNC=0` environment row disables async even if the UI switch is on. Remove that row to let the normal selection govern it.

If objects appear late or rendering becomes unreliable, disable async or return to 3.1+ and restart. Async compilation is not frame generation, and its presence is not a guarantee of higher sustained FPS.

The legacy 1.10.3 path filters the launcher's tiler/texture-LOD overrides and HUD counters for descriptors, allocations and API level. Saved choices are retained for a later supported renderer. Other unsupported custom settings may be ignored by the selected binary. Windows-only shared handles, GDI and non-null Windows event handles for fence completion are unsupported in this legacy port.

Enable the **DXVK version** HUD counter to check the actual renderer's version string. Support/performance reports also distinguish selected and loaded pairs where a session snapshot exists. A saved selection by itself does not prove successful rendering.

## Vulkan driver selection

The app includes **Bundled Turnip R8**, labeled Mesa 26.0.0. **Import & use driver ZIP** accepts compatible AdrenoTools packages with `meta.json` and ARM64 Vulkan libraries, including supported archives wrapped in one folder.

The importer checks paths, duplicates, size limits, metadata/API requirements, ELF architecture and memory-page alignment before installation in app-private storage. It does not modify Android's system driver and does not require root. A valid package can still fail on a particular GPU or in this game.

Keep the working bundled choice available. A missing/invalid import or a loader-open failure can fall back to the existing driver path; a driver that loads but renders incorrectly may require manual rollback. Fully restart after changing drivers. An Adreno Turnip archive does not add support for a different GPU family.

## Shader cache manager

Before launching, open **Drivers → Shader cache manager** to see managed cache sizes and available storage. Select the driver's caches you want to clear. This removes managed cache data, not drivers or saves.

Revision 13 separates caches by renderer and driver while preserving the established 3.1+ cache location. Clearing one driver's managed cache group clears its renderer subdirectories too. Switching versions does not itself delete caches. Legacy 1.10.3 uses its state-cache path; the 2.7.1 alternatives use the selected driver's cache, while 3.1+ retains its existing shader-cache handling.

Expect compilation and possible stutter after clearing. Old shared caches under `Games/GTAV` are outside these managed totals. Repeated cache deletion is not a routine FPS optimization.

## Environment variables and dxvk.conf

In **Advanced renderer**, custom environment rows and global custom config each have a master switch, initially Off. Each environment row also has its own switch. Saving or importing text does not automatically enable it.

| Input | Accepted form and limit |
| --- | --- |
| Environment | Up to 64 literal name/value rows; values are single-line and at most 4,096 characters |
| Config import | UTF-8, up to 64 KiB |
| Config text | Global `name = value` settings, comments, blank lines and quoted values; bounded editor/import size |
| Desktop executable sections | `[sections]` are rejected; use global settings for this runtime |

Rows are literal values, not shell commands. Enter a variable name and value separately; do not paste `export`, a shell script or a Windows batch file. Driver/cache/log/config paths needed by the launcher are reserved.

For example, a global custom config may contain:

```ini
# Optional frame cap; the regular FPS UI can also set it.
dxgi.maxFrameRate = 30
```

An optional Mesa cache-size row is `MESA_SHADER_CACHE_MAX_SIZE` with value `512M`. It limits cache size; it does not multiply FPS. Support depends on the selected driver. [Mesa environment variables](https://docs.mesa3d.org/envvars.html).

## Conflict priority and explanations

1. The launcher generates config from graphics, HUD, cap, workers and supported experiment selections.
2. Enabled custom global config is merged with it. **Launcher settings win** is the default; **Custom config wins** reverses priority for conflicting keys. Nonconflicting custom keys remain, and repeated custom keys use the last value.
3. Some enabled environment variables are interpreted separately by DXVK/Mesa and can override related config behavior. The config merge choice does not change those variables into ordinary config entries.
4. **Disable diagnostic logging** takes priority over custom logging settings. Managed paths and version compatibility filtering still apply.

The normal launch path writes a private effective config and sets `DXVK_CONFIG_FILE` before native initialization. **Preview effective settings** shows the next launch's values. **Explain active overrides** shows their source and replaced conflicting values, with Next launch and Applied at launch views when a saved startup snapshot exists.

Applied at launch is a record of what was supplied, not proof that every option was recognized or accepted by the renderer. If applying custom settings fails, a visible warning indicates defaults may be in use. There is no hot reload of a running renderer.

Upstream [DXVK configuration](https://github.com/doitsujin/dxvk/blob/master/dxvk.conf) and [HUD documentation](https://github.com/doitsujin/dxvk#debugging) help explain options, but may describe features newer than the selected native build.

## Reset scope

**Reset renderer overrides** clears custom rows/config, disables their master switches, resets conflict priority and returns to two compiler workers. It disables queue, tiler and texture-bias experiments. FPS, VSync, graphics, driver and DXVK selections are kept. Swappy and Android performance hints have separate switches; this is not a reset of all experiments or all app settings.

**Disable diagnostic logging** quiets managed launcher, DXVK and driver diagnostics and requests quieter engine output. Existing logs remain; Android/native crash reports may still be written. Explicit performance recording and support export remain user-controlled tools.

For Swappy, hints and HUD definitions, see [Graphics](GRAPHICS.md). For symptoms and rollback, see [Troubleshooting](TROUBLESHOOTING.md).

</details>
