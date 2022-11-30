# Led按钮

<img src="https://docs.retrogadgets.game/api/modules/LedButton.png" width="200" align="right">

最丰富的输入组件。几乎所有的按钮实际上都是Led按钮，以实现多种功能。它们有各种形状和大小，但本节不会提及。它们是简单的开/关输入组件，通常用鼠标控制，同时也作为单一颜色值的输出设备。

Led按钮投射的光是物理的，会照亮未点亮的Led按钮和其他组件。

## 属性

### ButtonState 按钮状态 - `boolean` **[Read only]**
按钮按下时为`true`，否则为`false`。

### ButtonDown 按钮按下 - `boolean` **[Read only]**
按钮按下时的瞬间返回`true`，常用于只执行一次的操作。

### ButtonUp 按钮抬起 - `boolean` **[Read only]**
按钮抬起时的瞬间返回`true`。

### LedState Led状态 - `boolean`
Les的开关状态。如果为`true`，按钮会发出`LedColor`颜色的光。如果为`false`, 则不发光。初始状态可由multitool inspector设置。

不发光类似于发黑色的光。

### LedColor Led颜色 - `color`
Led的颜色，在`LedState`为`true`的时候发出，可以在任何时候由程序更改。初始值可由multitool inspector设置。


## Input sources 输入源
使用[GamepadChip](../misc/GamepadChip.md) or [KeyboardChip](../misc/KeyboardChip.md)时的属性。

### InputSource 输入源 - `InputSource`


## 硬件
可以通过multitool inspector设置，但不能通过软件设置。

### Symbol 标志 - `Symbol` *(hardware)* ⚠️ 不适用于变体。
按钮上显示的标志。可以用paint tool绘制成和背景不同的颜色。**小的Led按钮没有这个属性**