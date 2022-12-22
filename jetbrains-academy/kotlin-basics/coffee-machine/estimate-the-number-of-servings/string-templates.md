# String templates

## Theory

때때로 변수의 값을 텍스트에 넣고 싶을 때가 있습니다. 운이 좋게도 Kotlin 은 문자열 템플릿을 제공합니다!

오늘의 온도에 대한 메시지를 표시해야한다고 가정해봅시다:

```
Now, the temperature in ... is ... degrees Celsius.
```

`...` 대신 특정 값을 표시해야 합니다.

`city` 와 `temp` 변수가 있고, 문자열 연결을 통해 결과를 만들 수 있습니다.

```kotlin
val city = "Paris"
val temp = "24"

println("Now, the temperature in " + city + " is " + temp + " degrees Celsius.")
```

간단한 해결방법이죠. 하지만 완벽한가요? 아직 약간 좀 어색합니다.

Kotlin 은 문자열 템플릿을 사용하여 위와 동일한 작업을 수행하는 더 편리한 방법을 제공합니다. 변수의 이름 앞에 `$` 달러 기호를 작성하면 됩니다:

```kotlin
val city = "Paris"
val temp = "24"

println("Now, the temperature in $city is $temp degrees Celsius.")
```

더욱 코드를 읽기 쉬워졌고 위와 동일한 메시지를 출력합니다.

```
Now, the temperature in Paris is 24 degrees Celsius.
```

새로운 변수를 만들수도 있습니다:

```kotlin
val value = "55"
val currency = "dollars"
val price = "$value $currency" // "55 dollars"
```

## Templates for expressions

문자열 템플릿을 사용해서 문자열안에 표현식을 넣을 수도 있습니다. `$` 달러 기호 다음에 중괄호를 적고 그 안에 표현식을 작성하면 됩니다:

```kotlin
val language = "Kotlin"
println("$language has ${language.length} letters in the name")
```

결과:

```
Kotlin has 6 letters in the name
```

`language.length` 은 평가될 식입니다. 만약 중괄호를 적지 않는다면 다른 값이 출력됩니다:

```
Kotlin has Kotlin.length letters in the name
```

따라서 실수를 피하기 위해서는 문자열 템플릿안의 표현식에 중괄호를 항상 사용해야합니다. 변수 값만 출력하려면 중괄호를 추가하지 마세요

## Idiom

> 프로그래밍에서 관용구(Idiom)는 자주 사용하는 코드 형태나 패턴입니다 관례 라고도 할 수 있습니다. (내 의견)

더 자세한 내용은 [여기](https://kotlinlang.org/docs/idioms.html)에서 확인할 수 있습니다.
