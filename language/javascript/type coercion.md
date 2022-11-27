---
description: 타입 변환과 단축 평가
---

# type coercion

**타입 변환**이란 기존 원시 값을 사용해 **다른 타입의 새로운 원시 값을 생성**하는 것
기존 변수 값을 재할당하여 변경하는 것이 아니다.

---

### 암묵적 타입 변환 (implicit coercion)

자바스크립트 엔진이 개발자의 의도와는 상관 없이 코드 문맥을 고려해 타입 변환 시킨다.

```javascript
"10" + 2; // '102'

5 * "10"; // 50

!0; // true
```

- 문자열 타입으로 변환

```javascript
1 + "2"; // '12'

// ES6 템플릿 리터럴의 표현식 삽입
`1 + 1 = ${1 + 1}`; // '1 + 1 = 2'

null + ""; // 'null'

true + ""; // 'true'

Infinity + ""; // 'Infinity'
-Infinity + ""; // '-Infinity'
```

- 숫자 타입으로 변환

```javascript
1 - "1"; // 0

+""; // 0
+"0"; // 0
+"1"; // 1

+"string"; // NaN

+null; // 0

+undefined; // NaN

+{}; // NaN

+[]; // 0

+[10, 20]; // NaN
```

빈 문자열, 빈 배열, null, false 는 0으로, true 는 1

**객체와 빈 배열이 아닌 배열, undefined 는 NaN 가 된다는 것에 주의하자**

- 불리언 타입으로 변환

```javascript
if ("") console.log("1"); // undefined
if (true) console.log("2"); // 2
if (0) console.log("3"); // undefined
if ("str") console.log("4"); // 4
if (null) console.log("5"); // undefined
```

#### Truthy | Falsy

자바스크립트 엔진은 불리언 타입이 아닌 값을 Truthy (참으로 평가되는 값) 또는
Falsy (거짓으로 평가되는 값) 으로 구분한다.

false로 평가되는 Falsy 값 기억하쟈 !

```javascript
false;

undefined;

null;

0, -0;

NaN;

""(빈문자열);
```

이 외의 모든 값은 모두 true로 평가되는 Truthy 값이다.

---

### 명시적 타입 변환 (explicit coercion)

개발자의 의도에 따라 명시적으로 타입을 변경한다.

- 문자열 타입으로 변환

```javascript
String(123); // '123'
NaN.toString(); // 'NaN'
```

- 숫자 타입으로 변환

```javascript
Number("123"); // 123
Number(true); // 1

parseInt("1234"); // 1234
parseFloat("10.34"); // 10.34

true * 1; // 1
true * 3; // 3
false * 1; // 0
```

- 불리언 타입으로 변환

```javascript
Boolean("x"); // true
Boolean(""); // false
Boolean("false"); // true

Boolean([]); // true
Boolean({}); // truie

!!0; // false
!!1; // true
!!NaN; // false
!!""; // false
!!"123"; // true
```

---

### 단축 평가

- 논리 연산자를 사용한 단축 평가

```javascript
"cat" && "dog"; // 'dog'
```

왜 이런 결과가 나왔을까?
차근 차근 짚어보자

우선 위 표현식의 경우 첫 번째 피연산자가 truthy 값이므로 두 번째 피연산자를 평가해 보아야한다.

1. 논리곱 연산자(&&)는 좌항에서 우항으로 평가된다.

2. 첫 번째 피연산자는 truthy 값이므로 true

3. 두 번째 피연산자도 truthy 값이므로 true

4. 이때 논리곱 연산자는 **논리 연산의 결과로 두 번째 피연산자를 반환**한다.

```javascript
"cat" || "dog"; // 'cat'
```

위 표현식은 첫 번째 피연산자가 Truthy 값이므로 두 번째 피연산자까지 평가하지 않아도 된다.

이때 논리합 연산자는 **논리 연산의 결과로 첫 번째 피연산자를 반환**한다.

#### 즉 **_단축 평가는 표현식을 평가하는 도중에 평가결과가 확정된 경우 나머지 평가 과정을 생략하는 것을 말한다._**

- 단축 평가를 사용하여 if문 대체

```javascript
var done = true;
var message = "";

// done이 true라면 '완료' 출력
message = done && "완료"; // 완료

// 삼항 조건 연산자로도 가능하다
// 좌항의 평가식이 false라면 우항의
done = false;
message = (done && "완료") || "미완료"; // 미완료
```

- 함수 매개변수에 기본값 설정

ES6의 매개변수의 기본값 설정 방법 (default param)

```javascript
function getStringLength(str = "") {
  return str.length;
}
```

### null 병합 연산자

```javascript
// 단축평가
(falsy) || 'as' // as | falsy 값일 때 두 번째 피연산자가 출력이었는데

// null 병합 연산자는
(null | undefined) ?? 'as' // as | null이나 undefined가 올 때만 실행된다.
```
