# Day 02 — Hello World & 코드 구조

> 파트: **1. 기본** | 예상 소요: 30~60분

## 📖 오늘 읽을 챕터

- https://ko.javascript.info/hello-world
- https://ko.javascript.info/structure
- https://ko.javascript.info/strictmode

## 🎯 학습 목표

- [x] `<script>` 태그로 코드를 실행한다.
- [x] 문(statement), 세미콜론, 주석을 이해한다.
- [x] `"use strict"`의 의미를 이해한다.

---

## 📝 핵심 개념 정리

### 1. JavaScript 실행하기

웹페이지에서는 HTML의 `<script>` 태그 안에 JavaScript 코드를 넣어 실행한다. 브라우저는 `<script>` 태그를 만나면 코드를 처리하며, 코드는 기본적으로 위에서 아래 순서로 실행된다.

```html
<!doctype html>
<html lang="ko">
  <head>
    <meta charset="UTF-8">
    <title>첫 JavaScript</title>
  </head>
  <body>
    <script>
      alert("Hello, JavaScript!");
    </script>
  </body>
</html>
```

과거에는 JavaScript를 지원하지 않는 브라우저를 위해 `<script>` 태그 안에 별도 표기를 넣기도 했지만, 모던 JavaScript에서는 사용하지 않는다.

### 2. 외부 파일로 분리하기

코드가 길어지면 JavaScript 파일을 별도로 만들고 `src` 속성으로 HTML에 연결한다.

```html
<!-- 상대 경로 -->
<script src="js/script.js"></script>

<!-- URL 전체도 사용할 수 있음 -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.21/lodash.min.js"></script>

<!-- 여러 파일은 작성한 순서대로 실행됨 -->
<script src="js/script1.js"></script>
<script src="js/script2.js"></script>
```

`src`를 사용한 `<script>` 태그 안의 코드는 실행되지 않는다. 외부 파일과 태그 내부 코드 중 하나를 선택해야 한다.

```html
<!-- 잘못된 예시: alert는 무시됨 -->
<script src="file.js">
  alert("실행되지 않습니다");
</script>

<!-- 올바른 예시 -->
<script src="file.js"></script>
<script>
  alert("태그 내부 코드");
</script>
```

- 외부 파일은 브라우저 캐시에 저장될 수 있어 여러 페이지에서 재사용하기 좋다.
- 같은 스크립트를 다시 내려받지 않아 트래픽과 로딩 시간을 줄일 수 있다.
- 현재 Day 02에서는 `practice.html`과 같은 폴더의 `hello.js`를 연결해 실습한다.

나중에는 `<head>`에서 `defer`를 붙이는 방법도 자주 사용한다. HTML 파싱을 막지 않고, HTML을 모두 읽은 뒤 실행한다.

```html
<script src="app.js" defer></script>
```

---

### 3. 문(statement)과 세미콜론

문(statement)은 JavaScript가 실행하는 하나의 명령 단위다. 한 줄에 하나의 문을 작성하면 읽기 쉽다.

```javascript
console.log("Hello");
console.log("World");
```

JavaScript는 줄바꿈 위치에 세미콜론을 자동 삽입하는 경우가 많다(ASI, Automatic Semicolon Insertion). 하지만 모든 줄바꿈이 문장의 끝을 뜻하지는 않는다.

```javascript
// + 뒤는 아직 완성되지 않은 표현식이므로 다음 줄까지 이어진다.
alert(3 +
  1 +
  2);
```

특히 `[`나 `(`로 시작하는 다음 줄은 앞 문과 이어져 의도하지 않은 동작을 만들 수 있다.

```javascript
alert("에러가 발생합니다.")[1, 2].forEach(alert);
// alert의 반환값에 [1, 2]를 적용한 것으로 해석될 수 있다.

// 문을 분명히 나누면 안전하다.
alert("제대로 동작합니다");
[1, 2].forEach(alert);
```

- 세미콜론은 생략할 수 있는 경우가 많지만, 명확하게 쓰는 편이 안전하다.
- `return`, `throw`, `break`, `continue` 뒤에는 값을 다음 줄에 두지 않는다.
- 한 줄에 여러 문을 몰아쓰지 않는다.

### 4. 주석(comment)

주석은 코드에 설명을 남기는 메모이며, JavaScript 엔진은 주석을 무시하므로 실행에 영향을 주지 않는다.

```javascript
// 이 주석은 한 줄 전체를 차지합니다.
alert("Hello");

alert("World"); // 문 뒤에도 작성할 수 있습니다.

/*
  여러 줄 주석 예제
  여러 줄에 걸친 설명을 작성할 때 사용합니다.
*/
```

- 중첩 주석은 지원하지 않는다.
- 배포 전 압축(minification) 과정에서는 주석이 제거되는 경우가 많다.
- 좋은 주석은 코드가 *무엇을 하는지*보다 *왜 그렇게 작성했는지*를 설명한다.

---

### 5. 엄격 모드: `"use strict"`

JavaScript는 기존 코드와의 호환성을 위해 오래된 동작을 오랫동안 유지해 왔다. ES5(2009)부터는 `"use strict";` 지시자를 통해 더 안전한 모던 동작을 선택할 수 있게 됐다.

```javascript
"use strict";

message = "안녕하세요";
// ReferenceError: 선언하지 않은 변수에는 값을 넣을 수 없음
```

엄격 모드에서는 선언하지 않은 변수에 값을 할당하는 실수를 즉시 오류로 잡는다.

#### 작성 위치와 범위

`"use strict";`는 스크립트 또는 함수 본문의 첫 문에 둔다.

```javascript
"use strict"; // 파일 전체에 적용

function greet() {
  "use strict"; // 함수 안에만 적용할 수도 있음
  console.log("안녕하세요");
}
```

일반 코드 아래에 쓰면 지시자로 인식되지 않는다.

```javascript
alert("some code");
"use strict"; // 엄격 모드가 켜지지 않음
```

- 엄격 모드를 취소하는 `"no use strict"` 같은 지시자는 없다.
- `class`와 JavaScript 모듈(`type="module"`)은 기본적으로 엄격 모드다.

#### 브라우저 콘솔에서 사용하기

브라우저 콘솔에는 엄격 모드가 기본 적용되지 않을 수 있다. 여러 줄을 입력할 수 있는 콘솔이라면 아래처럼 첫 줄에 작성한다.

```javascript
"use strict";
// Shift + Enter로 줄을 바꾼 뒤 테스트할 코드를 작성
```

여러 줄 입력이 어려운 환경에서는 즉시 실행 함수로 감쌀 수 있다.

```javascript
(function () {
  "use strict";

  // 테스트할 코드
})();
```

---

## ✅ 과제 풀이

### 과제 1. 외부 스크립트 실행하기

`hello.js`에 아래 코드를 작성하고 `practice.html`에서 `<script src="hello.js"></script>`로 연결했다.

```javascript
alert("자바스크립트!");
```

### 과제 2. 코드 구조 확인하기

```javascript
console.log("준비");
console.log("시작");
console.log("끝");
```

Console에는 `준비` → `시작` → `끝` 순서로 출력된다.

### 완료 체크

- [x] 같은 폴더의 `practice.html`을 브라우저에서 열고 Console 메시지를 확인했다.
- [x] `<script src="hello.js"></script>`로 별도 `.js` 파일을 연결했다.
- [x] `"use strict";`를 맨 위에 넣고, 선언 없이 값을 넣었을 때 오류가 나는 것을 확인했다.

## 🔁 복습 메모

- `<script>` 태그 안에 코드를 쓰거나 `src`로 외부 `.js` 파일을 연결한다.
- 외부 파일과 태그 내부 코드는 같은 `<script>` 태그에서 함께 사용하지 않는다.
- JavaScript 문은 기본적으로 위에서 아래로 실행되며, 세미콜론 자동 삽입을 과신하지 않는다.
- `//`는 한 줄 주석, `/* ... */`는 여러 줄 주석이다.
- `"use strict";`는 오래된 위험한 동작을 오류로 잡아 준다.

---

⬅️ [이전날](../Day01/README.md) | [로드맵](../../README.md) | [다음날](../Day03/README.md) ➡️
