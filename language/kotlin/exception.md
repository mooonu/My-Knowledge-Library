# 예외처리

- Kotlin 의 모든 예외 클래스는 최상위 예위 클래스인 `Throwable` 을 상속한다

<img width="853" alt="exception" src="https://user-images.githubusercontent.com/86511086/204520629-e7532a6e-e804-4862-80d0-d20a803904ec.png">

- Error : 시스템에 비정상적인 상황이 발생. 예측이 어렵고 기본적으로 복구가 불가능 함
  - e.g. OutOfMemoryError, StackOverflowError, etc
- Exception : 시스템에서 포착 가능하여 (try-catch) 복구 가능. 예외 처리 강제
  - IOException, FileNotFoundException, etc
  - `@Transactional` 에서 해당 예외가 발생하면 기본적으로 롤백이 동작하지 않음
    - rollbackFor 를  사용해야함
- RuntimeException : 런타임시에 발생하는 예외. 예외 처리를 강제하지 않음
  - e.g. NullPointerException, ArrayIndexOutOfBoundsException, etc
- Kotlin 에서는 자바의 Exception 계층을 Kotlin 패키지로 래핑한다



- 자바에서 Checked Exception 은 컴파일 에러가 발생하기 때문에 무조건 try-catch 로 감싸거나 throws 로 예외를 전파해야한다

```java
try {
  Thread.sleep(1); // 감싸지 않으면 컴파일에러 발생
} catch (InterruptedException e) {
  // 예외 처리
}
```



- Kotlin 은 `Checked Exception` 을 강제하지 않는다

```kotlin
Thread.sleep(1); // 컴파일 에러 발생 x
```



- 원하는 경우에 try-catch 를 사용할 수 있다

```kotlin
try {
  Thread.sleep(1)
} catch (e: Exception) {
  // 예외 처리
}
```



- Kotlin 의 try-catch 는 **표현식**이다

```kotlin
val a = try {
  "1234".toInt()
} catch (e: NumberFormatException) {
  println("catch 동작")
}

println(a) // 1234
```



- `finally` 를 사용하면 try-catch 의 마지막에 수행될 코드를 작성할 수 있다 (자바와 동일)

```kotlin
fun main() {
    try {
        throw Exception()
    } catch (e: Exception) {
        println("예외 발생")
    } finally {
        println("finally")
    }
}
// 예외 발생
// finally
```



- Kotlin 에서 Exception 을 발생시키려면 `throw` 를 사용한다

```kotlin
throw Exception("예외 발생")
/*
Exception in thread "main" java.lang.Exception: 
	at MainKt.main(Main.kt:2)
	at MainKt.main(Main.kt)
*/
```



- `throw` 역시 **표현식** 따라서 리턴할 수 있음

```kotlin
fun failFast(message: String): Nothing {
  throw IllegalArgumentException(message)
}

// 표현식임을 보여주는 다른 예제
val nullableValue: String? = null
val value = nullableString ?: throw IllegalStateException()
```



- `Nothing` 타입을 사용하면 컴파일러는 해당 코드 이후는 실횡되지 않는다는 경고를 보여줌

```kotlin
failFast("에러 발생")

// Unreachable code
println("메시지가 출력 될까?")
/*
Exception in thread "main" java.lang.IllegalArgumentException: 예외 발생
	at MainKt.failFast(Main.kt:8)
	at MainKt.main(Main.kt:2)
	at MainKt.main(Main.kt)
*/
```

> `Nothing` 타입이란? - 아직은 이해하기 어려우니 기초를 더 공부하고 정리하자에용



- 엘비스 연산자와 `Nothing` 타입을 사용하면 null 안전 코드를 작성하지 않아도 된다

절대로 null 이 나오지 않기 때문

```kotlin
fun main() {
  val a: String? = null
  val b: String = a ?: failFast("a is null")
  
  println(b.length)
}

fun failFast(message: String): Nothing {
  throw IllegalArgumentException(message)
}
```

