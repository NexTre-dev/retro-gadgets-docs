# Slider

<img src="https://docs.retrogadgets.game/api/modules/Slider.png" width="200" align="right">

Kaydırıcı, çeşitli yönlere yönlendirilebilen 1B sürüklenebilir bir giriş aygıtıdır. Etkileşimde bir [Knob](./Knob.md)'a benzer.


## Özellikler

### Value - `number`
Kaydırıcının 0 ile 100 arasında değişen konumsal değeri.

### IsMoving - `boolean` **[Sadece okuma]**
Kullanıcı şu anda Kaydırıcıyı fareyle tutuyorsa `true`. Kaydırma tekerleği ile bir değer değiştirildiğinde ayarlanmadığından bu, değişiklikleri algılamak için kullanılmamalıdır. Bunun yerine, örneğin, Kaydırıcıyla etkileşim devam ederken belirli bir değere ayarlamaya çalışmaktan kaçınmak için kullanılabilir.

## Event - `SliderValueChangeEvent`
[CPU](../misc/CPU.md) olay sisteminin parçası olarak yayılan olay.

Değer değiştirildiğinde gönderilir.

### Value - `number`
