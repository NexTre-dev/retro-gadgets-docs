# Webcam 网络摄像头

<img src="https://docs.retrogadgets.game/api/modules/Webcam.png" width="200" align="right">

网络摄像头允许您在运行Retro Gadgets的设备上获取真实摄像头的`RenderBuffer`。可以使用此功能，通过[VideoChip-视频芯片](../misc/VideoChip.md)将摄像头数据绘制到屏幕上。

## 属性

### RenderTarget 渲染目标 - `VideoChip`
接收摄像头传输数据的[VideoChip-视频芯片](../misc/VideoChip.md)。 只有这个视频芯片可以渲染摄像头传输的`RenderBuffer`。


## 方法

### GetRenderBuffer() 获取渲染数据 `RenderBuffer`
获取摄像头的`RenderBuffer`。获取的数据可以作为[VideoChip-视频芯片](../misc/VideoChip.md)模块的`DrawRenderBuffer`方法的参数。**只有设置为`RenderTarget`的视频芯片可以获取和绘制数据。**