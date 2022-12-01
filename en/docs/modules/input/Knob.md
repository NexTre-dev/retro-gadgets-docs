# Knob

<img src="https://docs.retrogadgets.game/api/modules/Knob.png" width="200" align="right">

Knobs are 1D input devices which angle from pointing all the way to the left (a value of -100) to pointing all the way to the right (a value of 100). Knobs are adjusted by dragging the mouse left and right. Currently, Knobs act like [sliders](Slider.md), and only represent a 1D axis, **they cannot point downward**.

## Properties

### Value - `number` 
The position of the knob, ranging from -100 (pointing fully left), between 0 (pointing fully up), to 100 (pointing fully right). You can set this from software to programmatically move the Knob. For realism, it is recommended you animate any changes to the Knob, as otherwise it will simply snap to new values.

### IsMoving - `boolean` **[Read only]**
`true` if the user currently is holding the Knob with the mouse. This should not be used to detect changes, as it is not set when a value is changed with the scrollwheel. This can instead be used to, for example, avoid trying to set the knob to a specific value while it is still being interacted with.

## Event - `KnobValueChangeEvent`
The event emitted as part of the [CPU](../misc/CPU.md) event system.

Sent when the value is changed.

### Value - `number`