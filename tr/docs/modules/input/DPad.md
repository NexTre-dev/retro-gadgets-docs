# DPad

<img src="https://docs.retrogadgets.game/api/modules/DPad.png" width="200" align="right">

DPad'ler [Çubuklar](Stick.md)'a benzerler, tek farkları bir defada yalnızca bir aşırı uç çıktı verebilmeleridir.

## Özellikler

### X - `number` **[Read only]**
DPad'e sola basıldığında -100, sağa basıldığında 100. Aksi takdirde 0.

### Y - `number` **[Read only]**
DPad'e yukarı doğru basıldığında 100, aşağı doğru basıldığında -100. Aksi takdirde 0

## Giriş kaynakları
[GamepadChip](../misc/GamepadChip.md) veya [KeyboardChip](../misc/KeyboardChip.md) ile kullanım özellikleri.

### InputSourceX - `InputSource`
### InputSourceY - `InputSource`

## Olay - `DPadValueChangeEvent`
[CPU](../misc/CPU.md) olay sisteminin parçası olarak yayılan olay.

Değer değiştirildiğinde gönderilir.

### X - `number`
### Y - `number`



