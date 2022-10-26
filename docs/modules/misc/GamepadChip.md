# GamepadChip

<img src="https://docs.retrogadgets.game/api/modules/GamepadChip.png" width="200" align="right">

The GamepadChip is used to get input from a connected gamepad or controller.

***⚠️ I don't know how this thing works and it has no official documentation.***

## Properties

### GamepadIndex - `number` **[Read only]**

## Methods

### GetButton(name `InputName`) `InputSource`

### GetAxis(name `InputName`) `InputSource`

### GetButtonAxis(name `InputName`) `InputSource`

## Input Names **[Read only]**
Input names can be accessed by `GamepadChip.`nameOfInput, and are listed below.
 - `LeftStickX`
 - `LeftStickY`
 - `RightStickX`
 - `RightStickY`
 - `ActionBottomRow1`
 - `a`
 - `ActionBottomRow2`
 - `b`
 - `ActionBottomRow3`
 - `c`
 - `ActionTopRow1`
 - `x`
 - `ActionTopRow2`
 - `y`
 - `ActionTopRow3`
 - `z`
 - `LeftShoulder1`
 - `LeftBumper`
 - `LeftShoulder2`
 - `LeftTrigger`
 - `RightShoulder1`
 - `RightBumper`
 - `RightShoulder2`
 - `RightTrigger`
 - `Center1`
 - `Back`
 - `Center2`
 - `Start`
 - `Center3`
 - `Guide`
 - `LeftStickButton`
 - `RightStickButton`
 - `DPadUp`
 - `DPadRight`
 - `DPadDown`
 - `DPadLeft`