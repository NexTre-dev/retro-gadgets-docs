# CPU
<img src="https://docs.retrogadgets.game/api/modules/CPU.png" width="200" align="right">

The CPU is responsible for most gadget interactivity and runs Lua asset files. CPUs (currently) do not need to be connected to or on the board of any part of the gadget they interact with. They can currently load a single Lua asset.
## Properties

### Source - `Code` **[Read only]**
Source defines what "file" the CPU will run, and is typically set with the multitool inspector. You can set it to any Lua asset.

### Time - `number` **[Read only]**
The time since the gadget is turned on, expressed in seconds.
```lua
local cpu:CPU = gdt.CPU0
function update()
	log(tostring(cpu.Time)) --Example: 0.521000027656552
end
```

### DeltaTime - `number` **[Read only]**
The time elapsed since the last tick, expressed in seconds. Essentially, this is the difference (or *delta*) between the last `update()` call. This is useful to update animations and timers without relying on remembering `Time`.
```lua
local cpu:CPU = gdt.CPU0
function update()
	log(tostring(cpu.DeltaTime)) --At 60/60 tps, this is roughly 0.01666 repeating. An example real value is: 0.01600000075995922
end
```

