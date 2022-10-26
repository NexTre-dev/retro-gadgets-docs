# Led

<img src="https://docs.retrogadgets.game/api/modules/Led.png" width="200" align="right">

The Led is a basic output device capable of displaying a color. Light emitted by the Led is physical and will light nearby modules and objects.

## Properties

### State - `boolean`
Whether the Led should be on. If `true`, the Led emits light of `Color`. If `false`, the Led does not emit light. The initial value can be set with the multitool inspector.

Not emitting light is similar to trying to emit light with the color black.

### Color - `color`
The color of the Led, which will be emitted when `State` is `true`. This can be set programmatically at any time. The initial value can be set with the multitool inspector.