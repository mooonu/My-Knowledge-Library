# Property accessors

## Property getter

`name` 속성을 가진 간단한 클래스 `Client` 가 있다고 가정하겠습니다:

```kotlin
class Client {
    val name = "Unknown"
}

val client = Client()
```

프로퍼티의 값을 가져오는 방법:

```kotlin
client.name
```

위의 방법은 매우 간단하지만 사실은 속성의 값을 얻고 싶을 때 **getter** 라고 불리는 `get()` 함수를 호출해야합니다. 

```kotlin
class Client {
    val name = "Unknown"
        get() {
            return field
        }
}

// or with omitted curly brackets and the body of the get() function

class Client {
    val name = "Unknown"
        get() = field
}
```

해당 함수는 그저 값이 무엇인지 물어보았기 때문에 아무것도 하지 않고 값만 반환합니다. 값을 얻으려할 때 `get()` 함수의 결과를 얻을 것 입니다. 그래서 `field` 가 무엇일까요? Kotiln의 각 속성은 `field` 키워드로 속성의 값에 접근할 수 있는 **backing field** 를 갖습니다.

이 경우, getter 는 `name` 변수의 값을 반환합니다. 이는 값이 예상되는 동작이므로 Kotlin은 이 함수를 생성하며 이것을 작성할 필요가 없습니다. 만약 getter 의 로직을 변경하려면 자신만의 `get()` 함수를 작성해야합니다.



## Custom getter

`name` 에 접근할 때마다 고객의 이름을 출력하기:

```kotlin
class Client {
    val name = "Unknown"
        get() {
            println("Somebody wants to know $field name")
            return field
        }
}

val client = Client()

val name = client.name // prints Somebody wants to know Unknown name
println(name)          // prints Unknown
```

custom getter 의 또다른 용도는 다른 무언가를 반환할 때 사용합니다. 예를 들어 전체 고객 정보를 변수에 저장하는 작업이 될 수 있습니다. 한 사람에 대한 정보를 변경하는 경우 이 변수도 변경해야 합니다. 만약 custom getter 를 사용하는 경우 요구가 있을 때 변경하는 정보를 생성할 수 있습니다. 아래 예제에서 `Client` 클래스는 고객의 나이를 저장하는 `age` 속성과 정보를 반환하는 `info` 속성을 얻을 수 있습니다:

```kotlin
class Client {
    var name: String = "Unknown"
    var age: Int = 18
    val info: String
        get() {
            return "name = $name, age = $age"
        }
}

val client = Client()
println(client.info) // name = Unknown, age = 18
client.name = "Lester"
client.age = 20
println(client.info) // name = Lester, age = 20
```



## Property setter

이제 속성 값을 가져오는 프로세스를 변경할 수 있게 되었습니다. 속성 값을 변경하는 과정도 알아보도록 하겠습니다:

```kotlin
class Client {
    var name = "Unknown" // default value
}

val client = Client()
client.name = "Ann"      // name property now stores "Ann"
```



속성의 값을 설정할 때는 **setter** 라 불리는 `set()` 함수를 호출해야 합니다. 

```kotlin
class Client {
    var name = "Unknown"
        set(value) {
            field = value
        }
}
```

해당 함수는 하나의 인자를 가지고 아무것도 반환하지 않습니다. ( 컨벤션에 의해 `value` 라는 이름을 지었습니다, 다른 이름을 사용할 수 있습니다. ) 알다시피 `field` 속성의 현재 값이 포함되어 있으며 다른 값으로 재할당해 변경할 수 있습니다.

이 경우 setter 는 `name` 변수의 값을 전달받는 값으로 변경합니다. 이는 예상되는 결과이므로 Kotlin이 처리해주며 작성할 필요가 없습니다.



## Custom setter

`set()` 함수는 강력한 도구이며 setter 의 로직을 사용자 정의할 수 있습니다: 

```kotlin
class Client {
    var name = "Unknown"
        set(value) {
            println("The name is changing. Old value is $field. New value is $value.")
            field = value
        }
}

val client = Client()
client.name = "Ann"   // The name is changing. Old value is Unknown. New value is Ann.
```

setter 는 초기화할 때가 아닌 속성을 변경하려 할 때만 호출됩니다.

custom setter 를 사용하는 또다른 방법은 다른 값을 할당하려는 경우입니다. 고객의 나이를 저장하는 `age` 속성을 추가하겠습니다. 물론 age 는 음수가 될 수 없습니다. 이를 고려하여 custom setter 를 추가할 수 있습니다:

```kotlin
class Client {
    var name = "Unknown"
    var age = 18
        set(value) {                      
            field = if (value < 0) {
                println("Age cannot be negative. Set to $defaultAge")
                defaultAge
            } else
                value
        }
    val defaultAge = 18
}

val client = Client()
client.age = -1      // Age cannot be negative. Set to 18.
println(client.age)  // 18
```



## Additional features

속성에 대해 setter 와 getter 를 모두 구현할 수 있습니다:

```kotlin
class Client {
    var name = "Unknown"
        get() {
            println("Somebody wants to know $field name")
            return field
        }
        set(value) {
            println("The name is changing. Old value is $field. New value is $value.")
            field = value
        }
}
```



생성자의 속성에 getter 또는 setter 를 사용하려는 경우 속성을 "이동" 시키면 됩니다. 이 경우 생성자의 속성이 아닌 다른 변수를 사용해야 한다는 점을 기억하세요:

```kotlin
class Client(name: String, age: Int) {
    var fullName: String = name
        set(value) {
            println("The name is changing. Old value is $field. New value is $value.")
            field = value
        }
    var age: Int = age   // this is a new property, not a property from the constructor
        set(value) {
            println("The age is changing. Old value is $field. New value is $value.")
            field = value
        }
}
```



속성을 초기화할 때 setter 가 호출되지 않는다는 점을 명심하세요. 생성자에게도 해당됩니다:

```kotlin
class Client(name: String) {
    var name: String = name
        set(value) {
            println("The name is changing. Old value is $field. New value is $value.")
            field = value
        }
}

val client = Client("Annie")  // without output
client.name = "Ann"           // The name is changing. Old value is Annie. New value is Ann.
```



`set()` 함수가 변수에 재할당 하기 때문에 `val` 변수에는  setter 를 사용할 수 없습니다. 물론 `val` 속성의 내부 상태를 변경할 수는 있습니다.

```kotlin
class Passport(number: String) {
    var number = number
    set(value) {
        println("Passport number has changed.")
        field = value
    }
}

class Client {
    val passport = Passport("1234567")
}

val client = Client()
println(client.passport.number)       // 1234567
/*
client.passport = Passport("2345678") // This will not work.
*/
client.passport.number = "2345678"    // This will change the passport number
                                      // prints Passport number has changed
println(client.passport.number)       // 2345678
```
