# 함수

- 함수의 선언

```kotlin
fun 함수명(인자: 타입): 반환 타입 {
  	return 결과
}

fun sum(a: Int, b: Int): Int {
  	return a + b
}
```



- 함수 본문은 표현식이 될 수 있다

  `표현식은 값으로 평가될 수 있는 문(statement)이다.`

```kotlin
fun sum(a: Int, b: Int): Int = a + b
```



- 타입 추론을 이용한 함수 선언

```kotlin
fun sum(a: Int, b: Int) = a + b
```



- 중괄호가 있는 경우에는 타입 추론 불가

```kotlin
fun sum(a: Int, b: Int) {
  	return a + b // error
}
```



- 반환 타입이 없는 경우 Unit이 반환 타입이 된다

```kotlin
fun printSum(a: Int, b: Int): Unit {
    println("$a + $b = ${a + b}")
}

// Unit 생략 가능
fun printSum(a: Int, b: Int) {
    println("$a + $b = ${a + b}")
}
```



- **Default Arguments** ( 자바에는 디폴트 기능이 없음 )

```kotlin
fun greeting(message: String = "hello world!!") {
  	println(message) 
}

fun main() {
  	greeting() // hello world!!
  	greeting("메롱") // 메롱
}
```



- **Named Arguments**

인자에 맞는 값을 입력할 때 실수를 줄여줄 수 있음

```kotlin
fun log(level: String = "INFO", message: String) {
    println("[$level]$message")
}

fun main() {
    log(message = "인포 로그")
    log(level = "DEBUG", "디버그 로그")
    log("WARN", message = "워닝 로그")
    log(level = "ERROR", message = "에러 로그") // good
}
```

