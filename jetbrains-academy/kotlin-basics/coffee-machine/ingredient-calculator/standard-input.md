# Standard input

### Theory

표준 입력은 프로그램에 공급되는 데이터 스트림입니다. 기본적으로 키보드에서 데이터를 가져오지만 파일에서도 가져올 수 있습니다.

모든 프로그램이 표준 입력이 필요한 건 아닙니다 하지만 우리는 꽤나 자주 사용할 거에요. 유용한 프로그램을 만들기 전에 당신은 표준 입력에서 데이터를 읽는 방법을 이해해야 합니다.



### Kotlin functions

Kotlin 은 표준 입력으로부터 **데이터를 읽는** 유용한 함수를 가지고 있습니다. 그것은 바로 `readLine` 인데요, 줄 전체를 **문자열로** 읽습니다.

```kotlin
val line = readLine()!!
```

`readLine()!!` 으로 읽기 때문에 line 변수의 타입은 String입니다.

<mark style="background-color:purple;">엥 왠 느낌표가 있냐구요? 나중에 설명하겠습니다. 지금은, 특수한 타입으로 기억해두세요</mark>\ <mark style="background-color:purple;">JetBrains Academy's 에서</mark> [<mark style="background-color:purple;">이것</mark>](https://hyperskill.org/learn/step/7619)<mark style="background-color:purple;">에 관해 읽어볼 수 있습니다.</mark>&#x20;

다음은 표준 입력에서 줄을 읽어 표준 출력으로 보내는 프로그램입니다:

```kotlin
fun main() {
    val line = readLine()!!
    println("$line, hello")
}
```

입력:

```kotlin
moonu
```

출력:

```kotlin
moonu, hello
```

이 기능에는 몇 가지 단점이 있습니다. 동일한 줄에서 여러 값을 하나씩 읽으려면 추가 작업을 수행해야 합니다.

**Kotlin 1.6 부터는** 다른 입력 함수를 사용하여 데이터를 입력할 수 있습니다:

```kotlin
val line = readln()
```

이 함수는 `readLine()!!` 처럼 작동하고, 보이시는 것처럼 간결합니다.

만약 숫자를 입력받아야 한다면 이런 구조를 사용할 수 있습니다:\
`val number = readLine()!!.toInt()` 또는 `val number = readln().toInt()`

종종 문자열을 단어 별로 자르고 싶을 때도 있잖아요. 공백 또는 문자와 같은 하나 이상의 구분 기호로 다른 단어와 구분할 수 있답니다. 다음과 같은 방법으로 할 수 있어요:

```kotlin
val (a, b) = readLine()!!.split(' ')    // for input "Hello world!" a is "Hello" and b is "world!"
val (c, d, e) = readLine()!!.split(' ') // can read, for example "Go for it"

// or since Kotlin 1.6

val (a, b) = readln().split(' ')
val (c, d, e) = readln().split(' ')
```



### Java Scanner

표준 입력에서 데이터를 가져오는 또 다른 방법은 Java `Scanner`를 사용하는 것입니다. 다른 자바 라이브러리와 상호 운용이 가능하기 때문에 Kotlin 에서 바로 접근할 수 있어요. `Scanner` 를 사용하면 다른 타입들 (strings, numbers, etc) 을 읽을 수 있어요.



이것을 사용하려면 `import` 문을 소스코드와 함께 파일의 위에 추가해야합니다:

```kotlin
import java.util.Scanner
or
import java.util.*
```

두가지 방법 중 하나를 사용하여 프로그램에 `Scanner`를 추가할 수 있습니다. import 에 관해서는 추후에 이야기 해드릴게요.

`Scanner` 로 초기화된 변수를 생성해봅시다:

```kotlin
val scanner = Scanner(System.`in`)
```

`` System.`in` ``은 Kotlin에서 사용하는 예약어라서 Java에서 사용하던 변수명을 \`\`으로 감싸서 사용하는 것입니다.



```kotlin
val line = scanner.nextLine() // read a whole line, i.e. "Hello, Kotlin"
val num = scanner.nextInt()   // read a number, i.e. 123
val string = scanner.next()   // read a string, i.e. "Hello"
```

`scanner.next()`는 줄이 아닌 오직 한 단어만 읽습니다. 유저가 `Hello, Kotlin` 을 입력하면, 이것은 `Hello,` 만 읽습니다.

`scanner.nextLine()` 또는 `scanner.nextInt()` 또는 다른 항목을 호출하면 프로그램에서 입력 데이터를 **예상**합니다. 다음은 올바른 입력 데이터의 예입니다:

```java
Hello, Kotlin
123
Hello
```

scanner.next() 또는 scanner.nextLine()을 사용해서 숫자를 문자열로 읽을 수 있습니다.

또한 `Scanner`는 다른 유형의 값을 읽기 위한 여러 가지 방법(기능)을 제공합니다. \
자세한 내용은 [Class Scanner](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)를 참고하세요.

```kotlin
import java.util.Scanner // a class (type) from the Java standard library

fun main() {
    val scanner = Scanner(System.`in`) // reads data

    val num1 = scanner.nextInt() // reads the first number
    val num2 = scanner.nextInt() // reads the second number

    println(num2) // prints the second number
    println(num1) // prints the first number
}
```
