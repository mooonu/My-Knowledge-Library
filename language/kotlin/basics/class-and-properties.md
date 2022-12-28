# 클래스와 프로퍼티

## 클래스

* `class` 키워드를 사용하여 클래스를 선언

```kotlin
class Coffee {
  // ...
}
```

* Kotlin 의 클래스는 본문을 생략할 수 있다

```kotlin
class EmptyClass
```

* Kotlin 의 생성자는 기본 생성자와 하나 이상의 보조 생성자가 존재할 수 있다

```kotlin
class Coffee constructor(val name: String)
```

* 기본 생성자는 `constructor` 를 생략할 수 있다

```kotlin
class Coffee(val name: String)
```

* Kotlin 에서는 클래스에 프로퍼티를 선언할 때 `후행 쉼표` `trailing comma` 를 사용할 수 있다

```kotlin
class Coffee(
  val name: String,
  val price: Int, // trailing comma
) {
  // ...
}
```

후행 쉼표를 사용하면 이전의 마지막 줄을 수정하지 않고 프로퍼티를 쉽게 추가할 수 있고 git 에서 diff 로 코드를 비교했을 때 **변경사항을 명확히 알 수 있다**.

* 후행 쉼표를 사용하고 diff

![after](https://user-images.githubusercontent.com/86511086/205248380-4a0f87cb-d561-469f-a38b-4ede7808f25f.png)

* 후행 쉼표를 사용하지 않고 diff

![before](https://user-images.githubusercontent.com/86511086/205248909-916e9707-504a-485d-971c-9eb7837e1b4b.png)

## 프로퍼티

* Kotlin 의 프로퍼티는 `val` , `var` 키워드를 모두 사용할 수 있다

```kotlin
class Coffee(
  var name: String = "", // default arguments
  var price: Int = 0,
)
```

* 프로퍼티를 수정하거나 사용하려면 참조를 사용하면 된다

```kotlin
fun main() {
  val coffee = Coffee()
  coffee.name = "아이스 아메리카노"
  coffee.price = 2000
  
  println("${coffee.name} 가격은 ${coffee.price}")
}
```

## getter, setter

* Kotlin 은 var 로 선언된 프로퍼티는 `getter` 와 `setter` 를 자동으로 생성한다 ( 디컴파일 해보면 존재함 )
* 아래 코드는 필드의 `setter` 를 사용해 값을 할당

```kotlin
coffee.name = "아이스 아메리카노"
```

* 해당 필드를 사용할 때는 `getter` 를 사용

```kotlin
println("${coffee.name} 가격은 ${coffee.price}")
```

* val 로 선언된 프로퍼티는 `getter` 만 존재한다

당연히 값을 변경할 수 없기 때문이다.

```kotlin
class Coffee(
  var name: String = "",
  var price: Int = 0,
) {
  val brand: String
      get() = "스타벅스" // custom getter
}

fun main() {
  val coffee = Coffee()
  coffee.name = "아이스 아메리카노"
  coffee.price = 2000
  
  // brand 포함 출력
  println("${coffee.brand} ${coffee.name} 가격은 ${coffee.price}")
}
```

* val 로 선언된 프로퍼티에 한하여 커스텀 setter 를 만들 수 있다

```kotlin
class Coffee(
  var name: String = "",
  var price: Int = 0,
) {
  val brand: String
      get() {
        return "스타벅스" // 만약 코드가 길어진다면 이렇게도 표현할 수 있음
      }
  
  var quantity: Int = 0
      set(value) { // custom setter
        if (value > 0) { // 수량이 0 이상인 경우에만 값을 할당
          field = value
        }
    }
}

fun main() {
  val coffee = Coffee()
  coffee.name = "아이스 아메리카노"
  coffee.price = 2000
  coffee.quantity = 1 // 수량 추가
  
  // brand 포함 출력
  println("${coffee.brand} ${coffee.name} 가격은 ${coffee.price} 수량은 ${coffee.quantity}")
}
```

Kotlin은 getter, setter 에서 `field` 라는 식별자를 사용해 필드의 참조에 접근하는 데 이를 `Backig Field` 에 접근한다고 한다.

그렇다면 Backing Field 가 필요한 이유가 무엇일까?

Kotlin 에서 프로퍼티에 값을 할당할 때 실제로는 setter를 사용하는데 이때 무한 재귀 즉 `StackOverflow` 가 발생할 수 있다.

```kotlin
var quantity: Int = 0
    set(value) {
      if (value > 0) {
        quantity = value // 재귀 호출
        /*
        프로퍼티 값을 직접 할당하게 되면
        프로퍼티가 다시 내부의 set 을 호출하게 된다 (무한 반복)
        */
      }
  }
```

> field 에 대해서 다시 정리하자 ! 조금 아리송하네용

* Kotlin 의 프로퍼티는 객체지향적이다. 기본적으로 객체지향에서 객체의 **상태**는 **프로퍼티**로 표현하고 **행위**는 **메서드**로 표현하는데 자바는 상태를 메서드로 나타낸다.

```java
// 자바코드 예시
public class Java_Coffee {
  private boolean isIced;
  
  public boolea isIced() {
    retur isIced;
  }
  
  public void setIced(boolean iced) {
    isIced = iced;
  }
}

class Barista {
  public static void mai(String[] args) {
    Java_Coffee coffee = new Java_Coffee();
    coffee.setIced(true);
    
    if (coffee.isIced()) { // 상태를 메서드로 표현
      	System.out.println("아이스 커피");
   	 }
   }
 }
```

* Kotlin 은 프로퍼티를 사용해 상태를 나타낼 수 있기 때문에 자바보다 객체지향적으로 코드를 작성할 수 있다.

```kotlin
class Coffee(
  var name: String = "",
  var price: Int = 0,
  var iced: Boolean = false,
) {
  val brand: String
      get() {
        return "스타벅스" 
      }
  
  var quantity: Int = 0
      set(value) { 
        if (value > 0) { 
          field = value
        }
    }
}

fun main() {
  val coffee = Coffee()
  coffee.name = "아이스 아메리카노"
  coffee.price = 2000
  coffee.quantity = 1
  coffee.iced = true
  
  if (coffee.iced) { // 프로퍼티의 상태
    println("아이스 커피")
  }
}
```
