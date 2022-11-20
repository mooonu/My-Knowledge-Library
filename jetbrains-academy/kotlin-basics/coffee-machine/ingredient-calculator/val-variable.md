# Val variable

### Val variables

```kotlin
val pi = 3.1415
val helloMsg = "Hello"

println(pi)       // 3.1415
println(helloMsg) // Hello
```

두 변수 모두 수정될 수 없습니다, 하지만 언제든 우리가 원할 때 접근할 수 있죠.

`val` 변수를 수정하려고 하면 컴파일러는 `Val cannot be reassinged` 에러를 보여줄 겁니다.

```kotlin
val pi = 3.1415
pi = 3.1416 // error line
```



만약 `val` 변수가 값이 할당되기 이전에 사용된다면, 컴파일러는 다음과  같은 에러를 보여줄 겁니다.

```kotlin
val boolFalse: Boolean
println(boolFalse) // error line
```

위의 코드로 `Variable 'boolFalse' must be initialized` 에러를 보게 될 겁니다.\
이것을 수정하려면 **변수에 접근하기 전 값을 할당**해주면 됩니다.

```kotlin
val boolFalse: Boolean // not initialized
boolFalse = false      // initialized
println(boolFalse)     // no errors here
```

###

### Val variables and mutability

```kotlin
// list creation
val myMutableList = mutableListOf(1, 2, 3, 4, 5)
// trying to update the list
myMutableList = mutableListOf(1, 2, 3, 4, 5, 6) // error line
```

두번째 줄에서는 `val` 변수에 재할당 하려고 했기 때문에 컴파일되지 않습니다. 그러나, 꼭 기억해야할 요점이 있습니다.

<mark style="background-color:yellow;">val 변수의</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">**내부 상태는 항상 변경할 수 있습니다.**</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">즉, 변수를 재할당하는 것은 금지되어 있지만 다른 방법으로 내용을 수정할 수 있습니다.</mark>



So, the following code is correct:

```kotlin
// list creation
val myMutableList = mutableListOf(1, 2, 3, 4, 5)
// adding a new element
myMutableList.add(6)   // it works
// printing the list
println(myMutableList) // [1, 2, 3, 4, 5, 6]
```

보다시피, 다른 정수를 추가하여 `list` 의 내부 상태를 변경했습니다. add() 함수를 호출할 때, **변수 자체의 값을 바꾸는 것이 아니라 변수가 나타내는 list의 상태를 변경했습니다.**



### Const variables

Kotlin에는 `const` 수식어도 있는데, 이것은 `val` 키워드 앞에 컴파일 타임 상수를 선언하는 데 사용됩니다. 런타임에도 바뀌지 않습니다:

```kotlin
const val MY_STRING = "This is a constant string"
```

아래 코드를 따라가면 에러를 볼 수 있는데, 프로그램이 실행되기 전에 값을 알 수 없고 상수가 아니기 때문입니다:

```kotlin
const val MY_STRING = readln() // not a constant String!!!
```



`const` 수식어가 적용되려면 몇가지 제약이 있습니다. 첫번째로, String 이거나 원시 타입의 변수만 가능합니다:

```kotlin
const val CONST_INT = 127
const val CONST_DOUBLE = 3.14
const val CONST_CHAR = 'c'
const val CONST_STRING = "I am constant"
const val CONST_ARRAY = arrayOf(1, 2, 3) // error: only primitives and strings are allowed
```

게다가, `const` 는 함수 외부의 최상위 레벨에서 선언되어야 합니다:

```kotlin
const val MY_INT_1 = 1024 // correct line

fun main() {
    const val MY_INT_2 = 2048 // error: Modifier 'const' is not applicable to 'local variable'
}
```



### When to use val variables

`val` 키워드가 변수에 대해 어떻게 작동되는지 이해하길 바라며. 이것을 언제 사용하는지 고민할 때가 되었습니다.

**좋은 방법은 기본적으로** `val` **변수를 사용하는 것이 좋습니다.** 그런 다음 코드를 보고 필요에 따라 `var` 변수로 바꾸세요.

```kotlin
var a = 1024
val b = 256
val c = 128
a += b * c
```

이 방법을 사용하면 최소한의 가변 변수로 코드를 작성할 수 있으므로 오류가 줄어듭니다.
