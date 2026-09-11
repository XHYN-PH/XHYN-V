# Adjust graphics and performance

[Back to XHYN V](../README.md)

**Save a working profile, change one setting, then restart the game to compare.**

## The main settings

| Setting | What it does |
| --- | --- |
| Resolution | Lower values reduce image sharpness and GPU workload |
| Lower graphics detail | Applies a lower-detail preset; Off restores saved original detail |
| Individual graphics controls | Adjusts textures, shadows, reflections, grass and MSAA |
| Population and distance | Adjusts supported world settings when the game exposes them |
| FPS limit | Sets a target cap; it cannot make the game reach an unsupported frame rate |

Custom resolution goes from 0–100%, with a pixel preview. **0% selects a small nonzero minimum.** Turning custom scale off returns to the selected preset, not automatically to full resolution.

## Graphics still look low?

Close the game, turn lower detail off, and also check **individual overrides, resolution and texture LOD bias**. These are separate settings. The next launch restores saved baseline detail.

Use **Restore full graphics backup** only if you also want to restore the older resolution and other settings in that snapshot.

## Choose your HUD

Open **Performance HUD / Choose HUD counters** and check only what you want to see.

- **DXVK:** FPS, frame timing, estimated GPU load, memory and renderer counters.
- **App statistics:** app CPU, app RAM and Android thermal severity—not a temperature reading.

Restart for native DXVK HUD changes. The app statistics HUD can be moved through MENU.

## Optional experiments

Advanced menus include queue/tiler/texture-bias tuning, **Swappy frame pacing** and **Android performance hints**. Try these individually; they are not guaranteed boosts. Swappy adjusts frame scheduling; it does not generate frames.

The local performance recorder exports app CPU/RAM/thermal data. It does **not** export game FPS or 1% lows.

[Performance tips](PERFORMANCE.md) · [DXVK and drivers](ADVANCED_RENDERER.md)

<details>
<summary><strong>Technical details and full reference (optional)</strong></summary>

Graphics and renderer changes normally apply after a fresh game launch. Save a working profile before experimenting. **Settings status** distinguishes choices saved for next launch from the startup snapshot; the snapshot cannot prove a driver honored every option.

## Resolution

Choose **Use current game resolution**, a 50/67/75/83/100% preset, or enable a custom **0–100%** render scale. The preview shows actual pixel dimensions. Scaling preserves aspect ratio, uses even dimensions and clamps to a nonzero drawable minimum.

**0% means the minimum supported size, not a zero-pixel image.** Several low values may resolve to the same clamped dimensions. Disabling custom scale returns to the selected preset on the next launch; it does not automatically select 100%.

Sliders snap in tens while preserving endpoints and existing values until edited. Render scale changes the workload/image resolution, not the phone panel's physical resolution. This is ordinary resolution scaling, not FSR, AI upscaling or frame interpolation.

## Reversible lower detail

**Lower graphics detail** saves a baseline so disabling it can restore the values from before the preset. Later normal-to-low cycles can capture a newer baseline. The original full graphics backup is a separate, broader snapshot.

**Individual graphics controls** has its own master switch. Texture, shadow, reflection and grass choices offer Keep preset, Normal, High and Very high; MSAA/reflection MSAA offer Keep preset, Off, 2× and 4×.

| Lower detail | Individual controls | Result |
| --- | --- | --- |
| Off | Off | Saved original detail |
| On | Off | Lower-detail preset |
| Off | On | Original detail with selected individual overrides |
| On | On | Lower-detail preset with selected individual overrides |

**Keep preset** restores that managed key to its underlying low/original value. Turning all detail overrides off restores the saved normal-detail values. Unrelated XML entries are retained, and invalid/missing recovery data produces an error rather than guessed settings.

If graphics remain blurry, also inspect resolution, custom scale, individual overrides and texture LOD bias. Restoring detail does not reset these independent selections. A backup captured while the game was already low detail cannot reconstruct unknown earlier values.

**Restore full graphics backup** also restores the resolution and other settings captured in that full snapshot. Use it only when that broader restoration is intended.

## Population and distance

In Advanced menus, **Graphics → Population and distance** offers an optional master switch and Keep original or 0–100% values in tens.

| Control | Existing engine setting |
| --- | --- |
| Population density | `CityDensity` |
| Distance scale | `LodScale` |
| Pedestrian variety | `PedVarietyMultiplier` |
| Vehicle variety | `VehicleVarietyMultiplier` |

Only existing, unique numeric fields in the current settings file are available. Missing fields are disabled. Density is one combined control, not separate pedestrian and traffic-density sliders. Zero does not guarantee an empty world or remove scripted entities.

The first enabled use records original values. Disabling a selection or the feature restores those values on the next launch. Keep recovery sidecar files with the settings when moving the game folder. This recovery is separate from the detail-preset baseline.

## Frame delivery and compilation

| Control | Choices and meaning |
| --- | --- |
| FPS presets | No added limit, 24, 30, 40, 45, 50, 60, 90, 120, 144 |
| Custom FPS | Integer 10–240; 0 removes the launcher's added cap |
| VSync | Automatic, Use game setting, Off, On, Half refresh rate |
| Compiler workers | Auto, 1, 2, 4 |
| Frame-queue experiment | Off by default; 1–4 queued frames when enabled |

Automatic VSync uses the existing launcher behavior: off with an added cap, otherwise defer to the game. **Use game setting** leaves the current XML VSync value and removes the DXVK sync-interval override. “No added limit” does not remove caps imposed elsewhere or disable VSync automatically.

Auto compiler workers delegates the count to the renderer. More workers may finish compilation sooner but compete with gameplay CPU work. A shorter queue changes buffering and can affect latency or stutter. Neither setting creates extra frames. Custom config can override launcher values when its priority is enabled.

The launcher also requests an appropriate available display mode for its frame target. Android/OEM policy and supported refresh modes still determine what can actually be used.

## Renderer and native experiments

| Option | Purpose | Current boundary |
| --- | --- | --- |
| Tiler mode | Selects DXVK's tile-based rendering policy: Auto, Enabled or Disabled | Optional override; unavailable through the 1.10.3 launcher path |
| Texture LOD bias | Positive bias from 0.0–1.0 prefers less detailed texture mip levels | Can soften textures; not upscaling; unavailable through the 1.10.3 launcher path |
| Swappy frame pacing | Coordinates Vulkan presentation with Android display timing and the launcher FPS target | Included since r12, Off by default; unsupported paths keep original presentation |
| Android performance hints | Reports measured work from the presentation thread to Android | Off by default; API 33+ where available; Android may ignore hints |

Tiler/LOD settings are under **Advanced renderer**. Native options are under **Graphics → Native performance experiments** in Advanced menus. Disable an experiment and restart to remove its launcher/native contribution; separately entered custom config may remain active.

Swappy's purpose is presentation timing, as described by the [Android Frame Pacing documentation](https://developer.android.com/games/sdk/frame-pacing). XHYN V's integration is an optional experiment, not a measured benefit on every driver. Its dialog reports Off, Waiting, Active or original-path status. It paces one eligible swapchain and keeps the original path when initialization or the rendering arrangement is unsuitable.

Performance hints describe measured acquire-to-present CPU work on the same presentation thread, excluding image-acquisition and pacing waits. They do not measure all CPU/GPU work, force clocks or override thermal limits. API/session failure leaves ordinary rendering available. [Android Performance Hint API](https://developer.android.com/ndk/reference/group/a-performance-hint).

Keep frame caps aligned when testing Swappy. Change one experiment at a time. Current gameplay feedback does not establish pacing or hint effectiveness.

## Graphics profiles

Performance, Balanced and Quality presets plus up to **32 custom graphics profiles** store resolution, detail, world settings, FPS, VSync, workers, queue and supported renderer experiments. Use, update, rename or delete saved snapshots.

A graphics profile does not bundle DXVK/driver selection, custom environment/config text, touch controls or all app preferences. Use [Complete setup profiles](PROFILES_AND_BACKUPS.md) when those settings need to travel together.

## Choose HUD counters independently

Open **Graphics → Performance HUD / Choose HUD counters**. Select only the counters you need; CPU-only or RAM-only does not force a full renderer overlay.

| Source | Available information | Interpret correctly |
| --- | --- | --- |
| App statistics | CPU, RAM, Android thermal status | App CPU normalized over logical processors; RAM is app PSS; thermal status is severity, not a temperature sensor |
| DXVK HUD | FPS, frame-time graph, estimated GPU load, GPU memory, device information, compiler activity, command-stream thread, draw calls, submissions, pipelines, descriptors, allocations, DXVK version and API/feature information | Values and availability depend on the selected renderer; GPU load is an estimate |

DXVK 1.10.3 filters descriptors, allocations and API-level HUD selections. Saved choices return when a supporting renderer is selected. App CPU/RAM/thermal counters remain independent.

The app statistics overlay can move, use horizontal/vertical orientation, and change opacity. **MENU → App statistics HUD → Move statistics HUD** lets you drag and save its position. The native DXVK overlay is separate and keeps its own placement. Native HUD changes require restart; app HUD appearance changes refresh through the in-game tools.

## Local performance recording

Open **MENU → Performance report → Start recording**, then **Stop and save** and export through Android's picker. The report contains device, selected/loaded renderer, driver and settings information, plus app CPU/RAM/thermal samples and summaries.

CPU/thermal sampling is approximately once a second, PSS refresh approximately every three seconds, and sampling pauses without focus. Up to 7,200 recent samples are retained with dropped-sample/aggregate accounting for longer recordings. Until stopped and saved, recording is in memory and can be lost in a crash.

**This recorder does not export actual game FPS, frame times, GPU utilization or 1% lows.** Do not label its CPU samples as an FPS benchmark. It is user-started, saved locally, exported only by choice, and independent of the diagnostic-logging toggle.

See [Performance](PERFORMANCE.md) for a practical tuning order and comparison procedure.

</details>
