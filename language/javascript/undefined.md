# 메모

### map, forEach, reduce 에 대하여

`map`은 배열의 각 요소를 변환해서 **새로운 배열**을 만드는 함수

```javascript
const arr = [1, 2, 3];
const newArr = arr.map(x => x * 2);
console.log(newArr); // [2, 4, 6]
```

누적 계산에는 `forEach` 또는 `reduce` 가 적합

* forEach: 배열을 순회하면서 작업만 하고 결과를 따로 저장 (새 배열 안 만들어).
* reduce: 배열을 순회하면서 값을 누적해서 하나의 결과로 만든다.

```javascript
array.reduce((accumulator, currentValue) => { 계산 }, initialValue);

// 덧셈예시
const arr = [1, 2, 3];
const sum = arr.reduce((acc, curr) => acc + curr, 0);
console.log(sum); // 6
// acc = 0 (시작)
// curr = 1 -> 0(acc) + 1(curr) = 1
// curr = 2 -> 1(acc) + 2(curr) = 3
// curr = 3 -> 3(acc) + 3(curr) = 6

```

* accumulator (줄여서 acc): 누적된 값. 계산 결과가 쌓이는 곳.
* currentValue (줄여서 curr): 현재 처리 중인 배열 요소.
* initialValue: 누적 시작값(
  * 초기값 없음: 첫 번째 요소가 `acc`, 두 번째부터 계산 → 맞아!
  * 초기값 있음: 초기값이 `acc`, 첫 번째 요소부터 계산

`(acc, curr) => acc + curr`는 "이전 값(acc)과 현재 값(curr)을 더해"라는 뜻.
