# LedButton

<img src="https://docs.retrogadgets.game/api/modules/LedButton.png" width="200" align="right">

The most abundant input component. Almost all buttons are actually LedButtons, for versatility. They come in many shapes and sizes, none of which are the image used in this article. They are simple on/off inputs, typically held with the mouse, which double as output devices for a single color value.

Light cast by LedButtons is physical and will light unlit LedButtons and other components.

## Properties

### ButtonState - `boolean` **[Read only]**
`true` if the button is currently held down, `false` otherwise.

### ButtonDown - `boolean` **[Read only]**
`true` for the first tick the button starts being held. Useful for performing actions only one time per hold.

### ButtonUp - `boolean` **[Read only]**
`true` for the first tick the button stops being held. 

### LedState - `boolean`
Whether the Led should be on. If `true`, the button emits light of `LedColor`. If `false`, the button does not emit light. The initial value can be set with the multitool inspector.

Not emitting light is similar to trying to emit light with the color black.

### LedColor - `color`
The color of the Led, which will be emitted when `LedState` is `true`. This can be set programmatically at any time. The initial value can be set with the multitool inspector.


## Input sources
Properties for use with the [GamepadChip](../misc/GamepadChip.md) or [KeyboardChip](../misc/KeyboardChip.md).

### InputSource - `InputSource`

## Event - `LedButtonEvent`
The event emitted as part of the [CPU](../misc/CPU.md) event system.

Sent when the button is pressed or released.

### ButtonDown - `boolean`
True if this event is for a button beginning to be held.
### ButtonUp - `boolean`
True if this event is for when a button stops being held.

## Hardware
These properties can be set with the multitool inspector, but cannot be set in software.

### Symbol - `Symbol` *(hardware)* ⚠️ Not available in all variants.
A symbol to display on the button. Symbols can be painted with the paint tool to be a different color than the background. **Smaller LedButtons do not have this property.**