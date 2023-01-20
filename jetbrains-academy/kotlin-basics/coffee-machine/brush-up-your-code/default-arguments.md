# Default arguments

## Functions with default arguments

Kotlin에서 함수를 선언할 때 함수의 매개변수에 디폴트 값을 할당할 수 있습니다. 이 함수를 호출하려면 디폴트 값이 있는 인자를 생략하거나 일반적인 방법으로 호출할 수 있습니다.

여기 두 매개변수를 가진 `printLine` 함수가 있습니다. 첫번째 인자는 `line` 으로 선언되어 있고 두번째 인자는 `end` 로 선언되어 있습니다. 두 인자 모두 디폴트 값을 가지고 있습니다.

```kotlin
fun printLine(line: String = "", end: String = "\n") = print("$line$end")
```

해당 예시를 보면 타입을 명시 후 매개변수에 `=` 연산자를 사용해 값을 할당했습니다.

이제 전체 코드를 확인해보겠습니다.

```kotlin
fun printLine(line: String = "", end: String = "\n") = print("$line$end")

fun main() {
    printLine("Hello, Kotlin", "!!!") // prints "Hello, Kotlin!!!"
    printLine("Kotlin") // prints "Kotlin" with an ending
    printLine() // prints an empty line like println()
}
```

첫 호출 때 두 인자(`"Hello, Kotlin"`, `"!!!"`)는 함수로 전달됩니다. 다음 호출 때는 (`"Kotlin`")인자만 전달됩니다 따라서 함수에게 전달되는 두번째 인자는 디폴트 값(`"\n"`)입니다. 그 다음 호출 때는 아무런 인자가 없기 때문에 디폴트 값으로 작동합니다.

출력:

```kotlin
Hello, Kotlin!!!Kotlin 
```

> 첫 번째 인자 없이 두 번째 인자를 전달할 수 없습니다. Kotlin은 두 번째 매개변수에만 값을 할당하고자 하는 것을 이해하지 못합니다.



## Mixing default and regular arguments.

디폴트 값을 가진 매개변수와 일반 매개변수를 함께 사용할 수도 있습니다.

```kotlin
fun findMax(n1: Int, n2: Int, absolute: Boolean = false): Int {
    val v1: Int
    val v2: Int

    if (absolute) {
        v1 = Math.abs(n1)
        v2 = Math.abs(n2)
    } else {
        v1 = n1
        v2 = n2
    }

    return if (v1 > v2) n1 else n2
}

fun main() {
    println(findMax(11, 15)) // 15
    println(findMax(11, 15, true)) // 15
    println(findMax(-4, -9)) // -4
    println(findMax(-4, -9, true)) // -9
}
```

## Idiom

```kotlin
fun foo(a: Int = 0, b: String = "") { 

}
```
