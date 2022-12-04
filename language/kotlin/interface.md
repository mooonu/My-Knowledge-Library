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
