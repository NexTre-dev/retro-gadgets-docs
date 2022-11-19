# DPad

<img src="https://docs.retrogadgets.game/api/modules/DPad.png" width="200" align="right">

DPads схожі на [Cтіки](Stick.md), за винятком того, що вони можуть виводити тільки значення по осі X або Y.

## Властивості

### X - `number` **[Тільки для читання]**
-100 при натисканні ліворуч, 100 при натисканні праворуч. 0 якщо не рухати стіком.

### Y - `number` **[Тільки для читання]**
100 при натисканні вгору, -100 при натисканні вниз. 0 якщо не рухати стіком.

## Вхідні дані
Властивості для використання з [GamepadChip](../misc/GamepadChip.md) або [KeyboardChip](../misc/KeyboardChip.md).

### InputSourceX - `InputSource`
### InputSourceY - `InputSource`