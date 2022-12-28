# Type of the numeric expression

### Theory

당신은 이미 타입 변환을 수행하는 법을 알고 있습니다. 여기 조금 더 향상된 측면이 있습니다: 예를들어, 당신은 `Int` 타입의 변수를 `Long` 변수에 할당할 수 없음을 알고 있습니다. 그렇다면 `Int` 와 `Long` 타입을 합한다면? 이 경우 컨텍스트에서 타입 추론이 사용됩니다.

### Type coercion

컴파일러는 타입 변환을 자동으로 설정하고 결과 타입을 더 큰 타입으로 결정합니다.

![type2](https://user-images.githubusercontent.com/86511086/203941463-91505731-e9af-45b5-8050-9fba7eb12abc.png)

결과 타입이 이전 타입보다 더 크기 때문에 데이터의 손실이 없습니다.

<mark style="background-color:purple;">Kotlin 에서 타입 변환은 드물게 일어납니다. 오직 number 와 string 에서만 동작합니다.</mark>

### Examples

* `Int` 에서 `Long`:

```kotlin
val num: Int = 100
val longNum: Long = 1000
val result = num + longNum // 1100, Long
```

`result` 는 1100 이지만 `Long` 변수와 `Int` 변수의 합이므로 타입이 `Long` 으로 자동 캐스팅됩니다. 만약 결과 타입을 `Int` 로 선언한다면 오류가 날 것입니다 `Long` 타입을 `Int` 변수에 할당할 수 없기 때문입니다. `Int` 타입의 변수에는 오로지 `Int` 타입의 값 또는 정수만 할당할 수 있습니다.

* `Long` 에서 `Double`:

```kotlin
val bigNum: Long = 100000
val doubleNum: Double = 0.0
val bigFraction = bigNum - doubleNum // 100000.0, Double
```

### Short and Byte types

여러 타입의 변수가 있는 식의 결과가 가장 큰 타입으로 자동 캐스팅되는 방법을 확인할 수 있습니다. 그러나 `Byte` 와 `Short` 타입은 조금 다릅니다. 이 타입들을 계산해야한다면 계산의 결과 타입은 `Int` 입니다:

* `Byte` and `Byte`

```kotlin
val one: Byte = 1
val two: Byte = 2
val three = one + two // 3, Int
```

* `Short` and `Short`

```kotlin
val fourteen: Short = 14
val ten: Short = 10
val four = fourteen - ten // 4, Int
```

* `Short` and `Byte`

```kotlin
val hundred: Short = 100
val five: Byte = 5
val zero = hundred % five // 0, Int
```

So what should we do if we want to sum two `Byte` variables and get a `Byte` result? Well, in this case, you must manually perform type conversion:

두 개의 `Byte` 합의 결과를 `Byte` 로 얻고 싶으면 어떻게 해야할까요? 이런 경우에는 명시적 타입 변환을 사용해야합니다:

```kotlin
val one: Byte = 1
val five: Byte = 5
val six = (one + five).toByte() // 6, Byte
```

### Summary

요약하자면 다른 숫자 타입의 식이 있는 경우 다음 규칙을 사용하여 결과 타입을 파악할 수 있습니다.

1. 피연산자 중 하나의 타입이 `Double` 이면 결과는 `Double` 입니다.
2. 피연산자 중 하나의 타입이 `Float` 이면 결과는 `Float` 입니다.
3. 피연산자 중 하나의 타입이 `Long` 이면 결과는 `Long` 입니다.
4. 그 외의 경우 `Int` 입니다.

<mark style="background-color:purple;">변수에 값을 넣을 때는 형 변환이 일어나지 않습니다.</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">`val longValue: Long = 10.toInt()`</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">10은</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">`Int`</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">이고</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">`longValue`</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">에는</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">`Long`</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">타입이 필요하므로 틀렸습니다.</mark>
