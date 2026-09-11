# What's changed?

[Back to XHYN V](README.md)

XHYN V is a **modified build based on the China Android Launcher of GTA V**, with community modifications by **XHYN_PH 🇵🇭**.

## Revision 13 —

- Four included Android DXVK versions: 3.1+, 2.7.1+, 2.7.1 GPLAsync and 1.10.3 Native.
- Version-aware settings, separate caches and DXVK choices saved in complete setups.
- Renderer loading checks and rollback support. A full restart is required.

[Revision 13 notes](docs/releases/v0.13.md)

## Revision 12 —

- Return to launcher home, Russian/French menus and complete setup sharing.
- Button fading, groups/locks, zoom/pan, bigger touch areas and swipe actions.
- More graphics choices and optional Swappy pacing/Android performance hints.

## Revision 11 —

- Input test screen, button combinations and temporary alternate bindings.
- Compact configurable toolbar, Creator mode and menu appearance options.
- Save backups, support exports, cache management and overlay refinements.

Earlier updates added the custom launcher, editable touch layouts, English game configuration, reversible lower detail, driver imports and HUD tools.


<details>
<summary><strong>Full revision history (optional)</strong></summary>

Check [Releases](https://github.com/XHYN-PH/XHYN-V/releases) for published APKs.

## 0.13 — 

- Added **Drivers → Choose DXVK version**, also available through Advanced renderer.
- Kept the original **DXVK 3.1+** pair as the default and unchanged from r12.
- Added an adapted **2.7.1+ compatibility pair** from the supplied comparison APK, without its engine, SDL, driver or unrelated hooks.
- Built **DXVK 2.7.1 GPLAsync** for Android ARM64 with an asynchronous-shader switch.
- Built an experimental **DXVK 1.10.3 Native** Android ARM64 port with explicit limits for unsupported Windows interfaces.
- Added matched-pair preload, payload size/hash checks, extracted-file repair and recovery to the original renderer on the next restart after library-load failure.
- Separated caches by renderer and driver while retaining the established 3.1+ cache path.
- Added DXVK/async choices to complete setups, with migration for older files.
- Filtered unsupported legacy options/HUD counters while retaining user preferences for compatible renderers.
- Added selected/loaded renderer information to diagnostics and translated selector text across seven languages; 675 menu dictionary entries.
- Retained the r12 engine, SDL, driver, Vulkan loader, input helper and original DXVK libraries byte-for-byte.

See [0.13 notes](docs/releases/v0.13.md) for selection, rollback and validation scope.

## 0.12 — 

- Added **MENU → Launcher home** to close gameplay and return to a fresh launcher process; no autosave or suspended session.
- Added Russian and French, bringing menu language selection to seven languages.
- Added configurable idle/active button fading, delay and finite transitions.
- Added named groups, position locks, editor zoom/pan/Fit, and larger invisible touch areas with visible-button priority.
- Added Linear, Precision and Acceleration response curves for touch mouse-look.
- Added directional swipe bindings and reliable release/cancellation handling.
- Added reversible population density, distance, pedestrian-variety and vehicle-variety controls for existing engine XML fields.
- Added optional DXVK tiler policy and texture LOD bias settings.
- Added explanations of override sources/conflicts and immutable applied-at-launch views.
- Added complete setup profiles containing graphics, all touch modes, driver references, custom renderer settings and native experiment switches.
- Compiled and integrated optional **Swappy frame pacing** into Vulkan presentation; Off by default with original-path fallback.
- Added optional **Android performance hints** using measured presentation-thread work where the platform/path supports them; Off by default.
- Retained eight of the nine original native libraries; the Vulkan loader changed for the native integration.

Swappy was deferred in r11 and first included in r12. Selectable replacement DXVK pairs arrived in r13. Spatial upscaling and frame interpolation remain outside the release.

See [0.12 notes](docs/releases/v0.12.md).

## 0.11 — 

- Added an input test screen without launching the game.
- Added simultaneous key/mouse combinations, double tap, long press and a temporary modifier layer.
- Added per-button symbols/colors, menu accent/text size and Simple/Advanced views.
- Added a reorderable, collapsible quick toolbar and Creator mode with optional watermark/restore handle.
- Added applied/pending settings indicators.
- Added managed driver cache sizes, free-space display and selective cache clearing.
- Added timestamped save backups, retention, restore preview, checksum verification, interruption recovery and ZIP export.
- Added a selectable support ZIP with previews matching exported text.
- Reduced unnecessary overlay polling, repeated draw-time work and temporary touch-state allocations.
- Preserved all nine native libraries from r10.

Swappy was a deferred prototype in this revision, not an installed feature. It was integrated in r12. No game-FPS or battery improvement was measured by the isolated overlay checks.

See [0.11 notes](docs/releases/v0.11.md).

## 0.10 — 

- Added optional floating movement and left-handed empty-space camera zones.
- Added an eight-slot keyboard/mouse shortcut wheel and eight control pages per mode.
- Included pages/movement preferences in portable profiles and added a visual starter gallery.
- Added reversible individual textures, shadows, reflections, grass and MSAA choices.
- Expanded FPS presets/custom 10–240 caps, VSync and Auto/1/2/4 compiler workers.
- Added optional DXVK queue tuning, environment rows, global `dxvk.conf`, master switches, merge priority and effective-settings preview.
- Added a movable app CPU/RAM/thermal HUD and user-started local performance recording/export.
- Added Indonesian and Brazilian Portuguese, bringing menu selection to five languages.
- Changed slider editing to steps of ten while preserving endpoints and untouched saved values.
- Expanded graphics profile fields and corrected restoration of underlying low/original detail when individual overrides are removed.


## 0.9 — 

- Added independent camera/aim sensitivity, inversion and optional gyro aiming.
- Added editor undo/redo, multi-select, snapping, alignment and group resizing.
- Added built-in/custom graphics profiles and Android thermal-status HUD selection.
- Added physical-controller digital remapping, stick dead zones and touch auto-hide; hardware testing remained a separate requirement.

## 0.8 — 

- Added English, Filipino and Spanish launcher/control-tool language selection.
- Added the dark purple launcher, title logo and compact movable control tools.
- Added named control profiles with Android picker import/export.
- Added custom render scale with a nonzero minimum and diagnostic-logging controls.

## 0.7 — 

- Changed mobile on-foot/driving camera input to keyboard/mouse touch paths.
- Added editable/duplicable buttons, shapes, bindings, visibility and appearance with bounded layout sizes.
- Added the optional SDL-state cursor and individually selectable HUD counters.
- Retained existing graphics restoration, driver imports and community branding.

## 0.6 — 

- Enlarged toggles and tappable settings rows
- Added expanded HUD choices and optional app CPU/PSS statistics.
- Added native-controller, mobile on-foot, driving and keyboard/mouse modes with separate layouts.
- Established package `com.xhynph.v` and the subsequent update-signing line. Earlier Test packages used a different identity.

## 0.5 — 

- Renamed the app to XHYN V and added the tabbed launcher, layout preview and community credits.
- Fixed lower-detail Off leaving previously written low values in the settings file; added reversible detail recovery and migration of affected earlier settings.
- Preserved full graphics backup as a separate restoration tool.
- Added compatible app-local AdrenoTools driver ZIP import/selection with validation and rollback support.

## 0.4 — 

- Added render-scale presets, FPS choices, lower detail and an FPS counter.
- Added saved graphics backup, a touch-layout editor and persistent in-game MENU.
- Added control movement/size/visibility, opacity and optional vibration, with input cancellation on focus/menu transitions.

## 0.3 —

- Changed the embedded game argument from `-uilanguage=chinesesimp` to `-uilanguage=american` for English.

## Test 02 —

- Added bundled Mesa Turnip and app-local driver loading.
- Unified Vulkan lookup paths across the renderer, SDL and engine integration.
- Retained the earlier graphics-lock wait mitigation and separated test cache/diagnostic handling.
- User feedback progressed to actual gameplay after the earlier startup failures.

## Test 01 —

- Investigated pipeline failures, graphics-device loss and startup watchdog stalls.
- Adjusted the graphics-lock wait and an incomplete Vulkan compatibility fallback.
- This first test alone did not resolve the reported black-screen problem; later driver-path changes