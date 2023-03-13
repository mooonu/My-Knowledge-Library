# 변수

- 변수 선언 키워드와 선언
  - **val** (value) 는 초기화된 후에는 변경할 수 없는 **불변 변수( constant )일 때 선언**
    `read-only`
  - **var** (variable) 는 변경할 수 있는 **가변 변수를 선언**

```kotlin
val name: String = "moonu"

var age: Int = 23
```



- **val** 는 값이 `런타임` 에 결정된다

재할당하는 것은 금지되어 있지만, 다른 방법으로 내용을 수정할 수 있음 즉 **내부 상태는 변경할 수 있다.**

```kotlin
// 런타임 결정 예시
fun sum(a: Int, b: Int) = a + b

fun main() {
		val num = sum(40, 20)
  	println(num)
}

// 내부 상태 변경 예시
fun main() {
    val myMutableList = mutableListOf(1, 2, 3, 4 ,5)
    println(myMutableList) // [1, 2, 3, 4, 5]
    myMutableList.add(100)
    println(myMutableList) // [1, 2, 3, 4, 5, 100]
}
```

위처럼 변수 자체의 값을 바꾸는 것이 아닌 변수가 나타내는 List의 상태를 변경함.



- kotlin 에는 **const** 수식어도 있는데 이는 값이 `컴파일` 에 결정



`const` 가 적용되기 위한 제약조건 1 : String 또는 원시 타입의 변수만 적용이 가능함

```kotlin
const val CONST_INT = 127
const val CONST_DOUBLE = 3.14
const val CONST_ARRAY = arrayOf(1, 2, 3) // error: only primitives and strings are allowed
```



제약조건 2 : 함수 외부의 탑-레벨에서 선언되어야 함

```kotlin
const val MY_INT_1 = 1024 // correct line

fun main() {
    const val MY_INT_2 = 2048 // error: Modifier 'const' is not applicable to 'local variable'
}
```



하지만 클래스 내에서 사용하려면 `companion object` 에 선언해야함

``` kotlin
class Constant() {
    companion object {
        const val PI: Double = 3.14
        const val NAME: String = "김승현"
    }
}

fun main() {
    val constant = Constant()
    println(constant.NAME) // error
  
  	println(Constant.NAME) // 김승현 
}
/*
const val의 경우 컴파일 시에 데이터가 메모리에 존재하기 때문에, 사용 시 객체를 생성해서 이에 접근하는 것이 아니고, 클래스명.상수명의 형태를 사용해서 직접 접근
*/
```



- **var** 의 규칙 - 초기 값과 같은 타입의 값만 사용 가능 (타입 고정)

```kotlin
var number = 10
number = 11 // ok
number = "twelve" // error
```



- 타입 생략 (타입 추론)

```kotlin
val/var identifier = initialization

val name = "moonu"
```



- 지연 할당

변수를 선언하고 나중에 초기화하는 것을 지연 할당이라고 함 하지만 이때는 타입 추론이 동작하지않음
따라서 나중에 초기화 한다면 타입을 명시해줘야함

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



