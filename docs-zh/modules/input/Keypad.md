# Keypad

<img src="https://docs.retrogadgets.game/api/modules/Keypad.png" width="200" align="right">

键盘是一个按钮网格，表示几个4x4表格的状态。可以通过multitool来向它们传递信号，但与大多数按钮不同的是，它们不是LED。

## 属性

### ButtonsState 按钮状态 - `{{boolean}}` **[Read only]**
一个表示每个按钮状态布尔值的多维表。
表中的元素由[列][行]定位。如果对应的按钮被按下，则表元素返回`true`，否则返回`false`。

### ButtonsDown 按下 - `{{boolean}}` **[Read only]**
类似于`ButtonsState`, 但是只在对应按钮最初按下时那一帧返回 `true`。

### ButtonsUp 抬起 - `{{boolean}}` **[Read only]**
类似于`ButtonsState`, 但是只在对应按钮最初松开时那一帧返回`true`。

## 硬件
此属性可以通过multitool inspector设置，但不能通过软件设置。

### 信号 - `{{Symbol}}` *(hardware)*
一个表示相关按钮信号的表格，信号可以通过paint tool设置成和背景色不同的颜色，但一个Keypad的所有信号应该是相同的颜色。