# Simple performance tips

[Back to XHYN V](../README.md)

1. **Save your working setup** before experimenting.
2. **Choose a realistic FPS cap.** A higher limit does not make a slow scene faster.
3. **Try a lower resolution**, then compare the same scene.
4. **Reduce expensive detail settings** such as shadows, reflections or MSAA if needed.
5. **Keep useful shader caches.** New areas and new renderer/driver combinations may stutter while compiling.
6. **Test one DXVK or driver change at a time.** Older does not automatically mean faster.
7. **Try native experiments last**, individually, and keep them only if your experience improves.

If performance starts well and worsens later, note the session length and thermal status. Heat, scene changes and memory pressure can affect results.

For a fair comparison, keep the phone, scene, actual resolution, quality and FPS cap the same. Compare repeated runs after caches warm up, and report visual problems alongside FPS.

**The local recorder exports app CPU/RAM/thermal data, not game FPS.** Use an actual FPS measurement if sharing benchmark claims.

[Graphics settings](GRAPHICS.md) · [DXVK and drivers](ADVANCED_RENDERER.md)

<details>
<summary><strong>Technical details and full reference (optional)</strong></summary>

XHYN V provides controls over workload, compilation and frame delivery. The current user report is positive, but there is no controlled benchmark proving a specific FPS gain over earlier revisions or a Windows compatibility build. Keep a working configuration and compare one change at a time.

## A practical tuning order

1. **Save your working setup.** Record DXVK, driver, actual render dimensions and the scene. Use Complete setup profiles to keep a rollback configuration.
2. **Choose a sustainable FPS target.** An added cap can reduce unnecessary work when the game would otherwise render faster. A cap cannot make a slow scene reach the target, and mismatched caps/VSync can affect pacing.
3. **Adjust resolution for GPU-heavy scenes.** Try a lower preset and compare the same scene. If FPS barely changes, another limit may dominate. Check the pixel preview; the percentage alone is not enough to compare different screens.
4. **Adjust detail deliberately.** Test shadows, reflections, MSAA and grass separately, or use the reversible lower-detail preset. Retain the image quality you prefer instead of assuming every low setting helps equally.
5. **Try population/distance where available.** These may change scene workload, but the engine must expose the relevant XML fields. They are not a guaranteed fix for CPU stalls or scripted scenes.
6. **Let shaders warm up.** First visits to a scene or a new renderer/driver can compile work. Keep useful caches. Clear a cache to investigate a specific problem, not after every launch.
7. **Compare renderers, then drivers.** Keep all other settings fixed. Start with the working 3.1+ path; test alternatives individually and return if they cause missing graphics or instability. A version number is not a performance ranking.
8. **Test advanced experiments last.** Queue length, tiler policy, texture bias, GPLAsync, Swappy and Android hints have different effects. Enable one, restart and inspect both image correctness and consistency.

Swappy targets presentation timing; it does not produce interpolated frames. Its integration can help or introduce waits on a particular combination. Android's description explains the difference between a game's workload and when frames appear on screen. [Android Frame Pacing](https://developer.android.com/games/sdk/frame-pacing).

## What can still cause lag?

| Symptom | Things to investigate |
| --- | --- |
| Stutter entering a new area, then improvement on repeat | Shader/pipeline compilation or asset streaming; inspect compiler activity and repeat the route |
| Consistently slow detailed scenes | Resolution, shadows/reflections/MSAA, GPU workload and the driver |
| Little change after lowering resolution | CPU simulation, synchronization, streaming, a cap or another bottleneck; this is a clue, not proof |
| Good initial speed, worse after a longer session | Thermal/power limits, memory pressure or workload changes; record duration and Android thermal severity |
| Uneven delivery despite an apparently adequate average | Caps/VSync, queue behavior, shader spikes and optional pacing settings |
| Missing objects after enabling GPLAsync | Async compilation behavior or a rendering regression; disable async and compare |

Native ARM64 execution removes the need for translating the engine's x86 instructions, but does not remove engine work or DXVK/driver costs. See [Architecture](ARCHITECTURE.md).

## Overlay refinements already included

For ordinary play, select only HUD counters you use. Disable managed diagnostic logging if you do not need routine diagnostics, then re-enable it for a short bug reproduction. Neither choice guarantees a noticeable speed increase.

</details>
