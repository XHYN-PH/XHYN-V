# Controls, layouts and profiles

[Back to the project](../README.md)

## Choose a mode

Open **Controls** in the launcher. In-game options are also available through **MENU**.

| Mode | Input behavior | Typical use |
| --- | --- | --- |
| Native controller | Existing analog/controller mapping | Traditional virtual gamepad |
| Mobile on foot | Keyboard/mouse bindings with touch camera look | Walking, aiming and general play |
| Mobile driving | Keyboard/mouse bindings with touch camera look | Vehicle-oriented touch layout |
| Keyboard/mouse touch | Keyboard/mouse controls with configurable buttons | A customized keyboard-style layout |

Switch modes and pages yourself; these presets do not detect whether the character has entered a vehicle. Each mode has its own working layout.

## Edit a layout

Open **Customize layout**. Use **Add** to create a button, then set its caption, keyboard/mouse binding and hold/toggle behavior. Buttons can use circle, rounded rectangle, rectangle, pill or diamond shapes, with adjustable dimensions, size and opacity.

Drag the compact tools by their handle or hide them to expose more of the canvas. Save commits the layout. Use Cancel to abandon the editor transaction.

The editor supports:

- Add, duplicate and remove, up to **256 total controls per layout**, including built-in controls.
- Undo/redo covering the most recent 60 edits.
- Multi-select, group movement/resizing, snap and edge/center alignment.
- Independent visibility, position, appearance and bindings.

Sliders snap in tens and keep their endpoints. Existing values between those steps stay unchanged until edited. Dragging a button is not restricted to increments of ten.

## Mouse look, floating movement and gyro

Under **Mouse, cursor & movement**, adjust horizontal and vertical sensitivity separately. Aiming sensitivity is a multiplier with a configurable aim binding; vertical inversion is available. Gyro can be Off, active while aiming, or active during mouse look when the device has a suitable sensor.

Optional **Floating movement stick** starts movement from the first touch on empty space on the movement side, then stops on release. It defaults Off and applies to mouse modes. Buttons retain touch priority. The native controller mode keeps its fixed analog mapping.

**Left-handed camera zones** swap empty-space movement and camera sides. Pair this option with a mirrored layout or the left-handed starter. It does not silently move every saved button.

The optional cursor supports **Off**, **Menus** and **Always**, with a size setting. Its display follows the runtime's mouse state; it does not turn the Android launcher into a desktop environment.

## Shortcut wheel

Enable the wheel under **Mouse, cursor & movement → Shortcut wheel** or **MENU → Shortcut wheel**. It defaults Off.

Configure up to eight keyboard or mouse shortcuts. Hold **WHEEL**, drag toward a slot and release. Release in the center or outside the selection area to cancel. A selected shortcut sends a short press of approximately 80 ms.

This is a configurable shortcut wheel. It does not read game weapon state or execute a macro sequence. Focus loss, menu transitions and page changes cancel synthetic touch input.

## Pages

Open **Control pages** to add, select, rename or delete pages. Each mode supports up to eight pages.

**Add page from current layout** preserves the previous layout as Page 1 when needed, duplicates it and switches to the new copy. Customize and save that copy. The **PAGE** chip appears when a mode has multiple pages and cycles between them during play.

Pages store their own button layout, captions, bindings, shapes and visibility. Movement/aiming preferences remain shared at the mode/app level. Deleting the last page entry retains its working layout.

## Profiles and gallery

Save a named profile before trying another layout. Profiles can be used, updated, renamed, duplicated, deleted, imported and exported through Android's file picker.

| Limit | Value |
| --- | --- |
| Saved profiles | Up to 128 |
| File format | `.xhyn-controls.json`, version 1 with optional newer fields |
| Maximum profile file | 512 KiB, including all pages |
| Pages per mode | Up to 8 |
| Controls per layout | Up to 256 |


Imports create a saved snapshot. Apply it deliberately to replace the working layout/pages. Malformed and oversized imports are rejected without replacing the current layout. Older version-1 profiles load with new optional features disabled when fields are absent.

The **Profile gallery** previews saved profiles and offers two-finger, four-finger and left-handed starters. Starters use keyboard/mouse input; opening a starter from native-controller mode targets the on-foot mode. Save your current profile before applying a starter if you want to keep both.


## Physical controllers (NOT TESTED)

Optional physical-controller settings provide remapping for ten standard digital buttons, independent left/right stick dead zones and automatic hiding/restoring of touch controls.

Analog triggers and D-pad behavior stay on the native input path. Nonstandard controllers may need further device testing. Dead-zone settings change the response around the center; they do not increase a stick's maximum camera speed.
