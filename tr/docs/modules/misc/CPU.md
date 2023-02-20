# CPU

<img src="https://docs.retrogadgets.game/api/modules/CPU.png" width="200" align="right">

CPU, çoğu gadget etkileşiminden sorumludur ve Lua varlık dosyalarını çalıştırır. CPU'ların (şu anda) etkileşime girdikleri aygıtın herhangi bir parçasına bağlanması veya kartı üzerinde olması gerekmez. Şu anda tek bir Lua varlığı yükleyebilirler.

## Özellikler

### Source - `Code` **[Sadece okuma]**
Kaynak, CPU'nun hangi "dosyayı" çalıştıracağını tanımlar ve genellikle multitool denetçisi ile ayarlanır. Herhangi bir Lua varlığına ayarlayabilirsiniz. Bir CPU oluşturulduktan sonra, otomatik olarak CPU0.lua adlı bir kod dosyası oluşturulur ve söz konusu CPU'ya otomatik olarak bağlanır.

### Time - `number` **[Sadece okuma]**
Gadget'ın açılmasından bu yana geçen süre, saniye cinsinden ifade edilir.

```lua
local cpu:CPU = gdt.CPU0
function update()
	print(cpu.Time) -- 0.521000027656552 (This will vary)
end
```

### DeltaTime - `number` **[Sadece okuma]**
Son tıklamadan bu yana geçen süre, saniye cinsinden ifade edilir. Temelde bu, son `update()` çağrısı arasındaki farktır (veya _delta_). Bu, 'Zaman'ı hatırlamaya gerek duymadan animasyonları ve zamanlayıcıları güncellemek ve değerleri düzgün bir şekilde enterpolasyon yapmak için kullanışlıdır (bkz. "Tutarlı interpolasyon oluşturma").

```lua
local cpu:CPU = gdt.CPU0
function update()
	print(cpu.DeltaTime) -- At 60/60 tps, this is roughly 0.01666 repeating.
	-- An example real value is: 0.01600000075995922
end
```

### EventChannels - `{module}` **[Sadece okuma]**
Olaylar, `function update()`'de bir döngüdeki değerleri kontrol etmek yerine, bir modül tarafından bildirildiğinde bir işlevi çalıştırmanın bir yoludur. Bu, önemli performans avantajları sağlayabilir ve bazı modülleri kullanmanın tek yoludur.

`EventChannels` dizisinde ayarlanan her modül, olayını tetiklediğinde bu CPU'da karşılık gelen `eventChannel` işlevini çalıştıracaktır.
Örneğin, `EventChannels[1]` içinde ayarlanan bir modül tetiklendiğinde, `eventChannel1` işlevini çalıştırır.

Her `eventFunction` iki parametreye sahip olmalıdır. İlki, olayı tetikleyen modüldür (ör. `eventChannel1` için bu, `EventChannels[1]` olacaktır). İkinci parametre, modül tarafından sağlanan `Olay`ın kendisidir.

`EventChannels` uzunluğu ve dolayısıyla olayları dinleyebileceğiniz benzersiz modüllerin miktarı CPU boyutuna göre belirlenir.
|  Boyut | Kanallar |
|-------:|:---------|
|  Küçük | 4        |
|  Orta  | 16       |
|  Büyük | 64       |

```lua
-- Example button event, assuming EventChannels[1] = gdt.LedButton0
function eventChannel1(sender:LedButton, arg:LedButtonEvent)
	print(arg.ButtonDown)
end
```

## Notlar

### Tutarlı enterpolasyon oluşturma

<!-- not sure if retro gadgets handles deltatime already? remove this section if that's the case -->

Bir şeyin hareketinin tutarlı kalmasını sağlamak, bununla ilgili herhangi bir şey yaparken inanılmaz derecede önemlidir. Bir kareyi 60 FPS'de hareket ettiriyorsanız, aynı mesafeyi 5 FPS'de de taşımak istersiniz. Ancak, çoğu genel durumda, bu olmaz. 0 değerinden 100 değerine geçiş yaparsanız, her kareyi 1 artırın:
```lua
local myNumber:number = 0

-- update() is called each frame
function update()
  myNumber = myNumber + 1
end
```

Bu, çerçeve hızı tutarlı olduğu sürece çoğu durumda işe yarar. Ancak, olmaması durumunda, 'myNumber'ın 100'e ulaşması için geçen süre, farklı kare hızları arasında değişiklik gösterecektir. Bu, tutarlı olması için bir değişkenin artışına (bir karakterin hareketi gibi) ihtiyaç duyduğunuz senaryolarda sorunlara yol açabilir, bu nedenle onu FPS ile senkronize etmenin bir yolunu bulmak önemlidir. Bu uygulama, tutarlı olması gereken ve yalnızca birkaç ekstra karakter içeren veri enterpolasyonu söz konusu olduğunda çoğu durumda uygulanır:

```lua
local myNumber:number = 0
local cpu:CPU = gdt.CPU0 -- Replace this with your CPU

function update()
	myNumber = myNumber + (1 * cpu.DeltaTime)
end
```

Artım değerini DeltaTime ile çarptığımız için, kare hızı ne olursa olsun, uzun vadede `myNumber`ın 100'e ulaşması yine aynı süreyi alacaktır.
