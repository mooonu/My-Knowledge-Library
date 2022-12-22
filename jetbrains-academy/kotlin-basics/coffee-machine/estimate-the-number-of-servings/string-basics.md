# String basics

## Theory

알다시피, Kotlin 에는 `String`, `Int`, `Double` 과 같이 많은 데이터 타입이 있습니다. 이번 주제에서는 `String` 타입을 집중적으로 다룰 것입니다. 간단한 "Hello world!" 도 문자열을 사용하기 때문에 아주 유용한 타입입니다. 문자열은 다음과 같이 `"" 큰따옴표`  로 둘러쌓인 0개 이상의 문자로 이루어져있습니다 `"John"`,`""`. 여러분은 분명히 프로젝트에 자주 문자열을 사용할 것이며 이제 문자열의 몇 가지 중요한 사항들을 살펴 보겠습니다. 



## The length of a string

종종 `String` 타입의 길이를 알고 싶을 때가 있을 겁니다. 문자열 길이는 큰따옴표로 둘러쌓인 문자의 개수로 결정되며 값을 알기 위해서는 `Int` 타입으로 값을 반환해주는 `.length` 를 사용합니다 :

```kotlin
val language = "Kotlin"
println(language.length) // 6

val empty = ""
println(empty.length) // 0
```



## Concatenating strings

`String` 의 다른 작업으로 문자열 연결이 있습니다. 이는 다른 문자열을 연결해 새로운 문자열을 만들 때 사용됩니다.

`+` 를 사용하여 두 문자열을 연결할 수 있습니다:

```kotlin
val str1 = "ab"
val str2 = "cde"
val result = str1 + str2 // "abcde"
```

두 문자열을 연결했을 때, 새로운 문자열이 생성됩니다.

```kotlin
val one = "1"
val two = "2"
val twelve = one + two 
println(one)      // 1, no changes
println(two)      // 2, no changes
println(twelve)   // 12
```

동일한 표현식으로 여러 문자열을 연결할 수 있습니다:

```kotlin
val firstName = "John"
val lastName = "Smith"
val fullName = firstName + " " + lastName
```

> 문자열 연결은 덧셈과 달리 제시된 수의 순서에 상관없이 계산을 하지 않기 때문에 `str1 + str2` 는 `str2 + str1` 과 같지 않습니다. 



## Appending values to strings

`+` 는 다른 타입의 값을 추가하는 데도 사용됩니다. 추가된 값은 자동으로 `String` 타입으로 변환되고 다음 대상 문자열로 연결됩니다.

```kotlin
val stringPlusBoolean = "abc" + 10 + true
println(stringPlusBoolean) // abc10true

val code = "123" + 456 + "789"
println(code) // 123456789
```

> 해당 표현식은 꼭 `String` 타입으로 시작해야합니다.

첫번째 피연산자가 number 인 경우 동작하지 않습니다.

```kotlin
val errorString = 10 + "abc" // an error here!
```

다른 상황을 고려한 예시:

```kotlin
val stringAndNumbers = "abc" + 11 + 22
println(stringAndNumbers) // abc1122
```

이게 왜 동작했을까요? 자, 첫번째로 문자열 `"abc"` 에 `11` 을 추가한 후 연결된 `abc11` 에  `22` 를 추가했기 때문입니다.

문자를 `String` 에 연결해도 새로운 `String` 이 만들어집니다.

```kotlin
val charPlusString = 'a' + "bc"
println(charPlusString) // abc
val stringPlusChar = "de" + 'f'
println(stringPlusChar) // def
```

또한 결과에 임의의 값을 추가해도 됩니다. 문자와 문자열을 더하면 `String` 이 반환되기 때문입니다:

```kotlin
val charPlusStringPlusInt = 'a' + "bc" + 123
println(charPlusStringPlusInt) // abc123
```

위 내용을 좀 덧붙히자면 `문자 a` 와 `숫자 1` 을 더하면  `문자 b` 가 나오게 됩니다. 그렇기에 `a` 와 숫자를 더하는 것이 아닌 `bc` 를 먼저 더하면 `String` 타입이 되므로 어떤 임의의 값을 추가해도 상관없다는 의미입니다.



## Repeating the string

만약 하나의 문자열을 두 번 이상 반복해야하는 경우 Kotlin은 `repeat` 함수를 제공합니다:

```kotlin
print("Hello".repeat(4)) // HelloHelloHelloHello
```



## Raw string

때때로 문자열에 줄넘김이나 따옴표 같은 심볼이 필요할 겁니다. 이는 다음과 같은 이스케이프 시퀀스로 할 수 있습니다:

```kotlin
// prints 'H' is the first letter of "Hello world!" string.
println("\'H\' is the first letter of \"Hello world!\" string.")
```

만약 새로운 줄과 특수 문자를 사용하여 많은 텍스트를 작성해야 하는 경우 읽기 어려울 수도 있습니다.

이런 경우, raw string 을 사용하면 됩니다. 이는 새로운 줄과 다른 문자들도 포함할 수 있습니다. 그저 `"""` 으로 텍스트를 감싸면 됩니다:

```kotlin
val largeString = """
    This is the house that Jack built.
      
    This is the malt that lay in the house that Jack built.
       
    This is the rat that ate the malt
    That lay in the house that Jack built.
       
    This is the cat
    That killed the rat that ate the malt
    That lay in the house that Jack built.
""".trimIndent() // removes the first and the last lines and trim indents
print(largeString)
```

결과:

```no-highlight
This is the house that Jack built.

This is the malt that lay in the house that Jack built.

This is the rat that ate the malt
That lay in the house that Jack built.

This is the cat
That killed the rat that ate the malt
That lay in the house that Jack built.
```

위 코드를 보시면 `.trimIndent()` 함수도 사용했습니다. 이 함수는 최소 들여쓰기를 제거하고 첫번째, 마지막 줄이 비어있는 경우 공백을 제거합니다:

