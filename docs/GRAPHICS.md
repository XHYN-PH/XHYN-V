# Graphics, HUD and performance reports

[Back to the project](../README.md)

## Apply changes deliberately

Start with a working configuration and change one setting at a time. Close and relaunch the game to apply renderer and file-based graphics changes. Save a graphics profile when a configuration works well on your device.

Settings are controls over workload and frame delivery. No preset guarantees a frame rate, and a higher FPS cap cannot create performance the device does not have.

## Resolution

Choose current resolution or the available percentage presets, or enable the custom **0–100%** render scale. The UI displays the resulting dimensions. Scaling keeps the aspect ratio and clamps to a nonzero drawable minimum with even pixel dimensions.

**0% selects the minimum, not a zero-sized image.** The minimum clamp can make several low percentages resolve to the same dimensions. Disabling custom scale returns to the selected preset on the next launch.

Slider editing uses multiples of ten and preserves endpoints. An older stored value such as 67% remains intact until you edit it.

## Lower detail and individual settings

The **Lower graphics detail** preset uses a saved original-detail snapshot so it can be turned off again. **Individual graphics controls** have a separate master switch, Off by default on upgrade.

| Setting | Choices |
| --- | --- |
| Textures, shadows, reflections, grass | Keep preset, Normal, High, Very high |
| MSAA and reflection MSAA | Keep preset, Off, 2x, 4x |

Enabled individual choices override the corresponding values in the low preset. **Keep preset** returns that managed value to the underlying low/original detail rather than retaining an old individual override.

| Lower detail | Individual master | Result |
| --- | --- | --- |
| Off | Off | Original saved detail |
| On | Off | Lower-detail preset |
| Off | On | Original detail plus chosen individual overrides |
| On | On | Lower-detail preset plus chosen individual overrides |

Turning all detail overrides off restores the original detail snapshot. A separate full XML backup is also available. Only supported scalar XML settings are changed; unrelated entries are retained.

Resolution is separate. If the picture remains blurry after restoring detail, check custom resolution and the selected resolution preset. If a particular setting remains overridden, also check individual controls and custom renderer configuration.

## FPS, VSync and compiler workers

| Control | Choices and behavior |
| --- | --- |
| FPS presets | No added limit, 24, 30, 40, 45, 50, 60, 90, 120, 144 |
| Custom FPS | Integer 10–240; 0 removes the launcher's added limit |
| VSync | Automatic, Use game setting, Off, On, Half refresh rate |
| Compiler workers | Auto, 1, 2, 4; upgrade retains 2 |
| Frame-queue experiment | Off by default; enabled value is 1–4 queued frames |

Automatic VSync follows the existing launcher behavior: off with an added cap, otherwise defer to the game. **Use game setting** leaves the current XML VSync value unchanged and removes the DXVK sync-interval override.

Auto compiler workers delegates the count to the renderer. More workers can compete with the game for CPU while compiling shaders; fewer can prolong compilation. Use the compiler HUD counter to distinguish compilation activity from ordinary gameplay load.

The queue experiment sets `dxgi.maxFrameLatency`. A shorter queue may alter input delay or introduce stutter. It does not install Android Swappy or interpolate frames. Custom config can override these choices when **Custom config wins** is selected.

## Graphics profiles

Performance, Balanced and Quality presets are available, along with up to 32 custom named graphics snapshots. Save/use/update/rename/delete profiles from **Graphics profiles**.

Revision 10 snapshots include individual detail settings, FPS/VSync, worker selection and queue tuning. Older/built-in profiles use the established defaults for newly added fields. Custom environment variables and custom `dxvk.conf` text are managed separately.

## HUD counters

Use **Graphics → Choose HUD counters** to enable individual counters.

| Source | Available information | Meaning |
| --- | --- | --- |
| App statistics | CPU, RAM, Android thermal status | This app's CPU usage and proportional RAM; thermal severity reported by Android |
| Native DXVK HUD | FPS, frame times, estimated GPU load, memory, device info, compiler and other renderer counters | Renderer-provided values supported by this binary |

App CPU is normalized across logical processors. App RAM is PSS, not whole-device RAM usage. Android thermal status is a severity level, not a CPU/GPU temperature reading. GPU load in the DXVK HUD is an estimate, not a universal hardware sensor measurement.

Under **MENU → App statistics HUD**, select horizontal/vertical orientation, opacity or **Move statistics HUD**. Drag and release to save its position; reset returns it to the default area. If no app counter is enabled, movement uses a placeholder.

The DXVK overlay is separate and keeps its native position. App HUD changes refresh after closing the relevant in-game dialog; native DXVK HUD changes require restart.

## Local performance reports

Open **MENU → Performance report → Start recording**. Stop and save, then export the last report through Android's file picker.

- App CPU and thermal samples are collected about once a second; RAM PSS refreshes about every three seconds.
- Sampling pauses when the game loses focus.
- Up to 7,200 recent samples are retained; longer sessions track dropped samples and aggregate totals.
- Reports include device/API, driver, graphics selections, renderer configuration and CPU/RAM/thermal summaries.
- Recording is in memory until **Stop and save**. A crash can lose an unfinished recording.
- Reports are saved locally and exported only by user action. They are independent of the diagnostic-logging toggle.

The recorder does not capture game FPS, frame times, GPU utilization or 1% lows. Those should not be claimed from its app-statistics samples. Review exported configuration and device information before sharing a report.
