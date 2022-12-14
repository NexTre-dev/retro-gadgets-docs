# RealityChip

<img src="https://docs.retrogadgets.game/api/modules/RealityChip.png" width="200" align="right">

Reality Chip надає значення з реального положення пристрою, і в майбутньому може робити більше.

Цікаво, що він має назву "RB", імовірно, тому, що його внутрішня назва - " Reality Bridge" ("Міст реальності").
## Властивості
Всі поточні властивості оновлюються щосекунди.

### Cpu.TotalUsage - `number` **[Тільки для читання]**
Загальне використання процесора системи 0-100. Це значення зазвичай відрізняється від того, що ви бачите в диспетчері завдань, оскільки диспетчер завдань використовує іншу метрику, до якої має доступ лише він. Це також може бути помилкою з windows.

### Cpu.CoresUsage - `{number}` **[Тільки для читання]**
Масив, що містить використання процесора кожного логічного ядра процесора 0-100.

### Ram.Available - `number` **[Тільки для читання]**
Доступна оперативна пам'ять, виражена в МБ. Це не загальний розмір, це залишок пам'яті.

### Ram.Used - `number` **[Тільки для читання]**
Використана оперативна пам'ять виражена в МБ.

Ви можете об'єднати дві метрики оперативної пам'яті у відсотках.
```lua
local reality:RealityChip = gdt.RealityChip0

function update()
	local percent = reality.Ram.Used/(reality.Ram.Available + reality.Ram.Used)
	log(tostring(percent*100)) -- 70.83448438808485 (Відсоток буде змінюватися)
end
```

### Network.TotalSent - `number` **[Тільки для читання]**
Сумарно передано мережевими інтерфейсами виражено в Мбіт.

### Network.TotalReceived - `number` **[Тільки для читання]**
Сумарно отримано від мережевих інтерфейсів, виражено в Мбіт.