# ScreenButton

<img src="https://docs.retrogadgets.game/api/modules/ScreenButton.png" width="200" align="right">

Ekran Düğmesi, hem düğmenin hem de [Screen](../output/Screen.md) kombinasyonudur. Bu nedenle, hem giriş hem de çıkış aygıtı olarak işlev görür. **Giriş altında sıralanmıştır.**


## Özellikler

### VideoChip - `VideoChip`
Bu düğmenin [VideoChip](../misc/VideoChip.md) ve [Screen](../output/Screen.md) kısmı bağlıdır.

### ButtonState - `boolean` **[Sadece okuma]**
düğme şu anda basılı tutuluyorsa `doğru`, aksi halde `yanlış`.

### ButtonDown - `boolean` **[Sadece okuma]**
düğmenin tutulmaya başladığı ilk onay işareti için `true`. İşlemleri tutma başına yalnızca bir kez gerçekleştirmek için kullanışlıdır.

### ButtonUp - `boolean` **[Sadece okuma]**
düğmenin tutulmasının durduğu ilk işaret için `true`.


## Giriş Kaynakları
[GamepadChip](../misc/GamepadChip.md) veya [KeyboardChip](../misc/KeyboardChip.md) ile kullanım özellikleri.

### InputSource - `InputSource`


## Event - `ScreenButtonEvent`
[CPU](../misc/CPU.md) olay sisteminin parçası olarak yayılan olay.

Düğmeye basıldığında veya bırakıldığında gönderilir. [LedButton](./LedButton.md) olayıyla aynı.

### ButtonDown - `boolean`
Bu olay, tutulmaya başlayan bir düğme içinse doğrudur.
### ButtonUp - `boolean`
Bu olay, bir düğmenin tutulması durduğundaysa doğrudur.