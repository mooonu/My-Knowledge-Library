# Member functions

## Writing member functions

데이터뿐만 아니라 동작도 객체에 저장해야합니다. **멤버 함수**는 동일한 클래스에 속한 전체 객체에 대해 공통적인 동작을 구현합니다. 

멤버함수는 클래스의 내부에 함수처럼 존재합니다. 아래 예시에서 클래스에 `print()` 함수 하나를 선언했습니다:

```kotlin
class MyClass {
    fun print() = println("Hello from print")
}
```

해당 함수는 특정 클래스의 객체에서 동작하고 필드에 접근할 수 있기 때문에 **멤버** 함수라고 불립니다:

```kotlin
class MyClassWithProperty(var property: Int) {
    fun printProperty() {
        println(this.property)
    }
}
```

`this` 키워드는 클래스의 현재 인스턴스를 가리킵니다. 위 예제의 `this` 는 선택사항이며 생략할 수 있습니다.

함수처럼, 멤버 함수도 인자를 받고 정의된 클래스 타입과 모든 타입의 값을 반환할 수 있습니다.

> 클래스의 안에 있는 함수의 정식명칭은 멤버함수 입니다. 종종 메서드라고 불립니다.



## Calling member functions

객체의 필드 값을 출력하는 예제:

```kotlin
val myObject = MyClassWithProperty(10)
myObject.printProperty()  // prints "10"
```

멤버 함수를 호출할 때 클래스의 객체를 생성해야합니다. 그 다음 객체 이름 옆에 `.` 를 작성하고 괄호안에 필요하다면 인자와 함께 함수 이름을 작성합니다.
