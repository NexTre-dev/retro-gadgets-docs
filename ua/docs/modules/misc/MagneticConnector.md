# Магнітний з'єднувач

<img src="https://docs.retrogadgets.game/api/modules/MagneticConnector.png" width="200" align="right">

Магнітні з'єднувачі дозволяють з'єднувати і роз'єднувати окремі плати в заданих точках. На жаль, магнітні роз'єми - це, по суті, просто магніти, і вони не повідомляють, до чого вони підключені. Плати, з'єднані одна з одною за допомогою магніту з живленням (світло-зеленого кольору, перемикається кнопкою), будуть сприйматися як одна.

ℹ️ Знаючи стан всіх роз'ємів, можна в певних конфігураціях дізнатися розташування плат, що підключаються.

## Властивості

### ButtonState - `boolean` **[Тільки для читання]**
Стан фізичної кнопки на роз'ємі. `true`, якщо кнопка утримується.

### IsConnected - `boolean` **[Тільки для читання]**
`true`, якщо з'єднувач з'єднаний з іншим з'єднувачем. 

## Зауваження
Сподіваємось, що в повній версії буде надано більше інформації. Наразі, є обмежений набір конфігурацій, які можна перевірити, або відстежувати всі роз'єми і визначати, які два перемикаються, коли плати підключаються або відключаються, щоб відстежувати, що до чого підключено.