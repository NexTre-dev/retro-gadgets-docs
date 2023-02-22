# Lcd

<img src="https://docs.retrogadgets.game/api/modules/Lcd.png" width="200" align="right">

**Lcd modülünün API'si "LcdDisplay" olarak gösterilir.**

Lcd, özelleştirilebilir bir ön plan ve arka plan rengiyle 32 karaktere kadar bir dizi görüntüleyebilir.

Lcd'nin ekranı 16x2'dir. **Lcd, herhangi bir sözcük kaydırma işlemi gerçekleştirmeyecek** ve bir sonraki satıra geçerken sözcükleri bölecektir.

## Özellikler

### Text - `string`
Görüntülenecek metin. Sol üstten başlayarak ve 16 karakterden sonra sarmalanarak görüntülenecektir. Sığamayan metin kırpılacaktır.
```lua
local display:LcdDisplay = gdt.Lcd0
display.Text = "Hello! How are  you today?"
--Extra space between are and you to avoid splitting word
```
![Lcd'deki Metin](../../../assets/docs/Lcd/Lcd.png)

#### Satırları otomatik olarak biçimlendirme

Her satırı birbirinden bağımsız olarak düzenlemek için Lua'nın yerleşik işlevini [`string.format`](https://www.lua.org/manual/5.3/manual.html#pdf-string.format) kullanabilirsiniz. ikisi de 16 karakterden uzun değildir.

```lua
LCD.Text = string.format("%- 16s%- 16s",line1, line2)
```
Bu satırlar daha uzun olabilirse, ilk veya son karakterleri korumak için satırları kırpabilirsiniz :
```lua
-- this will crop from the start of the string:
line1 = string.sub(line1, 1, 16)
-- this will crop from the end of the string:
line1 = string.sub(line1, math.max(1,string.len(line1)-15))
```

### BgColor - `color`
Lcd için arka plan rengi.

### TextColor - `color`
Görüntülenen metnin rengi.
