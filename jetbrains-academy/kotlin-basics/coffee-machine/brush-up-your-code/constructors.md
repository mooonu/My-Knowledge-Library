# Constructors

## Default constructor

생성자는 클래스의 새 객체를 초기화하는 클래스 멤버입니다. 다른 말로 생성자는 속성을 정의하여 새로운 객체의 상태를 설정합니다. 따라서 객체를 생성하려면 생성자를 호출해야합니다.

클래스 `Size` :

```kotlin
class Size {
    var width: Int = 1
    var height: Int = 1
}
```

객체를 생성하는 방법을 복습해보겠습니다. 클래스 이름 다음에 빈괄호를 작성합니다:

```kotlin
val size = Size()
```

이는 실제로 생성자를 호출하는 방법이며 인자 없이 함수를 호출하는 것과 방법이 같습니다. 모든 클래스는 생성자가 필요하고 생성자가 명시적으로 선언되어있지 않다면 컴파일러는 자동으로 기본 생성자를 생성합니다.



## Primary constructor

기본 생성자를 정의하려면 클래스 이름 뒤 괄호 안에 클래스 초기화 인자를 넣어야 합니다.

`Size` 클래스의 기본 생성자:

```kotlin
class Size(width: Int, height: Int) {
    val width: Int = width
    val height: Int = height
    val area: Int = width * height
}
```

보통 생성자를 선언하려면 매개변수 뒤에 `constructor` 키워드를 작성해야합니다. Kotlin의 기본 생성자는 해당 키워드를 생략할 수 있습니다.

키워드를 생략하지 않은 방법:

```kotlin
class Size constructor(width: Int, height: Int) {
    val width: Int = width
    val height: Int = height
    val area: Int = width * height
}
```



## Property declarations

기본 생성자 **안에** 간단한 속성을 선언할 수 있습니다. 속성을 변경하지 못하게 하려면 괄호안 매개변수 옆에  `val` 키워드를 작성합니다. 변경할 수 있도록 하려면 `var` 키워드를 사용합니다.

```kotlin
class Size(val width: Int, height: Int) {
    val height: Int = height
    val area: Int = width * height
}
```

```kotlin
class Size(val width: Int, val height: Int) {
    val area: Int = width * height
}
```



## Default and named arguments

기본 생성자 안의 디폴트 값은 클래스 본문과 같은 방법으로 설정할 수 있습니다. `val` 또는 `var` 키워드로 속성을 선언하고 할당 연산자를 사용해 디폴드 값을 작성합니다:

```kotlin
class Size(var width: Int = 1, var height: Int = 1) {
    val area: Int = width * height
}
```

기본 생성자에 디폴트 값을 넣은 클래스의 객체를 생성할 때는 인자를 생략합니다:

```kotlin
val size = Size() // width == 1, height == 1
```

클래스의 인스턴스를 생성할 때 named arguments 를 사용하거나 속성 이름없이 값을 제공할 수 있습니다.

```kotlin
val size1 = Size(3, 5) // width == 3, height == 5
val size2 = Size(width = 3, height = 5) // width == 3, height == 5
val size3 = Size(height = 5, width = 3) // width == 3, height == 5
```

객체를 생성할 때 디폴트 값을 사용하여 일부 속성을 생략할 수도 있습니다. 그러나 기본 생성자에서 인자의 순서를 어기려면 항상 named arguments 를 사용해야 합니다:

```kotlin
val sizeWide = Size(10) // width == 10, height == 1
val sizeHigh = Size(height = 10) // width == 1, height == 10
```

기본 생성자는 클래스를 간결하게 정의하는 편리한 방법입니다. 코드가 중복되지 않도록 하려면 기본 생성자와 디폴트 값을 사용하세요.



## Single line classes

기본 생성자에 다른 클래스 멤버가 남아 있지 않다면 중괄호를 생략할 수 있습니다. `area` 속성이 없다고 가정하겠습니다:

```kotlin
class Size(val width: Int, val height: Int)
```

이러한 클래스들은 실생활에서 자주 볼 수 있습니다. 예를들어 데이터 클래스같은 것들이죠 나중에 더 자세히 다루겠습니다.



## Init

기본 생성자는 어떤 코드도 포함할 수 없습니다: 오직 전달받은 인자에 의해 클래스 속성의 값이 설정되는 것 뿐입니다. 때때로 속성의 일부를 설정하기 원한다면 **initializer blocks** 을 이용할 수 있습니다. `init`  키워드가 앞에 붙습니다:

```kotlin
class Size(_width: Int, _height: Int) {
    var width: Int = 0
    var height: Int = 0

    init {
        width = if (_width >= 0) _width else {
            println("Error, the width should be a non-negative value")
            0
        }
        height = if (_height >= 0) _height else {
            println("Error, the height should be a non-negative value")
            0
        }
    }
}
```

`init` 키워드는 기본 생성자의 확장 역할을 하는 코드 블록입니다. 예를 들어 아래 코드는 기본 생성자에서 객체 속성이 설정된 후 메시지를 출력합니다:

```kotlin
class Size(val width: Int, val height: Int) {
    init {
        println("Initializer block that prints the width ($width) and the height ($height)")
    }
}
```

클래스 본문에는 여러개의 initializer blocks 이 있을 수 있습니다. 이 경우 속성의 값 초기화 및 `init` 블록은 순서대로 실행됩니다.

```kotlin
class Size(_width: Int, _height: Int) {
    // 1: the width property is initialized
    val width = _width

    // 2: 1st init block is executed
    init {
        println("First initializer block that prints the width $width")
    }

    // 3: the height property is initialized
    val height = _height

    // 4: 2nd init block is executed
    init {
        println("Second initializer block that prints the height $height")
    }

    // 5: the area property is initialized
    val area = width * height
}
```

위의 예에서 매개변수 이름은 클래스 멤버(`width`, `height` )와 구별하기 위해 밑줄로 시작합니다.(`_width`, `_height`) 가장 보편적인 규약입니다.
