# Keypad

<img src="https://docs.retrogadgets.game/api/modules/Keypad.png" width="200" align="right">

Tuş takımları, durumu çeşitli 4x4 tablolarda bildiren bir düğme ızgarasıdır. Multitool ile semboller verilebilir, ancak çoğu düğmenin aksine LED değildir.

## Özellikler

### ButtonsState - `{{boolean}}` **[Sadece okuma]**
Her düğmenin durumunu bir boole değeriyle eşleyen çok boyutlu bir tablo.
Tablo [sütun][satır] ile adreslenmelidir. İlgili düğme basılı tutuluyorsa her tablo hücresi `true`, aksi halde `false` değerini döndürür.

### ButtonsDown - `{{boolean}}` **[Sadece okuma]**
`ButtonsState` gibi, ancak çerçeve için yalnızca `true` ise ilgili düğme başlangıçta basılı tutulur.

### ButtonsUp - `{{boolean}}` **[Sadece okuma]**
`ButtonsState` gibi, ancak çerçeve için yalnızca `true` olduğunda karşılık gelen düğme serbest bırakılır.

## Olay - `KeypadButtonEvent`
[CPU](../misc/CPU.md) olay sisteminin parçası olarak yayılan olay.

Bir düğme durumu değiştirildiğinde gönderilir.

### X - `number`
Değişen düğmenin X dizini.
### Y - `number`
Değişen düğmenin Y dizini.
### ButtonDown - `boolean`
### ButtonUp - `boolean`

## Donanım
Bu özellikler, multitool denetçisi ile ayarlanabilir, ancak yazılımda ayarlanamaz.

### Symbols - `{{Symbol}}` *(hardware)*
Karşılık gelen düğmelerde görüntülenecek bir sembol tablosu. Semboller, boyama aracıyla arka plandan farklı bir renge boyanabilir, ancak Tuş takımındaki tüm semboller aynı renkte olacaktır..
