# Coding style convetions

## Conventions

프로그래머는 코드를 만드는 것보다 다른 사람이 작성한 코드를 읽는 데 더 많은 시간을 할애합니다. 따라서 명확하고 간결하게 코드를 작성하는 것은 매우 중요합니다. 만약 협업을 한다면 코드의 모든 라인이 통일되어야 하는데, 코드 스타일 규칙은 더 읽기 쉽게 도와줍니다.

**코드 스타일 규칙**은 읽기 쉬운 코드를 표준화하고 유지 및 관리하는 데 도움이 됩니다. 이것은 엄격한 규칙이라기 보다는 권고에 가깝습니다. 개발자들이 이 규칙을 따라간다면, 코드는 일관성을 갖게 됩니다.

모든 주요 프로그래밍 언어에는 이러한 규칙이 있으며, Kotlin 도 마찬가지입니다. 공식 문서에서 찾아볼 수 있습니다 [Official Documentation](https://kotlinlang.org/docs/reference/coding-conventions.html). 모든 규칙을 한꺼번에 배울 필요는 없습니다. 새로운 개념을 익힌 후 자주 열어볼 수 있습니다. 이번 주제에서는 이러한 규칙의 몇 가지 중요한 부분을 알아보겠습니다.

## First steps

몇 가지 코드 규칙:

1. 들여쓰기에는 한 개의 탭 대신 4개의 공백을 사용합니다. 운영 체제와 다른 IDE에 따라 한 탭이 항상 네개의 공백에 해당하지는 않습니다
2. Kotlin 은 세미콜론이 필요하지 않습니다
3. 중괄호는 줄의 끝부분에서 시작합니다
4. 중괄호의 닫는 부분은 마지막 줄 시작 부분에서 닫습니다.

예시:

```kotlin
fun main() { // opening curly brace
    println("Hi") // this statement is offset by 4 spaces and has no `;` at the end
} // closing brace
```
