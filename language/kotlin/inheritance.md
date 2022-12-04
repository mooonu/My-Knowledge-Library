# 상속

## 자바의 상속

- 객체지향 핵심 원칙 중 하나인 `상속` 은 기존 코드를 재사용하거나 확장할 수 있다.
- 자바는 기본적으로 모든 클래스가 상속이 가능하나 상속에 대한 부작용이 발생할 경우를 대비해 `final` 키워드로 상속을 막을 수 있다.
- 대표적으로 `System` 클래스

```java
System.out.println("hello world");

public final class System {
  // ...
}
```

이펙티브 자바에서는 `상속을 위한 설계와 문서를 작성하고 그렇지 않으면 상속을 금지하라` 라는 주제가 있는데 여기에는 상속에 대한 여러 문제점에 대해 나와있으며 결과적으로 상속을 목적으로 만든 클래스가 아니라면 `모두 final 로 작성하는 것이 좋다`



## Kotlin 의 상속

- 자바의 모든 클래스 조상은 `Object` Kotlin 에서 모든 클래스의 조상은 `Any` 
- Any 에는 equals, hashCode, toString 이 존재하고 모든 클래스로 자동 상속된다
- Kotlin 의 클래스는 **기본적으로 final 클래스와 같이 상속을 막고** 꼭 필요한 경우 `open` 키워드로 상속을 허용할 수 있다.

```kotlin
open class Dog
```



- 하위 클래스에서 상위 클래스를 확장하려면 (상속 받으려면) 클래스 뒤에 `:` 을 추가하고 상위 클래스를 작성

```kotlin
class BullDog: Dog()
```



- 함수나 프로퍼티를 재정의할때도 마찬가지로 `open` 키워드로 오버라이드에 대해 허용해야한다

```kotlin
open class Dog {
    open var age: Int = 0

    open fun bark() {
        println("멍멍")
    }
}

class BullDog(): Dog() {
    override var age: Int = 2

    override fun bark() {
        println("컹컹")
    }
}
```



- 프로퍼티는 기본 생성자를 사용해 오버라이드 할 수 있다

```kotlin
open class Dog(open var age: Int = 0) {
    open fun bark() {
        println("멍멍")
    }
}

class BullDog(override var age: Int = 0) : Dog() {
    override fun bark() {
        println("컹컹")
    }
}

fun main() {
    val dog = BullDog(age = 3)
    println(dog.age)
    dog.bark()
}
// 3
// 컹컹
```



- `override` 된 함수나 프로퍼티는 기본적으로 open 되어 있으므로 하위 클래스에서 오버라이드를 막기 위해선 final 을 앞에 붙힌다

```kotlin
open class BullDog(override var age: Int = 0) : Dog() {
    final override fun bark() {
        println("컹컹")
    }
}

class ChildBullDog : BullDog() {
    override var age: Int = 0

    override fun bark() { // 컴파일 에러
        println("컹컹")
    }
}
```



- 하위 클래스에서 상위 클래스의 함수나 프로퍼티를 접근할 때는 `super` 키워드를 사용한다

```kotlin
open class Dog(open var age: Int = 0) {
    open fun bark() {
        println("멍멍")
    }
}

open class BullDog(override var age: Int = 0) : Dog() {
    override fun bark() {
        super.bark()
        println("컹커러컹컹")
    }
}

fun main() {
    val dog = BullDog(age = 3)
    dog.bark()
}
// 멍멍
// 컹커러컹컹
```

