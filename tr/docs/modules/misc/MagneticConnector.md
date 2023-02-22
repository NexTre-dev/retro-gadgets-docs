# MagneticConnector

<img src="https://docs.retrogadgets.game/api/modules/MagneticConnector.png" width="200" align="right">

Manyetik Konnektörler, ayrılmış kartların ayar noktalarında bağlanmasına ve bağlantısının kesilmesine izin verir. Güçlendirilmiş bir mıknatısla (açık yeşil, düğmeyle değiştirilebilir) birbirine bağlanan kartlar tek olarak alınacaktır.

## Özellikler

### AttachedConnector - `MagneticConnector` **[Read only]**
Buna bağlı `MagneticConnector`.

### ButtonState - `boolean` **[Read only]**
Konektördeki fiziksel düğmenin durumu. düğme tutuluyorsa `true`.

### IsConnected - `boolean` **[Read only]**
bağlayıcı başka birine bağlıysa `true`.

## Event - `MagneticConnectorEvent`
[CPU](./CPU.md) olay sisteminin bir parçası olarak yayılan olay.

Bir `MagneticConnector` diğerine bağlandığında gönderilir.

### IsConnected - `boolean`
bağlayıcı başka birine bağlıysa `true`.