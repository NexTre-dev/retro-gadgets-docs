# RealityChip

<img src="https://docs.retrogadgets.game/api/modules/RealityChip.png" width="200" align="right">

The Reality Chip provides values from the real state of the device, and may do more in the future.

It is curiously labeled "RB", presumably because it is internally called the "Reality Bridge".

## Properties
All current properties refresh every second.

### Cpu.TotalUsage - `number` **[Read only]**
The total CPU usage of the system 0-100. This value is usually not what you would see in Task Manager, as task manager uses a different metric that only it has access to. This may also be a bug with windows.

### Cpu.CoresUsage - `{number}` **[Read only]**
An array that contains the cpu usage of each logical CPU core 0-100.

### Ram.Available - `number` **[Read only]**
Available RAM expressed in MB. This is not the total size, this is remaining memory.

### Ram.Used - `number` **[Read only]**
Used RAM expressed in MB.

You can combine the two RAM metrics into percentage.
```lua
local reality:RealityChip = gdt.RealityChip0

function update()
	local percent = reality.Ram.Used/(reality.Ram.Available + reality.Ram.Used)
	log(tostring(percent*100)) -- 70.83448438808485 (This will vary)
end
```

### Network.TotalSent - `number` **[Read only]**
Total sent by network interfaces expressed in Mbps.

### Network.TotalReceived - `number` **[Read only]**
Total received from network interfaces expressed in Mbps