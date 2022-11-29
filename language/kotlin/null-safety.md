# 널 안정성

## 널 참조의 위험성

- 자바를 포함한 많은 프로그래밍 언어에서 가장 많이 발생하는 예외 유형이 `NullPointerException`
- 줄여서 `NPE`
- 자바에서는 `NPE` 를 줄이기 위해 JDK8 에서 `Optional` 을 지원하기 시작
- 자바의 `Optional` 은 값을 래핑하므로 객체 생성에 따른 오버헤드가 발생하고, 컴파일 단계에서 Null 가능성을 검사하지 않음



## Kotlin 에서 NPE 를 해결하는 다양한 방법

- Kotlin 은 언어적 차원에서 NPE 가 발생할 가능성을 제거함
- Kotlin 의 타입은 기본적으로 `Non-Null` 타입이므로 Null 을 허용하지 않음

```kotlin
val a: String = null // compile error

var b: String = "aabbcc"
b = null // compile error
```



- Kotlin 은 null 을 허용하는 `Nullable` 타입을 제공한다
- `Nullable` 참조는 컴파일 단계에서 널 안정성을 제공

```kotlin
// ? 안전 연산자를 사용하게 되면 null인 경우에는 length가 동작하지 않음
var a: String? = null
a.length // complie error
```



- Nullable 참조에 대한 접근은 **안전 연산자**를 사용

```kotlin
var a: String? = null
val result = a?.length 
println(result) // null
```



- **엘비스 연산자**를 사용해 null 이 아닌 경우 특정 값을 사용하도록 하기

```kotlin
var a: String? = null
a?.length

// if...else 문으로 분기를 나누어 null 제어하기
val b: Int = if (a != null) a.length else 0

// 엘비스 연산자
// 좌변이 null 이면 우변을 리턴한다
var b = a?.length ?: 0 

```



## Java 의 null 처리 코드를 Kotlin 으로 재작성하기

```java
import java.util.Optional;

public class Java_NullSafety {
    public static String getNullStr() {
        return null;
		}
    public static int getLengthIfNotNull(String str) {
        if (str == null || str.length() == 0) {
						return 0; 
        }
        return str.length();
    }
    public static void main(String[] args) {
        String nullableStr = getNullStr();
      
        // Optional 사용
        nullableStr = Optional.ofNullable(nullableStr).orElse("null 인 경우 반환");

				// Optional 을 주석처리(위 코드)하고 null을 참조하더라도 컴파일 오류가 발생하지 않음
				int nullableStrLength = nullableStr.length(); 
      	System.out.println(nullableStrLength);
      
				// 메서드 내부에서 null 을 검사하는 방법
				int length = getLengthIfNotNull(null); 
      	System.out.println(length);
		} 
}
```



- Kotlin 으로 변경한 null 처리 코드

```kotlin
fun getNullStr(): String? = null

// null 검사, 만약 null 이면 우변을 리턴
fun getLengthIfNotNull(str: String?) = str?.length ?: 0

fun main() {
  	// null 가능성이 있는 값 저장
  	val nullableStr = getNullStr()

  	// 안전 연산자를 사용하여 null 확인, 안전 연산자가 없다면 compile error 가 발생함
    val nullableStrLength = nullableStr?.length
    println(nullableStrLength) // null

    val length = getLengthIfNotNull(nullableStr)
    println(length) // 0
  
  	println(getLengthIfNotNull(null)) // 0
}
```



## Kotlin 에서도 NPE 가 발생할 수 있다

```kotlin
// 명시적 NPE 호출
throw NullPointerException() // NPE error
```



- 단언 연산자 `!!`
  - `non-null` 에 대한 단언 연산자 
  - 이 코드는 null 이 발생하지 않는 안전한 코드임을 알려주지만 (프로그래머가)
  - **null 을 없애주지는 않는다.**

 `!!` 해당 연산자를 개발한 개발자는 코드의 가독성을 저하시켜 "**해당 코드는 잘 체크해야 한다**" 라는 의미를 담았다고 함

```kotlin
val c: String? = null
val d = c!!.length // NPE error
```



- 이 외에도 자바와 상호운용하는 경우 
  자바에서 NPE 를 유발하는 코드를 코틀린에서 사용하면 NPE 가 발생할 수 있다.

```kotlin
// Java 로 작성된 위 코드 참고
// compile error 를 보여주지 않음 ..!
println(Java_NullSafety.getNullStr().length) // NPE error
```



- **Kotlin 에서 Java 코드를 사용할 때는 항상 Nullable 가능성을 염두해 안전 연산자와 엘비스 연산자를 사용하자**

```kotlin
println(Java_NullSafety.getNullStr()?.length)
```

