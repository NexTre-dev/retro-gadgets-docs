# Webcam

<img src="https://docs.retrogadgets.game/api/modules/Webcam.png" width="200" align="right">

Web kamerası, Retro Gadget'ları çalıştıran cihazda gerçek web kamerasının bir "RenderBuffer"ını almanızı sağlar. Bunu, kamera beslemesini [VideoChip](../misc/VideoChip.md) içeren bir ekrana çizmek için kullanabilirsiniz.


## Özellikler

### RenderTarget - `VideoChip`
Bu kameranın içerik akışını yaptığı [VideoChip](../misc/VideoChip.md). Yalnızca bu VideoChip, bu Web Kamerası tarafından alınan "RenderBuffer"ı çizebilir.

### AccessDenied - `boolean`
Bu araca çok amaçlı araçtaki İzinler panelinden kamera izni verilmediyse. (Genelde Ekrana Kilit Simgesiyle Yansır)

### IsActive - `boolean`

### IsAvailable - `boolean`
Ana bilgisayarda kamera varsa kullanılabilir.


## Metodlar

### GetRenderBuffer() `RenderBuffer`
`RenderBuffer` kamerasını alır. Elde edilen oluşturma arabelleği daha sonra [VideoChip](../misc/VideoChip.md) modülünün 'DrawRenderBuffer' yöntemine beslenebilir. **Yalnızca "RenderTarget" olarak tanımlanan VideoChip arabelleği çizebilir.**

## Event - `WebcamIsActiveEvent`
[CPU](../misc/CPU.md) olay sisteminin parçası olarak yayılan olay.

Web Kamerası etkin durumu değiştirildiğinde gönderilir.

### IsActive - `boolean`
### IsAvailable - `boolean`
### AccessDenied - `boolean`