# Keypad

<img src="https://docs.retrogadgets.game/api/modules/Keypad.png" width="200" align="right">

Keypads are a grid of buttons, which report state in several 4x4 tables. They can be given symbols with the multitool, but unlike most buttons are not LEDs.

## Properties

### ButtonsState - `{{boolean}}` **[Read only]**
A multi-dimensional table mapping the state of each button to a boolean value.
The table must be addressed with [column][row]. Each table cell returns `true` if the corresponding button is being held down, otherwise `false`.

### ButtonsDown - `{{boolean}}` **[Read only]**
Like `ButtonsState`, but only `true` for the frame the corresponding button is initially held down.

### ButtonsUp - `{{boolean}}` **[Read only]**
Like `ButtonsState`, but only `true` for the frame the corresponding button is released.

## Hardware
These properties can be set with the multitool inspector, but cannot be set in software.

### Symbols - `{{Symbol}}` *(hardware)*
A table of symbols to display on the corresponding buttons. Symbols can be painted with the paint tool to be a different color than the background, but all symbols in a Keypad will be the same color.
