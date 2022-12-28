# 열거형

## enum 클래스의 사용

- 서로 연관된 상수들의 집합을 `enum class` 를 사용해서 정의할 수 있음
- 결제 상태를 나타내는 `PaymentStatus` enum 클래스:

```kotlin
enum class PaymentStatus {
    UNPAID,
    PAID,
    FAILED,
    REFUND,
}
```



- enum 클래스도 클래스이므로 생성자와 프로퍼티 정의 가능

```kotlin
enum class PaymentStatus(val label: String) {
    UNPAID("미지급"),
    PAID("지급완료"),
    FAILED("지급실패"),
    REFUND("환불"),
}
```



- 정의된 프로퍼티를 사용하는 방법:

```kotlin
println(PaymentStatus.PAID.label) // 지급완료
```



- 정의된 상수 목록 뒤에 함수를 정의할 경우  `}` 뒤에 `;` 을 붙여야한다
- 결제 가능 여부를 확인하는 `isPayable` 함수:

```kotlin
enum class PaymentStatus(val label: String) {
    UNPAID("미지급"),
    PAID("지급완료"),
    FAILED("지급실패"),
    REFUND("환불"),
  
    fun isPayable(): Boolean = false
}
```



- 각각의 결제 상태에 따라 상태를 다르게 구현
- abstract 함수를 가질 수 있고 각각의 상수는 익명 클래스형태로 abstract 함수를 구현할 수 있음

```kotlin
enum class PaymentStatus(val label: String) {
    UNPAID("미지급") {
        override fun isPayable(): Boolean = true
    },
    PAID("지급완료") {
        override fun isPayable(): Boolean = false
    },
    FAILED("지급실패") {
        override fun isPayable(): Boolean = false
    },
    REFUND("환불") {
        override fun isPayable(): Boolean = false
    };
  
    abstract fun isPayable(): Boolean
}

fun main() {
    if (PaymentStatus.UNPAID.isPayable()) {
        println("결제 가능 상태") // 결제 가능 상태
    }
}
```



- enum 클래스에서 인터페이스를 상속받고 구현
- enum 에서 독자적으로 abstract를 가지는 것 보다는
  재사용 가능성 그리고 유지보수를 위해 인터페이스로 분리하는 것이 좋음

```kotlin
enum class PaymentStatus(val label: String) : Payable {
    UNPAID("미지급") {
        override fun isPayable(): Boolean = true
    },
    PAID("지급완료") {
        override fun isPayable(): Boolean = false
    },
    FAILED("지급실패") {
        override fun isPayable(): Boolean = false
    },
    REFUND("환불") {
        override fun isPayable(): Boolean = false
    };
}

interface Payable {
    fun isPayable(): Boolean
}
```



- `valueOf` 를 사용해서 enum 클래스 생성하기

```kotlin
val paymentStatus = PaymentStatus.valueOf("PAID")
println(paymentStatus.lable) // 지급완료
```



- enum 클래스의 동등성 비교 `==` 

```kotlin
if (paymentStatus == PaymentStatus.PAID) {
		println("결제 완료 상태") // 결제 완료 상태
}
```



- 상수를 나열하려면 `values(): Array<EnumClass>` 를 사용한다

```kotlin
fun main() {
    for (status in PaymentStatus.values())
        println("[${status.name}] ${status.label} : ${status.ordinal}")
}
/*
[UNPAID] 미지급 : 0
[PAID] 지급완료 : 1
[FAILED] 지급실패 : 2
[REFUND] 환불 : 3
*/
```

