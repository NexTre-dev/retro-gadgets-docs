# ROM
<img src="https://docs.retrogadgets.game/api/modules/ROM.png" width="200" align="right">

ROM is a chip that is used to access user and system data. You will use it to load SpriteSheets, AudioSamples, and many other types of data. Its contents are loaded from the gadget's inner files.

Only one ROM can be in a gadget. Expectedly, it is *read only*.

## Properties
Assets in ROM are accessed by specifying the **namespace**, followed by the **type of data** (plural) and return `{string, (data type)}`. For example:

```lua
---- All spritesheets
gdt.ROM.User.SpriteSheets
---- Get spritesheet named "font"
gdt.ROM.User.SpriteSheets.font
-- OR
gdt.ROM.User.SpriteSheets["font"]
```

The **User** namespace corresponds to files imported into the gadget. The **System** namespace corresponds to built-in files, such as the default font.

The datatype can be any of the following:

- **Assets** : Every asset loaded regardless of type.
- **SpriteSheets** : Images.
- **Codes** : Lua assets.
- **AudioSamples** : Sound files.