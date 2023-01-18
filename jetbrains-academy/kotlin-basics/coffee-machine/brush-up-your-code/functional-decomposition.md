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





