# Веб-камера

<img src="https://docs.retrogadgets.game/api/modules/Webcam.png" width="200" align="right">

Веб-камера дозволяє отримати `RenderBuffer` реальної веб-камери на пристрої під управлінням Retro Gadgets. Ви можете використовувати це для виведення зображення з камери на екран за допомогою [VideoChip](../misc/VideoChip.md).


## Властивості

### RenderTarget - `VideoChip`
[VideoChip](../misc/VideoChip.md), на який ця камера передає вміст. Тільки цей відеочіп може малювати `RenderBuffer`, отриманий цією веб-камерою.


## Методи

### GetRenderBuffer() `RenderBuffer`
Отримує буфер рендерингу камери `RenderBuffer`. Отриманий буфер рендерингу може бути переданий до методу `DrawRenderBuffer` модуля [VideoChip](../misc/VideoChip.md). **Тільки VideoChip, заданий як `RenderTarget`, може малювати буфер.**.