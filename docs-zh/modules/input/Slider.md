# Slider 滑块

<img src="https://docs.retrogadgets.game/api/modules/Slider.png" width="200" align="right">

滑块是一个一维可拖动输入设备，可以朝向多个方向。它在交互中类似于[Knob 旋钮](./Knob.md)。


## 属性

### Value 值 - `number`
滑块的位置值，范围从0到100。

### IsMoving 是否在移动 - `boolean` **[Read only]**
如果用户当前用鼠标按住滑块则返回`true`。这不应用于检测滑块值的更改，因为当使用滚轮更改值时不会触发。可以用来避免在还与滑块交互时设置滑块的值。