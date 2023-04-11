# The classification of basic types

### Theory

이번 주제에서, 우리는 코틀린에서 기본 타입의 분류와 속성에 대해 배울 것입니다. 당신은 아마 기본 타입을 알고 있을 겁니다. 기본 타입은 의미에 따라 여러 그룹으로 나눌 수 있습니다. 같은 그룹의 타입들은 비슷하게 작동합니다만 그것들은 크기와 결과가 다르고 다른 범위의 값을 나타냅니다.



### Numbers

Kotiln은 **정수**와 **소수**에 대한 여러 타입을 제공합니다.

**정수는**(0, 1, 2, ...) `Long`, `Int`, `Short`, `Byte` 로 4가지 타입이 있습니다. 이 유형들은 다른 크기를 가지고 있고 다른 범위의 값을 나타냅니다. 정수형 범위는 -(2n-1) 에서 (2n-1) 로 계산할 수 있습니다, 여기서 n은 비트(bits)입니다. 범위는 0을 포함하므로 상한에서 1을 뺀 것입니다.

* `Byte`: 8 bits (1 byte), range varies from -128 to 127;
* `Short`: 16 bits (2 bytes), range varies from -32768 to 32767;
* `Int`: 32 bits (4 bytes), range varies from −(231) to (231)−1;
* `Long`: 64 bits (8 bytes), range varies from −(263) to (263)−1.

크기는 변경할 수 없습니다. 운영체제나 하드웨어에 의존하지 않습니다.

가장 일반적인 정수형 타입은 `Int` 와 `Long` 입니다. 연습할 때는 `Int` 를 사용하세요. 만약 숫자를 자유롭게 사용해야 한다면 `Long` 을 이용하세요:

```kotlin
val zero = 0 // Int
val one = 1  // Int
val oneMillion = 1_000_000  // Int

val twoMillion = 2_000_000L           // Long because it is tagged with L
val bigNumber = 1_000_000_000_000_000 // Long, Kotlin automatically chooses it (Int is too small)
val ten: Long = 10                    // Long because the type is specified

val shortNumber: Short = 15 // Short because the type is specified
val byteNumber: Byte = 15   // Byte because the type is specified
```

**실수형**은 숫자를 소수로 나타냅니다. Kotlin은 `Double` 와 `Float` 두 가지 타입이 있습니다. 이러한 유형은 제한된 수의 소수 자릿수(`Float`의 경우 \~6-7, `Double`의 경우 \~14-16)만 저장할 수 있습니다. `Double` 타입은 연습할 때 일반적으로 사용합니다.

```kotlin
val pi = 3.1415              // Double
val e = 2.71828f             // Float because it is tagged with f
val fraction: Float = 1.51f  // Float because the type is specified
```

숫자 유형의 최댓값과 최솟값을 표현하려면(`Double`, `Float` 포함), 유형 이름 뒤에 `.` 을 입력한 다음 `MIN_VALUE` 또는 `MAX_VALUE` 을 입력해야합니다.

```kotlin
println(Int.MIN_VALUE)  // -2147483648
println(Int.MAX_VALUE)  // 2147483647
println(Long.MIN_VALUE) // -9223372036854775808
println(Long.MAX_VALUE) // 9223372036854775807
```

byte 또는 bits 단위의 정수 유형 크기를 가져올 수도 있습니다. (1 byte = 8 bits):

```kotlin
println(Int.SIZE_BYTES) // 4
println(Int.SIZE_BITS)  // 32
```



### Characters

Kotiln은 다양한 문자(대문자와 소문자), 숫자 및 기타 기호를 나타내는 `Char` 타입이 있습니다. 각각의 문자는 `' '` 로 나타냅니다. 크기는 Short 타입과 비슷합니다 (2 bytes = 16 bits):

```kotlin
val lowerCaseLetter = 'a'
val upperCaseLetter = 'Q'
val number = '1'
val space = ' '
val dollar = '$'
```

문자는 상형문자와 우리가 나중에 고려할 특별한 기호를 포함하여 많은 알파벳의 기호를 나타낼 수 있습니다.



### Booleans

Kotiln 은 Boolean 이라 불리는 타입을 제공합니다. 오직 true 와 false 두 가지 값만 저장할 수 있습니다.\
1bit 의 정보만 나타내지만 크기는 정확하게 정의되지 않았습니다.

```kotlin
val enabled = true
val bugFound = false
```

종종 조건문에서 이 유형을 사용할 겁니다.



### Strings

The `String` type represents a sequence of characters in **double quotes**. It is one of the most popular types.

```kotlin
val creditCardNumber = "1234 5678 9012 3456"
val message = "Learn Kotlin instead of Java."
```

`String` 타입은 `" "` 로 문자열을 나타냅니다. `String`은 가장 인기있는 타입 중 하나입니다.











