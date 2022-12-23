# Relational operators

## List of relational operators

- `==`
- `!=`
- `>` 
- `>=`
- `<`
- `<=`

관계 연산자는 피연산자 타입에  상관없이 불리언 값을 반환합니다.



## Comparing integer numbers

관계 연산자를 사용하면 두 정수를 비교할 수 있습니다:

```kotlin
val one = 1
val two = 2
val three = 3
val four = 4

val oneIsOne = one == one // true

val res1 = two <= three // true
val res2 = two != four  // true
val res3 = two > four   // false
val res4 = one == three // false
```



관계 연산자를 산술 연산자와 함께 사용할 수 있습니다. 여기에서 관계 연산자는 산술 연산자보다 우선 순위가 낮습니다.

Kotlin 은 두 합을 계산합니다 그런다음 `>` 연산자로 비교합니다:

```java
val number = 1000
val result = number + 10 > number + 9 // 1010 > 1009 is true
```

결과는 `true` 입니다.

`Int` 와 `Long` 의 동일성은 확인할 수 없습니다 `>`, `<`, `>=`, `>=` 로는 자유롭게 비교할 수 있지만 `!=` 과 `==` 는 사용할 수 없습니다. 오직 같은 타입만 동일성을 체크할 수 있습니다. 따라서 `Int`를 `Long` 으로 변환해줘야합니다.

```kotlin
val one: Long = 1
val zero: Int = 0

println(one >= zero)          // OK, prints true  
// println(one == zero)          Error
println(one == zero.toLong()) // OK, prints false
```



## Joining relational operations

해당 표현식은 작동하지 않습니다:

```java
a <= b <= c
```

`||` 및 `&&` 와 같은 논리 연산자를 사용하여 두 개의 불리언 식을 만들어야 합니다.

예를 들어, 다음 식의 유효성을 확인해야 한다고 가정해 보겠습니다:

```java
100 < number < 200
```

그러기 위해서는 다음과 같이 작성해야합니다:

```java
number > 100 && number < 200
```

또한, 괄호 안에 표현식을 넣어 나눌 수 있습니다.

```java
(number > 100) && (number < 200)
```

하지만 관계 연산자가 더 높은 우선 순위를 가지기 때문에 괄호는 필수적이지 않습니다.



## 예제

Write a program that reads three integer numbers and prints `true` if the first number lies between the second and third one (inclusive). Otherwise, it is to print `false`.

The sorting order of the two last arguments can be any.

**Sample Input 1:**

```
3
3
3
```

**Sample Output 1:**

```
true
```

**Sample Input 2:**

```
40
30
50
```

**Sample Output 2:**

```
true
```

**Sample Input 3:**

```
40
100
20
```

**Sample Output 3:**

```
true
```



```kotlin
fun main() {
    val a = readLine()!!.toInt()
    val b = readLine()!!.toInt()
    val c = readLine()!!.toInt()
    val result = a <= b && a >= c || a <= c && a >= b
    println(result)
}
```

- readable and clear

```kotlin
fun main() {
    val a = readLine()!!.toInt()
    val b = readLine()!!.toInt()
    val c = readLine()!!.toInt()
    val result = a in c..b || a in b..c
    println(result)
}
```









