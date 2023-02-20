# Stick

<img src="https://docs.retrogadgets.game/api/modules/Stick.png" width="200" align="right">

**Stick modülünün API'si `AnalogStick` olarak gösterilir.**

Çubuklar, bir fare ile sürüklendiklerinde ofseti bildiren ve etkileşimde bulunulmadığında orijine sıfırlanan 2B giriş aygıtlarıdır. Bir çubuğun maksimum menzili dairesel bir şekildir, bu nedenle kardinal olmayan açılarda bileşenler uç noktalarda olmayacak, ancak bileşke vektörlerinin büyüklüğü 100 olacaktır.

## Özellikler

### X - `number` **[Read only]**
Çubuğun X ekseni boyunca -100 ile 100 arasında değişen konumu.

### Y - `number` **[Read only]**
Çubuğun Y ekseni boyunca -100 ile 100 arasında değişen konumu.

## Giriş Kaynakları
[GamepadChip](../misc/GamepadChip.md) veya [KeyboardChip](../misc/KeyboardChip.md) ile kullanım özellikleri.

### InputSourceX - `InputSource`
### InputSourceY - `InputSource`

## Event - `StickValueChangeEvent`
[CPU](../misc/CPU.md) olay sisteminin parçası olarak yayılan olay.

Değer değiştirildiğinde gönderilir.

### X - `boolean`
### Y - `boolean`