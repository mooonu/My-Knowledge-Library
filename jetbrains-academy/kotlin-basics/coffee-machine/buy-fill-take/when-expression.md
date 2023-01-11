# When expression

## Theory

Kotlin 은 변수의 값에 따라서 다른 작업을 수행하는 `when` 표현식을 제공합니다. 여러 가지 옵션을 편리하게 접근할 수 있습니다. 이 표현식은 `if` 를 대체할 수 있고 읽기 쉬운 코드를 만들어 줍니다.



## Alternatives

아래 프로그램은 두 정수의 덧셈, 뺄셈, 곱셈을 수행합니다. `when` 을 사용하여 어떤 연산을 수행할지 결정합니다:

```kotlin
fun main(){
    val (var1, op, var2) = readln().split(" ")

    val a = var1.toInt()
    val b = var2.toInt()

    when (op) {
        "+" -> println(a + b)
        "-" -> println(a - b)
        "*" -> println(a * b)
        else -> println("Unknown operator")
    }
}
```

`when` 에서 op 와 일치하는 값을 찾습니다. `"+", "-", "*"` 세 가지 분기와 `else` 로 나뉘어 있습니다. `else` 는 일치하는 값이 없다면 작동됩니다. `else` 는 선택사항이므로 사용하지 않을 수 있습니다. 만약 위와 같은 코드를 `if` 로 작성한다면 읽기 쉽지 않을 것입니다.

여러개를 처리해야하는 경우 `,` 를 통해 분리할 수 있습니다. 하나의 분기에서 필요한 만큼 결합할 수 있습니다. 이전 프로그램의 코드를 수정한 예제:

```kotlin
when (op) {
    "+", "plus" -> println(a + b)
    "-", "minus", -> println(a - b) // trailing comma
    "*", "times" -> println(a * b)
    else -> println("Unknown operator")
}
```

여러 문이 있는 복잡한 블록을 분기로 사용할 수도 있습니다:

```kotlin
when (op) {
    "+", "plus" -> {
        val sum = a + b
        println(sum)
    }
    "-", "minus" -> {
        val diff = a - b
        println(diff)
    }
    "*", "times" -> {
        val product = a * b
        println(product)
    }
    else -> println("Unknown operator")
}
```



## When as an expression

`when` 은 결과를 반환할 수 있습니다. 이 경우 모든 분기는 어떠한 것을 반환하기 때문에 `else` 가 필요합니다. 

```kotlin
val result = when (op) {
    "+" -> a + b
    "-" -> a - b
    "*" -> a * b
    else -> "Unknown operator"
}
println(result)
```

위처럼 변수를 추가로 선언하지 않아도 되고 결과를 즉시 함수로 반환합니다:

```kotlin
println(when(op) {
    "+" -> a + b
    // ...
    else -> "Unknown operator"
})
```

다른 곳에서 결과를 사용할 필요가 없거나 코드를 짧게 유지할 때 이 방법을 사용하세요.

만약 `{...}`  로 둘러싸인 블록이 포함된 경우 마지막 줄은 단일 값이거나 복합 식이어야하며, 이 식을 수행하여 `when` 식의 결과로 반환됩니다.

```kotlin
"+" -> {
    val sum = a + b
    sum
}
```



## Branch conditions and ranges

`when` 은 값과 직접 일치한 것 뿐만 아니라 복잡한 검사 기능을 제공합니다.

아래 프로그램은 `a`, `b`, `c` 를 읽고 `a` 와 `b` 를 이용하여 `c` 를 계산하는 방법을 결정합니다. 만약 `c` 를 여러 방법으로 계산할 수 있다면 첫 번째 방법만 출력합니다. 

```kotlin
fun main(){
    val (var1, var2, var3) = readln().split(" ")

    val a = var1.toInt()
    val b = var2.toInt()
    val c = var3.toInt()

    println(when (c) {
        a + b -> "$c equals $a plus $b"
        a - b -> "$c equals $a minus $b"
        a * b -> "$c equals $a times $b"
        else -> "We do not know how to calculate $c"
    })
}
```

만약 `5 3 2` 를 입력했다면 프로그램은 `2 equals 5 minus 3` 을 출력할 것이고, `0 0 0` 을 입력했다면 `0 equals 0 plus 0` 을 출력할 것입니다.

또 다른 흥미로운 것은 값이 범위에 속하는지 여부를 확인할 수 있는 것입니다:

```kotlin
when (n) {
    0 -> println("n is zero")
    in 1..10 -> println("n is between 1 and 10 (inclusive)")
    in 25..30 -> println("n is between 25 and 30 (inclusive)")
    else -> println("n is outside a range")
}
```

변수 `n` 이 정수 0 이라면 프로그램은 첫 번째 분기로, `n` 이 1-10 에 포함되어 있다면 두 번째 분기로, 25-30 이라면 세 번째 분기로 평가할 것입니다. 만약 `n` 이 어떠한 범위에도 포함되지 않는 경우에는 `else` 분기로 평가됩니다.

단일 값과 마찬가지로 `,` 를 이용해 범위를 결합할 수도 있습니다.

```kotlin
in a..b, in c..d -> println("n belongs to a range")
```



## When without arguments

매개변수 없이 `when` 표현식을 사용할 수 있습니다. 이 경우 모든 분기의 조건은 불리언식이며, 분기 조건이 참일 때 분기가 실행됩니다. 여러 조건이 참이라면 첫 번째 조건만 실행됩니다.

```kotlin
fun main(){
    val n = readln().toInt()
    
    when {
        n == 0 -> println("n is zero")
        n in 100..200 -> println("n is between 100 and 200")
        n > 300 -> println("n is greater than 300")
        n < 0 -> println("n is negative")
        // else-branch is optional here
    }
}
```
