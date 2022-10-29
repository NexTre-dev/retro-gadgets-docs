# SegmentDisplay

<img src="https://docs.retrogadgets.game/api/modules/SegmentDisplay.png" width="200" align="right">

## Properties 

### States - `{{boolean}}`
A table that maps the lit/unlit state of all the Leds in the display.

Each segment can be accessed in the table starting from the top of the display to the period in the display in a clockwise fashion as shown in the image below.

<img src="../../../assets/docs/ReferenceSegmentDisplay.png">

So if you wanted to display 2 for example, you would need to turn on 1, 2, 4, 5, and 7.

<img src="../../../assets/docs/ExampleSegmentDisplay.png" width="300">

### Colors - `{{color}}`
A table that maps the color of all the Leds in the display.