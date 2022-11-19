# LedMatrix

<img src="https://docs.retrogadgets.game/api/modules/LedMatrix.png" width="200" align="right">

An LedMatrix is an 8x8 matrix of [Led](./Led.md)s. It is recommended you read the Led API for information on how individual Leds function, this module is simply a composite.

## Properties

### States - `{{boolean}}`
A 2D table of [Led](./Led.md) states. Addressed with [column][row].

### Colors - `{{color}}`
A 2D table of [Led](./Led.md) colors. Addressed with [column][row].