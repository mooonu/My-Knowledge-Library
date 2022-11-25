# Arithmetic operations

### Theory

우리는 종종 일상에서 거스름돈을 계산하거나 방의 너비를 계산하거나 사람의 수를 세는 등 산술 연산을 수행합니다. 컴퓨터는 이런 연산을 도와줍니다.



### Binary operators

Kotiln 은 다섯개의 산술 연산자가 있습니다:

- 덧셈 `+`
- 뺄셈 `-`
- 곱셈 `*`
- 나눗셈 `/`
- 나머지 `%`

이러한 연산자는 이항이므로 두 값을 피연산자로 사용합니다. 피연산자는 연산자가 적용되는 값 또는 변수입니다. 예시로, 식 1 + 3 에서 1과 3은 피연산자이고 `+` 는 연산자입니다.

덧셈, 뺄셈, 곱셈 출력 결과:

```kotlin
println(13 + 25) // prints 38
println(20 + 70) // prints 90

println(70 - 30) // prints 40
println(30 - 70) // prints -40

println(21 * 3)  // prints 63
println(20 * 10) // prints 200
```



`/` 연산자는 두 숫자의 정수 부분을 나눕니다. 소수점은 버려집니다.

```kotlin
println(8 / 3) // 2
println(41 / 5) // 8
```

`%` 연산자는 나눗셈의 나머지를 찾습니다.

```kotlin
println(10 % 3) // prints 1 because 10 divided by 3 leaves a remainder of 1
println(12 % 4) // prints 0 because 12 divided by 4 leaves no remainder
```



### Complex expressions

산술 연산자를 결합하여 복잡한 식을 쓸 수 있습니다:

```kotlin
println(1 + 3 * 4 - 2) // 11
```

계산 순서는 산술 연산을 할 때 규칙과 일치합니다. 곱셈이 덧셈과 나눗셈보다 우선 순위가 높기에 `3 * 4`가 먼저 계산됩니다.

괄호를 사용하여 실행 순서를 지정할 수 있습니다:

```kotlin
println((1 + 3) * (4 - 2)) // prints 8
```



### Unary operators

단항 연산자는 피연산자로 단일 값을 가집니다.

- `+` 를 단일로 사용할 경우 그대로 값을 반환합니다. 이는 선택적 연산자이므로 실제로는 생략하게 됩니다.

```kotlin
println(+5) // prints 5
println(+(-5)) // prints -5
```

- A **unary minus** negates a value or expression:

```kotlin
println(-8)  // prints -8
println(-(100 + 4)) // prints -104
```

둘 다 곱셈과 나눗셈 연산자보다 우선 순위가 높습니다.



### Precedence order

1. 괄호
2. 단항 연산자인 `+` `-`
3. 곱셈, 나누기와 modulus
4. 덧셈과 뺄셈

이 순서를 기억하세요: 정확한 계산을 위해서는 중요합니다.
