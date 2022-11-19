# VideoChip
[Тільки для читання]
<img src="https://docs.retrogadgets.game/api/modules/VideoChip.png" width="200" align="right">

VideoChip являє собою зображення з підключених до нього екранів, і використовується для малювання на них.

## Властивості

### Mode - `VideoChipMode`
Буферний режим, який може бути як `SingleBuffer`, так і `DoubleBuffer`. 

Єдиний буфер дозволяє працювати з одним екранним буфером, який постійно змінюється по мірі надходження нових команд. Наприклад, якщо ви намалюєте коло, воно буде надіслано прямо в буфер і негайно відобразиться на екрані. Однак, з DoubleBuffer ви маєте справу з двома різними буферами відео, які регулярно чергуються. Кожного кадру буфер, який ви редагуєте, змінюється; ви можете редагувати буфер A, в той час як буфер B проектується на екрани, до яких підключений чіп. У наступному кадрі зміни в буфері A будуть представлені на екрані (екранах), в той час як будь-які інші зміни для цього кадру будуть внесені в буфер B. Як правило, це не впливає на спосіб відображення відео, але якщо ви відчуваєте мерехтіння, відставання або заїкання при використанні SingleBuffer, вам слід переключитися на DoubleBuffer.

### Height - `number` **[Тільки для читання]**
Висота в пікселях буфера рендерингу. Область враховує всі дисплеї, підключені до даного VideoChip.

### Width - `number` **[Тільки для читання]**
Ширина в пікселях буфера рендерингу. Область враховує всі дисплеї, підключені до даного VideoChip.

## Methods

### Clear(color `color`)
Очищає всю область зображування вказаним **кольором**. Зазвичай використовується перед малюванням кожного кадру.
```lua
local video:VideoChip = gdt.VideoChip0

function update()
	video:Clear(color.white)
	-- <...>
end
```

### SetPixel(position `vec2`, color `color`)
Встановлює піксель у вказаній позиції у вказаний **колір**.

<img src="../../../assets/docs/VideoChip/PixelGrid.png" width="200" align="right">

### DrawPointGrid(gridOffset `vec2`, dotsDistance `number`, color `color`)
Малює пунктирну сітку на **всій області відображення**, зі зміщенням. Параметр dotsDistance виражає відстань у пікселях по обох осях між точками. Це дивна функція, але її можна використовувати для фонів.
```lua
local video:VideoChip = gdt.VideoChip0

function update()
	video:Clear(color.blue)
	video:DrawPointGrid(vec2(0,3), 3, color.white)
end
```

### DrawLine(start `vec2`, end `vec2`, color `color`)
Малює лінію від початку позиції до кінця позиції, використовуючи вказаний колір.

### DrawCircle(position `vec2`, radius `number`, color `color`)
Малює порожнє коло в заданій позиції, з заданим радіусом, заданим кольором.

### FillCircle(position `vec2`, radius `number`, color `color`)
Малює заповнене коло в заданій позиції, з заданим радіусом, заданим кольором.

### DrawRect(position1 `vec2`, position2 `vec2`, color `color`)
Малює порожній прямокутник з position1 в position2 заданим кольором.

### FillRect(position1 `vec2`, position2 `vec2`, color `color`)
Малює заповнений прямокутник з position1 в position2 заданим кольором.

### DrawTriangle(position1 `vec2`, position2 `vec2`, position3 `vec2`, color `color`)
Малює порожній трикутник з вершинами в position1, position2 та position3 заданим кольором.

### FillTriangle(position1 `vec2`, position2 `vec2`, position3 `vec2`, color `color`)
Малює заповнений трикутник з вершинами в position1, position2 та position3 заданим кольором.

<img src="../../../assets/docs/VideoChip/ExampleImageDrawing.png" width="200" align="right">

### DrawSprite(position `vec2`, spriteSheet `SpriteSheet`, spriteX `number`, spriteY `number`, tintColor `color`, backgroundColor `color`)
Малює певний спрайт з таблиці спрайтів. **Position** - позиція на екрані. **SpriteSheet** - це `SpriteSheet`, завантажений з ресурсів. **SpriteX** та **Y** задають зміщення з якого місця малювати спрайт, базуючись на сітці масштабування в редакторі **(не пікселі)**. **TintColor** дозволяє помножити колір спрайту ( встановіть значення `color.white`, щоб намалювати спрайт власним кольором). **BackgroundColor** можна встановити прозорим (`color.clear`) для збереження прозорості.
```lua
-- Ресурси
local spriteSheet:SpriteSheet = GetSpriteSheet("ExampleImageAsset")

-- Апаратне забезпечення
local video:VideoChip = gdt.VideoChip0

-- Update
function update()
	video:Clear(color.white)
	video:DrawSprite(vec2(5,5), spriteSheet, 0, 0, color.white, color.clear)
end
```
<img src="../../../assets/docs/VideoChip/ExampleImageAsset.png" style="max-width: 400px">

<img src="../../../assets/docs/VideoChip/SpriteFont.png" width="200" align="right">

### DrawText(position `vec2`, fontSprite `SpriteSheet`, text `string`, textColor `color`, backgroundColor `color`)
Пише **текст** на екрані, використовуючи **fontSprite** як шрифт для відображення. **fontSprite** - це спеціальний вид SpriteSheet, що представляє текстовий шрифт, який не може бути створений звичайним чином. Таким чином, єдиний шрифт, який можна використовувати, завантажується через `local spriteFont = GetSpriteSheet("Builtin/StandardFont")`.
```lua
-- Ресурси
local spriteFont = GetSpriteSheet("Builtin/StandardFont")

-- Апаратне забезпечення
local video:VideoChip = gdt.VideoChip0

-- Update
function update()
	video:Clear(color.black)
	video:DrawText(vec2(5,5), spriteFont, "Hello!", color.yellow, color.clear)
end
```


### RasterSprite(position1 `vec2`, position2 `vec2`, position3 `vec2`, position4 `vec2`, spriteSheet `SpriteSheet`, spriteX `number`, spriteY `number`, tintColor `color`, backgroundColor `color` )
Малює **цілий сторінку спрайтів**, розміщуючи її на квадраті, позначеному position1, position2, position3 та position4.

### DrawRenderBuffer(position `vec2`, renderBuffer `RenderBuffer`, width `number`, height `number`)
Малює буфер рендерингу (імовірно, з компоненту **Webcam**) у потрібному положенні, ширині та висоті.


## Зауваження

### Суміжні типи

#### `vec2`
vec2 - двовимірний вектор, зазвичай використовується для вказівки на координати екрану. По суті, це єдине значення, яке представляє два числа. Ви можете легко створити новий vec2, а потім отримати доступ до його властивостей за допомогою `x` і `y`.
```lua
local pos:vec2 = vec2(20,10)
log(tostring(pos.X)) -- 20
log(tostring(pos.Y)) -- 10
```
`vec2(0,0)` це верхній лівий кут полотна.

Існує також vec3, але він зазвичай не використовується для екранів. Ви можете використовувати його для систематизації.

#### `color`
`color` представляє колір і використовується для світлодіодів або для малювання на екрані. Ви можете створити колір кількома способами.
```lua
Color(r, g, b) -- Значення 0-255
ColorRGBA(r, g, b, a) -- Альфа також 0-255, 0 - прозорий
ColorHSV(h, s, v) -- Hue 0-360, інші значення 0-100
```
Є кілька вбудованих кольорів, таких як `color.blue` або `color.black`. У майбутньому вони будуть перераховані на спеціальній сторінці для `color`.

Ви можете отримати доступ до `R`, `G`, `B` та `A` в залежності від кольору.

#### `SpriteSheet`
Дивіться `DrawSprite(...)`

### Приклад проекту
Вбудований гаджет **RasterBoy** чудово підходить для кращого розуміння того, як працює графіка. 