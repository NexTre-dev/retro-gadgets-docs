# PowerButton

<img src="https://docs.retrogadgets.game/api/modules/PowerButton.png" width="200" align="right">

The Power Button is the main entrypoint to your gadget. Pressing it toggles "play mode" on and off. During play mode CPUs run and the gadget cannot be edited. Pressing it again will end play mode and return the gadget to its initial state.

The tabs at the end of the power buttons cannot collide with other components and are used to both differentiate between the three types, as well as aid in moving them with the mouse. The different power buttons are:

- Square with a red tab that must be placed on the edge of a straight surface.
- Round with a smaller red tab containing a single ridge. It is the exact same as the red one, except that it is around half as short and lies on the ridges of the gadget.
- Round with a blue tab that is similar to default, however it is able to be placed anywhere that is not an edge, as long as it does not collide with any components.

You can remove the power button (unlike the multitool connector), but you can only have one.

## Properties

### ButtonState - `boolean` **[Read only]**
This is always `false`.
```lua
local button:PowerButton = gdt.PowerButton0
function update()
	log(tostring(button.ButtonState)) -- "false", always
end
```