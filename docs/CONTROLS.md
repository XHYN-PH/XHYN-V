# Make the controls yours

[Back to XHYN V](../README.md)

## Pick a mode

Open **Controls → Switch control mode**.

| Mode | Best starting point for |
| --- | --- |
| Native controller | A traditional virtual gamepad |
| Mobile on foot | Walking and aiming with keyboard movement and mouse swipes |
| Mobile driving | Steering and driving buttons |
| Keyboard/mouse touch | Building your own keyboard-style layout |

Switch **Foot / Drive** yourself when needed. The app does not detect whether you entered a vehicle.

## Add or edit buttons

1. Open **Customize layout**.
2. Tap a control to edit it, or choose **Add**.
3. Set its label, binding, shape, size and position.
4. Press **Save**. Cancel discards the layout edits.

You can duplicate buttons, select several together, undo changes, group/lock positions, or zoom and pan. Move or hide the small tool panel when it covers your layout.

## Make aiming comfortable

Under **Mouse, cursor & movement**, adjust horizontal/vertical sensitivity and aiming speed. Try **Linear** mouse response first. Optional Precision/Acceleration, floating movement, left-handed zones, gyro and cursor settings are also available.

Use **Button fading** to reduce clutter or increase a button's **Touch area size** to make it easier to press. Transparent buttons can still accept touches.

## Save and share

Use **Manage profiles** to save or export a layout. Each mode can have eight pages; the PAGE tool switches between them. Profiles use XHYN V's own format, not Winlator's.

Use **Test inputs** to try the layout without starting the game.

[Profiles and backups](PROFILES_AND_BACKUPS.md) · [Toolbar and menu](INTERFACE.md)

<details>
<summary><strong>Technical details and full reference (optional)</strong></summary>

Open **Controls** in the launcher or **MENU** during gameplay. If an advanced tool is hidden, enable Advanced menus under **Settings → Menu appearance**.

## Choose an input mode

| Mode | Input used | Typical purpose |
| --- | --- | --- |
| Native controller | The runtime's existing analog/controller mapping | Traditional virtual gamepad |
| Mobile on foot | Keyboard movement and relative mouse swipes | Walking, camera look and aiming |
| Mobile driving | Keyboard/mouse bindings with a driving-oriented layout | Steering, pedals and vehicle actions |
| Keyboard/mouse touch | Configurable keyboard and mouse buttons | A custom keyboard-style layout |

The mobile modes use actual SDL keyboard/mouse input rather than simulating camera movement through the right controller stick. Each mode retains its own working layout. Switch **Foot / Drive** yourself; the overlay does not detect vehicles or other game state.

Mouse modes provide configurable movement bindings, with WASD-style movement in the default layouts. Adjust bindings to match this runtime's in-game key configuration. A touch preset is not a guarantee that every action has the desired binding in every game menu.

## Build a layout

Select **Customize layout**, choose an existing control or press **Add**, then adjust position, size, caption, visibility and bindings. Use **Save** to commit the editor transaction or **Cancel** to discard the layout edits.

| Editor feature | Behavior |
| --- | --- |
| Add / duplicate / remove | Up to **256 total controls per layout**, including built-in controls |
| Shapes | Circle, rounded rectangle, rectangle, pill and diamond |
| Style | Per-button label or icon, color, opacity, dimensions and visibility |
| Undo / redo | Most recent 60 edits |
| Multi-select | Move/resize selections, snap, align edges or centers |
| Groups | Name a selection and select its group again later; each control has one group name |
| Position locks | Prevent accidental geometry edits; bindings and styling remain editable |
| Zoom and pan | Buttons or pinch for 1×–3× editor zoom; Fit resets the view; Pan canvas moves the view |
| Compact tools | Drag the tool panel or hide it to expose the layout beneath it |

Zoom/pan affects the editor view only. It does not enlarge controls during gameplay. Explicit reset-all restores defaults, including locked geometry. Slider editing snaps in tens while preserving endpoints and untouched older values; free dragging is not restricted to steps of ten.

## Larger touch areas and fading

**Button style & actions → Touch area size** enlarges the hit area from 100% to 250% without enlarging the artwork. A direct hit inside another visible button takes priority over an expanded area. Expanded outlines appear in the editor; selection and dragging use the visible control footprint.

**Button fading** is optional. Choose idle opacity from 0–100%, active opacity from 10–100%, and a delay of 1–10 seconds. Held buttons remain active; idle fading uses a short transition. These opacity values multiply the overall control opacity. A fully transparent button can still accept input, and the toolbar remains accessible.

## Buttons, combinations and gestures

Added keyboard/mouse buttons support the following actions. Built-in native-controller controls keep their original controller actions; changing their appearance does not convert their input type.

| Action | Behavior |
| --- | --- |
| Normal hold | Holds its binding while pressed |
| Tap on / tap off | Toggles a binding until tapped again or input is canceled |
| Combination | Up to four distinct keys/mouse buttons held together; not a timed macro |
| Double tap | The second short tap starts within 300 ms of the first release; the second press holds the binding |
| Long press | Activates after 450 ms, then holds until release |
| Hold modifier layer | Temporarily changes newly pressed buttons to their configured alternate bindings |
| Directional swipe | Assign up/down/left/right combinations; the first qualifying direction remains active until release |

A tap on a directional-swipe button sends its primary binding briefly. An unassigned swipe does nothing. Changing a button's primary key in the main editor clears its normal combination, so check the action configuration afterward.

The modifier is one temporary alternate layer, independent of persistent pages. An already-held button keeps the exact binding it started with until release. Blank alternate bindings retain the normal action. Focus loss, canceled touches, menus and layout/page changes release synthetic input to avoid stuck keys.

## Mouse look, movement and aiming

Under **Mouse, cursor & movement**, adjust horizontal and vertical look sensitivity, the aiming multiplier and its aim binding, and vertical inversion. The available look-sensitivity range is 0.25×–8×.

**Mouse response curve** offers Linear, Precision and Acceleration with strength from 0–100%. Linear is the default. Precision reduces small/slow motion for fine adjustment; Acceleration increases faster swipes. The curve applies to touch mouse-look, while physical mouse and gyro retain their own paths.

Optional **Floating movement stick** starts from the first touch on empty movement-side space and stops on release. It applies to mouse modes and defaults Off. Buttons retain touch priority. Native-controller mode keeps its fixed analog mapping.

**Left-handed camera zones** exchange the empty-space movement and camera sides. They do not automatically mirror every saved button; use a mirrored layout or a left-handed starter as well.

Optional gyro can operate while aiming or during mouse look, depending on the selected mode and runtime state. It requires a suitable sensor and device testing. It does not replace the touch sensitivity controls.

## Cursor and shortcut wheel

The cursor supports **Off**, **Menus** and **Always**, plus size adjustment. It follows the runtime's SDL mouse state. Relative mouse-look may hide or capture a cursor according to that state; this is not a desktop-wide Android mouse pointer.

Enable **Shortcut wheel** to configure up to eight keyboard/mouse shortcuts. Hold **WHEEL**, drag toward a slot and release. Releasing in the center or outside the selection area cancels. A selection sends a short press. The wheel does not read the game's weapon inventory or automatically select a known in-game item.

## Pages, profiles and gallery

Each mode supports **eight control pages**. Add a page from the current layout, rename it and customize the copy. The **PAGE** tool appears when multiple pages exist. Pages keep their own button layouts, styles, visibility and bindings; movement/aim preferences are not independently configured per page.

Save up to **128 named control profiles** and use, update, rename, duplicate, delete, import or export them. A `.xhyn-controls.json` profile contains one mode and its pages plus applicable movement/appearance preferences. Import creates a saved snapshot; use it deliberately to replace the working layout. The file limit is 512 KiB, including its pages.

The **Profile gallery** previews saved layouts and offers two-finger, four-finger and left-handed keyboard/mouse starters. A starter opened from native-controller mode targets on-foot mode. Save your current layout before replacing it if you want both.

These profiles are XHYN V's format. Direct Winlator `.icp` import is not implemented. For all four modes and renderer/graphics settings in one export, use [Complete setup profiles](PROFILES_AND_BACKUPS.md).

## Test inputs without launching the game

**Controls → Test inputs** shows the saved layout, touch actions, hardware keys, mouse buttons and controller axes. A crosshair visualizes mouse/gyro movement. Orange overlap outlines are conservative hit-bound indications, not exact proof that two shapes collide everywhere.

Use **INFO** to collapse the panel, **Reset** to release inputs/clear movement, and **Done** to leave. The test does not launch the engine or send SDL/game input. Gyro visualization uses the saved sensitivity even when normal gameplay gyro is disabled; it stops when the test closes or loses focus.

## Physical controllers

The implementation provides remapping for ten standard digital buttons, independent stick dead zones and automatic touch-overlay hiding/restoration. D-pad and analog trigger behavior remain on the native input path. Dead zones change response near the stick center, not maximum turning speed.

For toolbar, Creator mode and closing gameplay to return home, see [Interface](INTERFACE.md).

</details>
