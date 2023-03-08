# VideoChip

<img src="https://docs.retrogadgets.game/api/modules/VideoChip.png" width="200" align="right">

The Video Chip represents the canvas of its connected screens, and is used to draw to them.

## Properties

### Mode - `VideoChipMode`
The buffer mode, which can either be `SingleBuffer` or `DoubleBuffer`. 

A single buffer allows you to work on a single screen buffer that is always changing as new commands are sent. If you were to draw a circle, for example, it would be sent straight to the buffer and get displayed immediately. However, with DoubleBuffer, you are dealing with two different video buffers that alternate regularly. Every frame, the buffer that you are editing alternates; you could be editing buffer A, while buffer B is being projected to the screens the chip is connected to. The next frame, the changes in buffer A would be presented to the screen(s) while any other changes for that frame would be made to buffer B. Generally, this won't make a difference in the way the video is displayed, but if you are experiencing flickering, lag, or stuttering while using SingleBuffer, you should switch to DoubleBuffer.

### Height - `number` **[Read only]**
Height in pixels of the rendering buffer. The area takes in account all the displays connected to this VideoChip.

### Width - `number` **[Read only]**
WIdth in pixels of the rendering buffer. The area takes in account all the displays connected to this VideoChip.

## Methods

### Clear(color `color`)
Clears all the render area with the specified **color**. Usually used before drawing each frame.
```lua
local video:VideoChip = gdt.VideoChip0

function update()
	video:Clear(color.white)
	-- <...>
end
```

### SetPixel(position `vec2`, color `color`)
Sets the pixel at the specified position to the specified **color**.

### SetPixelData(PixelData `PixelData`)
⚠️ **This feature is new and undocumented as of Retro Gadgets 0.1.5, things might change in the future.**  
Draws PixelData to the screen. **Provided PixelData must to be the same size as the VideoChip.**


<img src="../../../assets/docs/VideoChip/PixelGrid.png" width="200" align="right">


### DrawPointGrid(gridOffset `vec2`, dotsDistance `number`, color `color`)
Draws a dotted grid on the **entire display area**, with an offset. The dotsDistance parameter express the distance in pixels, on both axis, between dots. This is a strange function, but can be uses for backgrounds.
```lua
local video:VideoChip = gdt.VideoChip0

function update()
	video:Clear(color.blue)
	video:DrawPointGrid(vec2(0,3), 3, color.white)
end
```

### DrawLine(start `vec2`, end `vec2`, color `color`)
Draws a line from position start to position end, using the specified color.

### DrawCircle(position `vec2`, radius `number`, color `color`)
Draws an empty circle at the specified position, with the specified radius, in the specified color.

### FillCircle(position `vec2`, radius `number`, color `color`)
Draws a filled circle at the specified position, with the specified radius, in the specified color.

### DrawRect(position1 `vec2`, position2 `vec2`, color `color`)
Draws an empty rect from position1 to position2, in the specified color.

### FillRect(position1 `vec2`, position2 `vec2`, color `color`)
Draws a filled rect from position1 to position2, in the specified color.

### DrawTriangle(position1 `vec2`, position2 `vec2`, position3 `vec2`, color `color`)
Draws an empty triangle with vertices in position1, position2 and position3, in the specified color.

### FillTriangle(position1 `vec2`, position2 `vec2`, position3 `vec2`, color `color`)
Draws a filled triangle with vertices in position1, position2 and position3, in the specified color.

<img src="../../../assets/docs/VideoChip/ExampleImageDrawing.png" width="200" align="right">

### DrawSprite(position `vec2`, spriteSheet `SpriteSheet`, spriteX `number`, spriteY `number`, tintColor `color`, backgroundColor `color`)
Draws a specific sprite frame from the spriteSheet. **Position** is for the position on the screen. **SpriteSheet** is a `SpriteSheet` loaded from assets. **SpriteX** and **Y** determine the offset for which sprite to draw, based on the zoom grid in the editor **(not pixels)**. **TintColor** allows you to multiply the sprite color (set to `color.white` to draw the sprite as-is). **BackgroundColor** can be set to transparent (`color.clear`) to keep transparency.
```lua
-- Assets
local spriteSheet:SpriteSheet = gdt.ROM.User.SpriteSheets.ExampleImageAsset

-- Hardware
local video:VideoChip = gdt.VideoChip0

-- Update
function update()
	video:Clear(color.white)
	video:DrawSprite(vec2(5,5), spriteSheet, 0, 0, color.white, color.clear)
end
```
<img src="../../../assets/docs/VideoChip/ExampleImageAsset.png" style="max-width: 400px">

### DrawCustomSprite(position `vec2`, spriteSheet `SpriteSheet`, spriteOffset `vec2`, spriteSize `vec2`, tintColor `color`, backgroundColor `color`)
⚠️ **This feature is new, as of Retro Gadgets 0.1.3, and not fully tested yet.**  
Draws **a portion** of the spritesheet, `SpriteSheet` (defined by **spriteOffset** and **spriteSize**), without taking the standard grid into account, with **spriteX** and **spriteY** being replaced with **spriteOffset** and **spriteSize**.

<img src="../../../assets/docs/VideoChip/SpriteFont.png" width="200" align="right">

### DrawText(position `vec2`, fontSprite `SpriteSheet`, text `string`, textColor `color`, backgroundColor `color`)
Writes **text** to the canvas, using **fontSprite** as the font to be displayed. **fontSprite** is a special kind of SpriteSheet representing a textual font that can be created inside of the sprite editor.
```lua
-- Assets
local spriteFont = gdt.ROM.System.SpriteSheets.StandardFont

-- Hardware
local video:VideoChip = gdt.VideoChip0

-- Update
function update()
	video:Clear(color.black)
	video:DrawText(vec2(5,5), spriteFont, "Hello!", color.yellow, color.clear)
end
```


### RasterSprite(position1 `vec2`, position2 `vec2`, position3 `vec2`, position4 `vec2`, spriteSheet `SpriteSheet`, spriteX `number`, spriteY `number`, tintColor `color`, backgroundColor `color` )
Draws a specific sprite frame from the spriteSheet mapping it on a quad identified by position1, position2, position3, and position4. The locations of `position1`, `position2`, `position3` and `position4` are the top-left, top-right, bottom-right and bottom-left respectively. 

### RasterCustomSprite(position1 `vec2`, position2 `vec2`, position3 `vec2`, position4 `vec2`, spriteSheet `SpriteSheet`, spriteOffset `vec2`, spriteSize `vec2`, tintColor `color`, backgroundColor `color`)
⚠️ **This feature is new, as of Retro Gadgets 0.1.3, and not fully tested yet.**  
Draws a portion of the spritesheet, `SpriteSheet` (defined by `spriteOffset` and `spriteSize`), without taking the standard grid into account, onto a quad defined by `position1`, `position2`, `position3`, and `position4`. The locations of `position1`, `position2`, `position3` and `position4` are the top-left, top-right, bottom-right and bottom-left respectively, as with `RasterSprite`.

### DrawRenderBuffer(position `vec2`, renderBuffer `RenderBuffer`, width `number`, height `number`)
Draws a render buffer (supposedly coming from **Webcam** component) at the desired position, width and height.


# `PixelData`
⚠️ **This feature is new and undocumented as of Retro Gadgets 0.1.5, things might change in the future.**

PixelData is a buffer you can draw to, similar to the VideoChip itself.  
As PixelData lives entirely in Lua, draw calls on it (such as `SetPixel`) are much faster the same call on the VideoChip. You can later draw the entire PixelData to a VideoChip at once.

## Properties

### Height - `number` **[Read only]**
<!-- Making it readonly because when you try to write to the variable, it demands `userdata` instead of number -->
Height of the PixelData.

### Width - `number` **[Read only]**
<!-- Same as above-->
Width of the PixelData.

## Constructors

### new(width `number`, height `number`, color `color`) `PixelData`
Creates a new instance of PixelData. `color` defines the color every pixel will be when initialized.

## Methods

### Clear(color `color`)
Clears the PixelData to a specified color.

### SetPixel(x `number`, y `number`, color `color`)
Sets the specified pixel to the color provided.

### GetPixel(x `number`, y `number`) `color`
Returns the color of a pixel on the `x` and `y` axis specified.

## Example usage
<img src="./../../../assets/docs/VideoChip/PixelData.gif" width="250" align="right">

```lua
local vc = gdt.VideoChip0
local pixelData = PixelData.new(128, 128, color.clear) -- Has to be the same size as the VideoChip.
local z = 0

function update()
	z += 0.01
	for y = 1, 128 do
 		for x = 1, 128 do
			-- Get perlin noise value
			local noise = math.noise((x + 0.5) / 16, (y + 0.5) / 16, z)
			-- Convert to color
			local color_value = math.floor((noise + 1) / 2 * 255)
			local col = Color(color_value, color_value, color_value)
			pixelData:SetPixel(x, y, col)
		end
	end
	vc:SetPixelData(pixelData)
end
```



## Remarks

### Related types

#### `vec2`
vec2 is a two dimensional vector, usually used to point to screen coordinates. Basically a single value that represents two numbers. You can make a new vec2 easily, and then access its properties with `x` and `y`.
```lua
local pos:vec2 = vec2(20,10)
print(pos.X) -- 20
print(pos.Y) -- 10
```
`vec2(0,0)` is the top left corner of the canvas.

There is also vec3, but it is not usually used for screens. You may use it for organization.

#### `color`
`color` represents a color, and is used for LEDs or for drawing to the screen. You may construct a color in a few ways.
```lua
Color(r, g, b) -- Values 0-255
ColorRGBA(r, g, b, a) -- Alpha is also 0-255, 0 is transparent
ColorHSV(h, s, v) -- Hue is 0-360, the other values are 0-100
```
There are a few built in colors, such as `color.blue` or `color.black`. In the future, these will be listed in a dedicated page for `color`.

You may access `R`, `G`, `B`, and `A` on a `color`.

#### `SpriteSheet`
See `DrawSprite(...)`

### Example project
The built-in **RasterBoy** gadget is great to get a better understanding of how graphics work. 
