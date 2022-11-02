# Шкала
<img src="https://docs.retrogadgets.game/api/modules/Gauge.png" width="200" align="right">

**В API модуль Gauge представлено як `AnalogGauge`.**

Шкала є елегантним пристроєм виводу, який приблизно відображає дробове значення.

Стрілка має імпульс і буде сповільнюватися і стрибати до нових значень.

## Властивості

### Value - `number`
Положення від 0 до 100, де 0 - крайня ліва частина діапазону (позначена - ), а 100 - права частина (позначена + )

![Крайні точки Шкали](../../../assets/docs/Gauge/Gauge.png)


## Приклади

### Керування шкалою за допомогою Ручки
```lua
local gauge:AnalogGauge = gdt.Gauge0
local knob:Knob = gdt.Knob0

function update()
	gauge.Value = (knob.Value + 100) / 2
end
```