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
	log(tostring(cpu.Time)) --Example: 0.521000027656552
end
```

### DeltaTime - `number` **[Read only]**

The time elapsed since the last tick, expressed in seconds. Essentially, this is the difference (or _delta_) between the last `update()` call. This is useful to update animations and timers without relying on remembering `Time`, as well as interpolate values smoothly (see "Creating consistent interpolation").

```lua
local cpu:CPU = gdt.CPU0
function update()
	log(tostring(cpu.DeltaTime)) --At 60/60 tps, this is roughly 0.01666 repeating.
	--An example real value is: 0.01600000075995922
end
```

## Remarks

### Creating consistent interpolation

📝 This section is written in a casual tone, and should be re-worded.

<!-- not sure if retro gadgets handles deltatime already? remove this section if that's the case -->

Making sure the movement of something stays consistent is incredibly important when doing anything relating to such. If you are moving a square at 60 FPS, you want to move it the same distance in 5 FPS as well. However, in most general cases, this does not happen. If you transition from a value of 0 to 100, incrementing by 1 each frame:
```lua
local myNumber:number = 0

-- update() is called each frame
function update()
  myNumber = myNumber + 1
end
```
This would work well in most cases, if the framerate was consistent. However, there's a _glaring flaw_. If the program is running at 60FPS, `myNum` would be at 100 within around 1.7 seconds. If it was running at 30FPS, it would be at 100 within 3 seconds. If it was at 5FPS, it would be at 100 within 20 seconds!! How can we somehow sync up the incrementation so that it is consistent no matter what your frames-per-second is? The answer is incredibly simple, and is applied everywhere when dealing with movement: multiply the incrementation value by the DeltaTime.
```lua
local myNumber:number = 0
local cpu:CPU = gdt.CPU0 -- Replace this with your CPU

function update()
	myNumber = myNumber + (1 * cpu.DeltaTime)
end
```
Now, no matter what our framerate is, it will still take the same amount of time to reach 100 on 5FPS as it would on 60FPS. If framerate is a concern and you want to interpolate between two values smoothly, from things like movement to animations, it would be a good idea to use DeltaTime to control it.
