# Сегментний дисплей

<img src="https://docs.retrogadgets.game/api/modules/SegmentDisplay.png" width="200" align="right">

## Властивості

### States - `{{boolean}}`
Таблиця, яка відображає увімкнений/вимкнений стан усіх світлодіодів на дисплеї.

Доступ до кожного сегменту таблиці можна отримати, починаючи з верхньої частини дисплея до вказаного періоду за годинниковою стрілкою, як показано на зображенні нижче.

<img src="../../../assets/docs/SegmentDisplay/ReferenceSegmentDisplay.png">

Таким чином, якщо ви хочете відобразити, наприклад, 2, вам потрібно буде увімкнути 1, 2, 4, 5 і 7.

<img src="../../../assets/docs/SegmentDisplay/ExampleSegmentDisplay.png" width="300">

### Colors - `{{color}}`
Таблиця, яка відображає колір всіх світлодіодів на дисплеї.