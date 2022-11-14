# DPad

<img src="https://docs.retrogadgets.game/api/modules/DPad.png" width="200" align="right">

DPads are similar to [Sticks](Stick.md), except that they can only output one extreme at a time.

## Properties

### X - `number` **[Read only]**
-100 when the DPad is being pressed to the left, 100 when being pressed to the right. 0 otherwise.

### Y - `number` **[Read only]**
100 when the DPad is being pressed upwards, -100 when being pressed downwards. 0 otherwise.

## Input sources
Properties for use with the [GamepadChip](../misc/GamepadChip.md) or [KeyboardChip](../misc/KeyboardChip.md).

### InputSourceX - `InputSource`
### InputSourceY - `InputSource`