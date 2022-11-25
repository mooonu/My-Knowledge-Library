# Reading data with a readln

### Theory

이 주제에서 사용자의 입력으로부터 정보를 읽는 방법과 상호작용하는 방법을 배울 수 있습니다.\
프로그램은 꽤 자주 사용자에게 특정 정보를 요청합니다. 또한 우리는 readln() 함수로 변수를 관리하고 다른 타입으로 작동하도록 하는 방법을 살펴보겠습니다.



### Standard input

**표준입력**은 프로그램에 입력되는 데이터 스트림입니다. 운영체제에서 지원합니다. 기본적으로 표준입력은 키보드에서부터 데이터를 가져오지만 파일에서 데이터를 가져오는 것도 가능합니다.

모든 프로그램이 표준입력을 사용하진 않습니다, 그래도 당신은 꽤 자주 사용할 겁니다. \
프로그래밍 문제를 해결하는 방법은 다음과 같습니다:

* 표준입력으로부터 데이터 읽기
* 결과를 얻기위한 데이터 처리
* 결과를 출력

무언가 유용한 프로그램을 작성하기 이전에 데이터를 입력받고 읽는 방법을 이해해야합니다.



### Using readln

코틀린에서는 입력을 통한 데이터를 읽기 위해서 `readln()` 함수를 사용할 수 있습니다.\
이 함수는 한 줄을 문자열로 읽습니다:

```kotlin
val line = readln()
```

변수가 선언된 줄의 타입은 `String` 입니다 `readln()` 표현식이 `String` 값으로 반환하기 때문입니다.



만약 Kotiln의 이전 버전으로 작업하신다면 `readln()` 대신에 `readLine()!!` 을 사용해야 합니다.\
이 함수는 동일하게 작동하지만 `readln()` 은 더 짧고 선호됩니다. 따라서 Kotiln 1.6 또는 그 상위 버전에서는 `readln()` 을 사용하면 됩니다.

```kotlin
val line = readLine()!! // before Kotlin 1.6
```

아마도 느낌표 때문에 작은 혼란이 있을겁니다. 이 구문은 **컴파일러에게 비어 있지 않은 입력을 보장**합니다. \
나중에 더 자세히 이야기하겠습니다.



입력을 받은 후 출력하는 예제:

```kotlin
fun main() {
    val line = readln()
    println(line)
}
```

입력 예제:

```
Hello, Kotlin
```

출력 결과:

```
Hello, Kotlin
```

기본적으로 입력한 데이터의 정보를 확인하기 위해서는 엔터키를 눌러야 합니다.

이제 `readln()` 을 사용해서 다른 타입의 데이터를 읽는 방법을 알아봅시다.



### toInt() and toLong()

때때로 사용자로부터 숫자 데이터를 얻어야 하는 경우가 있습니다. 예를들어 졸업년도 또는 사용자의 나이에 대한 정보를 얻어야하는 상황을 말합니다. 숫자 데이터를 얻기 위해서는 `toInt()` 함수를 사용합니다. \
입력을 정수로 변경하려면 `toInt()` 와 `.` 구문을 사용합니다:

```kotlin
println("Print any number: ") 
val number = readln().toInt() 
print("You printed the number: ")
print(number) 
```

입력 예제:

```
56
```

출력 결과:

```
Print any number: 
56 
You printed the number: 56
```



큰 수를 처리하려면 `toLong()` 함수를 사용합니다:

```kotlin
println("How much is your yacht worth?")
val cost = readln().toLong()
print("You printed: ")
print(cost)
```

출력 결과:

```
How much is your yacht worth?
10000000000
You printed: 10000000000
```



### toDouble() and toBoolean()

더 정확한 값을 얻으려면 어떻게 해야할까요? 휘발유 1리터의 값을 정확히 알아내야한다고 가정해보면\
`toInt()` 나 `toLong()` 은 값을 정수로 반환하니 사용하지 않을 겁니다. 따라서 `toDouble()` 을 사용해야합니다.

```kotlin
println("Print any double type number:")
val number = readln().toDouble()
println("You printed the number: ")
print(number)
```

출력 결과:

```
Print any double type number:
0.5673421
You printed the number: 
0.567342
```

Boolean 에서도 동일하게 작동됩니다: `toBoolean()`

```kotlin
println("The earth is flat. Print true or false:")
val answer = readln().toBoolean()
print("The earth is flat: ")
print(answer)
```

출력 결과:

```
The earth is flat. Print true or false:
false
The earth is flat: false
```



### Multiple inputs

여러 입력을 받고 처리하는 게 가능할까요? 당연히 가능합니다: 여러개의 변수를 선언하고 각각의 값으로 `readln()`을 사용합니다.&#x20;

```kotlin
val a = readln()
val b = readln().toInt()
val c = readln()
print(a)
print(" ")
print(b)
print(" ")
print(c)
```

```
You earned
100
points!
```



### **Reading multiple values in one line**

한 줄에 두 개의 값을 넣고 싶다면, 다음과 같은 구성을 사용해보세요:

```kotlin
val (a, b) = readln().split(" ")
println(a)
println(b)
```

입력 예제:

```
Hello, Kotlin
```

출력 결과:

```
Hello,
Kotlin
```

여기서의 split 함수는 문자열을 공백으로 잘라서 변수 `a`, `b` 에 저장합니다.



같은 방법으로, 한 줄당 최대 5개의 값을 읽을 수 있습니다.

```kotlin
val (a, b, c, d) = readln().split(" ")
println(a)
println(b)
println(c)
println(d)
```

입력 예제:

```
Have a nice Kotlin
```

출력 예제:

```
Have
a
nice
Kotlin
```

