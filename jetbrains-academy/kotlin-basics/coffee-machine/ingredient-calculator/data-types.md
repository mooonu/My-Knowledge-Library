# Data types

### Variable types

```kotlin
val text = "Hello, I am studying Kotlin now."
val n = 1
```

이 경우에 Kotlin은 text는 string임을 n은 number임을 알고 있습니다. Kotlin은 두 변수의 타입을 자동으로 결정합니다. 이 메커니즘을 **타입 추론**이라고 합니다.



우리가 타입 추론을 사용하여 변수를 선언하는 방법:

```kotlin
val/var identifier = initialization

val name = "moonu"
```

**타입을 지정하여 변수를 선언하는 방법:**

```kotlin
val/var identifier: Type = initialization 

val name: String = "moonu"
```

<mark style="background-color:purple;">메모, 타입 이름은 항상 대문자로 시작합니다.</mark>



이전 예제와 동일하게 변수를 선언하고 타입을 지정합니다:

```kotlin
val text: String = "Hello, I am studying Kotlin now."
val n: Int = 1
```

`Int` 타입은 변수에 정수 (`0`, `1`, `2`, ..., `100_000_000`, ...)를 저장하는 것을 의미합니다. `String` 타입은 변수를 문자열(`"Hello"`, `"John Smith"`)로 저장하는 것을 의미합니다.



타입 추론을 사용한다면, 당신의 코드가 더 읽기 쉽고 간결할 겁니다. 하지만 경우에 따라서 타입을 지정하는 것이 더 나을 수 있습니다. 예를 들어, **우리가 변수를 선언하고 나중에 초기화해야 한다면 타입 추론은 동작하지 않을 겁니다.**

```kotlin
val greeting // error
greeting = "hello"
```

위의 예제는 틀렸습니다 왜냐하면 Kotlin은 그저 선언된 변수의 타입을 추론할 수 없고, 모든 변수는 타입을 가져야 하기 때문입니다. 반대로, 아래의 예제는 프로그래머에 의해 타입이 지정되었기 때문에 동작합니다

```kotlin
val greeting: String // ok
greeting = "hello"
```



### Type mismatch

데이터 타입의 가장 중요한 기능 중 하나는 부적절한 값을 변수에 할당하지 않도록 보호해줍니다. \
코드가 동작하지 않는 아래 예제를 봅시다:

```kotlin
val n: Int = "abc" // Type mismatch: inferred type is String but Int was expected
```

`type mismatch` 에러 보셨죠? 이건 변수에 부적절한 값을 할당했음을 의미합니다.\
타입추론으로 선언된 가변 변수에 부적절한 값을 할당하는 경우에도 같은 현상이 발생합니다:

```kotlin
var age = 30 // the type is inferred as Int
age = "31 years old" // Type mismatch
```

<mark style="background-color:purple;">메모, 변수의 타입을 변경할 수 없습니다.</mark>

