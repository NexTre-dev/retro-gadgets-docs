# KeyboardChip

<img src="https://docs.retrogadgets.game/api/modules/KeyboardChip.png" width="200" align="right">

Мікросхема KeyboardChip використовується для отримання вхідних даних з підключеної клавіатури. При підключенні до чогось, що може взаємодіяти, він може дозволити компоненту керувати за допомогою клавіатури.

**_❔ Цей компонент все ще перебуває в процесі розробки._**

## Methods

<!-- TODO: Поясніть ці методи. -->
### GetButton(name `InputName`) `InputSource`

### GetButtonAxis(name `InputName`) `InputSource`

## Input Names **[Read only]**
Імена входів можна отримати за допомогою `KeyboardChip.`nameOfInput, і вони перераховані нижче.
- `Return`
- `Space`
- `LeftArrow`
- `RightArrow`
- `DownArrow`
- `UpArrow`
- `Backspace`
- `Escape`
- `Tab`
- `Clear`
- `Pause`
- `Exclaim`
- `DoubleQuote`
- `Hash`
- `Dollar`
- `Percent`
- `Ampersand`
- `Quote`
- `LeftParen`
- `RightParen`
- `Asterisk`
- `Plus`
- `Comma`
- `Minus`
- `Period`
- `Slash`
- `Alpha0`
- `Alpha1`
- `Alpha2`
- `Alpha3`
- `Alpha4`
- `Alpha5`
- `Alpha6`
- `Alpha7`
- `Alpha8`
- `Alpha9`
- `Colon`
- `Semicolon`
- `Less`
- `Equals`
- `Greater`
- `Question`
- `At`
- `LeftBracket`
- `Backslash`
- `RightBracket`
- `Caret`
- `Underscore`
- `BackQuote`
- `A`
- `B`
- `C`
- `D`
- `E`
- `F`
- `G`
- `H`
- `I`
- `J`
- `K`
- `L`
- `M`
- `N`
- `O`
- `P`
- `Q`
- `R`
- `S`
- `T`
- `U`
- `V`
- `W`
- `X`
- `Y`
- `Z`
- `LeftCurlyBracket`
- `Pipe`
- `RightCurlyBracket`
- `Tilde`
- `Delete`
- `Keypad0`
- `Keypad1`
- `Keypad2`
- `Keypad3`
- `Keypad4`
- `Keypad5`
- `Keypad6`
- `Keypad7`
- `Keypad8`
- `Keypad9`
- `KeypadPeriod`
- `KeypadDivide`
- `KeypadMultiply`
- `KeypadMinus`
- `KeypadPlus`
- `KeypadEnter`
- `KeypadEquals`
- `Insert`
- `Home`
- `End`
- `PageUp`
- `PageDown`
- `F1`
- `F2`
- `F3`
- `F4`
- `F5`
- `F6`
- `F7`
- `F8`
- `F9`
- `F10`
- `F11`
- `F12`
- `F13`
- `F14`
- `F15`
- `Numlock`
- `CapsLock`
- `ScrollLock`
- `RightShift`
- `LeftShift`
- `RightControl`
- `LeftControl`
- `RightAlt`
- `LeftAlt`
- `RightCommand`
- `LeftCommand`
- `AltGr`
- `Help`
- `Print`
- `SysReq`
- `Break`
- `Menu`

## Зауваження

### Конфігурація мультитула

Іноді компонентами можна керувати безпосередньо з мікросхеми клавіатури без необхідності прописувати хитросплетіння в коді.

<img src="../../../assets/docs/KeyboardChip/KeyboardInput.png">

Використовуючи мультитул, ви можете надати компонентам, таким як Sticks, вхідний сигнал InputSourceX та вхідний сигнал InputSourceY, які будуть керувати тим, як кнопка клавіатури маніпулює осями, по яких вона рухається. При виборі _NEGATIVE_ і _POSITIVE_ входу, NEGATIVE повинен бути той, який переміщує стік вниз або вліво; в основному, в негативному напрямку. POSITIVE - навпаки. Зіставивши S з NEGATIVE і W з POSITIVE, ми можемо переміщати стік вгору і вниз за допомогою клавіш W (вгору) і S (вниз). Цей метод є абстракцією ручної техніки, що використовується в коді за допомогою власних методів KeyboardChip, і, як правило, набагато простіший і швидший. Однак, він може не забезпечувати потрібної вам розширюваності, бути занадто обмеженим або не застосовуватися до об'єкта. У такому випадку краще зробити це вручну у Lua-файлі.
