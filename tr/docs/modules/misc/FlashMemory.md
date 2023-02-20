# Flash Memory
<img src="https://docs.retrogadgets.game/api/modules/FlashMemory.png" width="200" align="right">

Çevirmenden not: Bu arkadaş sayesinde CPUlar arası veri aktarımı da yapabiliyorsunuz. Şarj sistemi yaparken işe yarıyor.

Flash Bellek **250KiB**'ye kadar (en büyük değişkende) tablo verilerini kalıcı olarak depolar. Flash Belleğe kaydedilen veriler, gadget kapatıldığında veya oyun kapatıldığında korunur.

## Özellikler

### Usage - `number` **[Sadece okuma]**
Bayt cinsinden ne kadar veri kullanılıyor. Asla `Boyutu` aşmayın. Yoksa veri kaydetmez.

### Size - `number` **[Sadece okuma]**
Bayt cinsinden toplam depolama. Çip başına değişir ve sabit kalır.
En kısa çipten en uzun çipe doğru sıralanan boyutlar:

- 4  KiB
- 32 KiB
- 250 KiB (256 KB)

Çekmecelerde boyutlar bulunmakta. Küçük-Orta-Büyük şeklinde buradaki ile aynı sıralı.

## Metodlar

### Save(table `{}`) `boolean`
**⚠️ Bu yöntemin işlevselliği henüz test edilmedi.**

Tablo verilerini belleğe kaydeder, **çipteki önceki belleğin üzerine yazar.** Kalan bellek yeni verileri sığdırmak için yetersizse `false` döndürür.

```lua
local memory:FlashMemory = gdt.FlashMemory0

memory:Save({"foo", "bar", "baz"})
log( memory:Load()[1] ) -- "foo"
```

### Load() `{}`

Şu anda çipte yüklü olan her şeyi döndürür. Bu, verilerin yeni bir kopyasıdır, yani üzerinde yapılan değişiklikler kaydedilmeyecektir. Örneğin, `memory:Load()[3] = "baz"` çalışmaz.
