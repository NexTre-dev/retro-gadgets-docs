# Küresel Yöntemler
Aşağıda, programınızın herhangi bir yerinde çağrılabilecek yöntemlerin bir listesi bulunmaktadır.

## ~~Varlıklar~~
**❌ Bu yöntemler ROM lehine kaldırılmıştır. Bunları yalnızca uyumluluk amacıyla kullanın.**

### GetSpriteSheet(name `string`) `SpriteSheet`
MultiTool varlık listesinden bir SpriteSheet sağlar.

### GetPalette(name `string`) `Palette`
**❌ Bu yöntem kullanımdan kaldırıldı.**

**⚠️ Bu yöntemin işlevselliği henüz test edilmedi.**

### GetAudioSample(name `string`) `AudioSample`
MuliTool varlık listesinden bir AudioSample sağlar. mp3 ve wav'ı destekler.

### GetCode(name `string`) `Code`
Dinamik olarak bir CPU'ya atanabilen MuliTool varlık listesinden bir Lua dosyası sağlar.

## Renk

### Color(r `number`, g `number`, b `number`) `color`
RGB değerlerinden bir renk nesnesi oluşturur ve döndürür. Üç parametre 0 - 255 aralığında olmalıdır.

### ColorRGBA(r `number`, g `number`, b `number`, a `number`) `color`
Bir alfa kanalıyla birlikte RGB değerlerinden bir renk nesnesi oluşturur ve döndürür. Dört parametre 0 - 255 aralığında olmalıdır. Alfa kanalı için 0 tamamen saydamdır ve 255 opaktır.

### ColorHSV(h `number`, s `number`, v `number`) `color`
HSV değerlerinden bir renk nesnesi oluşturur ve döndürür. Ton için aralıklar 0 - 360 ve doygunluk ve değer aralığı 0 - 100 olmalıdır.

## Konsol

### log(message `string`)
MultiTool konsoluna bir mesaj yazdırır. Lua'nın tüm veri türlerini kabul eden yerleşik `yazdır` işlevinin aksine, bu yöntem tek bir dize kullanmanızı gerektirir. Diğer veri türlerini kullanmak için `tostring()` kullanın.

### logWarning(message `string`)
MultiTool konsoluna bir tür önlem veya tavsiye belirten sarı metin yazdırır; bir uyarı.

### logError(message `string`)
Yeni bir satır eklemeden MultiTool konsoluna bir mesaj yazdırır. Aksi takdirde `log()` ile aynı şekilde çalışır.

### write(text `string`)
Prints a message to the MultiTool console without adding a new line. Functions identically to `log()` otherwise.

### writeln(text `string`)
Metnin sonuna yeni bir satır eklenmesi dışında "write()" ile aynı şeyi yapar. `log()` ile aynı şekilde çalışır.


### setFgColor(colorId `number`)
**⚠️ The functionality of this method has not yet been tested.**

Sets the text color in the MultiTool console.

### setBgColor(colorId `number`)
**⚠️ Bu yöntemin işlevselliği henüz test edilmedi.**

MultiTool konsolundaki arka plan rengini ayarlar.

### resetFgColor()
**⚠️ Bu yöntemin işlevselliği henüz test edilmedi.**

MultiTool konsolundaki metin rengini sıfırlar.

### resetBgColor()
**⚠️ Bu yöntemin işlevselliği henüz test edilmedi.**

MultiTool konsolundaki arka plan rengini sıfırlar.

### resetColors()
**⚠️ Bu yöntemin işlevselliği henüz test edilmedi.**

MultiTool konsolundaki renkleri sıfırlar.

### setCursorPos(column `number`, line `number`)
Yeni metnin eklendiği MultiTool konsolunda imleç konumunu ayarlar.

<img src="../../assets/docs/Global/CursorPos.png" width="300" />

### setCursorX(column `number`)
MultiTool konsolunda imlecin X konumunu ayarlar. Konsol, kaydırmadan önce en fazla 28 karakter görüntüleyebilir.

### setCursorY(line `number`)
MultiTool konsolunda imlecin Y konumunu ayarlar. Konsol, taşmadan önce maksimum 8 satır görüntüleyebilir.

### moveCursorX(deltaColumn `number`)
**⚠️ Bu yöntemin işlevselliği henüz test edilmedi.**

MultiTool'un imlecinin X konumunu `deltaColumn` ile değiştirir.

### moveCursorY(deltaLine `number`)
**⚠️ Bu yöntemin işlevselliği henüz test edilmedi.**

MultiTool'un imlecinin Y konumunu `deltaLine` kadar değiştirir.

### saveCursorPos()
**⚠️ Bu yöntemin işlevselliği henüz test edilmedi.**

Konsol imlecinin konumunu belleğe kaydeder.

### restoreCursorPos()
**⚠️ Bu yöntemin işlevselliği henüz test edilmedi.**

`saveCursorPos()` tarafından kaydedilen imleç konumunu geri yükler ve sonuca ayarlar.

### clear()
MultiTool konsolunu temizler.

### clearToEndLine()
**⚠️ Bu yöntemin işlevselliği henüz test edilmedi.**