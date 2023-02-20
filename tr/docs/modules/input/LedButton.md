# LedButton

<img src="https://docs.retrogadgets.game/api/modules/LedButton.png" width="200" align="right">

En bol girdi bileşeni. Çok yönlülük için neredeyse tüm düğmeler aslında LedButton'lardır. Hiçbiri bu makalede kullanılan görüntü olmayan birçok şekil ve boyutta gelirler. Bunlar, tek bir renk değeri için çıktı aygıtı olarak ikiye katlanan, tipik olarak fareyle tutulan basit açma/kapama girişleridir.

LedButtons tarafından sağlanan ışık fizikseldir ve ışıksız LedButtons ve diğer bileşenleri aydınlatır.

## Özellikler

### ButtonState - `boolean` **[Sadece Okuma]**
düğme şu anda basılı tutuluyorsa `doğru`, aksi halde `yanlış`.

### ButtonDown - `boolean` **[Sadece Okuma]**
düğmenin tutulmaya başladığı ilk onay işareti için `true`. İşlemleri tutma başına yalnızca bir kez gerçekleştirmek için kullanışlıdır.

### ButtonUp - `boolean` **[Sadece Okuma]**
düğmenin tutulmasının durduğu ilk işaret için `true`.

### LedState - `boolean`
Led'in açık olup olmadığı. `true` ise, düğme `LedColor` ışığı yayar. `yanlış` ise, düğme ışık yaymaz. Başlangıç ​​değeri multitool denetçisi ile ayarlanabilir.

Işık yaymamak, siyah renkle ışık yaymaya benzer.

### LedColor - `color`
`LedState` `true` olduğunda yayılacak olan Led'in rengi. Bu, herhangi bir zamanda programlı olarak ayarlanabilir. Başlangıç ​​değeri multitool denetçisi ile ayarlanabilir.


## Giriş kaynakları
[GamepadChip](../misc/GamepadChip.md) veya [KeyboardChip](../misc/KeyboardChip.md) ile kullanım özellikleri.

### InputSource - `InputSource`

## Event - `LedButtonEvent`
[CPU](../misc/CPU.md) olay sisteminin parçası olarak yayılan olay.

Düğmeye basıldığında veya bırakıldığında gönderilir.

### ButtonDown - `boolean`
Bu olay, tutulmaya başlayan bir düğme içinse doğrudur.
### ButtonUp - `boolean`
Bu olay, bir düğmenin basılı tutulmayı durdurduğu zaman için geçerliyse doğrudur.

## Donanım
Bu özellikler, multitool denetçisi ile ayarlanabilir, ancak yazılımda ayarlanamaz.

### Symbol - `Symbol` *(hardware)* ⚠️ Tüm varyantlarda mevcut değildir.
Düğmede görüntülenecek bir sembol. Semboller, arka plandan farklı bir renk olacak şekilde boyama aracıyla boyanabilir. **Daha küçük LedButton'larda bu özellik yoktur.**