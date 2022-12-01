# CPU

<img src="https://docs.retrogadgets.game/api/modules/CPU.png" width="200" align="right">

The CPU is responsible for most gadget interactivity and runs Lua asset files. CPUs (currently) do not need to be connected to or on the board of any part of the gadget they interact with. They can currently load a single Lua asset.

## Properties

### Source - `Code` **[Read only]**
Source defines what "file" the CPU will run, and is typically set with the multitool inspector. You can set it to any Lua asset. Upon creating a CPU, a code file is created automatically titled CPU0.lua, and it is automatically connected to said CPU.

### Time - `number` **[Read only]**
The time since the gadget is turned on, expressed in seconds.

```lua
local cpu:CPU = gdt.CPU0
function update()
	log(tostring(cpu.Time)) -- 0.521000027656552 (This will vary)
end
```

### DeltaTime - `number` **[Read only]**
The time elapsed since the last tick, expressed in seconds. Essentially, this is the difference (or _delta_) between the last `update()` call. This is useful to update animations and timers without relying on remembering `Time`, as well as interpolate values smoothly (see "Creating consistent interpolation").

```lua
local cpu:CPU = gdt.CPU0
function update()
	log(tostring(cpu.DeltaTime)) -- At 60/60 tps, this is roughly 0.01666 repeating.
	-- An example real value is: 0.01600000075995922
end
```

### EventChannels - `{module}` **[Read only]**
Events are a way to run a function when notified by a module, instead of checking values in a loop in `function update()`. This can grant major performance benefits, and is the only way to use some modules.

Each module set in the `EventChannels` array will run the corresponding `eventChannel` function on this CPU when it triggers its event.  
For example, when a module set in `EventChannels[1]` triggers, it will run the `eventChannel1` function.

Each `eventFunction` should have two parameters. The first one is the module that triggered the event (e.g. for `eventChannel1` this would be `EventChannels[1]`). The second paramater is the `Event` itself, provided by the module.

The length of `EventChannels`, and thus the amount of unique modules you can listen to events from, is determined by the CPU size.
|   Size | Channels |
|-------:|:---------|
|  Small | 4        |
| Medium | 16       |
|  Large | 64       |

```lua
-- Example button event, assuming EventChannels[1] = gdt.LedButton0
function eventChannel1(sender:LedButton, arg:LedButtonEvent)
	log(tostring(arg.ButtonDown))
end
```

## Remarks

### Creating consistent interpolation

<!-- not sure if retro gadgets handles deltatime already? remove this section if that's the case -->

Making sure the movement of something stays consistent is incredibly important when doing anything relating to such. If you are moving a square at 60 FPS, you want to move it the same distance in 5 FPS as well. However, in most general cases, this does not happen. If you transition from a value of 0 to 100, incrementing by 1 each frame:
```lua
local myNumber:number = 0

-- update() is called each frame
function update()
  myNumber = myNumber + 1
end
```

This would work well in most cases, as long as the framerate is consistent. However, in the case that it isn't, the time it would take for `myNumber` to reach 100 would vary between different framerates. This can present issues in scenarios where you need the incrementation of a variable to be consistent (such as the movement of a character), so it's important to find a way to sync it to the FPS. This practice is applied in most circumstances when it comes to data interpolation that must be consistent, and only involves a few extra characters:

```lua
local myNumber:number = 0
local cpu:CPU = gdt.CPU0 -- Replace this with your CPU

function update()
	myNumber = myNumber + (1 * cpu.DeltaTime)
end
```

Because we multiplied the incrementation value by the DeltaTime, no matter the framerate, in the long run, it will still take the same amount of time for `myNumber` to reach 100.
