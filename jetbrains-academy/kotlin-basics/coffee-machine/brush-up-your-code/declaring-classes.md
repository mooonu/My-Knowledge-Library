# Declaring classes

> property: 속성, 변수, 필드, 데이터
>
> method: 함수, 동작, 행동
>
> object: 물리적인 메모리 영역에서 실행되고 있는 클래스의 실체
>
> instance: 메모리에 올라간 객체를 인스턴스라고 부른다.

## Declaring new classes

새 클래스를 정의하려면 `class` 키워드를 입력하고 그 후 클래스의 이름을 작성합니다. `Emptiness` 클래스를 정의해보겠습니다:

```kotlin
class Emptiness {
    // empty body
}
```

Kotlin 에서 클래스의 내부가 비어있다면 중괄호는 생략할 수 있습니다. 그래서 다음과 같이 클래스를 정의할 수도 있습니다:

```kotlin
class Emptiness
```

`.kt` 파일 안에 클래스들을 정의할 수 있습니다. 보통은 파일 최상단에 클래스를 정의하는 것이 좋지만 어느 곳에든 정의할 수 있습니다. 



## Object creation

클래스를 정의하는 이유가 무엇일까요? 간단히 말해서 정의된 각 클래스는 새로운 타입이 됩니다. 그래서 클래스의 객체를 만들고 변수 및 값으로 저장할 수 있습니다. 때때로 표준 데이터 타입으로는 충분하지 않기에 유용합니다. 

클래스의 인스턴스를 만들기 위해서는 간단하게 클래스 이름과 빈괄호를 작성하면 됩니다. 해당 문법은 함수와 유사합니다. 이제 `Emptiness` 클래스를 이용해봅시다:

```kotlin
val empty: Emptiness = Emptiness()
```

`empty` 변수에 `Emptiness` 클래스의 객체를 할당했습니다. 따라서 이 변수는 `Emptiness` 타입을 가집니다. 그래서 다른 타입을 해당 객체에 재할당할 수 없습니다. Kotlin 의 일반적인 규칙으로 명시적인 지시어는 생략할 수 있습니다:

```kotlin
val empty = Emptiness()
```



## Class member

클래스의 내부에는 클래스 멤버를 포함할 수 있습니다. 지금은 Kotlin 의 필드를 대체하는 속성만 이야기하겠습니다. 물론 데이터도 저장할 수 있습니다.

> 모든 클래스 멤버는 선택사항입니다. 예를들어 `Emptiness` 클래스가 속성을 가지지 않는 것 처럼요



## Writing properties

속성은 변수 및 값과 아주 유사합니다. 만약 런타임 때 속성에 값을 할당하고 싶다면 `var` 로 선언합니다 그렇지 않다면 `val` 을 선택합니다.

또한 어떤 속성이든 엄격한 타입을 가지고 있는데, 문자열과 숫자와 같은 표준 타입이 될 수도 있고 또는 커스텀 타입이 될 수 있습니다.

데이터만 저장한다면 어떻게든 초기값을 받아야 하는데, 클래스 내부에서 속성을 설정할 수 있습니다.

클래스는 필요한 만큼 속성들을 가질 수 있습니다.

이제 병원 정보 시스템에서 환자를 나타내는 클래스를 선언해보겠습니다:

```kotlin
class Patient {
    var name: String = "Unknown"
    var age: Int = 0
    var height: Double = 0.0
}
```

`Patient` 클래스에 name, age, height 의 세 가지 속성을 재할당할 수 있음을 확인할 수 있습니다.

클래스의 각 개체에는 동일한 필드가 존재하지만 필드의 값은 객체마다 다를 수 있습니다.



## Accessing properties

객체의 속성에 접근하려면 첫번째로 객체를 생성해야합니다:

```kotlin
var patient = Patient()
```

아직은 객체의 속성을 변경할 수 없습니다 따라서 현재는 초기값만 가지고 있는 상태입니다. 이러한 속성의 값을 가져오려면 객체의 이름 옆에 `.` 과 속성의 이름을 입력합니다:

```kotlin
println(patient.name) // prints "Unknown"
println(patient.age)  // prints "0"
```



## Changing properties

아래 프로그램은 두 환자를 생성하고 속성을 설정합니다.

```kotlin
class Patient {
    var name: String = "Unknown"
    var age: Int = 0
    var height: Double = 0.0
}

fun main() {
    val john = Patient()
    john.name = "John"
    john.age = 30
    john.height = 180.0

    val alice = Patient()
    alice.name = "Alice"
    alice.age = 22
    alice.height = 165.0

    println("${john.name}: ${john.age} yrs, ${john.height} cm")
    println("${alice.name}: ${alice.age} yrs, ${alice.height} cm")
}
```

출력 결과:

```no-highlight
John: 30 yrs, 180.0 cm
Alice: 22 yrs, 165.0 cm
```

> Alice 의 속성을 할당할 때 John 의 속성은 바뀌지 않습니다.

또한 Alice 앞에 있는 `val` 은 Alice 에게 `Patient` 를 재할당할 수 없다는 것을 이해해야 합니다. 그러나 Alice 의 속성은 `Patient` 클래스 내에서 `var` 로 표시되므로 재할당할 수 있습니다.
