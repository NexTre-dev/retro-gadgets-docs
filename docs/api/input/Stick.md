# Stick

<img src="https://docs.retrogadgets.game/api/modules/Stick.png" width="200" align="right">

**The Stick device's API is exposed as `AnalogStick`.**

Sticks are 2D input devices which report offset when dragged with a mouse, and reset to origin when not being interacted with. The maximum range of a stick is a circular shape, so at non cardinal angles the components will not be at their extremes, but the magnitude of their resultant vector will be 100.

## Properties

### X - `number` **[Read only]**
The position of the stick along the X axis, ranging from -100 to 100.

### Y - `number` **[Read only]**
The position of the stick along the Y axis, ranging from -100 to 100.

## Input sources
Properties for use with the [GamepadChip](../misc/GamepadChip.md) or [KeyboardChip](../misc/KeyboardChip.md).

### InputSourceX - `InputSource`
### InputSourceY - `InputSource`