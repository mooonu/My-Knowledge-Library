# Functional decomposition

## Solving complex tasks

큰 기능을 여러 기능으로 분해하는 생각은 꽤나 직관적입니다. 만약 여러분이 피자를 요리하고 싶다면 여러분은 모든 재료를 오븐에 넣는 것이 아니라 반죽을 만드는 것부터 실제 요리에 이르기까지 별개의 작업으로 나눌 수 있습니다. 기능 분할은 피자를 요리하는 것이 아니라 큰 기능을 관련된 작은 조각으로 분해하는 것과 같습니다.

스마트 홈 앱을 시뮬레이션하는 프로그램을 생각해보겠습니다. 이 앱은 홈 디바이스를 원격으로 접근할 수 있습니다: 무선 스피커 시스템, 빛, 홈 보안, 잠금 등. 음악 켜기 및 끄기, 조명 켜기 및 끄기, 도어락 설정 등 세 가지 기능을 사용할 수 있는 스마트 홈 앱을 상상해보세요. 이제 컴퓨터 프로그램의 일부로 간주해 봅시다.

스마트 홈 앱이 작동하는 일반적인 알고리즘은 다음과 같은 단계로 나눌 수 있습니다:

1. 입력 데이터 분석 (입력된 비밀번호)
2. 비밀번호가 올바른지 확인
3. 사용자에게 무엇을 하고 싶은지 질문
4. 만약 지원한다면 이를 수행

단일 추가 함수 없이 코드에 이 프로그램이 있다고 상상해보세요. 해당 프로그램의 구조를 살펴보겠습니다:

```kotlin
fun main() {
    // ...
    val password = "76543210"
    var speakersState: String
    var lampState: String
    var doorState: String
    // ...

    // reading the password
    println("Enter password: ")
    val passwordInput = readln()

    // checking if the password is correct
    if (passwordInput != password) {
        println("Incorrect password!")
    } else {
        // asking the user what they want to do
        println("Choose the object: 1 – speakers, 2 – lamp, 3 – door")
        val action = readln()

        when (action) {
            "1" -> {
                // asking the user about the speakers
                when (speakersState) {
                    "on" -> {
                        // ...
                    }
                    "off" -> {
                        // ...
                    }
                    else -> {
                        // ...
                    }
                }
            }
            "2" -> {
                // asking the user about the lights...
            }
            "3" -> {
                // asking the user about the door...
            }
            else -> {
                // ...
            }
        }
    }
}
```

실제 프로그램에서 짧게 만든 버전이지만 코드가 여전히 과하게 보입니다. 위 코드는 우리의 문제에 완벽하게 작동하기에 이대로 내버려 둘 수 있습니다. 그러나 나중에 필요에 따라 조정하거나 기능을 확정하고 싶을 수도 있습니다.

이 코드를 여러 사용자에게 적용하려면 어떻게 해야할까요? 코드의 수를 늘리고 더 복잡하게 만드는 것일까요? 코드의 일부는 여전히 사용되고 일부는 삭제될 수 있습니다. 이 코드를 더 유연하게 만들기 위해 기능 분해를 사용할 수 있습니다.



## Decomposing a program into functions

기능 분할(Functional decomposion)은 큰 기능을 여러 기능으로 나누는 과정입니다. 각 기능은 필요한 결과를 얻기 위한 특정 작업을 수행합니다. 프로그램을 고려하여 여러 번 반복되거나 별도로 수행되는 작업을 식별해야 합니다. 이 방법은 우리가 읽고, 재사용하고 테스트 및 디버깅이 더 쉬운 기능을 얻는 방법입니다.

이제 다시 스마트 홈 앱으로 돌아와서, 어떤 단계를 별도의 기능으로 만들 수 있는지 알아보겠습니다. 우선 사용자와 관련된 작업을 분리하여 기능을 만들 수 있습니다: 음악을 제어하는 기능, 불을 켜고 끄는 기능, 도어락을 작동시키는 기능.

음악을 제어하는 `constrolMusic()` 함수를 확인해보세요. `controlLight()`, `controlDoor()` 함수도 동일한 알고리즘입니다.

```kotlin
// turns the music on and off
fun controlMusic() {
    println("on/off?")
    val tumbler = readln()
    when (tumbler) {
        "on" -> println("The music is on")
        "off" -> println("The music is off")
        else -> println("Invalid operation")
    }
}
```

해당 기능은 우리의 앱이 제공하는 주요 기능을 수행합니다. 작업은 크게 단순해졌으며 어떤 기능을 사용할 것인지 확인하는 데에만 사용됩니다.

비밀번호를 확인하는 기능도 분리할 수 있습니다:

```kotlin
// verifies the password and gives the access to Smart home actions if the password is correct
fun accessSmartHome() {
    val password = "76543210"
    print("Enter password: ")
    val passwordInput = readln()
    if (passwordInput == password)
        chooseAction()
    else
        println("Incorrect password!")
}
```

또한 `chooseAction()` 사용자가 작업을 선택할 수 있는 메뉴로 함수를 만들었습니다. 해당 함수는 사용자에게 어떤 것을 작업을 수행할 것인지 묻고 해당 기능을 제어합니다.

마지막으로, `main` 함수에서 나누었던 기능을 실행할 수 있습니다, 각 기능은 프로그램이 시작되면 호출됩니다:

```kotlin
fun main() {
    accessSmartHome()
}
```

`accessSmartHome` 함수는 비밀번호를 묻고 올바르다면 스마트 홈을 제어할 수 있도록 합니다.



## Adding new features

이제 다른 기능을 추가하려면 해당 기능을 정의하기만 하면 됩니다. 예를들어 새로운 스마트 디바이스가 생겼습니다. 우리는 해당 기기의 전원을 켜고 끄는 기능을 만듭니다. 새 함수를 사용하려면 `chooseAction()` 함수를 수정합니다.

```kotlin
// controls electric kettle
fun controlKettle() {
    // ...
}

// main menu for choosing the action
fun chooseAction() {
    // ...

    // adding new action 4
    println("Choose the object: 1 – speakers, 2 – lamp, 3 – door, 4 – kettle")
    // ...
        "4" -> controlKettle()
    // ...
}
```

보시다시피 이제 조금 바꾸더라도 에러가 나지 않을 프로그램을 만들었습니다. 별도의 함수로 정의되어 있기 때문에 별도의 컴포넌트를 쉽게 테스트 할 수 있습니다. 또한 이러한 방식은 나중에 추가할 기능을 쉽게 넣을 수 있게 합니다.



## Idiom

이미 `if` 와 `when` 은 표현식이 될 수 있음을 알고 있습니다. 따라서 코드를 단순화하는 한 가지 분명한 방법은 표현식을 사용하는 것입니다. 

```kotlin
fun transform(color: String): Int { // you can miss one of the returns
    when (color) {
        "Red" -> return 0
        "Green" -> return 1
        "Blue" -> return 2
        else -> return -1    
    }

fun transform(color: String): Int { // you can accidentally change the variable `colorNumber` 
    var colorNumber = -1
    when (color) {
        "Red" -> colorNumber = 0
        "Green" -> colorNumber = 1
        "Blue" -> colorNumber = 2
    }
    return colorNumber
}

fun transform(color: String): Int { // nice and concise code
    return when (color) {
        "Red" -> 0
        "Green" -> 1
        "Blue" -> 2
        else -> -1    
    }
}
```

single-expression 함수로 사용하기:

```kotlin
fun transform(color: String) = when (color) {
    "Red" -> 0
    "Green" -> 1
    "Blue" -> 2
    else -> -1    
}
```

`if` 표현식의 간결한 형태도 있습니다. 간결한 함수를 작성할 때 사용하세요:

```kotlin
fun max(a: Int, b: Int) = if (a > b) a else b
```
