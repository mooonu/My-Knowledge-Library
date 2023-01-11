# Repeating blocks

## Theory

가끔, 여러분은 어떤 코드를 여러번 반복해야할 때가 있습니다. 그것은 단순히 복사-붙혀넣기로 할 수 있지만 10만 번 반복해야 한다면 어떻게 해야할까요? 이 주제에서는 복사-붙혀넣기는 어울리지 않습니다.

다행히도 우리는 코드 블럭을 여러번 반복할 수 있는 특별한 것이 있습니다. 이것은 반복으로 알려져 있으며 여러번 반복할 때 유용합니다.

## Repeat loop

`repeat(n)` 과 `{...}` 중괄호안의 코드를 작성하여 간단하게 반복할 수 있습니다. `n` 은 몇 번 반복할 건지 결정하는 정수입니다.

```kotlin
repeat(n) {
    // statements
}
```

`Hello` 를 세 번 반복하는 예제:

```kotlin
fun main() {
    repeat(3) {
        println("Hello")
    }
}
```

출력:

```kotlin
Hello
Hello
Hello
```

> 만약 `n` 이 0 이거나 음수라면 반복하지 않습니다. 또한 1 이라면 반복하지 않고 식을 평가합니다.

Kotlin 은 `it` 식별자로 현재 반복을 확인할 수 있습니다:

```kotlin
fun main() {
    repeat(3) {
        println(it)
    }
}
```

출력:

```kotlin
0
1
2
```

> 괄호 안의 코드는 "람다식" 이라고 불립니다. 이것은 이름이 없고 표현으로 바로 전달되는 기능입니다.



## Reading and processing data in a loop

입력 값을 읽고 변수를 선언할 수 있으며 반복문 내에서 계산을 수행할 수도 있습니다.

아래 프로그램은 입력 값을 읽고 합을 계산합니다. 첫번째 입력값은 합을 구하는 값이 아니라 몇 번 입력을 받을 것인지 결정하는 것입니다.

```kotlin
fun main() {    
    val n = readln().toInt()
    var sum = 0
    
    repeat(n) {
        val next = readln().toInt()
        sum += next
    }
    
    println(sum)
}
```

해당 코드는 반복 횟수를 읽고 `n` 변수에 할당합니다. 그 후, 총합을 저장하는 변수를 생성합니다. 코드는 다음 숫자를 읽고 정확히 `n` 번 `sum` 에 더합니다. 그런 다음 반복이 종료되고 프로그램은 총합을 출력합니다.

입력:

```kotlin
5
40
15
30
25
50
```

출력:

```kotlin
160
```
