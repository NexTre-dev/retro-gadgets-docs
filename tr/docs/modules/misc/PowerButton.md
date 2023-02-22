# PowerButton

<img src="https://docs.retrogadgets.game/api/modules/PowerButton.png" width="200" align="right">

Güç Düğmesi, gadget'ınızın ana giriş noktasıdır. Basmak, "oynatma modunu" açar ve kapatır. Oynatma modu sırasında CPU'lar çalışır ve gadget düzenlenemez. Tekrar basmak oynatma modunu sonlandırır ve gadget'ı ilk durumuna döndürür.

Güç düğmelerinin sonundaki sekmeler diğer bileşenlerle çarpışmaz ve hem üç tür arasında ayrım yapmak hem de bunları fareyle hareket ettirmeye yardımcı olmak için kullanılır. Farklı güç düğmeleri şunlardır:

- Düz bir yüzeyin kenarına yerleştirilmesi gereken kırmızı şeritli kare.
- Tek bir sırt içeren daha küçük kırmızı çıkıntılı yuvarlak. Yaklaşık yarısı kadar kısa olması ve aygıtın kenarlarında durması dışında kırmızı olanla tamamen aynıdır.
- Varsayılana benzer mavi çıkıntılı yuvarlak, ancak herhangi bir bileşenle çarpışmadığı sürece kenar olmayan herhangi bir yere yerleştirilebilir.

Güç düğmesini kaldırabilirsiniz (çok amaçlı konektörün aksine), ancak yalnızca bir tane olabilir.

## Özellikler

### ButtonState - `boolean` **[Sadece okuma]**
bu her zaman `false`.
```lua
local button:PowerButton = gdt.PowerButton0
function update()
	print(button.ButtonState) -- "false", always
end
```