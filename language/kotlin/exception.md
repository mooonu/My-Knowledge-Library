# 예외처리

- Kotlin 의 모든 예외 클래스는 최상위 예위 클래스인 `Throwable` 을 상속한다

<img width="853" alt="exception" src="https://user-images.githubusercontent.com/86511086/204520629-e7532a6e-e804-4862-80d0-d20a803904ec.png">

- Error : 시스템에 비정상적인 상황이 발생. 예측이 어렵고 기본적으로 복구가 불가능 함
  - e.g. OutOfMemoryError, StackOverflowError, etc
- Exception : 시스템에서 포착 가능하여 (try-catch) 복구 가능. 예외 처리 강제
  - IOException, FileNotFoundException, etc
  - `@Transactional` 에서 해당 예외가 발생하면 기본적으로 롤백이 동작하지 않음
    - rollbackFor 를  사용해야함
- RuntimeException : 런타임시에 발생하는 예외. 예외 처리를 강제하지 않음
  - e.g. NullPointerException, ArrayIndexOutOfBoundsException, etc
- Kotlin 에서는 자바의 Exception 계층을 Kotlin 패키지로 래핑한다
