# Day 02 — Hello World & 코드 구조

> 파트: **1. 기본**  |  예상 소요: 30~60분

## 📖 오늘 읽을 챕터
- https://ko.javascript.info/hello-world
- https://ko.javascript.info/structure
- https://ko.javascript.info/strictmode

## 🎯 학습 목표
- [x] script 태그로 코드를 실행한다
- [x] 문(statement)과 세미콜론, 주석을 안다
- [x] 'use strict'의 의미를 이해한다

---

## 📝 핵심 개념 정리

### 1. `<script>` 태그 — HTML에 JS 넣기

브라우저에서 JS를 실행하려면 HTML 안에 `<script>` 태그로 코드를 넣음.

```html
<!DOCTYPE html>
<html>
<body>
  <p>스크립트 실행 전</p>

  <script>
    alert("Hello, world!");
  </script>

  <p>스크립트 실행 후</p>
</body>
</html>
```

- `<script>` 태그는 **`<body>` 어디에나, 몇 개든** 넣을 수 있음.
- 브라우저는 HTML을 위→아래로 읽다가 `<script>`를 만나면 **그 자리에서 즉시 코드를 실행**하고, 끝나면 다시 HTML 읽기를 이어감.

> 💡 옛날엔 `<script type="text/javascript">`, `<script language="...">` 같은 속성을 붙였지만 **지금은 필요 없음**. 그냥 `<script>` 만 쓰면 됨. (오래된 코드에서 보이면 "옛날 방식이구나" 하고 넘기기)

---

### 2. 외부 스크립트 — `src` 속성

코드가 길어지면 **별도의 `.js` 파일**로 빼서 `src`로 연결하는 게 정석.

```html
<script src="/path/to/script.js"></script>
<script src="https://cdnjs.example.com/lib.js"></script>  <!-- 절대 URL도 가능 -->
```

- **왜 파일로 분리?**
  1. HTML이 깔끔해짐 (역할 분리)
  2. 브라우저가 파일을 **다운로드 후 캐시(cache)** 에 저장 → 같은 파일을 여러 페이지가 써도 **한 번만 내려받음** → 빨라지고 트래픽 절약.

- ⚠️ **주의: `src`가 있으면 태그 안의 코드는 무시됨.** 둘을 같이 못 씀.
  ```html
  <!-- ❌ src가 있으면 안쪽 alert는 실행 안 됨 -->
  <script src="file.js">
    alert(1);   // 무시됨!
  </script>

  <!-- ✅ 따로 써야 둘 다 동작 -->
  <script src="file.js"></script>
  <script>
    alert(1);
  </script>
  ```

---

### 3. 문(Statement)과 세미콜론 `;`

- **문(statement)** = 특정 동작을 수행하는 "명령 한 덩어리". 문들은 세미콜론 `;` 으로 구분함.
  ```javascript
  alert("Hello");   alert("World");   // 세미콜론으로 두 문을 구분
  ```
- 대부분의 경우 **줄바꿈(개행)이 있으면 세미콜론을 생략**해도 됨. 브라우저가 알아서 넣어줌 → 이걸 **자동 세미콜론 삽입(ASI, Automatic Semicolon Insertion)** 이라 함.

- 🚨 **하지만 ASI는 항상 완벽하지 않음.** 자동으로 못 넣어서 버그가 나는 경우가 있음:
  ```javascript
  alert("Hello")
  [1, 2].forEach(alert)
  ```
  줄바꿈이 있어도 브라우저는 위를 **한 문장**으로 해석함:
  `alert("Hello")[1, 2].forEach(alert)` → **에러!**
  → **세미콜론을 붙였으면** 이런 실수가 없었음.

> ✅ **결론: 세미콜론은 웬만하면 붙이는 습관을 들이자.** 숙련자도 붙이는 걸 권장. (생략해도 되는 경우가 많지만, 안전하게)

---

### 4. 주석(Comment)

실행에 영향을 주지 않고, 코드 설명을 남기는 글.

```javascript
// 한 줄 주석 — 이 줄 끝까지 무시됨

/* 여러 줄 주석
   여러 줄에 걸쳐
   설명을 쓸 수 있음 */

alert("동작함"); // 코드 뒤에 붙여도 됨
```

- ⚠️ **주석은 중첩 불가.** `/* ... /* ... */ ... */` 처럼 안에 또 넣으면 에러.
- 주석은 최종 배포 시 **압축 도구가 자동으로 제거**하므로 성능 걱정 없이 자유롭게 달아도 됨.

> 💡 좋은 코드엔 주석이 적당히 있어야 함. "왜 이렇게 짰는지"를 남기는 게 핵심.

---

### 5. `'use strict'` — 엄격 모드 ⭐

2009년 ES5에서 새 기능들이 추가될 때, **기존 옛날 코드가 깨지지 않도록** 새 규칙을 기본값으로 켜지 않았음. 대신 **원할 때만 켜는 스위치**를 만든 것이 `'use strict'`.

```javascript
'use strict';

// 이 아래로는 "모던(엄격) 방식"으로 코드가 동작함
```

- **반드시 스크립트/함수 최상단에 위치**해야 함. 위에 실행되는 코드가 있으면 무시됨.
  ```javascript
  alert("...");   // 이게 먼저 오면
  'use strict';   // ❌ 엄격 모드 적용 안 됨!
  ```
  주석은 위에 있어도 괜찮음.

- **한 번 켜면 취소 불가.** `'no use strict'` 같은 건 없음.

- 엄격 모드는 이런 걸 함:
  - 실수를 **에러로** 잡아줌 (예: 선언 안 한 변수에 값 할당 금지)
  - 옛날의 헷갈리는 동작을 **더 합리적으로** 바꿈

> 🔑 **자동으로 엄격 모드가 켜지는 경우 (`'use strict'` 안 써도 됨):**
> - **`class`** 와 **모듈(module)** 안의 코드는 **항상 엄격 모드**로 동작함.
> - 그래서 요즘 실무 코드는 대부분 자동으로 엄격 모드. → 앞으로 클래스/모듈을 배우면 `'use strict'`를 직접 쓸 일이 줄어듦.

- 🖥️ **개발자 콘솔에서 엄격 모드 실험하려면?** 콘솔은 기본이 비엄격 모드라, 한 줄씩 치면 `'use strict'`가 적용 안 됨. → 이렇게:
  ```javascript
  'use strict'; <Shift+Enter로 줄바꿈>
  // ...테스트할 코드...
  ```
  전체를 한 번에 실행해야 적용됨. (요즘은 `class`/모듈 덕분에 콘솔에서 굳이 안 켜도 됨)

---

## 💻 코드 실습
```javascript
// (practice/01_fundamentals/Day02.html 을 브라우저로 열어 Console에서 확인)

'use strict';

// 1) 문과 세미콜론
alert("Hello");
alert("World");

// 2) 주석
// 이 줄은 무시됨
/* 이 블록도
   전부 무시됨 */
console.log("주석은 실행에 영향 없음");

// 3) 세미콜론 안 붙였을 때의 함정 (ASI 실패 예시)
// alert("Hello")
// [1, 2].forEach(alert)   // ← 세미콜론 없으면 에러! 붙이면 정상

// 4) 엄격 모드가 잡아주는 실수
// 선언(let/const/var) 없이 변수에 값 넣기 → 엄격 모드에선 에러
// x = 5;   // ReferenceError: x is not defined
let x = 5;   // ✅ 올바른 방법
console.log(x);
```

## ✅ 과제 풀이
<!-- hello-world / structure / strictmode 챕터의 확인 과제 -->

- [x] **"알림창 띄우기"** — HTML 파일을 만들고 `<script>` 안에 `alert("나 여기 있어요!");` 를 넣어 브라우저로 열어 팝업 확인.
- [x] **"외부 스크립트로 알림창 띄우기"** — 같은 코드를 `alert.js` 파일로 빼고 `<script src="alert.js"></script>` 로 불러와 동일하게 동작하는지 확인.
  ```html
  <!-- index.html -->
  <script src="alert.js"></script>
  ```
  ```javascript
  // alert.js
  alert("나 여기 있어요!");
  ```
- [x] **세미콜론 없이 실행해보기** — `alert("Hello")` 다음 줄에 `[1,2].forEach(alert)` 를 세미콜론 없이 두면 에러남을 눈으로 확인. 세미콜론을 붙이면 해결.

## 🔁 복습 메모 (다음날 30초 훑기용)
- `<script>` 는 body 어디든·여러 개 OK / 만나는 즉시 실행 → 이제 `type`·`language` 속성 안 씀
- 긴 코드는 **`<script src="...">`** 외부 파일로 (캐시되어 빠름) / **`src` 있으면 태그 안 코드는 무시**
- 문은 `;`로 구분, 줄바꿈이면 자동 삽입(ASI)되지만 **함정 있음 → 세미콜론 붙이는 습관**
- 주석: `//` 한 줄, `/* */` 여러 줄, **중첩 불가**
- **`'use strict';`** = 엄격 모드 ON, **최상단**에만, 취소 불가 / **`class`·모듈은 자동 엄격 모드**

---
⬅️ [이전날](Day01.md) | [로드맵](../README.md) | [다음날](Day03.md) ➡️
