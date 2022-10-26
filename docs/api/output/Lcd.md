# Lcd

<img src="https://docs.retrogadgets.game/api/modules/Lcd.png" width="200" align="right">

**The Lcd module's API is exposed as `LcdDisplay`.**

The Lcd can display a string of up to 32 characters, with a customizable foreground and background color.

The Lcd's display is 16x2. The **Lcd will not perform any word wrapping**, and will split words when moving to the next line.

## Properties

### Text - `string`
The text to display. It will be displayed starting at the top left and wrapping after 16 characters. Text that cannot fit will be clipped.
```lua
local display:LcdDisplay = gdt.Lcd0
display.Text = "Hello! How are  you today?"
--Extra space between are and you to avoid splitting word
```
![Text on an Lcd](../../../.github/assets/docs/Lcd.png)

### BgColor - `color`
Background color for the Lcd.

### TextColor - `color`
The color for the displayed text.