# 컬렉션

## 컬렉션 타입

- Kotlin 표준 라이브러리는 기본 컬렉션 타입인 `List`, `Set`, `Map` 을 제공한다
- 컬렉션의 종류
  - 불변 컬렉션 (Immutable) : 읽기 전용
  - 가변 컬렉션 (Mutable) : 삽입, 수정, 삭제와 같은 쓰기 작업이 가능

![계층 다이어그램](https://user-images.githubusercontent.com/86511086/208334832-4ee7884b-4e7a-49f5-950b-c72923aea699.PNG)



## List

- List 는 중복을 허용함
- 순서가 있기에 index로 특정 아이템을 가져올 수 있음

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

- Set 은 중복을 허용하지 않음
  - 중복된 값을 추가해도 무시된다
- 순서를 보장하지 않음 따라서 index로 특정 아이템을 가져올 수 없음

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
    mutableSet.add(5)
}
```



## Map

```kotlin
fun main() {
    // immutable map
    val numberMap = mapOf("one" to 1, "two" to 2)

    // mutable map
    val mutableMap = mutableMapOf<String, Int>().apply {
        put("three", 3)
    }
    mutableMap["one"] = 1
    mutableMap["two"] = 2
}
```



- Kotlin 에서는 컬렉션빌더를 제공하여 조금 더 쉽게 컬렉션을 생성할 수 있음

```kotlin
fun main() {
    // 컬렉션 빌더
    val numberList: List<Int> = buildList {
        add(1)
        add(2)
        add(3)
    }

    val numberSet = buildSet {
        add(1)
        add(2)
        add(3)
    }
}
```



- 하지만 컬렉션 빌더는 독특한 특징이 있음

컬렉션 빌더 내부에서는 mutable 반환은 immutable 라는 특징을 가지고 있다.
초기의 값을 쉽게 생성하고 immutable 한 변수를 만들고 싶다면 이를 이용하는 방법

```kotlin

fun main() {
    
    // mutableList 의 타입은 MutableList 임
    val mutableList: MutableList<Int> = mutableListOf<Int>().apply {
        add(1)
        add(2)
    }
    mutableList.add(3) // ok

	// 컬렉션 빌더의 타입은 List 즉 immutable 임
    val numberList: List<Int> = buildList {
        add(1)
        add(2)
        add(3)
    }
    numberList.add // compile error
}
```

