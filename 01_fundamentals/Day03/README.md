# Day 03 — 변수와 상수

> 파트: **1. 기본**  |  예상 소요: 30~60분

## 📖 오늘 읽을 챕터
- https://ko.javascript.info/variables

## 🎯 학습 목표
- [x] `let`, `const`, `var`로 변수를 선언한다
- [x] 변수 네이밍 규칙을 익힌다
- [x] 상수(`const`)와 대문자 상수 관례를 이해한다

## 📝 핵심 개념 정리
<!-- 읽으면서 내 말로 요약해보세요. 아래는 오늘 학습할 내용 미리보기입니다. -->

### 1. 변수란?

변수(variable)는 데이터를 담아 두는 이름 붙은 저장소다. 값을 나중에 다시 꺼내 쓰거나 바꿀 수 있다. `let` 키워드로 선언한다.

```javascript
let message;              // 선언
message = "Hello";        // 값 할당
console.log(message);     // Hello

let user = "John";        // 선언과 할당을 한 줄에
```

여러 변수를 한 문장에 선언할 수도 있지만, 가독성을 위해 한 줄에 하나씩 쓰는 편이 좋다.

```javascript
let user = "John", age = 25, message = "Hello";

let user = "John";
let age = 25;
let message = "Hello";
```

### 2. `var` — 오래된 방식

`var`는 `let`과 비슷하지만 동작 방식에 미묘한 차이가 있다(스코프, 호이스팅 등). 모던 JavaScript에서는 거의 쓰지 않으며 뒷부분 챕터에서 자세히 다룬다. 지금은 "`let`을 쓴다" 정도로만 기억한다.

### 3. 값 복사와 재할당

변수에는 값을 복사해 넣을 수 있고, 값은 얼마든지 바꿀 수 있다.

```javascript
let hello = "Hello world!";
let message2 = hello;     // hello의 값을 복사
console.log(hello, message2); // 둘 다 "Hello world!"
```

### 4. 변수 이름 짓기 규칙

- 문자, 숫자, `$`, `_`만 사용할 수 있다. 단, **첫 글자는 숫자가 될 수 없다**.
- 여러 단어는 카멜 표기법(camelCase)으로 잇는다: `myVeryLongName`.
- 대소문자를 구별한다: `apple`과 `APPLE`은 다른 변수.
- 예약어(`let`, `class`, `return`, `function` 등)는 이름으로 쓸 수 없다.
- 한글·유니코드도 가능하지만 영어 이름이 관례다.
- 사람이 읽고 의미를 알 수 있는 이름을 쓴다(`a`, `x`보다 `userName`, `shoppingCart`).

```javascript
let $ = 1;
let _ = 2;
let userName = "Pete";
let test123 = true;
// let 1a;   // 에러: 숫자로 시작 불가
// let my-name; // 에러: 하이픈 불가
```

### 5. 상수 `const`

값을 재할당하지 않는 변수는 `const`로 선언한다. 재할당을 시도하면 에러가 난다.

```javascript
const myBirthday = "18.04.1982";
// myBirthday = "01.01.2000"; // error, can't reassign the constant!
```

**대문자 상수**: 실행 전부터 값이 정해져 있고 기억하기 어려운 값은 대문자와 밑줄로 이름 짓는 관례가 있다.
즉, '하드 코딩한' 값의 별칭을 만들 때 사용하면 됩니다.

```javascript
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const BIRTHDAY = "18.04.1982";

// 실행 중 계산되어 정해지는 값은 일반 카멜표기법으로
const pageLoadTime = /* 페이지 로딩에 걸린 시간 */ 0;
```

### 6. 바람직한 변수명

변수명은 간결하고 명확해야 합니다. 변수가 담고 있는 것이 무엇인지 잘 설명할 수 있어야 합니다.

모던 자바스크립트 압축기(minifier)와 브라우저는 코드 최적화를 잘해 줍니다. 변수를 추가한다고 해서 성능 이슈가 생기지 않습니다.
값이 다를 경우, 변수를 다르게 선언해 주면 코드 최적화에 도움이 될 수도 있습니다.


## ✅ 과제

1. 변수 가지고 놀기
> 중요도: 2  
> admin과 name이라는 변수를 선언하세요.  
> name에 값으로 "John"을 할당해 보세요.  
> name의 값을 admin에 복사해 보세요.  
> admin의 값을 alert 창에 띄워보세요. "John"이 출력되어야 합니다.  


2. 올바른 이름 선택하기
> 중요도: 3  
> 현재 우리가 살고 있는 행성(planet)의 이름을 값으로 가진 변수를 만들어보세요. 변수 이름은 어떻게 지어야 할까요?  
> 웹사이트를 개발 중이라고 가정하고, 현재 접속 중인 사용자(user)의 이름(name)을 저장하는 변수를 만들어보세요. 변수 이름은 어떻게 지어야 할까요?

3. 대문자 상수 올바르게 사용하기
> 중요도: 4
> 아래 코드를 평가해 보시기 바랍니다.

```javascript
const birthday = '18.04.1982';

const age = someCode(birthday);
```

> 위 코드의 상수 birthday는 태어난 날짜 정보를 담고 있습니다.  age라는 상수는 나이에 관한 값을 담고 있는데 birthday를 조작하여 그 값을 도출합니다  
> (생일을 이용하여 나이를 도출하는 코드는 간결성을 위해 여기선 언급하지 않겠습니다. 이 문제에서 해당 코드가 중요한 역할을 하지 않기도 합니다).  
> 이런 상황에서 birthday를 대문자 상수로 바꾸는 것이 적절할까요? age 역시 대문자 상수로 바꾸는 것이 괜찮은 선택일까요?

```javascript
const BIRTHDAY = '18.04.1982'; // 대문자 상수로 바꿔도 괜찮을까요?

const AGE = someCode(BIRTHDAY); // 대문자 상수로 바꿔도 괜찮을까요?
```

## 🔁 복습 메모 (다음날 30초 훑기용)
- 변수 = 값을 담는 이름 붙은 저장소. 선언은 `let`, 재할당 안 하면 `const`.
- 한 줄에 하나씩 선언하는 게 읽기 좋다. `var`는 옛날 방식이라 지금은 `let` 위주.
- `let a = b`는 값을 **복사**한다. 이후 원본이 바뀌어도 복사본은 그대로.
- 이름 규칙: 문자·숫자·`$`·`_`만, **숫자로 시작 금지**, 예약어 금지, 대소문자 구별, camelCase.
- 좋은 이름 = 무엇을 담는지 설명하는 이름 (`a` ❌ → `userName` ⭕).
- `const`는 재할당 시 에러. 실행 전부터 정해진 하드코딩 값은 `COLOR_RED`처럼 대문자 상수로.
- 실행 중 계산되는 값은 `const`여도 camelCase(`pageLoadTime`)로 쓴다.

---
⬅️ [이전날](../Day02/README.md) | [로드맵](../../README.md) | [다음날](../Day04/README.md) ➡️
