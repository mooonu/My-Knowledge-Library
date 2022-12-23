# If expression

## Theory

조건식은 프로그램이 불리언 표현식의 값에 따라 다른 계산을 수행할 수 있게 해줍니다. 만약 `true` 라면 어떠한 작업을 수행할 것이고 `false` 라면 또다른 작업을 수행할 것입니다. 

조건식에는 여러 형식이 있으며 더 자세히 알아보도록 하겠습니다.



## The single if-case

```kotlin
if (expression) {
    // body: do something
}
```

만약 표현식이 참이라면 코드 블럭 안의 식이 실행됩니다. 참이 아니라면 프로그램은 무시합니다.

예를 들어, 이 코드는 `age` 의 값이 100보다 크면 "Very experienced person" 을 출력합니다.

```kotlin
val age = ... // an integer value
if (age > 100) {
    println("Very experienced person")
}
```

만약 조건이 거짓이라면, 아무런 작업을 수행하지 않습니다.

```kotlin
if (3 == 4) {
    println("3 is 4")
} // nothing
```

조건식이 불리언 타입의 변수인 경우도 있습니다. `b == true` 또는 `b == false` 를 쓰는 대신 해당 변수를 사용합니다:

```kotlin
val b = ... // it is true or false (Boolean)
if (b) { // or !b
    // do something
}
```



## The if-else-cases

조건식이 거짓일 때 `else` 키워드로 대체 작업을 수행할 수 있습니다.

```kotlin
if (expression) {    
    // do something
} else {
    // do something else
}
```

이 경우, if 표현식이 참이면 첫번째 코드 블럭이 실행되고, 거짓이면 두번째 코드 블럭이 실행됩니다. 둘 다 실행되는 것은 불가능합니다.

이 프로그램은 `num` 의 값에 따라 다른 텍스트를 출력합니다. 

```kotlin
val num = ... // the num is initialized by some value (Int)

if (num % 2 == 0) {
    println("It's an even number")
} else {    
    println("It's an odd number")
}
```

숫자가 짝수 또는 홀수이므로 만약 `num` 이 10 이면 `It's an even number"` 을 `num` 이 11 이면 `"It's an odd number`  ` 메시지를 보게 될 겁니다. 



## The if-else-if-cases

The most usual form of the conditional statement consists of several conditions and `else`-branches.

조건식의 가장 일반적인 형태는 여러 조건(expression)과 다른 분기(if)로 구성됩니다.

```kotlin
if (expression0) {
    // do something
} else if (expression1) {
    // do something else 1
// ...
} else if (expressionN) {
    // do something else N
}
```



예산에 따라 어떤 컴퓨터를 사야하는지 추천해주는 프로그램:

```kotlin
val dollars = ... // your budget (Int)

if (dollars < 1000) {
    println("Buy a laptop")
} else if (dollars < 2000) {
    println("Buy a personal computer")
} else if (dollars < 100_000) {
    println("Buy a server")
} else {
    println("Buy a data center or a quantum computer")
}
```

이 조건식에서는 분기가 4개로 나뉘어져 있습니다:

- `dollars < 1000`
- `dollars < 2000`
- `dollars < 100_100`
- `dollars >= 100_000`

만약 dollars 의 값이 `10_000` 이라면 "Buy a server" 을 출력할 것입니다.



## Nested If's

- 중첩 if

```kotlin
if (n % 2 == 0) {
    if (n % 3 == 0) {
        println("The number can be divided by 6")
    } else {
        println("The number can be divided by 2")
    }
} else {
    println("The number cannot be divided by 2")
}
```

## Condition is an expression

다른 언어와 달리 Kotlin 에서 if 문은 표현식입니다. 

더 큰 수를 찾고 변수에 저장하는 예제:

```kotlin
val max = if (a > b) {
    println("Choose a")
    a
} else {
    println("Choose b")
    b
}
```

 `if` 를 표현식으로 사용하려면 `else` 가 존재해야합니다.

본문에 하나의 문만 포함된 경우 축약할 수 있습니다.

```kotlin
val max = if (a > b) a else b
```

결과를 저장하기 위해 새 변수를 선언 할 필요는 없습니다.

```kotlin
fun main() {
    val a = readln().toInt()
    val b = readln().toInt()

    println(if (a == b) {
        "a equal b"
    } else if (a > b) {
        "a is greater than b"
    } else {
        "a is less than b"
    })
}
```



## Idiom

if 를 표현식으로 사용하는 것이 더 좋은 방법이다.

왠만하면 val 을 사용하자

```kotlin
val max = if (a > b) a else b // one line

...

var max = a // try to avoid var if possible
if (b > a) max = b
```

