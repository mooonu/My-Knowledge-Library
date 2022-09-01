# 데이터 타입

> 키워드
>
> 원시 타입 (숫자, 문자열, 불리언, undefined, null, symbol)
>
> 객체 타입 (객체, 함수, 배열 등)

### 숫자 타입 

javascript 는 int, double, float 등 정수와 실수를 구분하는 것과 다르게 하나의 숫자 타입만 존재한다.

ECMAScript 사양에 따르면 배정밀도 64비트 부동소수점 형식을 따른다. 즉,
**모든 수를 실수로 처리**하며 정수만 표현하기 위한 데이터 타입이 존재하지 않는다.

```javascript
// 모두 숫자 타입이다.
var integer = 10; // 정수
var double = 10.12; // 실수
var negative = -20; // 음의 정수
```

정수로 표시된다 해도 사실은 **실수**라는 것을 의미한다.

재밌는 점으로 숫자 타입은 추가적으로 세 가지 특별한 값도 표현할 수 있다.

```javascript
console.log(10 / 0); // Infinity
console.log(10 / -0); // -Infinity
console.log(10 / 'hi') // NaN
```

 javascript는 대소문자를 구별하므로 NaN 을 NAN, Nan 같이 표현하면 이를 식별자로 해석하여 에러가 발생하니 주의하자.

### 문자열 타입

문자열은 (' '), (" "), (``) 으로 텍스트를  감싼다. 가장 일반적인 표기법은 (' ') 을 사용하는 것이다.

```javascript
var string;
string = 'hi';
string = "hi";
string = `hi`; // ES6부터 
```

### 문자열 타입 (번외) - 템플릿 리터럴

ES6부터 템플릿 리터럴이라고 하는 새로운 문자열 표기법이 도입되었다.

템플릿 리터럴은 백틱 (``) 을 사용해 표현한다.

```javascript
var str = `hi`;
console.log(str); // hi

/* 
템플릿 리터럴 내에서는 이스케이프 시퀀스(\n)를 사용하지 않고도 줄바꿈 허용하며
모든 공백도 있는 그대로 적용된다.
*/
var template = `<ul>
	<li><a href="#">Home</a></li>
</ul>`
console.log(template);
/*
<ul>
	<li><a href="#">Home</a></li>
</ul>
*/

```

아주 아주 마음에 들고 흥미로운 것은 **표현식을 삽입할 수 있다**는 것이다. !!

```javascript
var first = 'SeungHyun';
var last = 'kim';

// ES6 표현식 삽입
console.log(`My name is ${first} ${last}.`);
// My name is SeungHyun Kim.
```

### 불리언 타입

- true
- false

### undefined 타입 과 null 타입

복습 겸 다시 적어보면 var 키워드로 선언한 변수는 할당되지 않으면 자바스크립트 엔진에 의해 암묵적으로 undefined로 초기화된다.

그렇다면 궁금할 수 있다. 만약 개발자가 변수에 값이 없다는 것을 명시하고 싶을 때 undefined를 사용해야 하는지.

그런 경우에는 undefined를 할당하는 것이 아니라 **null을 할당**한다.

null은 변수에 값이 없다는 것을 의도적으로 명시할 때 사용한다.

### 심벌 Symbol 타입

심벌은 ES6에서 추가된 7번째 타입으로, 변경 불가능한 원시 타입의 값이다.

- 이름이 충돌한 위험이 없는 객체의 유일한 프로퍼티 키를 만들기 위해 사용한다.
- 심벌은 리터럴을 통해 생성하는 것이 아닌 Symbol 함수를 호출해 생성한다.
- 이때 생성된 심벌 값은 외부에 노출되지 않으며, 절대 중복되지 않는 값이다.

```javascript
// 심벌 값 생성
var key = Symbol('key');
console.log(typeof key); // symbol

// 객체 생성
var obj = {};

// 이름이 충돌할 위험이 없는 값인 심벌을 프로퍼티 키로 사용한다.
obj[key] = 'value';
console.log(obj[key]) // value
```



------------------------------------------------------------------------------



아.. 여기 데이터 타입의 필요성 부터는 너무 어렵네 2회차의 나에게 맡긴다 !!



자바스크립트의 변수는 선언이 아닌 **할당에 의해 타입이 결정된다.**
그리고 **재할당에 의해 변수의 타입은 언제든지 동적으로 변할 수 있다.**

이러한 특징을 동적 타이핑(dynamic typing)이라 하며 자바스크립트를 동적 타입 언어라 한다.
