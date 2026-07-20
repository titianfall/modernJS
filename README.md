# 📚 모던 JavaScript 60일 학습 플랜

[ko.javascript.info](https://ko.javascript.info/) (모던 JavaScript 튜토리얼)을 기준으로
**JavaScript 언어편 전체**를 하루 1개 챕터 분량으로 쪼갠 학습 로드맵입니다.

## 📊 진행 현황
> **2 / 60일 완료** (약 3%) — 방금 **Day 02** 완료! 🎉

## 🗂️ 디렉토리 구조
챕터(파트)별로 폴더가 나뉘어 있습니다. 각 폴더 안에 해당 일차의 `.md` 파일이 들어있어요.
```
Javascript/
├── README.md                  ← 지금 이 파일 (로드맵 + 진도표)
│
├── 01_fundamentals/          📝 노트(.md)  Day 01~15
├── 02_code-quality/          📝 노트(.md)  Day 16~17
├── 03_objects/              📝 노트(.md)  Day 18~24
├── 04_data-types/          📝 노트(.md)  Day 25~34
├── 05_advanced-functions/          📝 노트(.md)  Day 35~42
├── 06_prototypes-classes/  📝 노트(.md)  Day 43~48
├── 07_error-handling/         📝 노트(.md)  Day 49
├── 08_async/            📝 노트(.md)  Day 50~55
├── 09_generators-modules/    📝 노트(.md)  Day 56~59
├── 10_finish/              📝 노트(.md)  Day 60
│
└── practice/                 💻 실습(.html) — 노트와 동일한 파트 구조
    ├── _template.html            (새 실습 복사용 빈 템플릿)
    ├── 01_fundamentals/  Day01~15.html
    └── ...                     (각 파트별 DayNN.html)
```
> **노트(.md)** = 읽고 정리하는 곳,  **실습(.html)** = 코드 직접 짜는 곳. 서로 분리돼 있어 깔끔합니다.
> 실습 방법은 [practice/README.md](practice/README.md) 참고.

## 📖 사용법
1. 오늘 차례의 `DayNN.md` 파일을 엽니다. (폴더는 진도표 링크를 클릭하면 바로 이동)
2. 상단 링크의 챕터를 읽고 → **학습 목표 체크박스**를 채웁니다.
3. **코드 실습** 칸에 직접 타이핑하며 실험합니다. (눈으로만 읽지 말기!)
4. 챕터 하단 **과제**를 풀고 기록합니다.
5. 아래 진도표의 상태(☐)를 **✅** 로 바꿔 진도를 추적합니다.
6. 파일 맨 아래 **이전날/다음날** 링크로 이어서 학습하세요.

> 💡 하루 한 칸씩, 무리하지 말고 꾸준히! 어려운 날(Day 37 클로저, Day 43 프로토타입, Day 55 async/await)은 이틀에 나눠 해도 좋습니다.

---

## 🗓️ 진도표

<details open>
<summary><b>📁 Part 1 · JavaScript 기본 문법</b>  <code>01_fundamentals/</code> — <sub>🔵 진행 중</sub></summary>

| 일차 | 주제 | 완료 |
|:----:|------|:----:|
| Day 01 | [JavaScript 소개](01_fundamentals/Day01.md) | ✅ |
| Day 02 | [Hello World & 코드 구조](01_fundamentals/Day02.md) | ✅ |
| Day 03 | [변수와 상수](01_fundamentals/Day03.md) | ☐ |
| Day 04 | [자료형](01_fundamentals/Day04.md) | ☐ |
| Day 05 | [상호작용 & 형 변환](01_fundamentals/Day05.md) | ☐ |
| Day 06 | [기본 연산자](01_fundamentals/Day06.md) | ☐ |
| Day 07 | [비교 연산자](01_fundamentals/Day07.md) | ☐ |
| Day 08 | [조건문 if와 '?'](01_fundamentals/Day08.md) | ☐ |
| Day 09 | [논리 연산자](01_fundamentals/Day09.md) | ☐ |
| Day 10 | [nullish 병합 연산자 ??](01_fundamentals/Day10.md) | ☐ |
| Day 11 | [반복문 while과 for](01_fundamentals/Day11.md) | ☐ |
| Day 12 | [switch 문](01_fundamentals/Day12.md) | ☐ |
| Day 13 | [함수](01_fundamentals/Day13.md) | ☐ |
| Day 14 | [함수 표현식 & 화살표 함수](01_fundamentals/Day14.md) | ☐ |
| Day 15 | [기본 문법 총복습](01_fundamentals/Day15.md) | ☐ |

</details>

<details>
<summary><b>📁 Part 2 · 코드 품질</b>  <code>02_code-quality/</code> — <sub>접힘</sub></summary>

| 일차 | 주제 | 완료 |
|:----:|------|:----:|
| Day 16 | [디버깅 & 코딩 스타일](02_code-quality/Day16.md) | ☐ |
| Day 17 | [테스트 & 트랜스파일](02_code-quality/Day17.md) | ☐ |

</details>

<details>
<summary><b>📁 Part 3 · 객체</b>  <code>03_objects/</code> — <sub>접힘</sub></summary>

| 일차 | 주제 | 완료 |
|:----:|------|:----:|
| Day 18 | [객체 기본](03_objects/Day18.md) | ☐ |
| Day 19 | [참조에 의한 객체 복사](03_objects/Day19.md) | ☐ |
| Day 20 | [가비지 컬렉션](03_objects/Day20.md) | ☐ |
| Day 21 | [메서드와 this](03_objects/Day21.md) | ☐ |
| Day 22 | [new 연산자와 생성자 함수](03_objects/Day22.md) | ☐ |
| Day 23 | [옵셔널 체이닝 ?.](03_objects/Day23.md) | ☐ |
| Day 24 | [심볼형 & 원시형 변환](03_objects/Day24.md) | ☐ |

</details>

<details>
<summary><b>📁 Part 4 · 자료구조와 자료형</b>  <code>04_data-types/</code> — <sub>접힘</sub></summary>

| 일차 | 주제 | 완료 |
|:----:|------|:----:|
| Day 25 | [원시값의 메서드 & 숫자형](04_data-types/Day25.md) | ☐ |
| Day 26 | [문자열](04_data-types/Day26.md) | ☐ |
| Day 27 | [배열](04_data-types/Day27.md) | ☐ |
| Day 28 | [배열과 메서드](04_data-types/Day28.md) | ☐ |
| Day 29 | [iterable 객체](04_data-types/Day29.md) | ☐ |
| Day 30 | [맵과 셋 (Map/Set)](04_data-types/Day30.md) | ☐ |
| Day 31 | [위크맵과 위크셋](04_data-types/Day31.md) | ☐ |
| Day 32 | [객체 순회 & 구조 분해](04_data-types/Day32.md) | ☐ |
| Day 33 | [날짜와 시간](04_data-types/Day33.md) | ☐ |
| Day 34 | [JSON](04_data-types/Day34.md) | ☐ |

</details>

<details>
<summary><b>📁 Part 5 · 함수 심화학습</b>  <code>05_advanced-functions/</code> — <sub>접힘</sub></summary>

| 일차 | 주제 | 완료 |
|:----:|------|:----:|
| Day 35 | [재귀와 스택](05_advanced-functions/Day35.md) | ☐ |
| Day 36 | [rest 파라미터와 spread](05_advanced-functions/Day36.md) | ☐ |
| Day 37 | [변수의 유효범위와 클로저](05_advanced-functions/Day37.md) | ☐ |
| Day 38 | [오래된 var & 전역 객체](05_advanced-functions/Day38.md) | ☐ |
| Day 39 | [함수 객체 & new Function](05_advanced-functions/Day39.md) | ☐ |
| Day 40 | [setTimeout과 setInterval](05_advanced-functions/Day40.md) | ☐ |
| Day 41 | [데코레이터, call/apply](05_advanced-functions/Day41.md) | ☐ |
| Day 42 | [함수 바인딩 & 화살표 다시보기](05_advanced-functions/Day42.md) | ☐ |

</details>

<details>
<summary><b>📁 Part 6~7 · 프로토타입 & 클래스</b>  <code>06_prototypes-classes/</code> — <sub>접힘</sub></summary>

| 일차 | 주제 | 완료 |
|:----:|------|:----:|
| Day 43 | [프로토타입 상속](06_prototypes-classes/Day43.md) | ☐ |
| Day 44 | [네이티브/프로토타입 메서드](06_prototypes-classes/Day44.md) | ☐ |
| Day 45 | [클래스와 기본 문법](06_prototypes-classes/Day45.md) | ☐ |
| Day 46 | [클래스 상속](06_prototypes-classes/Day46.md) | ☐ |
| Day 47 | [정적 멤버 & 캡슐화](06_prototypes-classes/Day47.md) | ☐ |
| Day 48 | [instanceof & 믹스인](06_prototypes-classes/Day48.md) | ☐ |

</details>

<details>
<summary><b>📁 Part 8 · 에러 핸들링</b>  <code>07_error-handling/</code> — <sub>접힘</sub></summary>

| 일차 | 주제 | 완료 |
|:----:|------|:----:|
| Day 49 | [try..catch & 커스텀 에러](07_error-handling/Day49.md) | ☐ |

</details>

<details>
<summary><b>📁 Part 9 · 프라미스 & async/await</b>  <code>08_async/</code> — <sub>접힘</sub></summary>

| 일차 | 주제 | 완료 |
|:----:|------|:----:|
| Day 50 | [콜백](08_async/Day50.md) | ☐ |
| Day 51 | [프라미스](08_async/Day51.md) | ☐ |
| Day 52 | [프라미스 체이닝](08_async/Day52.md) | ☐ |
| Day 53 | [프라미스 에러 핸들링](08_async/Day53.md) | ☐ |
| Day 54 | [프라미스 API](08_async/Day54.md) | ☐ |
| Day 55 | [async/await](08_async/Day55.md) | ☐ |

</details>

<details>
<summary><b>📁 Part 10~11 · 제너레이터 & 모듈</b>  <code>09_generators-modules/</code> — <sub>접힘</sub></summary>

| 일차 | 주제 | 완료 |
|:----:|------|:----:|
| Day 56 | [제너레이터](09_generators-modules/Day56.md) | ☐ |
| Day 57 | [async 이터레이터/제너레이터](09_generators-modules/Day57.md) | ☐ |
| Day 58 | [모듈 소개 & export/import](09_generators-modules/Day58.md) | ☐ |
| Day 59 | [동적 import](09_generators-modules/Day59.md) | ☐ |

</details>

<details>
<summary><b>📁 완주 · 전체 복습 & 미니 프로젝트</b>  <code>10_finish/</code> — <sub>접힘</sub></summary>

| 일차 | 주제 | 완료 |
|:----:|------|:----:|
| Day 60 | [전체 복습 & 미니 프로젝트](10_finish/Day60.md) | ☐ |

</details>


---
즐겁게 공부하세요! 🚀
