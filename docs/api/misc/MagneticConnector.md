# MagneticConnector

<img src="https://docs.retrogadgets.game/api/modules/MagneticConnector.png" width="200" align="right">

Magnetic connects allow separated boards to connect and disconnect at set points. Unfortunately, magnetic connectors are essentially just magnets and do not report what they're connected to. Boards connected to each other with a powered magnet (light green, toggleable with the button) will be picked up as one.

ℹ️ By knowing the state of all connectors, it is possible in certain configurations to know the arrangement of connectable boards.

## Properties

### ButtonState - `boolean` **[Read only]**
The state of the physical button on the connector. `true` if the button is being held.

### IsConnected - `boolean` **[Read only]**
`true` if the connector is connected to another one. The only indication of connectivity. 

## Remarks
This should hopefully report more information in the full release. For now, have a limited set of checkable configurations, or keep track of all connectors and detect which two switch when boards are connected or disconnected, in order to track what is connected to what.