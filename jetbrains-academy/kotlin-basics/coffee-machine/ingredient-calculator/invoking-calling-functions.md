# Invoking(calling) functions

### Theory

기억하시겠지만, 우리는 이전에 기능에 대해 논의한 적이 있습니다. 하지만 함수란 무엇일까요? 우리는 그것들을 어떻게 사용할까요? 함수는 명령어의 시퀀스이며, 우리는 프로그램에서 함수의 이름을 호출함으로써 함수를 사용할 수 있습니다. 함수는 하위 프로그램을 나타내며 데이터 인쇄, 제곱근 계산 등과 같은 표준 출력으로 여러 작업을 수행합니다.

아래 그림은 함수의 작동 방식을 보여줍니다. 기본적으로 입력된 매개변수(입력 데이터)를 처리하고 유용한 결과를 생성하거나 아무것도 생성하지 않습니다.

![Function](https://user-images.githubusercontent.com/86511086/202878660-3a19eefb-a324-4b1a-a4dc-5758b92c2e67.png)



### Functions arguments

함수를 사용하려면, 함수 이름 뒤에 괄호를 사용하여 호출합니다.



아래의 예시를 보면 `println` 함수에 매개변수를 넣어 호출합니다:

```kotlin
val text = "Hello"
println(text)
```

새 줄을 출력하기 위한 매개변수 없는 함수도 사용 가능합니다.

```kotlin
println()
```

따라서 일반적인 형태로 아래처럼 함수를 호출할 수 있습니다.

```kotlin
function1() // invokes function1 without an argument
function2(arg1) // invokes function2 while passing an argument
function3(arg1, arg2) // invokes function3 while passing two arguments
// ... and so on
```

여기서 `function` 은 함수의 이름입니다. (헷갈리지 마세요)



### Producing a result

일부 함수는 결과를 생성(반환)하기도 합니다. 변수에 할당할 수도 있습니다:

```kotlin
val result = function(arg)
```

Functions that take arguments and produce a result look like regular math functions.

예를 들어, 숫자의 절대값을 반환하는 함수를 살펴보겠습니다:

```kotlin
val number = -10
val nonNegNumber = Math.abs(number) // it takes -10 and returns 10
```

함수를 사용하며 얻는 이점은 어떤 기능을 사용하기 위해 구현할 필요가 없고 이미 구현된 함수를 그저 호출하기만 하면 되니까 편리한 장점이 있습니다.

`abs` 함수는 `.` 뒤에 쓰여집니다. 이유는 `Math` 객체가 여러 함수를 그룹화 하고 있기 때문인데, 그 중 하나를 호출하기 위해서는 그룹 이름을 써야 합니다. 지금은 자세히 설명하지 않고, 예시와 연습 문제에서 그런 것을 보게 될 것이라는 것만 기억하세요.

`println` 같은 모든 함수는 결과를 반환합니다.

```kotlin
val result = println("text")
println(result) // kotlin.Unit
```

`Unit` 이라 불리는 특별한 값은 사실상 결과가 없다는 것을 의미하죠. 당신의 함수가 아무것도 반환하지 않을 경우 `Unit`을 반환한다는 의미입니다. 지금은 이 정도만 이해하면 됩니다. 아마 당신이 C, Java 언어를 사용하다 왔다면 `Void` 라고 생각할 거에요.

