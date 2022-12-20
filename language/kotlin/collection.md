# 컬렉션

## 컬렉션 타입

- Kotlin 표준 라이브러리는 기본 컬렉션 타입인 `List`, `Set`, `Map` 을 제공한다
- 컬렉션의 종류
  - 불변 컬렉션 (Immutable) : 읽기 전용
  - 가변 컬렉션 (Mutable) : 삽입, 수정, 삭제와 같은 쓰기 작업이 가능

![계층 다이어그램](https://user-images.githubusercontent.com/86511086/208334832-4ee7884b-4e7a-49f5-950b-c72923aea699.PNG)



## List

```kotlin
fun main() {
    // immutable
    val currencyList = listOf("달러", "유로", "원")

    // mutable
    val mutableCurrencyList = mutableListOf<String>("엔")
    mutableCurrencyList.add("달러")
    mutableCurrencyList.add("유로")
    mutableCurrencyList.add("원")
}
```

- Mutable List 의 가독성 향상 방법 `apply`

```kotlin
fun main() {
    val mutableCurrencyList = mutableListOf<String>().apply {
        add("달러")
        add("유로")
        add("원")
    }
}
```



## Set

```kotlin
fun main() {
    // immutable set
    val numberSet = setOf(1, 2, 3, 4)

    // mutable set
    val mutableSet = mutableSetOf<Int>().apply {
        add(1)
        add(2)
        add(3)
        add(4)
    }
}
```



## Map

