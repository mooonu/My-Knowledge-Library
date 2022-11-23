# Type conversion

가장 일반적인 세 가지 숫자형이 있습니다 `Int`, `Long`, `Double`. 때때로, 한 숫자형 타입의 값을 다른 숫자형 타입 변수에 할당할 필요가 있을 겁니다. 이런 경우에는 `toInt()` `toLong()` `toDouble()`라는 특별한 함수를 호출하여 타입 변환을 해야합니다.

`Int` 타입의 `num` 이라는 변수를 가지고 있다고 상상해봅시다. 당신은 제곱근을 계산하는 `sqrt` 라 불리는 함수에 num 을 사용하길 원합니다. 하지만 `sqrt` 함수는 `Int`가 아닌 `Double` 타입이 필요합니다, 따라서 type mismatch 오류를 피해가려면  `toDouble()` 을 사용해 변환해야합니다.

```kotlin
val num: Int = 100

val res: Double = sqrt(num.toDouble())
println(res) // 10.0

println(num) // 100, it is not modified
```

`toDouble()`은 변수의 타입을 수정하지 않습니다. 이 함수는 `Double` 타입의 새로운 값을 생성합니다.

It's possible to perform these operations even when the target type is larger than the source type. So it means that we can convert `Int` to `Long`. It distinguishes Kotlin from other programming languages like Java and C#. They allow assigning numbers of a smaller type to variables of a larger type without extra actions.

대상 타입이 원본 타입보다 큰 경우에도 타입 변환을 수행할 수 있습니다. 이것은 `Int` 에서 `Long` 으로 변환이 가능하다는 의미입니다.&#x20;

```kotlin
val num: Int = 100
val bigNum: Long = num.toLong() // 100
```



`Char` 는 숫자형이 아닙니다 그러나 문자 코드에 따라 숫자를 문자로 변환하거나 문자에서 숫자로 변환할 수 있습니다.\
유니코드 표에서 코드를 확인할 수 있습니다. 이 코드는 기본적으로 정수입니다.

```kotlin
val n1: Int = 125
val ch: Char = n1.toChar() // '}'
val n2: Int = ch.code      // 125
```

만약 실수 타입 `Double` 값을 가지고 있고, 이를 정수형 `Int` 또는 `Long` 으로 변환하고 싶다면:

```kotlin
val d: Double = 12.5
val n: Long = d.toLong() // 12
```

보시다시피 소수점은 깔끔하게 없어집니다.



또한 위에서 언급한 함수를 사용하여 큰 수에서 작은 수로 (`Long` 또는 `Double` 에서 `Int`) 변환할 수 있습니다.

```kotlin
val d: Double = 10.2
val n: Long = 15

val res1: Int = d.toInt() // 10
val res2: Int = n.toInt() // 15
```



그러나 `Long` 및 `Double`은 `Int` 보다 더 큰 수를 저장하기 때문에 이 변환을 통해 값이 잘릴 수 있습니다.

```kotlin
val bigNum: Long = 100_000_000_000_000

val n: Int = bigNum.toInt() // 276447232; oops
```

결과적으로 우리는 잘린 값을 받았습니다. 이 문제는 **type overflow** (**해당 타입이 표현할 수 있는 최대 범위보다 큰 수를 저장할 때 발생하는 현상)** 로 알려져 있습니다. `Int` 에서 `Short` 또는 `Byte` 로 변환할 때도 같은 오류가 발생할 수 있습니다. 그래서 만약 큰 수에서 작은 수로 변환하고 싶다면 값이 잘려서 프로그램에 문제가 생기지 않도록 조심하세요.&#x20;



### **Conversion to Short and Byte types**

알다시피 `Short` 와 `Byte` 타입은 정말 작습니다. 이 타입들은 거의 사용하지 않으며 정수를 저장하고 싶다면 `Int` 를 사용해야합니다. 왜 이렇게 해야하는지 예시를 보여드리겠습니다.

일반적으로 `toShort()` 와 `toByte()` 함수를 사용하여 이러한 형식으로 변환할 수 있습니다.\
Kotlin 1.4 부터는 `Double` 또는 `Float` 를 변환할 때 이러한 함수는 사용하지 마십시오.\
이 기능은 향후 릴리즈에서 제거됩니다. 여기서 가장 큰 문제는 변수의 크기가 작아 예상치 못한 결과를 초래할 수 있다는 것입니다. 이제 `Double` 또는 `Float`를 `Int`로 변환한 다음 결과를 `Short` 또는 `Byte`로 변환해야 합니다.

```kotlin
val floatNumber = 10f
val doubleNumber = 1.0

val shortNumber = floatNumber.toShort() // avoid this
val byteNumber = doubleNumber.toByte()  // avoid this

val shortNumber = floatNumber.toInt().toShort() // correct way
val byteNumber = doubleNumber.toInt().toByte()  // correct way
```



### **String conversion**

가끔 다른 타입의 값을 문자열로 표현하고 싶을 때가 있을 겁니다. Kotlin 은 아무 타입의 값을 문자열로 변환할 수 있는 `toString()` 함수를 제공합니다.&#x20;

```kotlin
val n = 8     // Int
val d = 10.09 // Double
val c = '@'   // Char
val b = true  // Boolean

val s1 = n.toString() // "8"
val s2 = d.toString() // "10.09"
val s3 = c.toString() // "@"
val s4 = b.toString() // "true"
```



문자열은 숫자나 불리언 값으로 변환할 수 있지만 문자는 변환할 수 없습니다.

```kotlin
val n = "8".toInt() // Int
val d = "10.09".toDouble() // Double
val b = "true".toBoolean() // Boolean
```

만약 문자열 표현 형식이 잘못된 경우 오류가 발생합니다. 그 후에는 특별한 조치를 취하지 않으면 프로그램이 중단될 것 입니다. 이는 나중에 더 다루도록 하겠습니다.



그러나 문자열에서 불리언 값으로 변경한다면 오류가 발생하지 않습니다. 만약 문자열이 `"true"` (대소문자 상관없음) 이면 `true` 값을 생성하고 아니라면 `false` 를 생성합니다.

```kotlin
val b1 = "false".toBoolean() // false
val b2 = "tru".toBoolean()   // false
val b3 = "true".toBoolean()  // true
val b4 = "TRUE".toBoolean()  // true
```



### **Demonstration**

아래 프로그램은 위에서 설명한 기능을 보여줍니다. 숫자의 문자열 표현을 읽고 여러 다른 유형으로 변환한 다음 모든 변환 결과를 출력합니다.

```kotlin
fun main() {
    val something = readln()

    val d = something.toDouble()
    val f = d.toFloat()
    val i = f.toInt()
    val b = i.toByte()

    println(d)
    println(f)
    println(i)
    println(b)
    println(something.toBoolean())
}
```

Imagine, we have the following input:

```kotlin
1000.0123456789
```

The program will output the following:

```kotlin
1000.0123456789
1000.0123
1000
-24
false
```

출력을 자세히 살펴보갰습니다. 문자열로 표시된 숫자는 적절한 형식을 가지므로 `Double`로 성공적으로 변환됩니다.\
이 숫자는 안전하게 `Double` 타입으로 저장되었습니다. 그다음 이 숫자를 `Float` 로 변환했습니다.\
`Float` 타입은 소수점 이하의 숫자를 정해진 만큼 저장할 수 있기 때문에 손실이 발생합니다. 이를 `Int` 로 변환하면 소수점이 잘립니다. 숫자 1000은 Byte 가 저장할 수 있는 것보다 더 크기때문에 **type overflow** 가 발생합니다.\
마지막으로 입력 값이 `"true"`가 아니기 때문에 입력 문자열을 불리언으로 변환한 결과는 `false`입니다.\












