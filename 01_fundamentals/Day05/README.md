# Day 05 — 상호작용 & 형 변환

> 파트: **1. 기본**  |  예상 소요: 30~60분

## 📖 오늘 읽을 챕터
- https://ko.javascript.info/alert-prompt-confirm
- https://ko.javascript.info/type-conversions

## 🎯 학습 목표
- [x] `alert`, `prompt`, `confirm`으로 사용자와 상호작용한다
- [x] 각 함수의 반환값과 모달 창의 특징을 이해한다
- [x] 문자형·숫자형·불린형 변환 규칙을 이해한다

## 📝 핵심 개념 정리
<!-- 읽으면서 내 말로 요약해보세요. 아래는 오늘 학습할 내용 정리입니다. -->

브라우저는 사용자와 간단히 상호작용할 수 있도록 `alert`, `prompt`, `confirm`을 제공한다.
세 함수가 만드는 창은 모두 **모달 창(modal window)**이다.

`모달`이란 단어엔 페이지의 나머지 부분과 상호작용이 불가능하다는 의미가 내포되어 있습니다. 

모달 창이 떠 있는 동안에는 스크립트 실행이 멈추고, 사용자는 창을 닫기 전까지
페이지의 다른 부분과 상호작용할 수 없다. 창의 위치와 모양은 브라우저가 정하며 개발자가 바꿀 수 없다.

### 1. `alert` — 메시지 보여주기

```javascript
alert("안녕하세요!"); // 해당 메시지가 보이는 작은 창을 모달 창(modal window) 라고 합니다.
```

사용자가 **확인** 버튼을 누를 때까지 메시지를 보여준다.
값을 반환하지 않고, 사용자에게 내용을 알리는 용도로 사용한다.

### 2. `prompt` — 문자열 입력받기

```javascript
let age = prompt("나이를 입력해주세요.", 20);
alert(`당신의 나이는 ${age}살입니다.`);
```

문법은 `prompt(title, [default])`이다.

- `title`: 사용자에게 보여줄 질문
- `default`: 입력 칸에 미리 넣어둘 초깃값(선택 사항)
- **확인**을 누르면 입력한 값을 **문자열**로 반환한다.
- **취소** 또는 `Esc`를 누르면 `null`을 반환한다.

```javascript
let value = prompt("숫자 100을 입력해도 결과는 문자열입니다.", "");
console.log(typeof value); // 확인을 눌렀다면 "string"
```

> 💡 숫자를 입력받아 계산하려면 `Number(...)`로 명시적으로 변환해야 한다.
> 단, 취소 시 반환되는 `null`까지 숫자 `0`으로 변환될 수 있으므로 먼저 취소 여부를 확인한다.

### 3. `confirm` — 확인 또는 취소 받기

```javascript
result = confirm(question);

let isStudent = confirm("학생인가요?");
alert(isStudent);
```

질문과 함께 **확인**, **취소** 버튼을 보여준다.

- 확인 → `true`
- 취소 또는 `Esc` → `false`

### 4. 형 변환

값이 필요한 자료형으로 바뀌는 과정을 **형 변환(type conversion)**이라고 한다.
연산 과정에서 JavaScript가 자동으로 바꾸는 **암시적 형 변환**도 있고,
개발자가 `String`, `Number`, `Boolean`을 호출하는 **명시적 형 변환**도 있다.

```javascript
// alert(Value) 에서 문자형 외의 다른 형의 값을 전달받으면 문자형으로 자동 변환됩니다.
alert(123); // 숫자 123이 문자열로 자동 변환됨
console.log("6" / "2"); // 문자열이 숫자로 변환되어 3
```

### 5. 문자형으로 변환 — `String(value)`

문자열이 필요한 상황에서 자동으로 변환되거나 `String(value)`로 직접 변환한다.
대부분 값의 모습 그대로 문자열이 되므로 결과를 예상하기 쉽다.

```javascript
let value = true;
value = String(value);

console.log(value);        // (문자열)"true"
console.log(typeof value); // "string"
console.log(String(null)); // (문자열)"null"
```

### 6. 숫자형으로 변환 — `Number(value)`

수학 연산을 할 때 자동으로 변환되며, `Number(value)`로 직접 변환할 수도 있다.
숫자로 해석할 수 없는 문자열의 변환 결과는 `NaN`이다.

숫자형 값을 사용해 무언가를 하려 하는데 그 값을 문자 기반 폼(form)을 통해 입력받는 경우엔, 이런 명시적 형 변환이 필수입니다. 

```javascript
console.log("6" / "2"); // 3, 문자열이 숫자형으로 자동변환된 후 연산이 수행됩니다.

// Number(value) 함수를 사용하면 주어진 값(value)를 숫자형으로 명시해서 변환할 수 있습니다.
let str = "123";
console.log(typeof str); // string

let num = Number(str); // 문자열 "123"이 숫자 123으로 변환됩니다. 

console.log(Number("  123  ")); // 123 (양쪽 공백 제거)
console.log(Number("123z"));    // NaN (숫자 이외의 글자가 들어가 있는 문자열을 변환하려 할 경우)
console.log(Number(true));      // 1
console.log(Number(false));     // 0
```

**주요 숫자 변환 규칙**

| 변환 전 값 | `Number(...)` 결과 |
|---|---:|
| `undefined` | `NaN` |
| `null` | `0` |
| `true` / `false` | `1` / `0` |
| `""`, `"   "` | `0` |
| 숫자로 된 문자열 | 해당 숫자 |
| 숫자가 아닌 문자열 | `NaN` |

> ⚠️ `Number(null)`은 `0`이지만 `Number(undefined)`는 `NaN`이다.

### 7. 불린형으로 변환 — `Boolean(value)`

논리 연산에서 자동으로 일어나며 `Boolean(value)`로 직접 변환할 수 있다.

`false`로 변환되는 값은 다음 다섯 종류다.

```javascript
Boolean(0);         // false
Boolean("");        // false
Boolean(null);      // false
Boolean(undefined); // false
Boolean(NaN);       // false
```

이를 **falsy 값**이라고 하며, 이외의 값은 모두 `true`로 변환된다.

```javascript
Boolean(1);       // true
Boolean("hello"); // true
Boolean("0");     // true (주의) 문자열 "0"은 true 입니다.
Boolean(" ");     // true 공백이 있는 문자열도 비어있지 않은 문자열이기 때문에 true입니다.
```

> ⚠️ 문자열 `"0"`과 공백 문자열 `" "`은 내용이 있는 문자열이므로 `true`다.

## 💻 코드 실습
```javascript
// 사용자와 상호작용하기
let userName = prompt("이름을 입력해 주세요.", "");

if (userName === null) {
  alert("입력을 취소했습니다.");
} else {
  alert(`안녕하세요, ${userName}님!`);
}

let isStudent = confirm("학생인가요?");
console.log(isStudent); // 확인: true, 취소: false

// 문자형 변환
console.log(String(true));      // "true"
console.log(typeof String(10)); // "string"

// 숫자형 변환
console.log(Number("123"));     // 123
console.log(Number("  123  ")); // 123
console.log(Number("123z"));    // NaN
console.log(Number(null));      // 0
console.log(Number(undefined)); // NaN

// 불린형 변환
console.log(Boolean(0));   // false
console.log(Boolean(""));  // false
console.log(Boolean("0")); // true
console.log(Boolean(" ")); // true
```

## ✅ 과제
<!-- 먼저 스스로 풀어본 뒤, 아래 '정답 보기'를 펼쳐 확인하세요 -->

### 간단한 페이지 만들기
> 중요도: 4
>
> 사용자에게 이름을 물어보고, 입력받은 이름을 그대로 출력하는 페이지를 만들어 보세요.

<details>
<summary>정답 보기</summary>

```javascript
let name = prompt("이름을 입력해 주세요.", "");
alert(name);
```

- `prompt`가 입력한 이름을 문자열로 반환한다.
- 반환값을 `name`에 저장한 뒤 `alert(name)`으로 그대로 보여준다.
- 사용자가 취소하면 `prompt`는 `null`을 반환하므로 `alert`에는 `null`이 표시된다.

</details>

## 🔁 복습 메모 (다음날 30초 훑기용)
- `alert`는 메시지를 보여주고, `prompt`는 문자열 또는 `null`, `confirm`은 불린값을 반환한다.
- 세 함수의 창은 모두 **모달 창**이라서 닫힐 때까지 스크립트와 페이지 상호작용이 멈춘다.
- 명시적 형 변환은 `String(value)`, `Number(value)`, `Boolean(value)`를 사용한다.
- `Number(undefined)`는 `NaN`, `Number(null)`은 `0`이다.
- 숫자로 바꿀 문자열의 양쪽 공백은 제거되며, 빈 문자열은 `0`, 변환 실패는 `NaN`이 된다.
- 대표적인 falsy 값은 `0`, `""`, `null`, `undefined`, `NaN`이다.
- 문자열 `"0"`과 `" "`은 비어 있지 않으므로 `Boolean(...)` 결과가 `true`다.

---
⬅️ [이전날](../Day04/README.md) | [로드맵](../../README.md) | [다음날](../Day06/README.md) ➡️
