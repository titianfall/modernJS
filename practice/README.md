# 💻 실습(practice) 폴더

노트(`.md`)와 분리된 **실습 전용 공간**입니다. 파트별 폴더 안에 일차별 `DayNN.html`이 준비돼 있어요.

## 사용법
1. 오늘 차례의 `DayNN.html`을 **브라우저로 엽니다.**
   - VS Code라면 파일 우클릭 → *Open with Live Server* (확장 설치 시), 또는 그냥 더블클릭.
2. **F12 → Console** 탭을 엽니다.
3. `<script>` 안에 코드를 작성하고 저장 → 브라우저 새로고침(F5)으로 결과 확인.

## 구조
```
practice/
├── _template.html          ← 새 실습 만들 때 복사해서 쓰는 빈 템플릿
├── 01_fundamentals/  Day01~15.html
├── 02_code-quality/  Day16~17.html
├── ... (노트와 동일한 파트 구조)
└── 10_finish/      Day60.html
```

> 💡 Day 13(함수) 이후부터는 Node.js로 `.js` 파일을 실행하는 게 더 편할 수 있어요.
> 그때는 같은 폴더에 `DayNN.js`를 만들어 `node DayNN.js`로 실행하면 됩니다.
