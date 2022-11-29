# 흐름제어

### 종류

- If...else
- when
- for
- while



## if...else

- 기본 문법

```kotlin
if (condition) {
  	// true 
} else {
  	// false
}
```



- 사용

```kotlin
val job = "developer"

if (job == "developer") {
  	println("개발자임")
} else {
  	println("개발자 아님")
}
```



- Kotlin 의 if...else 는 **표현식**이다.

자바는 statement 이므로 값을 반환할 수 없음 ( Kotlin 과 반대 )

```kotlin
val age: Int = 23

val adult = if (age > 20) {
  	"성인"
} else {
  	"아이"
}

println(adult) // 성인
```



- Kotlin 은 삼항 연산자가 존재하지 않음 If...else가 표현식이므로 필요없다.

```kotlin
val a = 1
val b = 2
val c = if (b > a) b else a
```



## when

- 기본 문법

```kotlin
when (대상 변수) {
  	조건 -> 참인 경우 실행
  	조건 -> 참인 경우 실행
  	else -> 참이 없을 경우 실행
}
```



- 자바의 switch와 유사

기존 자바의 switch 문은 표현식이 아니어서 값을 반환하지 못했다. (최신 자바는 지원)

```java
int day = 2;
String result = "";
switch (day) {
    case: 1
      	result = "monday";
    		break;
    case: 2
      	result = "tuesday";
    		break;
}

System.out.println(result); // tuesday
```



- Kotlin 의 when 은 **표현식**이다.

```kotlin
// 위의 자바코드를 kotlin 의 when 식으로 변환
val day: Int = 2

val result = when (day) {
  	1 -> "monday"
  	2 -> "tuesday"
  	else -> "error"
}

println(result) // tuesday
```



- else 생략 가능

```kotlin
enum class Color {
    RED, GREEN, BLUE
}

fun getColor() = Color.RED

fun main() {
    // case1 : 모든 경우의 수 커버 o
    when (getColor()) {
        Color.RED -> println("red")
        Color.GREEN -> println("green")
        Color.BLUE -> println("blue")
        // 모든 경우의 수를 커버하므로 'else' 필요 없음
    }
    
    // case2 : 모든 경우의 수 커버 x
    when (getColor()) {
        Color.RED -> println("red")
        else -> println("not red")
        // GREEN, BLUE 의 경우가 남아 있으므로 else 필요
    }
}
```



- 여러 조건을 `,`  로 구분해 한 줄에서 정의할 수 있음

```kotlin
fun getNumber() = 2

fun main() {
  	when (getNumber()) {
      	0, 1 -> print("number == 0 or number == 1")
      	else -> print("0과 1이 아닌 경우")
    }
}
```



## for loop

> 자바의 `foreach` 와 유사



- 범위 연산자 `..` 을 사용해 for loop 돌리기

```kotlin
for (i in 0..3) { // 0 <= .. <= 3
  	println(i)
}
// 0
// 1
// 2
// 3
```



- `until` 을 사용해 반복하기 ( 뒤에 온 숫자는 포함하지 않음 )

```kotlin
for (i in 0 until 3) { // 0 <= until < 3
  	println(i)
}
// 0
// 1
// 2
```



- `step` 에 들어온 값 만큼 증가시키기

```kotlin
for (i in 0..6 step 2) {
  	println(i)
}
// 0
// 2
// 4
// 6
```



- `downTo` 를 사용해 반복하며 값 감소시키기 ( 1씩 감소함 )

```kotlin
for (i in 7 downTo 4) { // 1까지 감소하며 값 리턴하기
  	println(i)
}
// 7
// 6
// 5
// 4
```



- 전달받은 배열 반복하기

```kotlin
val arr = arrayOf(1, 2, "hello", true)

for (i in arr) {
  	println(i)
}
// 1
// 2
// hello
// true
```



## while loop

> 자바의 while 문과 동일



- 기본 문법

```kotlin
var x = 5

while (x > 0) {
  	println(x)
  	x--
}
// 5
// 4
// 3
// 2
// 1
```

