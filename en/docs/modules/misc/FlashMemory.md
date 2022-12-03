# Flash Memory
<img src="https://docs.retrogadgets.game/api/modules/FlashMemory.png" width="200" align="right">

Flash Memory persistently stores up to **250KiB** (at the largest variant) of table data. Data saved to Flash Memory is retained when the gadget is switched off or the game is closed.

## Properties

### Usage - `number` **[Read only]**
How much data is being used up in bytes. Never exceeds `Size`.

### Size - `number` **[Read only]**
The total storage in bytes. It varies per chip and remains constant. 
The sizes, in order from the shortest to the longest chip are:

- 4  KiB
- 32 KiB
- 250 KiB (256 KB)

## Methods

### Save(table `{}`) `boolean`
**⚠️ The functionality of this method has not yet been tested.**

Saves table data to memory, **overwriting the previous memory on the chip.** Returns `false` if the remaining memory is insufficient to fit the new data.

```lua
local memory:FlashMemory = gdt.FlashMemory0

memory:Save({"foo", "bar", "baz"})
log( memory:Load()[1] ) -- "foo"
```

### Load() `{}`

Returns everything that is currently loaded in the chip. This is a new copy of the data, meaning modifications to it will not be saved. For example, `memory:Load()[3] = "baz"` would not work.
