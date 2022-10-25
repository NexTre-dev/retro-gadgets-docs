# Audio Chip

<img src="https://docs.retrogadgets.game/api/modules/AudioChip.png" width="200" align="right">

The AudioChip is used to play audio. AudioChips do not currently need to be connected to speakers.

⚠️ This page is incomplete and unverified.

## Properties

### ChannelsCount - `number` **[Read only]**
Number of available channels for this AudioChip. Each channel can independently play an audio sample.

The number of channels available depends on the size of the chip. These values may change in the full release.

|   Size | Channels |
|-------:|:---------|
|  Small | 4        |
| Medium | 16       |
|  Large | 32       |

```lua
local audio:AudioChip = gdt.AudioChip0

log(tostring(audio.ChannelsCount)) --Returns the appropriate number from the table above
```

### Volume - `number`
The global AudioChip volume.


## Methods

### GetSpectrumData(channel `number`) `number[]`
Returns the audio spectrum values of a **channel**. Contains a table of 64 different number values, each one expressing the value of a different frequency.

### GetDspTime() `number`
Returns the current internal AudioChip's DSP time. It is meant to be used in combination with the PlayScheduled method. The returned number is expressed in seconds.

### Play(audioSample `AudioSample`, channel `number`)
Immediately plays an `AudioSample` on a specific **channel**.

### PlayScheduled(audioSample `AudioSample`, channel `number`, dspTime `number`)
Schedule the play of an `AudioSample` at a specific DSP time, expressed in seconds, on the specific **channel**. See `GetDspTime()`.

### PlayLoop(audioSample `AudioSample`, channel `number`)
Immediately plays an `AudioSample` on a specific **channel**, looping it.

### PlayLoopScheduled(audioSample `AudioSample`, channel `number`, dspTime `number`)
Schedule the play of an `AudioSample` at a specific DSP time, expressed in seconds, on the specific channel, looping it.

### Stop(channel `number`)
Stops any audio playing on a specific **channel**.

### Pause(channel `number`)
Pause the audio on a specific **channel**.

### UnPause(channel `number`)
Resumes the audio on a specific **channel**.

### IsPlaying(channel `number`) `boolean`
Returns `true` if the **channel** is currently playing audio.

### IsPaused(channel `number` ) `boolean`
Returns `true` if the **channel** is currently paused.

### GetPlayTime(channel `number` ) `number`
Returns the current play time of the **channel**, expressed in seconds.

### SeekPlayTime(time `number`, channel `number`)
Sets the current position of the play head, for the specific **channel**, expressed in seconds.

### SetChannelVolume(volume `number`, channel `number`)
Sets the current volume for a **channel**, 0-100 range.

### GetChannelVolume(channel `number`) `number`
Gets the current volume for a **channel**, 0-100 range.

### SetChannelPitch(pitch `number`, channel `number`)

Sets the pitch for a **channel**. Acts as a multiplier. A value of 1 means the default pitch for a sample, a value of 2 plays the sample one octave higher.

### GetChannelPitch(channel `number`) `number`
Gets the current pitch of a **channel**.
