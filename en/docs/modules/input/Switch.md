# Switch

<img src="https://docs.retrogadgets.game/api/modules/Switch.png" width="200" align="right">

Switches are boolean inputs which toggle state when clicked. They come in many shapes and sizes, and most are rotatable.


## Properties

### State - `boolean`
The state of the switch. Toggles between `true` and `false` every time the switch is clicked. The initial state can be set with the multitool inspector.


## Event - `SwitchStateChangeEvent`
The event emitted as part of the [CPU](../misc/CPU.md) event system.

Sent when the value is changed.

### State - `boolean`


## Hardware
These properties can be set with the multitool inspector, but cannot be set in software.

### Symbol - `Symbol` *(hardware)* ⚠️ Only available on a single variant.
A symbol to display on the switch. Symbols can be painted with the paint tool to be a different color than the background. **Only the side-mounded cassette toggle button has a symbol slot.**