# Named arguments

## Improving code readability

영화 티켓을 판매하는 판매원이 있다고 상상해보겠습니다, 티켓 가격은 하루 동안 동일하게 유지됩니다. 판매원이 일하는 동안 얼마를 벌었는지 계산하는 함수를 작성하기 위해 세 가지 매개변수를 사용할 수 있습니다:

```kotlin
fun calcEndDayAmount(startAmount: Int, ticketPrice: Int, soldTickets: Int) =
        startAmount + ticketPrice * soldTickets
```

- `startAmount` 는 처음에 가지고 있는 현금의 합입니다.
- `ticketPrice` 는 티켓의 가격입니다.
- `soldTickets` 은 오늘 하루동안 판매한 티켓의 수입니다.

함수 호출:

```kotlin
val amount = calcEndDayAmount(1000, 10, 500)  // 6000
```

이는 잘 동작하지만 각 인자가 어떤 역할을 하는지 알 수 없는 문제점을 가지고 있습니다. 물론 변수를 선언하고 전달할 수 있습니다 하지만 가끔은 변수가 아닌 값으로 작업해야할 때가 있습니다. **Named arguments** 는 코드를 더 읽기 쉽게끔 합니다. 이 문제점을 고치기 위해서는 함수의 각 인자에 이름을 적습니다.

```kotlin
val amount = calcEndDayAmount(
    startAmount = 1000,
    ticketPrice = 10,
    soldTickets = 500
)  // 6000
```

이제 코드가 더욱 이해하기 쉬워졌습니다.



## Reordering arguments

인자의 순서를 변경할 수 있습니다:

```kotlin
val amount = calcEndDayAmount(
    ticketPrice = 10,
    soldTickets = 500,
    startAmount = 1000
)  // 6000
```



## Named and positional arguments

일반적인 매개변수 뒤에 named arguments 를 사용하여 함수를 호출할 수도 있습니다.

```kotlin
calcEndDayAmount(1000, ticketPrice = 10, soldTickets = 500)  // 6000
```

Kotlin 1.4 이후 부터는 named arguments 뒤에 일반적인 매개변수를 사용할 수 있습니다. 하지만 다음과 같은 규칙이 존재합니다:

```kotlin
calcEndDayAmount(ticketPrice = 10, 500, 1000)   // Incorrect invocation!
calcEndDayAmount(startAmount = 1000, 10, 500)   // OK


calcEndDayAmount(soldTickets = 500, ticketPrice = 10, startAmount = 500) // OK
calcEndDayAmount(soldTickets = 500, ticketPrice = 10, 500)  // Incorrect invocation!
```



## Default and named arguments

또한 default arguments 와 함께 사용할 수도 있습니다. 디폴트 매개변수는 Kotlin이 어떤 매개변수를 할당해야 하는지 이해하지 못할 수 있기에 때때로 혼동됩니다.

이전 함수의 첫 번째 매개변수 설정:

```kotlin
fun calcEndDayAmount(startAmount: Int = 0, ticketPrice: Int, soldTickets: Int) =
        startAmount + ticketPrice * soldTickets
```

마지막 매개변수 두 개만 사용하여 호출한다면 동작하지 않습니다: 

```kotlin
val amount = calcEndDayAmount(10, 500)  // Won't work —
                                        // no value for soldTickets
```

다음과 같이 사용한다면 동작합니다:

```kotlin
val amount = calcEndDayAmount(ticketPrice = 10, soldTickets = 500)  // 5000
```



## Named arguments and default values

```kotlin
fun sum2(a: Int, b: Int = a) = a + b
 
sum2(1)    // 1 + 1
sum2(2, 3) // 2 + 3
```

아래 코드는 `b`가 초기화되지 않았기 때문에 동작하지 않습니다:

```kotlin
fun sum2(a: Int = b, b: Int) = a + b
```
