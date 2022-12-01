# Flash Memory
<img src="https://docs.retrogadgets.game/api/modules/FlashMemory.png" width="200" align="right">

Flash memory is a chip that stores up to **250KiB** of table data. It can be used to save constant data as its memory remains even after powering off.

## Properties

### Usage - `number` **[Read only]**
How much data is being used up in bytes. Never exceeds `Size`.

### Size - `number` **[Read only]**
The total storage in bytes. It varies per chip and remains constant. In order, from the shortest chip to the lengthiest chip, the sizes are as follows:

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

Returns everything that is currently loaded in the chip. This cannot be used to write to the memory directory, meaning something like `memory:Load()[3] = "baz"` would not work.
