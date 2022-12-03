# ROM
<img src="https://docs.retrogadgets.game/api/modules/ROM.png" width="200" align="right">

A ROM is used to access user and system assets. It contains the assets placed in a gadget from the assets list, as well as built-in assets.

It is primarily used to load images and audio for use with the [VideoChip](./VideoChip.md) and [AudioChip](./AudioChip.md).

Only one ROM can be in a gadget. Expectedly, it is *read only*.

## Usage
Assets in ROM are accessed by specifying the **namespace** followed by the **type of data**, (plural) and return `{string, (data type)}`. For example:

```lua
---- All spritesheets
gdt.ROM.User.SpriteSheets
---- Get spritesheet named "font"
gdt.ROM.User.SpriteSheets.font
-- OR
gdt.ROM.User.SpriteSheets["font"]
```

The **User** namespace corresponds to files imported into the gadget. These are the files that appear in the **asset list**:

![The asset list](../../../assets/docs/ROM/assets.png)

The **System** namespace corresponds to built-in files, such as the default font.

There are four data types you can query the ROM for:
- `Assets`: Every asset loaded regardless of type.
- `SpriteSheets`: Images, for use with the [VideoChip](./VideoChip.md).
- `Codes`: Lua assets, for use with the [CPU](./CPU.md).
- `AudioSamples`: Sound files, for use with the [AudioChip](./AudioChip.md).


<br>

-------------------------------------------------
<small>💡 ROM stands for Read Only Memory.</small>