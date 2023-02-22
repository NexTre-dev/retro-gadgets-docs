# RealityChip

<img src="https://docs.retrogadgets.game/api/modules/RealityChip.png" width="200" align="right">

Reality Chip, cihazın gerçek durumundan değerler sağlar ve gelecekte daha fazlasını yapabilir.

Muhtemelen dahili olarak "Reality Bridge" olarak adlandırıldığı için, merakla "RB" olarak etiketlenmiştir.

## Özellikler
Mevcut tüm özellikler her saniye yenilenir.

### Cpu.TotalUsage - `number` **[Sadece okuma]**
Sistemin toplam CPU kullanımı 0-100. Görev yöneticisi yalnızca kendisinin erişebildiği farklı bir ölçüm kullandığından, bu değer genellikle Görev Yöneticisi'nde göreceğiniz değer değildir. Bu ayrıca Windows ile ilgili bir hata olabilir.

### Cpu.CoresUsage - `{number}` **[Sadece okuma]**
Her mantıksal CPU çekirdeğinin 0-100 işlemci kullanımını içeren bir dizi.

### Ram.Available - `number` **[Sadece okuma]**
Kullanılabilir RAM, MB olarak ifade edilir. Bu toplam boyut değil, bu kalan hafıza.

### Ram.Used - `number` **[Sadece okuma]**
MB cinsinden ifade edilen kullanılmış RAM.

İki RAM ölçümünü yüzde olarak birleştirebilirsiniz.
```lua
local reality:RealityChip = gdt.RealityChip0

function update()
	local percent = reality.Ram.Used/(reality.Ram.Available + reality.Ram.Used)
	print(percent*100) -- 70.83448438808485 (This will vary)
end
```

### Network.TotalSent - `number` **[Sadece okuma]**
Mbps cinsinden ifade edilen ağ arayüzleri tarafından gönderilen toplam.

### Network.TotalReceived - `number` **[Sadece okuma]**
Mbps cinsinden ifade edilen ağ arayüzlerinden alınan toplam