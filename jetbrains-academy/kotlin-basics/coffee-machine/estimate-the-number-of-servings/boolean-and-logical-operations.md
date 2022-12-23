# Boolean and logical operations

## Theory

불리언 값은 프로그래밍에서 종종 사용되기에 이번 주제에서는 불리언에 대해 다룰 것 입니다. 기본적으로 불리언은 두 가지 반대의 상태를 제공합니다



## Boolean variables

불리언은 단 두 가지 `true` 와 `false` 를 가진 특별한 데이터 타입입니다:

```kotlin
val t = true  // t is true
val f = false // f is false

println(t) // true
println(f) // false
```

> Kotlin 에서는 정수 값을 불리언 변수에 할당할 수 없습니다 또한 `0` 은 `false` 와 같지 않습니다.



## Reading Boolean values

Kotlin 1.4 부터 불리언 값을 읽을 수 있습니다:

```kotlin
val b: Boolean = readLine().toBoolean()
```

그리고 Kotlin 1.6 부터는 이렇게도 읽을 수 있습니다:

```kotlin
val b: Boolean = readln().toBoolean()
```

`toBoolean()` 은 "true" 를 입력받았다면 `true` 를 반환합니다. (입력 값의 대소문자를 구분하지 않습니다), 다른 경우 `false` 를 반환합니다.

추측해보세요:

```kotlin
true
True
TRuE
T
false
```

결과:

```kotlin
println(readln().toBoolean()) // true
println(readln().toBoolean()) // true
println(readln().toBoolean()) // true
println(readln().toBoolean()) // false
println(readln().toBoolean()) // false
```

Kotlin 1.3 이상 버전에서는 `readLine()!!.toBoolean()` 을 사용할 수 있습니다.

```kotlin
val b: Boolean = readLine()!!.toBoolean()
```

Kotlin 1.5 이후로 다른 함수를 사용하여 `String` 을 `Boolean` 으로 변환할 수 있습니다. 
함수 `toBooleanStrict()` 는 문자열이 "true" 와 같다면 `true` 를 반환하고 문자열이 "false" 와 같다면 `false` 를 반환합니다. (대소문자를 구분합니다) 대소문자를 구분하기에 다르게 입력된다면 `java.lang.IllegalArgumentException` 에러가 발생하게 됩니다.
함수 `toBooleanStrictOrNull()` 은 위와 동일하게 값을 반환하지만 대소문자가 다르게 입력된다면 `null` 값을 반환합니다.

```kotlin
println("true".toBooleanStrict())     // true
// println("True".toBooleanStrict())  // program crashes
println("false".toBooleanStrict())    // false
// println("faLse".toBooleanStrict()) // program crashes

println("true".toBooleanStrictOrNull())  // true
println("false".toBooleanStrictOrNull()) // false
println("faLse".toBooleanStrictOrNull()) // null
```



## Logical operators

불리언 타입 변수는 논리 연산자의 도움을 받아 논리 문을 구성합니다. Kotlin 은 4가지 논리 연산자를 가지고 있습니다:
**NOT**, **AND**, **OR**, and **XOR:**

- NOT 은 불리언 값의 반대입니다. `!` 로 나타낼 수 있습니다.

```kotlin
val f = false // f is false
val t = !f    // t is true
```



- AND 는 두 피연산자가 모두 참이라면 `true` 를 반환합니다 그러지 않으면 `false` 를 반환합니다. `&&` 으로 나타낼 수 있습니다.

```kotlin
val b1 = false && false // false
val b2 = false && true // false
val b3 = true && false // false
val b4 = true && true  // true 
```



- OR 은 하나가 참이라면 `true` 를 반환합니다. 그렇지 않으면 `false` 를 반환합니다. `||` 으로 나타낼 수 있습니다.

```kotlin
val b1 = false || false // false
val b2 = false || true  // true
val b3 = true || false  // true
val b4 = true || true   // true
```



- XOR (exclusive OR) 은 불리언 피연산자가 서로 다른 값을 가진다면 `true` 를 반환합니다. 그렇지 않으면 `false` 를 반환합니다. `xor` 로 나타낼 수 있습니다.

```kotlin
val b1 = false xor false // false
val b2 = false xor true  // true
val b3 = true xor false  // true
val b4 = true xor true   // false
```

XOR 연산자는 다른 논리 연산자만큼 널리 사용되지 않습니다. 하지만 만약을 대비해서 사용할 수 있습니다.



## Logical operator precedence

우선 순위

- `!`
- `xor`
- `&&`
- `||`

```kotlin
val bool = true && !false // true because !false is evaluated first
```

`(...)` 괄호를 사용해서 실행 순서를 바꿀 수 있습니다.

```kotlin
val cold = false
val dry = true
val summer = false // suppose it is autumn now

val hiking = dry && (!cold || summer) // true, let's go hiking!
```
