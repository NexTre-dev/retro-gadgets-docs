# PowerButton

<img src="https://docs.retrogadgets.game/api/modules/PowerButton.png" width="200" align="right">

The Power Button is the main entrypoint to your gadget. Pressing it toggles "play mode" on and off. During play mode CPUs run and the gadget cannot be edited. Pressing it again will end play mode and return the gadget to its initial state.

There are three Power Buttons, one of which is square and goes past the edge of a gadget. You can remove the power button (unlike the multitool connector), but you can only have one.

## Properties

### ButtonState - `boolean` **[Read only]**
This is always `false`.
```lua
local button:PowerButton = gdt.PowerButton0
function update()
	log(tostring(button.ButtonState)) --false. always false.
end
```