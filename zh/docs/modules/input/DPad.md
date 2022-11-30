# DPad

<img src="https://docs.retrogadgets.game/api/modules/DPad.png" width="200" align="right">

DPads类似于[Sticks](Stick.md), 但一次只能输出一个极值。

## 属性

### X - `number` **[Read only]**
当DPad被向左按压时为-100，向右按压时为100. 其余情况下为0.

### Y - `number` **[Read only]**
当DPad被向上按压时为100，向下按压时为-100. 其余情况下为0.

## Input sources
用于[GamepadChip](../misc/GamepadChip.md)或[KeyboardChip](../misc/KeyboardChip.md)的属性。

### InputSourceX - `InputSource`
### InputSourceY - `InputSource`