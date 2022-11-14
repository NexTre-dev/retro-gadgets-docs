# Екранна кнопка

<img src="https://docs.retrogadgets.game/api/modules/ScreenButton.png" width="200" align="right">

Екранна кнопка - це комбінація кнопки та [екрану](../output/Screen.md). Таким чином, вона функціонує як пристрій введення та виведення. **Вона знаходиться в розділі "Введення"**.


## Властивості

### VideoChip - `VideoChip`
До [VideoChip](../misc/VideoChip.md) приєднується [екран](../output/Screen.md) цієї кнопки.

### ButtonState - `boolean` **[Тільки для читання]**
`true`, якщо кнопка в даний момент утримується натиснутою, `false` - у протилежному випадку.

### ButtonDown - `boolean` **[Тільки для читання]**
`true` при натисканні кнопки. Діє лише 1 тік(кадр)

### ButtonUp - `boolean` **[Тільки для читання]**
`true` при відтисканні кнопки. Діє лише 1 тік(кадр)


## Вхідні дані
Властивості для використання з [GamepadChip](../misc/GamepadChip.md) або [KeyboardChip](../misc/KeyboardChip.md).

### InputSource - `InputSource`