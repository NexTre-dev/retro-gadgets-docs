# ScreenButton 屏幕按钮

<img src="https://docs.retrogadgets.game/api/modules/ScreenButton.png" width="200" align="right">

屏幕按钮是按钮和[Screen 屏幕](../output/Screen.md)的组合。因此，它兼具输入和输出设备的功能。**它被归类到 Input（输入）类目下**

## 属性

### VideoChip 视频芯片 - `VideoChip`
此按钮的[Screen 屏幕](../output/Screen.md)部分所绑定的[VideoChip 视频芯片](../misc/VideoChip.md)

### ButtonState 按钮状态 - `boolean` **[Read only]**
按钮按下为`true`，否则为`false`。

### ButtonDown 按钮按下 - `boolean` **[Read only]**
按钮按下时的瞬间返回`true`，常用于只执行一次的操作。

### ButtonUp 按钮抬起 - `boolean` **[Read only]**
`true` for the first tick the button stops being held. 
按钮抬起时的瞬间返回`true`。


## Input sources 输入源
使用[GamepadChip](../misc/GamepadChip.md) or [KeyboardChip](../misc/KeyboardChip.md)时的属性.

### InputSource - `InputSource`