# Audio Chip

<img src="https://docs.retrogadgets.game/api/modules/AudioChip.png" width="200" align="right">

AudioChip використовується для відтворення звуку. Наразі AudioChips не потрібно підключати до динаміків.

⚠️ Ця сторінка є неповною та неперевіреною.

## Властивості

### ChannelsCount - `number` **[Тільки для читання]**

Кількість доступних каналів для даного AudioChip. Кожен канал може незалежно відтворювати звуковий файл. При відтворенні звуку на каналі, який вже використовується, він буде замінений новим звуком.

Кількість доступних каналів залежить від розміру мікросхеми. Ці значення можуть змінитися в повному релізі.

| Розмір  |  Канали  |
|--------:|:---------|
|  Малий  | 4        |
|Середній | 16       |
| Великий | 32       |

```lua
local audio:AudioChip = gdt.AudioChip0

log(tostring(audio.ChannelsCount)) -- Повертає відповідне число з вищенаведеної таблиці
```

### Volume - `number`
Глобальна гучність звуку AudioChip.


## Методи

### GetSpectrumData(channel `number`) `number[]`
Повертає значення звукового спектру **каналу**. Містить таблицю з 64 різних числових значень, кожне з яких виражає значення різної частоти.

### GetDspTime() `number`
Повертає поточний внутрішній час DSP AudioChip. Призначений для використання у поєднанні з методом PlayScheduled. Число, що повертається, виражається в секундах.

### Play(audioSample `AudioSample`, channel `number`)
Негайно відтворює `AudioSample` на певному **каналі**.

### PlayScheduled(audioSample `AudioSample`, channel `number`, dspTime `number`)
Запланувати відтворення `AudioSample` на певний час DSP, виражений у секундах, на певному **каналі**. Дивіться `GetDspTime()`.

### PlayLoop(audioSample `AudioSample`, channel `number`)
Негайно відтворює `AudioSample` на певному **каналі**, зациклюючи його.

### PlayLoopScheduled(audioSample `AudioSample`, channel `number`, dspTime `number`)
Запланувати відтворення `AudioSample` в певний час DSP, виражений в секундах, на певному каналі, зацикливши його.

### Stop(channel `number`)
Зупиняє відтворення будь-якого аудіо на певному **каналі**.

### Pause(channel `number`)
Призупинити відтворення звуку на певному **каналі**.

### UnPause(channel `number`)
Відновлює відтворення звуку на певному **каналі**.

### IsPlaying(channel `number`) `boolean`
Повертає `true`, якщо **канал** в даний час відтворює аудіо.

### IsPaused(channel `number` ) `boolean`
Повертає `true`, якщо **канал** в даний момент знаходиться на паузі.

### GetPlayTime(channel `number` ) `number`
Повертає поточний час відтворення **каналу**, виражений у секундах.

### SeekPlayTime(time `number`, channel `number`)
Встановлює поточну позицію доріжки відтворення для певного **каналу**, виражену в секундах.

### SetChannelVolume(volume `number`, channel `number`)
Встановлює поточну гучність для **каналу**, діапазон 0-100.

### GetChannelVolume(channel `number`) `number`
Отримує поточну гучність для **каналу**, діапазон 0-100.

### SetChannelPitch(pitch `number`, channel `number`)

Встановлює висоту тону для **каналу**. Діє як множник. Значення 1 означає висоту звуку за замовчуванням для семплу, значення 2 відтворює звук на одну октаву вище.

### GetChannelPitch(channel `number`) `number`
Отримує поточну висоту тону **каналу**.
