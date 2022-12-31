---
description: 표현식과 문
---

# expression and statement

> 키워드
>
> 값, 리터럴, 표현식,

**개념을 이해한다는 것은 바로 그것에 대해 정확히 이해하고 설명할 수 있다는 것.**

### 값

값은 **식**이 평가 되어 생성된 결과를 말한다.

```javascript
// 10 + 20은 평가되어 숫자 값 30을 생성한다.
10 + 20; // 30

// 변수에는 10 + 20이 평가되어 생성된 숫자 값 30이 할당된다.
var sum = 10 + 20;
```

여기서 알 수 있는 것은 변수(이름) sum의 메모리 공간에 10 + 20 이 아닌 평가된 숫자 값 30이 저장된다는 것이다.

이는 10 + 20은 **할당 이전에** 평가되어 값을 생성한다는 말이다.

### 리터럴

* 사람이 이해할 수 있는 문자 또는 약속된 기호를 사용해 값을 생성하는 **표기법**
* 값을 생성하기 위해 미리 약속한 표기법

```javascript
// 숫자 리터럴 3 / 정수 리터럴 3
3

// 부동소수점 리터럴
10.5

// 문자열 리터럴
'hello'

// 불리언 리터럴
true
false

// 객체 리터럴
{ name : 'Looksh', address : 'Si-heung' }

// 함수 리터럴
function() {}
```

자바스크립트 엔진은 코드가 실행되는 시점인 타임에 리터럴을 평가해 값을 생성한다.

### 표현식 expression

표현식은 **값으로 평가될 수 있는** 문(statement)이다.

표현식이 평가되면 새로운 값을 생성하거나 기존 값을 참조한다.

```javascript
/* 
100은 정수 리터럴이다. 리터럴 100은 자바스크립트 엔진에 의해 평가되어 값을 생성하므로
리터럴은 그 자체로 표현식이다.
*/
var score = 100;

/*
50 + 50 리터럴과 연산자로 이루어져 있지만 50 + 50도 
평가되어 숫자 값 100을 생성하므로 표현식이다.
*/
var score = 50 + 50;

// 변수 식별자를 참조하면 변수 값으로 평가되므로 값을 생성하 않지만 값으로 평가되므로 표현식이다.
score; // 100

// 함수/메서드 호출 표현식 (선언이 존재한다 가정)
square();
person.getName();
```

다양한 표현식이 있지만 값으로 평가된다는 점에서 모두 동일하다. 즉 **값으로 표현될 수 있는 문은 모두 표현식**이다.

재미있는 것은 문법적으로 값이 위치할 수 있는 자리에 표현식도 위치할 수 있는 것이다. ( 표현식을 값처럼 사용할 수 있다 )

```javascript
var x = 1 + 2;

// 식별자 표현식 x는 3으로 평가된다.
x + 3; // 6
// 좌항 x는 식별자 표현식이고, x에 3이 평가되어 할당되어 있기에 사용할 수 있다.
```

### 문 statement

statement는 프로그램을 구성하는 기본 단위이자 **최소 실행 단위**이다.

문은 여러 토큰(t)으로 구성된다.

```javascript
var(t) sum(t) =(t) 1(t) +(t) 2(t);(t)
```

문을 명령문이라고도 부른다.

* 선언문
* 할당문
* 조건문
* 반복문

등으로 구분할 수 있다.

```javascript
// 변수 선언 문
var x;

// 할당 문
x = 5;

// 함수 선언 문
function foo() {}

// 조건 문
if (x > 1) { console.log('fuck'); }
```

### 세미콜론 자동 삽입 기능

자바스크립트에는 문의 끝이라고 예측되는 지점에 세미콜론을 자동으로 붙혀주는 기능이 있다.

음 그냥 세미콜론을 잘 붙히자.

### 표현식과 문의 구별

```javascript
var score; // 표현식 x | 변수 선언문(런타임 이전에 실)
score = 100; // 표현식 o | 할당
```

### 표현식인 문과 표현식이 아닌 문

표현식인 문은 값으로 평가될 수 **있는** 문 표현식이 아닌 문은 값으로 평가될 수 **없는** 문

```javascript
// 표현식이 아닌 문은 값처럼 사용할 수 없다.
var foo = var x;

// 변수 선언문은 표현식이 아닌 문
var x;

// 할당문은 그 자체가 표현식이지만 완전한 문이기도 하다. 즉 할당문은 표현식인 문
x = 100;

// 표현식인 문은 값처럼 사용할 수 있다.
var foo = x = 100;
console.log(foo); // 100
```

재미있는 꿀팁 하나 ! 크롬 개발자 도구나 node.js 를 이용하여 코드를 칠 때

```javascript
console.log(10 / 0) // Infinity
undefined

var x;
undefined

x = 3;
3
```

무슨 차이인지 보이나요? 정리하자면

표현식이 아닌 문은 **완료 값으로 undefined**가 뜨고 표현식인 문은 **평가된 값**이 뜬다.