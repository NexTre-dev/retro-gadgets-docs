# Screen

<img src="https://docs.retrogadgets.game/api/modules/Screen.png" width="200" align="right">

The Screen module displays the visuals of a [VideoChip](../misc/VideoChip.md). **Screens can be seamlessly placed next to each other** and assigned to the same VideoChip to make larger screens. **Screen composites do not need to be square.**

## Properties

### VideoChip - `VideoChip`
The VideoChip this screen belongs to. Multiple screens can be assigned to the same VideoChip to make a larger screen. _This can be set dynamically, but is usually set with the multitool inspector._

### Offset - `vec2`
The difference between this screen's top-left corner and the top-left corner of the VideoChip canvas.
### Width - `number`
### Height - `number`