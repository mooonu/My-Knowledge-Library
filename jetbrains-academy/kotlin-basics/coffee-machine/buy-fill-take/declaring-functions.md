# Declaring funtions

## Program decomposition

Kotlin 은 함수라고 불리는 아주 유용한 기능을 지원합니다. 함수는 어떤 명령을 정리해 놓은 일련의 지시입니다. 어떤 면에서 함수는 하위 단계의 프로그램 같습니다. 함수는 이름을 가지며 필요할 때 호출하여 사용할 수 있습니다. Kotlin 표준 라이브러리에는 `println` 과 같은 많은 함수들이 있습니다. 만약 충분하지 않다면 새로운 함수를 선언하고 표준 함수와 같은 방법으로 호출할 수 있습니다.

함수는 프로그램을 재사용 가능하게 분리할 수 있습니다. 이를 decomposition(분리 또는 분해) 라고 부릅니다. 이러한 재사용 가능한 프로그램들을 언제든 원할 때 필요한 만큼 호출할 수 있습니다. 분리된 프로그램은 모듈식 구조를 갖습니다; 이것은 `main` 함수 안에 수천개의 코드 줄이 있는 것보다 유지보수가 쉽습니다. 



## Basic syntax

함수를 선언하기 위해서는 `fun` 키워드로 나타내고 함수의 이름, 괄호안에 매개변수를 작성하고 결과 값의 타입을 작성해줘야합니다. 

```kotlin
fun functionName(p1: Type1, p2: Type2, ...): ReturnType {
    // body
    return result
}
```

함수는 다음과 같은 구조를 따르고 있습니다:

- 변수 이름과 동일한 규칙 및 권장 사항을 따르고 있습니다.
- 괄호안의 매개변수는 각각 이름과 타입을 `:` 으로 분리합니다.
  매개변수는 `,` 으로 나누어 작성합니다.
- 반환 값 타입 (선택 사항 )
- 함수 내부의 코드 블럭은 문(statements)과 식(expressions)을 포함합니다.
- `return` 키워드 다음에 결과가 표시됩니다. (선택 사항)

매개변수의 타입과 결과는 `Int, Double, Boolean` 등 모든 타입이 될 수 있습니다. 



## Defining a simple function

정수의 합을 계산하는 함수를 선언하고 결과를 확인해봅시다.

```kotlin
fun sum(a: Int, b: Int): Int {
    val result = a + b
    return result
}

fun main() {
    val result1 = sum(2, 5)
    println(result1) // 7
    
    val result2 = sum(result1, 4)
    println(result2) // 11
}
```

우리가 함수를 처음 호출할 때, 값 `2` 와 `5` 를 매개변수로 전달했습니다. 그 후 함수의 매개변수 `a` 와 `b` 에 각각 할당 했습니다. 결과적으로 함수는 결과 값을 반환했습니다. `result` 타입은 함수에서 선언된 값의 반환 타입과 같습니다. 우리가 두번째 호출 할 때, `result1` 을 전달해서  `7` 과 `4` 가 매개변수가 되었습니다. 따라서 함수는 `11` 을 반환합니다.

> 함수의 매개변수는 오로지 해당 함수만 접근할 수 있습니다.



## Function parameters

아시다시피 매개변수는 함수의 출력 데이터를 제공합니다. 같거나 다른 타입의 매개변수를 하나 또는 여러개 선언할 수 있습니다. 또한 매개변수를 갖지 않는 함수를 선언할 수도 있습니다 하지만 괄호는 꼭 필요합니다.

예시: 

```kotlin
/**
 * The function returns its argument
 */
fun identity(a: Int): Int {
    return a
}

/**
 * The function returns the sum of two Ints
 */
fun sum(a: Int, b: Int): Int {
    return a + b
}

/**
 * The function just returns 3
 */
fun get3(): Int {
    return 3
}

fun main() {
    println(identity(1000)) // 1000
    println(sum(200, 300)) // 500    
    println(get3()) // 3
}
```

보시다시피, 우리는 `main` 함수 안에서 선언한 함수를 호출했습니다. 그러나 다른 정규 함수에서도 선언한 함수를 호출할 수 있습니다.

Kotlin 1.4 부터 매개변수의 끝에 `,` 를 작성할 수 있습니다. 변수를 쉽게 복사-붙혀넣을 수 있기 때문에 매개변수가 많거나 여러 줄에 걸쳐 매개변수를 작성하는 경우 유용할 수 있습니다.

```kotlin
fun sum(a: Int, b: Int, ): Int { // you can easily add some arguments
    // 
}

fun max(
    a: Int,
    b: Int,
): Int { // you can swap arguments without worrying about commas
    // 
}
```



## Return type

함수는 단일 값을 반환하거나 반환하지 않을 수 있습니다. 만약 함수가 무언가를 반환하는 경우 함수의 본문에는 `return` 키워드와 결과가 뒤에 와야 합니다. 때때로, 아무것도 반환하지 않고 싶다면, 아무것도 반환하지 않도록 함수를 선언하는 두가지 방법이 있습니다.

- 반환 타입 생략:

```kotlin
/**
 * The function prints the values of a and b
 */
fun printAB(a: Int, b: Int) {
    println(a)
    println(b)
}
```

-  `Unit` 을 반환 타입으로 지정:

```kotlin
/**
 * The function prints the sum of a and b
 */
fun printSum(a: Int, b: Int): Unit {
    println(a + b)
}
```



## Function body

`main` 의 내부와 같이 함수 본문에 모든 문을 작성할 수 있습니다. 매개변수 외에 해당 함수에서만 표시되는 새로운 변수를 선언할 수 있습니다.

예를 들어, 이 함수는 숫자의 마지막 자리를 추출한 다음 반환합니다.

```kotlin
fun extractLastDigit(number: Int): Int {
    val lastDigit = number % 10
    return lastDigit
}
```

추가 변수를 제외하여 위 코드를 단순하게 바꿀 수 있습니다.

```kotlin
fun extractLastDigit(number: Int): Int {
    return number % 10
}
```

함수의 본문에서 어떠한 연산자든 작동할 수 있습니다. 예시로 이 함수는 숫자가 양수인지 아닌지를 확인하는 관계 연산자를 이용했습니다:

```kotlin
fun isPositive(number: Int): Boolean {
    return number > 0
}
```

함수 `isPositive` 는 정수를 받아 불리언 값으로 반환합니다. 표현식의 `number > 0` 의 결과가 `true` 또는 `false` 이기 때문입니다.

예시 한 가지를 더 살펴봅시다. 반환문 (`return`) 뒤의 줄은 실행되지 않습니다. (unreachable code)

```kotlin
/**
 * It returns "hello"
 */
fun getGreeting(): String {
    return "hello"   // Ends the function
    println("hello") // Will not be executed
}
```



## Single-expression functions

함수가 단일 표현식을 반환하는 경우 다음과 같이 중괄호를 생략할 수 있습니다:

```kotlin
fun sum(a: Int, b: Int): Int = a + b

fun sayHello(): Unit = println("Hello")

fun isPositive(number: Int): Boolean = number > 0
```

반환 타입을 지정하는 것은 자동으로 유추할 수 있으므로 선택사항입니다.

```kotlin
fun sum(a: Int, b: Int) = a + b // Int

fun sayHello() = println("Hello") // Unit

fun isPositive(number: Int) = number > 0 // Boolean
```



## Idiom

같은 값 다른 코드 

더욱 짧고 간결하게 사용할 수 있음

```kotlin
fun theAnswer() = 42   // short and clear
...
fun theAnswer(): Int { // equivalent common function
    return 42
}
```
