# Webcam

<img src="https://docs.retrogadgets.game/api/modules/Webcam.png" width="200" align="right">

The webcam allows you to get a `RenderBuffer` of the real webcam on the device running Retro Gadgets. You can use this to draw the camera feed to a screen with a [VideoChip](../misc/VideoChip.md).


## Properties

### RenderTarget - `VideoChip`
The [VideoChip](../misc/VideoChip.md) this camera is streaming contents to. Only this VideoChip can draw the `RenderBuffer` retrieved by this Webcam.

### AccessDenied - `boolean`
If this gadget has not been granted camera permission from the Permissions panel in the multitool.

### IsActive - `boolean`

### IsAvailable - `boolean`
If the host computer has a camera able to be used.


## Methods

### GetRenderBuffer() `RenderBuffer`
Gets the camera `RenderBuffer`. The render buffer obtained can then be fed to the `DrawRenderBuffer` method of the [VideoChip](../misc/VideoChip.md) module. **Only the VideoChip defined as `RenderTarget` can draw the buffer.**

## Event - `WebcamIsActiveEvent`
The event emitted as part of the [CPU](../misc/CPU.md) event system.

Sent when the Webcam active state is changed.

### IsActive - `boolean`
### IsAvailable - `boolean`
### AccessDenied - `boolean`