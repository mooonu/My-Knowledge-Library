# Increment and decrement

### Theory

이 주제에서는 산술 연산자를 깔끔하고 짧게 쓰는 방법을 배우겠습니다.



### Assignment operations

할당연산자

이미 당신은 Kotlin 에서 산술 연산자인 덧셈과 뺄셈을 알고 있습니다:

```kotlin
var a = 3
a = a + 1 // 4
a = a - 1 // 3
```



이 외에도 산술 연산자와 할당 연산자를 결합한 **복합 할당 연산자**가 있습니다. 할당 연산자 `=` 는 변수가 두 번 반복되지 않도록 하는 여러 형식이 있습니다.

- `+=` 덧셈 후 할당: **A += B** equals **A = A + B**
- `-=` 뺄셈 후 할당: **A -= B** equals **A = A - B**
- `*=` 곱셈 후 할당: **A \*= B** equals **A = A \* B**
- `/=` 나눗셈 후 할당: **A /= B** equals **A = A / B**
- `%=` 나눗셈 후 나머지 할당: **A %= B** equals **A = A % B**

변수 하나에서 작동하는 할당 연산자를 살펴봅시다:

```kotlin
var a = 3
a += 2 // 5
a -= 2 // 3
a *= 2 // 6
a /= 2 // 3
a %= 2 // 1
```

숫자 2와 변수 a 를 계산하고 값을 할당 했습니다. 보다시피 해당 연산은 코드를 짧고 간결하게 만들어줍니다.



새로 선언된 변수에는 사용할 수 없고 이미 선언된 변수에만 적용할 수 있습니다:

```kotlin
var a: Int
a += 5 // compile-time error, Variable 'a' must be initialized
```



### Using increment and decrement

또 다른 일반적인 방법으로는 숫자를 하나씩 늘리거나 줄이는 것입니다. 물론 `+=1` 또는 `-=1` 을 사용할 수 있지만 Kotlin 은 훨씬 더 나은 방법을 제공합니다:

```kotlin
var num = 3
num++  // 4, increment
num--  // 3, decrement
```



위와 똑같이 동작합니다:

```kotlin
var num = 3
num += 1  // 4
num -= 1  // 3
```

보시다시피 `++` 는 `+=1` 과 동일하지만 더 단순한 방식으로 증가합니다. `--` 에서도 마찬가지입니다. 

> 오직 하나씩 증가하거나 감소할 수 있습니다.



### Prefix form

전위 증감 연산자는 **변수가 사용되기 이전**에 값을 바꿉니다.

전위 증가 연산자는 증가된 값을 반환합니다:

```kotlin
var a = 10
val b = ++a
println(a)  // a = 11
println(b)  // b = 11
```

첫번째로, 변수 `a`의 값이 하나 증가한 다음 그 값을 변수 `b`에 할당합니다. 그래서 `a` 와 `b` 는 11이 됩니다.



전위 감소 연산자는 감소된 값을 반환합니다:

```kotlin
var a = 10
val b = --a
println(a)  // a = 9
println(b)  // b = 9
```

변수 `a`의 값이 하나 감소한 다음 그 값을 변수 `b`에 할당합니다. 



### Postfix form

반대로, 후위 증감 연산자는 **변수가 사용된 후**에 값을 바꿉니다.

후위 증가 연산자는 하나 증가시키기 전 값을 반환합니다:

```kotlin
var a = 10
val b = a++
println(a)  // a = 11
println(b)  // b = 10
```

첫번째로, 변수`a` 의 값이 `b`에 할당된 후 변수 `a`의 값을 하나 증가시킵니다. 그래서 `a`는 11이고 `b`는 10 입니다.



후위 감소 연산자는 다음과 같이 반환합니다:

```kotlin
var a = 10
val b = a--
println(a)  // a = 9
println(b)  // b = 10
```



### Order of precedence

연산자 우선순위:

1. 괄호 ( (expr) );
2. 후위 증감 ( expr++, expr--);
3. 단일 증감, 전위 증감 ( -expr, ++expr, --expr );
4. 곱셈, 나눗셈, 나머지 ( *, /, % );
5. 덧셈, 뺄셈 ( +, - );
6. 할당 연산자 ( =, +=, -=, *=, /=, %= ).

```kotlin
val a = 2
var b = 3
val c = a + 4 * --b  
println(c)   // this is 10
```

감소 연산자가 곱셈과 덧셈보다 우선순위가 높습니다 따라서 `--b` 가 먼저 계산됩니다.
산술 연산과 마찬가지로 괄호를 사용하여 우선순위를 높일 수 있습니다:

```kotlin
var a = 5
val b = 9
val c = 3
val d = a++ + (b / 2) - c - 4
println(d)   // this is 2
```