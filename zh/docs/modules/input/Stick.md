# Stick 摇杆

<img src="https://docs.retrogadgets.game/api/modules/Stick.png" width="200" align="right">

**摇杆模块的API公开为`AnalogStick`。**

摇杆是二维输入设备，用鼠标拖动时显示偏移量，不交互时重置为原点。摇杆的最大范围是一个圆形，因此在非基本角度下，分量不会处于其极限，但其合成向量的大小将为100。

## 属性

### X - `number` **[Read only]**
摇杆在X轴的位置，从-100到100。

### Y - `number` **[Read only]**
摇杆在Y轴的位置，从-100到100。

## Input sources 输入源
使用[GamepadChip](../misc/GamepadChip.md) or [KeyboardChip](../misc/KeyboardChip.md)时的属性。

### InputSourceX - `InputSource`
### InputSourceY - `InputSource`