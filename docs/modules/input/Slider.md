# Slider

<img src="https://docs.retrogadgets.game/api/modules/Slider.png" width="200" align="right">

The slider is a 1D draggable input device that can be oriented in several directions. It is similar to a [Knob](./Knob.md) in interaction.


## Properties

### Value - `number`
The positional value of the slider, ranging from 0 to 100.

### IsMoving - `boolean` **[Read only]**
`true` if the user currently is holding the Slider with the mouse. This should not be used to detect changes, as it is not set when a value is changed with the scrollwheel. This can instead be used to, for example, avoid trying to set the Slider to a specific value while it is still being interacted with.