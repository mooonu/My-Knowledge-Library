# 상수, 리터럴, 형변환

정상수 아님주의



## 상수

변하지 않는 값 ( javascript 의 const )

보통 변하지 않는 값이면 상수명을 대문자로 하는 것이 관례다.



### 상수 선언

```java
final double PI = 3.14;
final int MAX_NUM = 100;

PI = 3.15; // 컴파일에러 : Cannot assign a value to final variable 'PI'
```

final 로 선언된 상수는 다른 값을 대입 할 수 없다.



## 리터럴

참 이 리터럴이라는 말은 익숙해지지 않는 것 같어,,, 입에 붙지도 않고

literal 을 영단어사전에 검색해보면 

- 문자 그대로의
- 직역의

따라서 이렇게 이해하는 게 더 편하겠다 **"진짜 말 그대로 값 이라니까?"**

변수의 값이 될 수 있는 3.14, 100, true, "hello" 같은 걸 말함



상수풀 나중에 기회되면 좀 더 알아보자.

리터럴이 로딩되면 -> 상수 풀에 저장되고 -> 변수에 넣을 때는 상수풀에서 꺼내 쓴다?



## 형변환

서로 다른 자료형의 값이 대입되는 경우 형 변환이 일어난다.



### 암시적 형변환

작은 수에서 큰 수 (적은 바이트에서 큰 바이트)
덜 정밀한 수에서 더 정밀한 수 ( 정수에서 실수 )

```java
long num = 3; // int 에서 long 으로 자동 형변환, L을 사용하지 않아도 된다.
System.out.println(num); // 3

float fNum = num; // long 에서 float 으로 자동 형변환
System.out.println(fNum); // 3.0
```



## 명시적 형변환

```java
double num = 3.14;
int iNum = (int)num; // 실수형을 정수형으로 표현하겠다 !

System.out.println(iNum); // 3
```

