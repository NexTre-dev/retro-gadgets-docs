# MagneticConnector

<img src="https://docs.retrogadgets.game/api/modules/MagneticConnector.png" width="200" align="right">

Magnetic Connectors allow separated boards to connect and disconnect at set points. Boards connected to each other with a powered magnet (light green, toggleable with the button) will be picked up as one.

## Properties

### AttachedConnector - `MagneticConnector` **[Read only]**
The `MagneticConnector` connected to this one.

### ButtonState - `boolean` **[Read only]**
The state of the physical button on the connector. `true` if the button is being held.

### IsConnected - `boolean` **[Read only]**
`true` if the connector is connected to another one.

### Motherboard - `Motherboard` **[Read only]**
The `Motherboard` attached with this `MagneticConnector`.

### Type - `string` **[Read only]**
Always returns `MagneticConnectorEvent`.

## Event - `MagneticConnectorEvent`
The event emitted as part of the [CPU](./CPU.md) event system.

Sent when a `MagneticConnector` is connected to another.

### IsConnected - `boolean` **[Read only]**
`true` if the connector is connected to another one. The only indication of connectivity.

### Type - `string` **[Read only]**
Always return `MagneticConnectorEvent`.
