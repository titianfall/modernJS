# Day 04 — 자료형

> 파트: **1. 기본**  |  예상 소요: 30~60분

## 📖 오늘 읽을 챕터
- https://ko.javascript.info/types

## 🎯 학습 목표
- [x] 8가지 자료형(number, bigint, string, boolean, null, undefined, object, symbol)을 안다
- [x] 원시형(primitive)과 객체형(object)의 차이를 이해한다
- [x] `typeof` 사용법을 익힌다

## 📝 핵심 개념 정리
<!-- 읽으면서 내 말로 요약해보세요. 아래는 오늘 학습할 내용 정리입니다. -->

JavaScript의 값은 항상 특정 **자료형(type)**에 속한다. 총 8가지가 있으며,
그중 7개는 **원시형(primitive)**, 나머지 하나(`object`)만 **객체형**이다.

JavaScript는 변수에 자료형 제약이 없는 **동적 타입(dynamically typed)** 언어다.
같은 변수에 문자열도, 숫자도 넣을 수 있다.

```javascript
let message = "hello"; // 지금은 문자열
message = 123456;      // 이제는 숫자 — 에러 없음
```

### 1. 숫자형 `number`

정수와 실수(부동소수점)를 모두 담는다. 사칙연산(`+ - * /`)과 나머지(`%`), 거듭제곱(`**`)이 가능하다.

```javascript
let n = 123;
n = 12.345;

console.log(2 ** 10); // 1024 (2의 10제곱)
```

특수한 숫자값 3가지도 숫자형에 속한다.

- `Infinity` / `-Infinity` : 무한대. `1 / 0` 처럼 0으로 나누면 나온다.
- `NaN` : "Not a Number". 잘못된 수학 연산의 결과. (`"글자" / 2`)
- `NaN`은 **전염성**이 있어서 어떤 연산을 해도 `NaN`이 된다. (`NaN + 1 → NaN`)
- 때문에 Javascript 내에서 수학 연산은 안전합니다. `NaN`을 반환하며 종료됩니다.

```javascript
console.log(1 / 0);        // Infinity
console.log("not a num" / 2); // NaN
```

### 2. BigInt형 `bigint`

`number`는 `±(2^53 - 1)`을 넘는 정수를 안전하게 표현하지 못한다.
아주 큰 정수가 필요할 땐 숫자 끝에 `n`을 붙여 `bigint`를 만든다.
길이에 상관 없이 정수를 나타낼 수 있습니다.

```javascript
// 끝에 `n`이 붙으면 BigInt 자료형 입니다.
const big = 1234567890123456789012345678901234567890n;
```

### 3. 문자형 

문자열 `string`   
따옴표로 감싼 텍스트. 따옴표 종류는 3가지이며 기능이 조금씩 다르다.

```javascript
let single = '작은따옴표';
let double = "큰따옴표"; 
let backtick = `백틱`; 
```

**백틱(`` ` ``)**은 특별하다. `${...}` 안에 변수나 표현식을 넣어 문자열에 끼워 넣을 수 있다(템플릿 리터럴).

```javascript
let name = "John";
console.log(`Hello, ${name}!`);   // Hello, John!
console.log(`1 + 2 = ${1 + 2}`);  // 1 + 2 = 3 // 평가가 끝난 후 문자열의 일부가 됩니다. 
```

> 💡 JavaScript에는 글자 하나를 위한 `character` 타입이 따로 없다. 전부 `string`이다.

### 4. 불린형 `boolean`

`true` / `false` 두 값만 가진다. 예/아니오, 참/거짓을 표현하며 비교 결과로도 나온다.

```javascript
let isGreater = 4 > 1; // true
let nameFieldChecked = true;
```

### 5. `null` 값

지금까지 소개한 자료형 중 어느 자료형에도 속하지 않는 값입니다.
오로지 null 값만 포함하는 별도의 자료형입니다. 

"존재하지 않는 값(nothing)", "비어 있음(empty)", "값을 알 수 없음(unknown)"을 의미하는 별도의 값.
"존재하지 않는 객체에 대한 참조(null pointer)"가 아니라, **비어 있음을 나타내는 값 그 자체**다.

```javascript
let age = null; // 나이를 아직 모름
```

### 6. `undefined` 값

null 값처럼 자신만의 자료형을 형성합니다. 

"값이 할당되지 않은 상태"를 의미한다. 

변수를 선언만 하고 값을 안 넣으면 `undefined`가 된다.

```javascript
let x;
console.log(x); // 'undefined' 가 출력됩니다.
```

> 🆚 `null` vs `undefined`
> - `undefined` : 아직 값이 **할당되지 않았다** (시스템이 기본으로 넣어줌)
> - `null` : "비어 있음"을 **개발자가 의도적으로** 넣은 값
> - 변수를 "비어 있음"으로 만들 땐 관례적으로 `null`을 쓴다.

### 7. 객체형 `object`와 심볼형 `symbol`

- `object` : 유일하게 원시형(primitive)이 아닌 타입. 여러 데이터와 복잡한 개체(entity)를 담는다(뒤 챕터에서 자세히).
- `symbol` : 객체의 고유한 식별자(unique identifier)를 만들 때 쓰는 특수 타입.

### 8. `typeof` 연산자

값의 자료형을 문자열로 반환한다. 두 가지 문법이 있다.

```javascript
// 1. 연산자: typeof x 
typeof 5        // "number"
typeof "text"   // "string"
typeof Symbol("id") // "symbol"

// 2. 함수: typeof(x)
typeof(5)       // "number"  ← 괄호 형태도 가능
```

**꼭 기억할 특이 케이스 3가지:**

```javascript
typeof null           // "object"  ⚠️ (언어의 오래된 오류, null은 객체가 아님!)
typeof alert          // "function" ⚠️ (함수는 객체지만 편의상 별도로 표시)
typeof Math           // "object"  (Math는 내장 객체)
```

## 💻 코드 실습
```javascript
// 8가지 자료형을 typeof로 하나씩 확인해보기
console.log(typeof 123);          // "number"
console.log(typeof 123n);         // "bigint"
console.log(typeof "hi");         // "string"
console.log(typeof true);         // "boolean"
console.log(typeof null);         // "object"  (⚠️ 유명한 버그)
console.log(typeof undefined);    // "undefined"
console.log(typeof {});           // "object"
console.log(typeof Symbol());     // "symbol"
console.log(typeof console.log);  // "function"

// NaN의 전염성 확인
console.log(NaN + 5);             // NaN
console.log("hello" * 2);         // NaN

// 템플릿 리터럴
let user = "홍길동";
console.log(`환영합니다, ${user}님!`);
```

## ✅ 과제
<!-- 먼저 스스로 풀어본 뒤, 아래 '정답 보기'를 펼쳐 확인하세요 -->

### 문자열 따옴표
> 중요도: 5
> 아래 스크립트의 출력 결과는?

```javascript
let name = "Ilya";

console.log( `hello ${1}` );      // ?
console.log( `hello ${"name"}` ); // ?
console.log( `hello ${name}` );   // ?
```

<details>
<summary>정답 보기</summary>

```
hello 1
hello name
hello Ilya
```

- `${...}` 안의 값이 평가되어 문자열에 삽입된다.
- `${1}` → 숫자 1이 그대로 → `hello 1`
- `${"name"}` → 문자열 리터럴 `"name"` 자체 → `hello name`
- `${name}` → 변수 `name`의 값 → `hello Ilya`
- 👉 백틱 안에서만 `${...}`가 동작한다. 작은/큰따옴표에서는 그냥 글자로 출력된다.

</details>

## 🔁 복습 메모 (다음날 30초 훑기용)
- 자료형은 총 **8개**: `number`, `bigint`, `string`, `boolean`, `null`, `undefined`, `object`, `symbol`.
- 이 중 `object`만 객체형, 나머지 7개는 **원시형(primitive)**.
- JS는 **동적 타입** — 한 변수에 문자열·숫자 자유롭게 재할당 가능.
- 숫자형 특수값: `Infinity`, `-Infinity`, `NaN`. `NaN`은 전염성 있어 연산 결과가 계속 `NaN`.
- `null` = 개발자가 넣는 "비어 있음", `undefined` = "값이 아직 할당 안 됨".
- `typeof`로 타입 확인. **함정**: `typeof null === "object"` (버그), `typeof 함수 === "function"`.
- 백틱 `` `${...}` ``만 변수 삽입(템플릿 리터럴) 가능.

---
⬅️ [이전날](../Day03/README.md) | [로드맵](../../README.md) | [다음날](../Day05/README.md) ➡️
