# How XHYN V works

[Back to XHYN V](../README.md)

**XHYN V is based on the China Android port of GTA V, modified by XHYN_PH.** The modifications add the launcher, control tools, tuning options and compatibility improvements described in these guides. Original game and port developers retain their credit.

## The three main parts

| Part | Simple explanation |
| --- | --- |
| Android ARM64 engine | Runs the game on your phone's CPU |
| DXVK | Converts the game's Direct3D graphics calls to Vulkan |
| Turnip | A Vulkan driver that lets supported Adreno GPUs draw the game |


## Why choose it over a Windows setup?

The engine already uses ARM64, so it avoids the x86-to-ARM CPU translation needed by a typical Windows-game setup. The controls and launcher are also tailored to this game. That can make setup easier and reduce translation work.

**It is not guaranteed to be faster.** Shaders, graphics settings, drivers and heat still matter.

## What are the limits?

- It runs this particular Android runtime, not arbitrary Windows games.
- Other phones, PC mods and game-data versions need compatibility testing.
- GTA Online is not a supported feature.
- DXVK is still required. There is no direct-Vulkan replacement, OpenGL option, FSR or frame interpolation in this build.

[Performance tips](PERFORMANCE.md) · [Compatibility](COMPATIBILITY.md)

The optional reference below includes the technical explanation and source links.

<details>
<summary><strong>Technical details and full reference (optional)</strong></summary>

## What “native” means here

The inspected XHYN V runtime contains `libgtav.so` as an **Android ARM64 ELF library**. Its engine instructions execute on the phone's ARM64 CPU. The inspected launch route loads that library with SDL and Android libraries; it does not launch a Windows game executable through Wine and an x86 CPU translator.

The graphics interface is a separate question. This engine uses Direct3D 11 and DXGI interfaces provided by Android-compatible DXVK libraries. DXVK translates that rendering work to Vulkan. Upstream DXVK explicitly describes native use without Wine as a way to port a game while retaining its existing rendering backend. [DXVK Native documentation](https://github.com/doitsujin/dxvk#dxvk-native).

The accurate description is **“an unofficial Android ARM64 launcher with DXVK-based Vulkan rendering.”** “Native Android” describes the executable platform and CPU path. It does not mean every graphics API is Android-specific or that no compatibility work remains.

## What each part does

| Component | Job in this build |
| --- | --- |
| XHYN V launcher and control tools | Settings, file access, touch layouts, profiles, driver/renderer choice and community interface |
| Existing Android ARM64 game runtime | Game logic, world simulation, asset loading, audio and generation of rendering work |
| SDL and Android integration | Window/surface, input and platform services used by the runtime |
| Selected DXVK DXGI/D3D11 pair | Converts the engine's Direct3D rendering interface into Vulkan operations |
| XHYN V Vulkan loader | Connects components to the selected app-local Vulkan driver; hosts optional presentation experiments |
| Turnip or another compatible selected driver | Implements Vulkan for the supported GPU and communicates with the device's graphics stack |
| Phone GPU | Executes the resulting graphics workload |

Turnip is Mesa's Vulkan driver for Adreno. It uses the actual GPU; it is not a CPU emulator. Native Android games also need graphics drivers, whether supplied with the device or selected by a compatible app. XHYN V's driver import affects this app and does not replace Android's system graphics driver. [Mesa Freedreno/Turnip documentation](https://docs.mesa3d.org/drivers/freedreno.html#turnip).

## Comparison with a typical Windows-game setup on Android

“Windows emulator” is often used informally for tools that combine several components. Winlator documents Wine plus Box86/Box64 for Windows applications. Box64 provides x86-64 execution on architectures such as ARM64. This is different from assuming every such tool boots a complete Windows virtual machine. [Winlator](https://github.com/brunodev85/winlator), [Box64](https://github.com/ptitSeb/box64).

The comparison below is specifically against an **x86/x64 Windows game running on an ARM Android phone**. Different tools and configurations can use different graphics backends.

| Area | XHYN V's inspected native route | Typical Windows compatibility route |
| --- | --- | --- |
| Game executable | Android ARM64 library | Windows x86/x64 executable |
| CPU instructions | Engine already uses ARM64 | A translator such as Box64 handles the architecture difference |
| Windows services | Engine uses its Android/SDL integration | Wine provides Windows API compatibility |
| Graphics | Native DXVK converts D3D11 to Vulkan | Often DXVK for D3D9–11; other APIs may use other backends |
| GPU driver | Compatible Vulkan driver, including Turnip | May use the same Turnip driver on supported Adreno hardware |
| Configuration scope | One runtime with integrated touch/graphics tools | General containers and per-application Windows settings |
| Application coverage | This specific Android runtime | Many compatible Windows programs and games |
| PC mods and tools | Windows binary compatibility is not established | Closer to the expected PC environment, although compatibility still varies |

## Where XHYN V can have an advantage

**CPU work can avoid an extra translation step.** Because the engine is already ARM64, its instructions do not need x86-to-ARM translation. This is an architectural reason to expect less translation work; it is not a measured FPS, battery or RAM improvement for XHYN V.

**The setup can be simpler for this game.** Controls, graphics restoration, DXVK versions, drivers, diagnostics and profiles are exposed in one launcher. Users do not need to configure a general Windows container for this launch route. That convenience still depends on having compatible game data and hardware.

**The interface is tailored to touch.** On-foot and driving presets, mouse swipes, editable pages, gesture buttons, fading and the compact toolbar are part of the app. These are usability advantages for users who prefer this integration; similar ideas also exist in compatibility tools.

**Changes can target this runtime.** Startup compatibility work, reversible graphics settings and input handling can be adjusted for the known engine integration. General compatibility tools must cover many applications with different requirements.

These are reasons this build may be a better fit for a particular user. A controlled comparison is still required before claiming it is faster than a particular Winlator build.

## Where the advantage stops

- **GPU and shader limits remain.** DXVK still translates graphics APIs and compiles pipelines. Vulkan driver bugs, device loss, cache warm-up, bandwidth and rendering load can dominate frame time.
- **Native code can still be demanding or buggy.** CPU simulation, streaming, synchronization and memory use remain real work. Native execution alone does not ensure efficient implementation or stability.
- **Phone limits remain.** Heat, power limits, memory pressure and storage behavior can outweigh savings elsewhere. No universal FPS, battery-life or minimum-RAM improvement has been measured.
- **Compatibility is narrow.** This package targets a particular Android runtime/data layout. Owning or installing a current PC copy does not establish data compatibility. A Windows environment may suit a specific PC version or mod better.
- **The binary interface matters.** XHYN V's DXVK selector contains four integrated Android pairs. Downloading a desktop DXVK DLL, older version or community fork does not make it loadable here.

- **Broader features are outside the current scope.** GTA Online, arbitrary Windows applications, Windows DLL/ASI mods and launcher compatibility are not supported or established features of this runtime.

## Can it run without DXVK?

Not with a launcher switch in this build. The inspected engine links against the DXVK DXGI/D3D11 libraries. Removing them would remove interfaces the engine expects. A direct Vulkan or OpenGL renderer would require substantial engine/render-backend work and validation; importing Turnip does not provide that replacement.

Changing DXVK versions changes the translator implementation. It does not remove graphics translation. Swappy changes presentation scheduling, and GPLAsync changes shader compilation behavior; neither adds frame interpolation. [Current renderer choices](ADVANCED_RENDERER.md).

For device evidence, see [Compatibility](COMPATIBILITY.md). For a fair comparison procedure, see [Performance](PERFORMANCE.md).

</details>
