# While loops

## Theory

조건이 `true` 인 동안 코드를 반복할 수 있는 다른 방법이 있습니다. 이 주제에서는 `while` 과 `do...while` 반복문을 어떻게 사용하는지 배울 것 입니다. 두 반복문의 차이점은 반복 순서와 조건의 평가입니다.



## While loop

`while` 반복문은 반복할 코드와 불리언 조건식을 포함하고 있습니다. 만약 조건이 `true` 라면 반복문을 시작합니다. 이것은 조건이 `false` 가 될 때까지 반복합니다. `while` 문은 실행 전에 조건을 확인하므로 pre-test loop 라고도 합니다.

```kotlin
while (condition) {
    // body: do something repetitive
}
```

반복문의 내부에는 변수 선언, 입력 값 읽기, 조건식, 중첩 반복문 등이 포함될 수 있습니다.

**무한 반복**시키려면 조건을 `true` 로 설정하세요:

```kotlin
while (true) {
    // body: do something indefinitely
}
```

무한 반복에 대해서는 나중에 다루겠습니다.

아래 프로그램은 `while` 반복문을 사용하여 `5` 보다 작을 때까지 숫자를 출력합니다.

```kotlin
fun main() {
    var i = 0

    while (i < 5) {
        println(i)
        i++
    }

    println("Completed")
}
```

처음으로 `0` 이 가변 변수 `i` 에 할당됩니다. 반복이 시작하기 전 프로그램은 `i < 5` 조건식이 `true` 인지 확인합니다. `i` 가 0 이라면 반복이 시작됩니다. 반복문의 내부에는 현재 `i` 의 값을 보여주고 `1` 을 더합니다. 그 후 `i < 5` 조건이 아직 유효한지 평가합니다. `i` 는 1이 되었고 여전히 `true` 입니다. 따라서 반복을 계속합니다. `i` 가 `5` 가 되었다면 `i < 5` 는 `false` 입니다 따라서 반복이 종료됩니다. 그 후 프로그램은 반복문을 탈출하여 `Completed` 를 출력합니다

```no-highlight
0
1
2
3
4
Completed
```

문자, 문자열 및 기타 데이터 타입을 처리하는 데도 사용할 수 있습니다. 아래 프로그램은 영어 문자를 한 줄로 표시합니다:

```kotlin
fun main() {
    var letter = 'A'
    
    while (letter <= 'Z') {
        print(letter)
        letter++
    }
}
```

프로그램은 첫 번째 문자 `A` 를 가져와서 문자가 `Z` 가 될 때까지 반복합니다. 현재 문자를 출력하고 다음 문자로 진행합니다.

```no-highlight
ABCDEFGHIJKLMNOPQRSTUVWXYZ
```

증감 연산자를 사용하여 다음 문자를 얻을 수 있습니다. (Unicode 에 따라)

다음 예제는 입력 값에서 임의의 단어를 읽은 다음 출력하는 프로그램입니다. `Scanner` 의 `hasNext` 함수를 사용하여 입력 값이 있는지 확인합니다.

```kotlin
import java.util.*

fun main() {
    val scanner = Scanner(System.`in`)
    while (scanner.hasNext()) {
        val next = scanner.next()
        println(next)
    }
}
```

Input:

```no-highlight
Kotlin is a modern language
```

Output:

```no-highlight
Kotlin
is
a
modern
language
```

입력 데이터의 크기를 모르는 경우 문자열에는 `scanner.hasNext()` 를 사용하고 정수에는 `scanner.hasNextInt()` 를 사용합니다. 

> Ctrl + D 를 눌러 콘솔에서 입력을 중지할 수 있습니다.

## Do...while loop

`do...while` 반복문은 먼저 실행하고 그 다음 프로그램의 조건을 테스트합니다. 만약 조건이 참이라면, 조건이 거짓이 될 때까지 계속합니다. `do...while` 반복문은 실행 후에 조건을 확인하므로 post-test loop 라고도 합니다. `while` 반복문은 실행 전에 조건을 테스트하고 `do...while` 문은 조건을 확인하기 전에 한 번은 먼저 실행하고 테스트합니다.

```kotlin
do {
    // body: do something
} while (condition)
```

아래는 입력 값을 읽고 출력하는 프로그램입니다. 만약 사용자가 `0` 을 입력했다면 입력 값을 출력하고 반복하지 않을 것 입니다:

```kotlin
fun main() {
    do {
        val n = readln().toInt()
        println(n)
    } while (n > 0)
}
```

> 반복문의 내부에 변수를 설정한 후 조건으로 사용할 수 있습니다.



입력:

```no-highlight
1
2
4
0
```

출력:

```no-highlight
1
2
4
0
```

`do...while` 문도 `while` 과 마찬가지로 무한 반복이 가능합니다.
