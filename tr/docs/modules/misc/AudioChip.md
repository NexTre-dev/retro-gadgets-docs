# Audio Chip

<img src="https://docs.retrogadgets.game/api/modules/AudioChip.png" width="200" align="right">

AudioChip, ses çalmak için kullanılır. AudioChip'lerin şu anda hoparlörlere bağlanmasına gerek yoktur.

**⚠️ Bu sayfa eksik ve doğrulanmamış.**

## Özellikler

### ChannelsCount - `number` **[Read only]**

Bu AudioChip için kullanılabilir kanal sayısı. Her kanal bağımsız olarak bir ses örneğini çalabilir. Halihazırda kullanılmakta olan bir kanalda bir ses çalarsanız, bu ses kesilir ve yeni sesle değiştirilir.

Kullanılabilir kanal sayısı çipin boyutuna bağlıdır. Bu değerler tam sürümde değişebilir.

|  Boyut | Kanallar |
|-------:|:---------|
|  Küçük | 4        |
|  Orta  | 16       |
|  Büyük | 32       |

```lua
local audio:AudioChip = gdt.AudioChip0

print(audio.ChannelsCount) -- Yukaridaki tablodan uygun sayiyi verir
```

### Volume - `number`
Küresel AudioChip hacmi.


## Metodlar

### GetSpectrumData(channel `number`) `number[]`
Bir **kanalın** ses spektrumu değerlerini döndürür. Her biri farklı bir frekansın değerini ifade eden 64 farklı sayı değerinden oluşan bir tablo içerir.

### GetDspTime() `number`
Geçerli dahili AudioChip'in DSP süresini döndürür. PlayScheduled yöntemiyle birlikte kullanılması amaçlanmıştır. Döndürülen sayı saniye cinsinden ifade edilir.

### Play(audioSample `AudioSample`, channel `number`)
Belirli bir **kanalda** hemen bir `AudioSample` oynatır.

### PlayScheduled(audioSample `AudioSample`, channel `number`, dspTime `number`)
Belirli **kanalda** saniye cinsinden ifade edilen belirli bir DSP zamanında bir `AudioSample` oynatmayı planlayın. `GetDspTime()` konusuna bakın.

### PlayLoop(audioSample `AudioSample`, channel `number`)
Belirli bir **kanalda** hemen bir `AudioSample` oynatır ve onu döngüye alır.

### PlayLoopScheduled(audioSample `AudioSample`, channel `number`, dspTime `number`)
Bir `AudioSample`ın belirli bir DSP zamanında, belirli bir kanalda saniye cinsinden ifade edilerek oynatılmasını programlayın ve onu döngüye alın.

### Stop(channel `number`)
Belirli bir **kanal** üzerinde çalan tüm sesleri durdurur.

### Pause(channel `number`)
Belirli bir **kanal** üzerinde sesi duraklatın.

### UnPause(channel `number`)
Sesi belirli bir **kanal** üzerinde sürdürür.

### IsPlaying(channel `number`) `boolean`
**kanal** şu anda ses çalıyorsa `true` değerini döndürür.

### IsPaused(channel `number` ) `boolean`
**kanal** şu anda duraklatılmışsa `true` değerini döndürür.

### GetPlayTime(channel `number` ) `number`
**kanalın** geçerli oynatma süresini saniye cinsinden ifade ederek döndürür.

### SeekPlayTime(time `number`, channel `number`)
Belirli **kanal** için oynatma kafasının geçerli konumunu saniye cinsinden ayarlar.

### SetChannelVolume(volume `number`, channel `number`)
Bir **kanal** için geçerli ses düzeyini 0-100 aralığında ayarlar.

### GetChannelVolume(channel `number`) `number`
Bir **kanal**, 0-100 aralığı için geçerli ses düzeyini alır.

### SetChannelPitch(pitch `number`, channel `number`)

Bir **kanal** için perdeyi ayarlar. Çarpan görevi görür. 1 değeri, bir örnek için varsayılan perde anlamına gelir; 2 değeri, örneği bir oktav daha yüksek çalar.

### GetChannelPitch(channel `number`) `number`
Bir **kanalın** geçerli perdesini alır.