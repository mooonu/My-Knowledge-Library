# Enum

enum은 상수를 한 곳에 저장하고 동시에 모두 처리할 수 있는 집합입니다.

## Basic Enums

`enum` 은 일반 클래스에서 열거형을 만들 수 있는 키워드입니다:

```kotlin
enum class Rainbow {
    RED, ORANGE, YELLOW, GREEN, BLUE, INDIGO, VIOLET
}
```

각 인스턴스는 enum의 개별 인스턴스입니다. 이제 주문 상태를 나타내는 예시로 수정해보겠습니다:

```kotlin
enum class Status {
    OPEN, PENDING, IN_PROGRESS, RESOLVED, REJECTED, CLOSED
}
```

`RED_COLOR` 와 같은 방식도 가능하고 `RedColor` 와 같은 방식도 가능합니다.

다시 첫번째 예로 돌아가서 각 색상은 Rainbow Enum의 인스턴스이므로 색상의 이름을 생성자에게 전달하여 초기화할 수 있습니다:

```kotlin
enum class Rainbow(val color: String) {
    RED("Red"),
    ORANGE("Orange"),
    YELLOW("Yellow"),
    GREEN("Green"),
    BLUE("Blue"),
    INDIGO("Indigo"),
    VIOLET("Violet")
}
```

색상 값을 사용하는 방법:

```kotlin
val color = Rainbow.RED.color
```

하지만 여러분은 "이걸 사용하면 얻는 이점은 뭐죠?" 라고 물을지도 모릅니다. 나중에 알게 될 것이며 우선은 enum을 수정하고 색상별로 매개변수를 하나 더 추가해보겠습니다:

```kotlin
enum class Rainbow(val color: String, val rgb: String) {
    RED("Red", "#FF0000"),
    ORANGE("Orange", "#FF7F00"),
    YELLOW("Yellow", "#FFFF00"),
    GREEN("Green", "#00FF00"),
    BLUE("Blue", "#0000FF"),
    INDIGO("Indigo", "#4B0082"),
    VIOLET("Violet", "#8B00FF")
}
```

이제 Rainbow Enum은 색상의 이름뿐만 아니라 HEX 값에 대한 정보도 포함하고 있습니다.

```kotlin
val rgb = Rainbow.RED.rgb
```

enum은 사용자 지정 클래스이므로 메서드를 추가할 수 있습니다.

```kotlin
enum class Rainbow(val color: String, val rgb: String) {
    RED("Red", "#FF0000"),
    ORANGE("Orange", "#FF7F00"),
    YELLOW("Yellow", "#FFFF00"),
    GREEN("Green", "#00FF00"),
    BLUE("Blue", "#0000FF"),
    INDIGO("Indigo", "#4B0082"),
    VIOLET("Violet", "#8B00FF");

    fun printFullInfo() {
        println("Color - $color, rgb - $rgb")
    }
}
```

호출:

```kotlin
val rgb = Rainbow.RED
rgb.printFullInfo()
```

출력:

```kotlin
Color - Red, rgb - #FF0000
```



## Inside Enum

`name`:

```kotlin
val color: Rainbow = Rainbow.RED
println(color.name) // RED
```



`ordinal`:

```kotlin
val color: Rainbow = Rainbow.GREEN
println(color.ordinal) // 3
```



`values()`:

```kotlin
fun isRainbow(color: String) : Boolean {
    for (enum in Rainbow.values()) {
        if (color.toUpperCase() == enum.name) return true
    }
    return false
}
```

```kotlin
println(isRainbow("black")) // false
```



`valueOf()`:

만약 적합한 인스턴스가 존재하지 않는다면 `IllegalArgumentException` 예외가 발생합니다. 대소문자를 구분하므로 기억해야합니다.

```kotlin
println(Rainbow.valueOf("RED")) // RED
```



잠시 `values()` 예시를 둘러보겠습니다:

```kotlin
enum class Rainbow(val color: String, val rgb: String) {
    RED("Red", "#FF0000"),
    ORANGE("Orange", "#FF7F00"),
    YELLOW("Yellow", "#FFFF00"),
    GREEN("Green", "#00FF00"),
    BLUE("Blue", "#0000FF"),
    INDIGO("Indigo", "#4B0082"),
    VIOLET("Violet", "#8B00FF"),
    NULL("", "");

    fun printFullInfo() {
        println("Color - $color, rgb - $rgb")
    }
}

fun findByRgb(rgb: String): Rainbow {
    for (rainbow in Rainbow.values()) {
        if (rgb == rainbow.rgb) return rainbow
    }
    return Rainbow.NULL
}
```

메서드 사용:

```kotlin
println(findByRgb("#FF0001")) // NULL
```

RGB 색상을 찾을 수 없는 경우를 반환하기 위해 NULL 상수를 추가했습니다.
