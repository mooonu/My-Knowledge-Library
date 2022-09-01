---
description: 변수
---

# variable

> 키워드
>
> 변수, 식별자, 호이스팅, 할당과 재할당

### 변수

하나의 값을 저장하기 위해 **확보한 메모리 공간** 자체 또는 그 메모리 공간을 **식별**하기 위해 붙인 이름을 말한다. 쉽게 말해 값의 위치를 가리키는 이름.

```javascript
var result = 10 + 20; // assignment​

console.log(result); // reference
```

### 식별자

변수 이름을 식별자 라고도 한다. (identifier)

식별자는 값이 아니라 값이 저장되어있는 메모리 주소를 기억하고 있다.

> result                 0x0669F913     30&#x20;
>
> 변수이름(식별자)     메모리 주소      메모리

식별자로 값을 구별해서 식별한다는 것은 메모리 주소를 통해 값에 접근할 수 있다는 의미

### 변수 선언

```javascript
var score; // undefined​

let result; // undefined​

var age = 23; // 23
```

자바스크립트는 **var 키워드로** 변수 선언 이후 값을 할당하지 않으면 자바스크립트 엔진에 의해 **undefined** 라는 값이 암묵적으로 할당되어 초기화된다

* const 키워드로 변수를 선언하면 SyntaxError 를 보여준다. (상수 선언에 초기화 없음)

```javascript
const score;
/ Uncaught SyntaxError: Missing initializer in const declaration
```

* 선언되지 않은 변수를 사용하면 ReferenceError 를 보여준다. (정의 되지 않은 변수)

```javascript
console.log(hungry);
/ VM311:1 Uncaught ReferenceError: hungry is not defined
```

### 호이스팅

```javascript
console.log(score); // undefined;
var score; // undefined 
```

ReferenceError 가 아닌 undefined 가 출력된다.

이유는

* 변수 선언이 런타임 (순차적으로 한 줄씩 실행되는 시점) 이 아닌 그 이전에 먼저 실행되기 때문이다. ( 모든 선언문은 런타임 이전 단계에서 먼저 실행된다. )
* 변수 선언이 어디에 있든 상관 없이 다른 코드보다 먼저 실행된다.

이를 **변수 호이스팅 (variable hoisting)** 이라고 한다.

* 변수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작한다.
* var, let, const, function, class 키워드를 사용해서 선언하는 모든 식별자는 호이스팅된다.\


### 값의 할당

```javascript
var score = 80; // 변수 선언과 값의 할당
```

값의 할당은 런타임 이전에 먼 실행되던 선언과 다르게 **런타임에 실행**된다.

```javascript
console.log(result); // undefined 
// 런타임 이전에 실행된 result 에는 이미 undefined로 초기화 되어 있으므로

​var result; // 변수 선언
result = 10; // 값의 할당 이는 런타임에 실행된다.​
// 변수의 선언과 값을 동시에 하는 것도 같다.

console.log(result) // 10// 런타임에 값의 할당이 일어나 10으로 재할당


```

만약 이렇다면?

```javascript
console.log(result); // undefined

​result = 10; // 값의 할당
var result; // 변수 선언​

console.log(result); // 10
```

결과는 같다.

호이스팅 되어 undefined 로 초기화 되고 런타임에 값의 할당이 일어나 10으로 재할당 되어 마지막 줄의 값은 10이 된다.

### 값의 재할당

변수에 값을 재할당 할 때는 이전의 값이 저장되어 있던 메모리 공간을 지우고 그 메모리 공간에 새롭게 저장하는 것이 아니라.

**새로운 메모리 공간을 확보**하고 **그곳에 새로운 값을 저장**한다.
