# Gauge

<img src="https://docs.retrogadgets.game/api/modules/Gauge.png" width="200" align="right">

**Gösterge modülünün API'si "AnalogGauge" olarak kullanıma sunulmuştur.**

Gösterge kabaca kesirli bir değer gösteren estetik bir çıktı cihazıdır.

**iğnenin ivmesi vardır ve gevşeyerek yeni değerlere sıçrar**, gadget kapalıyken veya ilk başta açıldığında bile.

## Özellikler

### Value - `number`
0 ile 100 arasında bir konum, 0 aralığın en solu (- etiketli) ve 100 sağ tarafı (+ etiketli)

![Göstergenin uç noktaları](../../../assets/docs/Gauge/Gauge.png)


## Örnekler

### ir Göstergeyi Düğmeyle Kontrol Etme
```lua
local gauge:AnalogGauge = gdt.Gauge0
local knob:Knob = gdt.Knob0

function update()
	gauge.Value = (knob.Value + 100) / 2
end
```
