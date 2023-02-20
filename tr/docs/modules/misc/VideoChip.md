# VideoChip

<img src="https://docs.retrogadgets.game/api/modules/VideoChip.png" width="200" align="right">

Video Çipi, bağlı ekranlarının tuvalini temsil eder ve bunlara çizim yapmak için kullanılır.

## Özellikler

### Mode - `VideoChipMode`
"SingleBuffer" veya "DoubleBuffer" olabilen arabellek modu.

Tek bir arabellek, yeni komutlar gönderildikçe sürekli değişen tek bir ekran arabelleği üzerinde çalışmanıza olanak tanır. Örneğin, bir daire çizecek olsaydınız, doğrudan tampona gönderilir ve hemen görüntülenirdi. Ancak, DoubleBuffer ile düzenli olarak değişen iki farklı video arabelleği ile uğraşıyorsunuz. Her kare, düzenlediğiniz arabellek değişir; tampon B çipin bağlı olduğu ekranlara yansıtılırken tampon A'yı düzenliyor olabilirsiniz. Bir sonraki karede, tampon A'daki değişiklikler ekranlara sunulurken, bu kare için yapılan diğer değişiklikler tampon B'ye yapılır. Genellikle bu, videonun görüntülenme biçiminde bir fark yaratmaz, ancak SingleBuffer'ı kullanırken titreme, gecikme veya takılma yaşıyorsanız, DoubleBuffer'a geçmelisiniz.

### Height - `number` **[Read only]**
İşleme arabelleğinin piksel cinsinden yüksekliği. Alan, bu VideoChip'e bağlı tüm ekranları hesaba katar.

### Width - `number` **[Read only]**
İşleme arabelleğinin piksel cinsinden genişliği. Alan, bu VideoChip'e bağlı tüm ekranları hesaba katar.

## Metodlar

### Clear(color `color`)
Belirtilen **renk** ile tüm oluşturma alanını temizler. Genellikle her çerçeveyi çizmeden önce kullanılır.
```lua
local video:VideoChip = gdt.VideoChip0

function update()
	video:Clear(color.white)
	-- <...>
end
```

### SetPixel(position `vec2`, color `color`)
Belirtilen konumdaki pikseli belirtilen **renk** olarak ayarlar.

<img src="../../../assets/docs/VideoChip/PixelGrid.png" width="200" align="right">

### DrawPointGrid(gridOffset `vec2`, dotsDistance `number`, color `color`)
**Tüm görüntüleme alanına** bir ofset ile noktalı bir ızgara çizer. dotsDistance parametresi, her iki eksende noktalar arasındaki mesafeyi piksel cinsinden ifade eder. Bu garip bir işlevdir, ancak arka planlar için kullanılabilir.
```lua
local video:VideoChip = gdt.VideoChip0

function update()
	video:Clear(color.blue)
	video:DrawPointGrid(vec2(0,3), 3, color.white)
end
```

### DrawLine(start `vec2`, end `vec2`, color `color`)
Belirtilen rengi kullanarak, konum başlangıcından konum sonuna kadar bir çizgi çizer.

### DrawCircle(position `vec2`, radius `number`, color `color`)
Belirtilen konumda, belirtilen yarıçapta, belirtilen renkte boş bir daire çizer.

### FillCircle(position `vec2`, radius `number`, color `color`)
Belirtilen konumda, belirtilen yarıçapa sahip, belirtilen renkte içi dolu bir daire çizer.

### DrawRect(position1 `vec2`, position2 `vec2`, color `color`)
Konum1'den konum2'ye belirtilen renkte boş bir dikdörtgen çizer.

### FillRect(position1 `vec2`, position2 `vec2`, color `color`)
Konum1'den konum2'ye belirtilen renkte doldurulmuş bir dikdörtgen çizer.

### DrawTriangle(position1 `vec2`, position2 `vec2`, position3 `vec2`, color `color`)
Belirtilen renkte, konum1, konum2 ve konum3'te köşeleri olan boş bir üçgen çizer.

### FillTriangle(position1 `vec2`, position2 `vec2`, position3 `vec2`, color `color`)
Belirtilen renkte, konum1, konum2 ve konum3'te köşeleri olan dolu bir üçgen çizer.

<img src="../../../assets/docs/VideoChip/ExampleImageDrawing.png" width="200" align="right">

### DrawSprite(position `vec2`, spriteSheet `SpriteSheet`, spriteX `number`, spriteY `number`, tintColor `color`, backgroundColor `color`)
Model Sayfasından belirli bir hareketli grafik çerçevesi çizer. **Konum** ekrandaki pozisyon içindir. **SpriteSheet**, varlıklardan yüklenen bir "SpriteSheet"tir. **SpriteX** ve **Y**, editördeki yakınlaştırma ızgarasına dayalı olarak **(piksel değil)** hangi hareketli grafiğin çizileceğini belirler. **TintColor**, hareketli grafiği çoğaltmanıza olanak tanır (hareketli grafiği olduğu gibi çizmek için "renk.beyaz" olarak ayarlayın). **BackgroundColor** saydamlığı korumak için saydam ('color.clear') olarak ayarlanabilir.
```lua
-- Assets
local spriteSheet:SpriteSheet = gdt.ROM.User.SpriteSheets.ExampleImageAsset

-- Hardware
local video:VideoChip = gdt.VideoChip0

-- Update
function update()
	video:Clear(color.white)
	video:DrawSprite(vec2(5,5), spriteSheet, 0, 0, color.white, color.clear)
end
```
<img src="../../../assets/docs/VideoChip/ExampleImageAsset.png" style="max-width: 400px">

### DrawCustomSprite(position `vec2`, spriteSheet `SpriteSheet`, spriteOffset `vec2`, spriteSize `vec2`, tintColor `color`, backgroundColor `color`)
⚠️ **Bu özellik, Retro Gadgets 0.1.3'ten itibaren yenidir ve henüz tam olarak test edilmemiştir.**  
**spriteX** ve **spriteY** ile standart ızgarayı hesaba katmadan hareketli grafik sayfasının **bir bölümünü** çizer (**spriteOffset** ve **spriteSize** tarafından tanımlanır) **spriteOffset** ve **spriteSize** ile değiştiriliyor.

<img src="../../../assets/docs/VideoChip/SpriteFont.png" width="200" align="right">

### DrawText(position `vec2`, fontSprite `SpriteSheet`, text `string`, textColor `color`, backgroundColor `color`)
Görüntülenecek yazı tipi olarak **fontSprite**'ı kullanarak tuvale **metin** yazar. **fontSprite**, hareketli grafik düzenleyicinin içinde oluşturulabilen bir metin yazı tipini temsil eden özel bir SpriteSheet türüdür.
```lua
-- Assets
local spriteFont = gdt.ROM.System.SpriteSheets.StandardFont

-- Hardware
local video:VideoChip = gdt.VideoChip0

-- Update
function update()
	video:Clear(color.black)
	video:DrawText(vec2(5,5), spriteFont, "Hello!", color.yellow, color.clear)
end
```


### RasterSprite(position1 `vec2`, position2 `vec2`, position3 `vec2`, position4 `vec2`, spriteSheet `SpriteSheet`, spriteX `number`, spriteY `number`, tintColor `color`, backgroundColor `color` )
Konum1, konum2, konum3 ve konum4 ile tanımlanan bir dörtlü üzerinde eşleyen hareketli grafik Sayfasından belirli bir hareketli grafik çerçevesi çizer. "position1", "position2", "position3" ve "position4" konumları sırasıyla sol üst, sağ üst, sağ alt ve sol alttır. 

### RasterCustomSprite(position1 `vec2`, position2 `vec2`, position3 `vec2`, position4 `vec2`, spriteSheet `SpriteSheet`, spriteOffset `vec2`, spriteSize `vec2`, tintColor `color`, backgroundColor `color`)
⚠️ **Bu özellik, Retro Gadgets 0.1.3'ten itibaren yenidir ve henüz tam olarak test edilmemiştir.**  
Standart ızgarayı hesaba katmadan hareketli grafik sayfasının bir bölümünü ("spriteOffset" ve "spriteSize" tarafından tanımlanır) "konum1", "konum2", "konum3" ve "konum4" tarafından tanımlanan bir dörtlü üzerine çizer. `. "position1", "position2", "position3" ve "position4" konumları, "RasterSprite" ile olduğu gibi sırasıyla sol üst, sağ üst, sağ alt ve sol alttır.

### DrawRenderBuffer(position `vec2`, renderBuffer `RenderBuffer`, width `number`, height `number`)
İstenen konum, genişlik ve yükseklikte bir işleme tamponu (sözde **Webcam** bileşeninden geliyor) çizer.


## Notlar

### İlgili türler

#### `vec2`
vec2, genellikle ekran koordinatlarını işaret etmek için kullanılan iki boyutlu bir vektördür. Temelde iki sayıyı temsil eden tek bir değer. Kolayca yeni bir vec2 oluşturabilir ve ardından "x" ve "y" ile özelliklerine erişebilirsiniz.
```lua
local pos:vec2 = vec2(20,10)
print(pos.X) -- 20
print(pos.Y) -- 10
```
`vec2(0,0)` tuvalin sol üst köşesidir.

Bir de vec3 var ama genelde ekranlar için kullanılmıyor. Organizasyon için kullanabilirsiniz.

#### `color`
`color` bir rengi temsil eder ve LED'ler için veya ekrana çizim yapmak için kullanılır. Bir rengi birkaç şekilde oluşturabilirsiniz.
```lua
Color(r, g, b) -- Values 0-255
ColorRGBA(r, g, b, a) -- Alpha is also 0-255, 0 is transparent
ColorHSV(h, s, v) -- Hue is 0-360, the other values are 0-100
```
`color.blue` veya `color.black` gibi birkaç yerleşik renk vardır. Gelecekte, bunlar `renk` için özel bir sayfada listelenecektir.

Bir `renkte` `R`, `G`, `B` ve `A`ya erişebilirsiniz.

#### `SpriteSheet`
Bkz. `DrawSprite(...)`

### Example project
Yerleşik **RasterBoy** aygıtı, grafiklerin nasıl çalıştığını daha iyi anlamak için harikadır.
