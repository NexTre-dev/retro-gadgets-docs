# Screen

<img src="https://docs.retrogadgets.game/api/modules/Screen.png" width="200" align="right">

Ekran modülü, [VideoChip](../misc/VideoChip.md) görsellerini görüntüler. **Ekranlar sorunsuz bir şekilde yan yana yerleştirilebilir** ve daha büyük ekranlar oluşturmak için aynı VideoChip'e atanabilir. **Ekran kompozitlerinin kare olması gerekmez.**

## Özellikler

### VideoChip - `VideoChip`
Bu ekranın ait olduğu VideoChip. Daha büyük bir ekran oluşturmak için aynı VideoChip'e birden fazla ekran atanabilir. _Bu, dinamik olarak ayarlanabilir, ancak genellikle multitool denetçisi ile ayarlanır._

### Offset - `vec2`
Bu ekranın sol üst köşesi ile VideoChip kanvasının sol üst köşesi arasındaki fark.
### Width - `number`
### Height - `number`