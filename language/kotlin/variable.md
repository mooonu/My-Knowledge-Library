# 변수

- 변수 선언 키워드와 선언
  - **val** (value) 는 초기화된 후에는 변경할 수 없는 **불변 변수( constant )일 때 선언**
    `read-only`
  - **var** (variable) 는 변경할 수 있는 **가변 변수를 선언**

```kotlin
val name: String = "moonu"

var age: Int = 23
```



- **var** 의 규칙 - 초기 값과 같은 타입의 값만 사용 가능 (타입 고정)

```kotlin
var number = 10
number = 11 // ok
number = "twelve" // error
```



- 타입 생략 (타입 추론)

```kotlin
val text = "Hello, I am studying Kotlin now."
val n = 1
```



- 지연 할당

```kotlin
val age: Int // 지연 할당을 위해선 타입 명시 필수
age = 23 // ok

val age
age = 23 // error
```



- 탑-레벨 선언 가능

```kotlin
var x = 5 // top-level

fun main() {
    x += 1
    println(x)
}
```
