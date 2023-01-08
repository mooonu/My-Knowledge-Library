# Ranges

## Theory

정수 `c` 가 `a` 보다 크거나 같고 `b` 보다 작거나 같다면 아마 이렇게 표현할 겁니다:

```kotlin
val within = a <= c && c <= b
```

위 코드는 잘 작동합니다. 그러나 Kotlin 은 범위(ranges)를 이용한 더 편리한 방법을 제공합니다.

```kotlin
val within = c in a..b // a<=..<=b
```

`a..b` 는 `a` 에서 `b` 까지의 범위입니다. `in` 은 값이 범위안에 해당하는지 확인하는 특별한 키워드입니다. 나중에 이 키워드가 다른 유형과 함께 사용되는 것을 보게 될 것입니다.

`within` 변수의 값은 `c`가 범위안에 포함된다면 `true` 이고 아니라면 `false` 입니다.

다른 예제:

```kotlin
println(5 in 5..15)  // true
println(12 in 5..15) // true
println(15 in 5..15) // true
println(20 in 5..15) // false
```

만약 오른쪽 값보다 작게끔 해야할 경우 1을 빼면 됩니다:

```kotlin
val withinExclRight = c in a..b - 1 // a <= c && c < b
```

만약 범위안에 없다는 걸 확인하고 싶다면 `in` 이전에 `!` (not) 을 추가합니다:

```kotlin
val notWithin = 100 !in 10..99 // true
```

논리연산자와 함께 사용할 수 있습니다. 아래 코드는 `c` 가 세 가지 범위 중 하나에 해당하는지 확인합니다.

```kotlin
val within = c in 5..10 || c in 20..30 || c in 40..50 // true if c is within at least one range
```

변수에 범위를 할당하고 나중에 이를 사용할 수도 있습니다:

```kotlin
val range = 100..200
println(300 in range) // false
```

사전 순서에 따라 정수 외에도 문자를 사용할 수 있습니다.

```kotlin
println('b' in 'a'..'c') // true
println('k' in 'a'..'e') // false
```
