# Global Methods
The following is a list of methods that can be called anywhere in your program.

## Assets

### GetSpriteSheet(name `string`) `SpriteSheet`
Provides a SpriteSheet from the MultiTool asset list.

### GetPalette(name `string`) `Palette`
**❌ This method is deprecated.**

**⚠️ The functionality of this method has not yet been tested.**

### GetAudioSample(name `string`) `AudioSample`
Provides an AudioSample from the MuliTool asset list. Supports mp3 and wav.

### GetCode(name `string`) `Code`
Provides a Lua file from the MuliTool asset list, which can be dynamically assigned to a CPU.

## Color

### Color(r `number`, g `number`, b `number`) `color`
Composes and returns a color object out of RGB values. The three parameters should be in the range of 0 - 255.

### ColorRGBA(r `number`, g `number`, b `number`, a `number`) `color`
Composes and returns a color object out of RGB values, along with an alpha channel. The RGB parameters should be in the range of 0 - 255 and the alpha parameter should be in the range of 0 - 1, where 0 is transparent and 1 is opaque.

### ColorHSV(h `number`, s `number`, v `number`) `color`
Composes and returns a color object out of HSV values. The ranges for the hue should be 0 - 360 and the range for the saturation and value should be  0 - 100.

## Console

### log(message `string`)
Prints a message to the MultiTool console. Unlike Lua's builtin `print` function which accepts all data types, this method requires you to use a single string. To use other data types, use `tostring()`.

### logWarning(message `string`)
Prints yellow text to the MultiTool console indicating some sort of precaution or advisement; a warning.

### logError(message `string`)
Prints red text to the MultiTool console indicating some sort of error or exception. This does not stop the program like other errors.

### write(text `string`)
Prints a message to the MultiTool console without adding a new line. Functions identically to `log()` otherwise.

### writeln(text `string`)
Does the same thing as `write()`, except adds a new line to the end of the text. Functions identically to `log()`.


### setFgColor(colorId `number`)
Doesn't seem to do anything, but possibly sets the text color in the MultiTool console.

### setBgColor(colorId `number`)
Doesn't seem to do anything, but possibly sets the background color in the MultiTool console.

### resetFgColor()
Doesn't seem to do anything, but possibly resets the text color in the MultiTool console.

### resetBgColor()
Doesn't seem to do anything, but possibly resets the background color in the MultiTool console.

### resetColors()
Doesn't seem to do anything, but possibly resets the colors in the MultiTool console.

### setCursorPos(column `number`, line `number`)
Sets the cursor position in the MultiTool console, where new text is added.

<img src="../../assets/docs/Global/CursorPos.png" width="300" />

### setCursorX(column `number`)
Sets the cursor's X position in the MultiTool console. The console can display a maximum of 28 characters before wrapping.

### setCursorY(line `number`)
Sets the cursor's Y position in the MultiTool console. The console can display a maximum of 8 lines before overflowing.

### moveCursorX(deltaColumn `number`)

### moveCursorY(deltaLine `number`)

### saveCursorPos()
**⚠️ The functionality of this method has not yet been tested.**

Saves the position of the console cursor to memory.

### restoreCursorPos()
**⚠️ The functionality of this method has not yet been tested.**

Restores the cursor position saved by `saveCursorPos()` and sets it to the result.

### clear()
Clears the MultiTool console.

### clearToEndLine()

## Lamp

### IsLampOn() `boolean`
Returns true if the desk lamp is emitting light.

### TurnLampOn()
Turns the desk lamp on.

### TurnLampOff()
Turns the desk lamp off.
