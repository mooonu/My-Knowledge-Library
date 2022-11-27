# 변수와 자료형

> 패키지명은 항상 소문자로 시작
> 클래명은 항상 대문자로 시작



## 변수

프로그램은 메모리 공간에 데이터를 보관하고, 여러 메모리 공간을 **변수**로 구분한다.
쉽게 말해 값을 사용하기 위해 선언하는 것을 말한다.

java의 변수는 javascript 와 다르게 **특정 타입의 데이터**만 저장할 수 있다.

예를들어 정수 변수는, 정수값만 저장할 수 있고
실수 변수는 실수값만 저장할 수 있다.



### 변수 선언

```java
public class VariableEx {
    public static void main(String[] args) {

        int num; // 변수 선언
        num = 10; // 값 초기화
        System.out.println(num); // 10

        float level = 20; // 선언과 동시에 값 초기화
        System.out.println(level); // 20
}
```



### 변수명 관례

변수명은 camelCase 를 사용하고, 의미를 제대로 알 수 있어야한다.

```java
int ns; // bad
int numberOfStudent; // good
```



## 데이터 타입

변수가 사용할 공간의 크기와 특성에 따라 데이터 타입을 사용하여 변수를 선언

### 정수

- byte - 1바이트
- short - 2바이트
- int - 4바이트
- long - 8바이트
  * 숫자의 뒤에 L을 써서 long 형임을 표시한다



### 문자

- char - 2바이트

  

어 왜 String은 없을까? 라고 생각할 수 있는데, String은 클래스이다 

여기에 나와있는 데이터 타입들은 **원시 자료형**이다. (즉, 기본 데이터 타입)



### 실수

실수는 기본적으로 long 으로 처리한다.

- float - 4바이트
  - 숫자의 뒤에 F, f를 명시해준다.
- double - 8바이트



### 논리

- boolean
  - true
  - false



## 자료형 없이 변수 사용하기

자바 10 부터는 초깃값을 통하여 데이터 타입을 추론할 수 있는 예약어를 지원함.

```java
var number = 100; // int 타입으로 추론함
var korean = "한국"; // String 타입으로 추론
var oops; // 오류
```





