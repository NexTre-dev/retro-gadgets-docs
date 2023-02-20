# Switch

<img src="https://docs.retrogadgets.game/api/modules/Switch.png" width="200" align="right">

Anahtarlar, tıklandığında durumu değiştiren boolean girişlerdir. Birçok şekil ve boyutta gelirler ve çoğu döndürülebilir.


## Özellikler

### State - `boolean`
Anahtarın durumu. Anahtar her tıklandığında `doğru` ve `yanlış` arasında geçiş yapar. Başlangıç ​​durumu multitool denetçisi ile ayarlanabilir.


## Event - `SwitchStateChangeEvent`
[CPU](../misc/CPU.md) olay sisteminin parçası olarak yayılan olay.

Değer değiştirildiğinde gönderilir.

### State - `boolean`


## Hardware
Bu özellikler, multitool denetçisi ile ayarlanabilir, ancak yazılımda ayarlanamaz.

### Symbol - `Symbol` *(hardware)* ⚠️ Only available on a single variant.
Anahtarda görüntülenecek bir sembol. Semboller, arka plandan farklı bir renk olacak şekilde boyama aracıyla boyanabilir. **Yalnızca yandan gömülü kaset geçiş düğmesinin bir simge yuvası vardır.**