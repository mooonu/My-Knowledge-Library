---
description: 연산자
---

# operator

> 키워드

연산자는 하나 이상의 표현식을 대상으로 여러 연산을 수행해 하나의 값을 만든다.
이때 연산의 대상을 **피연산자**라고 하며 값으로 평가될 수 있는 표현식이어야한다.

### 산술 연산자

산술 연산자는 피연산자를 대상으로 수학적 계산을 수행해 새로운 숫자 값을 만든다.
산술 연산이 **불가능한 경우, NaN을 반환**한다.

```javascript
/* 
이항 산술 연산자
피연산자의 값을 변경하지 않고, 새로운 값을 만든다.
*/
3 + 2; // 5
3 - 1; // 1
3 * 2; // 6
```

단항 산술 연산자는 독특한 특성을 가지고 있다.

```javascript
// 증감 연산자는 피연산자의 값을 변경한다.
var x = 1;

x++; // x = x + 1;
console.log(x); // 2

x--; // x = x - 1;
console.log(x); // 1

// ( - ) 단항 연산자는 음수를 양수로, 양수를 음수로 반전한 값을 반환한다.
-"10"; // -10 (문자열을 숫자로 타입 변환)
-(-10); // 10
-true; // -1
-"hello"; // NaN

// ( + ) 단항 연산자는 숫자 타입이 아닌 피연산자의 타입을 숫자 타입으로 변환하여 반환한다.
var x = "1";

console.log(+x); // 1 number
console.log(x); // '1' string

x = true;
console.log(+x); // 1
console.log(x); // true

x = "hello";
console.log(+x); // NaN
console.log(x); // 'hello'
```

증감 연산자는 위치에 의미가 있다.

- 피연산자 앞에 위치한 전위 증감 연산자는 **먼저 피연산자의 값을 증감시킨 후 다른 연산**을 수행한다
- 피연산자 뒤에 위치한 후의 증감 연산자는 **먼저 다른 연산을 수행한 후, 피연산자의 값을 증가**시킨다.

```javascript
var x = 5,
  result;

// 전위 증가 연산자 (선증가 후할당)
result = ++x;
console.log(result, x); // 6, 6

// 후위 증가 연산자 (선할당 후증가)
result = x++;
console.log(result, x); // 6, 7

// 전위 감소 연산자 (선감소 후할당)
result = --x;
console.log(result, x); // 6, 6

// 후위 감소 연산자 (선할당 후감소)
result = x--;
console.log(result, x); // 6, 5
```

문자열 연결 연산자 또한 독특한데, 타입 강제 변환이 일어난다.

```javascript
// + 경우 문자열로 변환
"1" + 2; // '12' string
1 + "2"; // '12'

// - 경우 숫자 타입으로 변환
1 - "2"; // -1 number
"2" - 1; // 1

// true 1로 변환
1 + true; // 2

// null 0으로 변환
1 + null; // 1

// undefined
1 + undefined; // NaN
+undefined; // NaN
```

### 할당 연산자

할당문은 값으로 평가되는 표현식이다.

```javascript
var x;

x = 10;
x += 5;
x -= 5;
x *= 5;
x /= 5;
x %= 5;

var str = "hello";

str += " world";
console.log(str); // 'hello world'
```

### 비교 연산자

아래는 동등/일치 비교 연산자로 결론만 말하자면
동등 비교 연산자는 예측하기 어려운 결과를 만들어내므로 사용하지 않는 편이 좋다 ( == )

```javascript
var x = 3;
var y = "3";

// 동등 비교
// 동등 비교 연산자는 좌항과 우항을 비교할 때 암묵적 타입 변환을 통해 타입을 일치시킴
x == y; // x와 y의 값이 같음 (true)

// 일치 비교
// 일치 비교 연산자는 암묵적 타입 변환을 하지 않고 값을 비교한다.
x === y; // x와 y의 값과 타입이 같음 (false)

// 부동등 비교
x != y; // x와 y의 값이 다름 (false);

// 불일치 비교
x !== y; // x와 y의 값과 타입이 다름 (true);
```

주의할 점 !

```javascript
// NaN은 자신과 일치하지 않는 유일한 값이다.
NaN === NaN; // false

// 양과 음의 비교
0 === -0; // true
0 == -0; // true
```

#### Object.is 메서드

위처럼 독특한 경우가 많으므로 ES6에서 도입된 Object.is 를 사용하면 정확한 비교 결과를 반환한다.

```javascript
Object.is(NaN, NaN); // true

Object.is(0, -0); // false
```
