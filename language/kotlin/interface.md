# 추상클래스 | 인터페이스

## 추상클래스

- Kotlin 은 `abstract` 키워드를 사용해 추상클래스를 사용한다
- 이때 하위 클래스에서 구현해야하는 프로퍼티나 함수 또한 abstract 키워드를 사용한다

```kotlin
abstract class Developer() {
    abstract var age: Int

    abstract fun code(language: String)
}

class BackendDeveloper(override var age: Int = 0): Developer() {
    override fun code(language: String) {
        println("I code with ${language}")
    }
}

fun main() {
    val backendDeveloper = BackendDeveloper(23)
    println(backendDeveloper.age)
    backendDeveloper.code("Kotlin")
}
```

> abstract 키워드로 선언된 메서드나 프로퍼티는 반드시 하위클래스에서 구현해줘야한다.



## 인터페이스

### 인터페이스 선언 방법

- `interface` 키워드  사용

```kotlin
interface Cart
```



- 인터페이스 내부에는 추상 함수와 자바 8의 디폴트 메서드 처럼 구현을 가진 함수를 모두 정의할 수 있다.

```kotlin
class Product(
    val name: String,
    val price: Int,
)

interface Cart {
    var coin: Int

    fun add(product: Product) // abstract method

    fun rent() { // default method
        /* ... */
    }
}
```



- 클래스에서 인터페이스를 구현할 때는 `:` 을 붙히고 인터페이스의 이름을 적는다
- 상속과 다른 점은 `()` 생성자 호출이 없다는 것

```kotlin
class MyCart() : Cart {
    override fun add(product: Product) {
        /* ... */
    }
}
```



### 인터페이스에 프로퍼티 선언

- Kotlin 의 인터페이스는 프로퍼티가 존재할 수 있다

```kotlin
interface Cart : Wheel {
    var coin: Int

    val weight: String
        get() = "20KG"

    /* ... */
}

class MyCart(override var coin: Int) : Cart {
    /* ... */
}
```



- MyCart 구현

```kotlin
interface Cart {
    var coin: Int

    val weight: String
        get() = "20KG"

    fun add(product: Product)

    fun rent() {
        if (coin > 0) println("카트를 대여합니다.")
    }
}

class MyCart(override var coin: Int) : Cart {
    override fun add(product: Product) {
        if (coin <= 0) println("코인을 넣어주세요")
        else println("${product.name}이(가) 카트에 추가됐습니다.")
    }
}

fun main() {
    val myCart = MyCart(coin = 100)
    myCart.rent() // 카트를 대여합니다
    myCart.add(Product("아이패드", 960_000)) // 아이패드이(가) 카트에 추가됐습니다.
  
    val myCart2 = MyCart(coin = 100)
    myCart2.rent()
    myCart2.add(Product("아이패드", 960_000)) // 코인을 넣어주세요
}
```



### 인터페이스 상속

- 상위 인터페이스를 가질 수 있다

```kotlin
interface Wheel {
    fun roll()
}

interface Cart : Wheel {
    override fun roll() {
        println("바퀴가 굴러갑니다")
    }
}

fun main() {
    val myCart = MyCart(coin = 100)
    myCart.rent() 
    myCart.add(Product("아이패드", 960_000))
    myCart.roll() // 바퀴가 굴러갑니다  
}
```



### 재정의 충돌 해결

- 클래스는 하나 이상의 인터페이스를 구현할 수 있다.
  Order 엔 add 가 구현이 되어있는 디폴트 함수이고 Cart 는 abstract 함수이다.
- 이때 동일한 시그니처를 가진 함수가 있는 경우 `super<인터페이스>` 를 사용해 호출할 수 있다

```kotlin
interface Cart { // 구현이 필요한 abstract 함수
    fun add(product: Product)
}

interface Order { // 구현이 되어있는 디폴트 함수
    fun add(product: Product) {
        println("${product.name} 주문이 완료되었습니다.")
    }
}

class MyCart(override var coin: Int) : Cart, Order {
    override fun add(product: Product) {
        if (coin <= 0) println("코인을 넣어주세요")
        else println("${product.name}이(가) 카트에 추가됐습니다.")

        // 주문      
        super<Order>.add(product)
    }
}
```



- 서로 다른 두 인터페이스에 같은 시그니처를 가진 디폴트 함수를 사용할 경우 어떻게 될까?

```kotlin
interface Cart : Wheel {
    fun printId() = println("1234")
}

interface Order {
    fun printId() = println("5678")
}

class MyCart(override var coin: Int) : Cart, Order // 컴파일 에러
```

하위 클래스에서 직접 구현하도록 컴파일 오류가 발생한다



- 하위 클래스에서 직접 구현

```kotlin
class MyCart(override var coin: Int) : Cart, Order {
    override fun printId() {
        super<Cart>.printId()
        super<Order>.printId()
    }
}
```



## 헷갈리는 나를 위해 - 추상클래스와 인터페이스의 차이점

- 추상클래스와 인터페이스 공통점
  - 대략적인 설계 명세를 구현
  - 하위클래스에서 구체화

둘이 하는 역할이 비슷해서 헷갈리니까 이제 차이점을 알아보자 !

```kotlin
// Abstract classes
abstract class Student() {
    val univ: String = "BCU"
    abstract var age: Int
    abstract var name: String
}

// interfaces
interface Student {
    // val univ: String = "BCU" // 컴파일 에러
    var age: Int
    var name: String
}
```

`추상클래스` 에서는 정의와 동시에 초기화도 가능하다 하지만 `인터페이스` 에서는 불가능하다

또한 추상클래스와 다르게 인터페이스를 이용한다면 **다중 상속이 가능**하다

> 더 추가 예정
