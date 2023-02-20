# Knob

<img src="https://docs.retrogadgets.game/api/modules/Knob.png" width="200" align="right">

Düğmeler, tamamen sola işaret etmekten (-100 değeri) tamamen sağa işaret etmeye (100 değeri) kadar açı yapan 1D giriş cihazlarıdır. Düğmeler, fareyi sola ve sağa sürükleyerek ayarlanır. Şu anda, Düğmeler [kaydırıcılar](Slider.md) gibi davranır ve yalnızca 1B ekseni temsil eder, **aşağıyı gösteremezler**.

## Özellikler

### Value - `number` 
-100 (tamamen sola dönük), 0 (tamamen yukarıyı gösterir) ile 100 (tamamen sağı gösterir) arasında değişen düğmenin konumu. Düğmeyi programlı olarak hareket ettirmek için bunu yazılımdan ayarlayabilirsiniz. Gerçekçilik için, Düğmede yapılan değişiklikleri canlandırmanız önerilir, aksi halde yeni değerlere kolayca yapışacaktır.

### IsMoving - `boolean` **[Read only]**
`true`, kullanıcı o anda Düğmeyi fareyle tutuyorsa. Kaydırma tekerleği ile bir değer değiştirildiğinde ayarlanmadığından bu, değişiklikleri algılamak için kullanılmamalıdır. Bunun yerine, örneğin, hala etkileşim halindeyken düğmeyi belirli bir değere ayarlamaya çalışmaktan kaçınmak için kullanılabilir.

## Event - `KnobValueChangeEvent`
[CPU](../misc/CPU.md) olay sisteminin parçası olarak yayılan olay.

Değer değiştirildiğinde gönderilir.

### Value - `number`