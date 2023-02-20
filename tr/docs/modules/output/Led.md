# Led

<img src="https://docs.retrogadgets.game/api/modules/Led.png" width="200" align="right">

Led, bir rengi gösterebilen temel bir çıktı cihazıdır. Led tarafından yayılan ışık fizikseldir ve yakındaki modülleri ve nesneleri aydınlatır.

## Özellikler

### State - `boolean`
Led'in açık olup olmadığı. `true` ise, Led `color` ışığı yayar. `false` ise, Led ışık yaymaz. Başlangıç ​​değeri multitool denetçisi ile ayarlanabilir.

Işık yaymamak, siyah renkle ışık yaymaya benzer.

### Color - `color`
`State` `true` olduğunda yayılacak olan Led'in rengi. Bu, herhangi bir zamanda programlı olarak ayarlanabilir. Başlangıç ​​değeri multitool denetçisi ile ayarlanabilir.