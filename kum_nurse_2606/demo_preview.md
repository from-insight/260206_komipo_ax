# 병원 업무 자동화 AI — 데모 모음

이 문서는 생성한 HTML 데모의 **일부를 미리 보여주고**, 링크를 누르면 **실제 파일로 연결**되도록 작성한 예시입니다.

> 💡 클릭으로 HTML이 실제로 열리게 하려면, 이 `.md`를 **VS Code 마크다운 미리보기 / Obsidian** 같은 로컬 뷰어에서 열거나 **GitHub Pages**에 올리세요. (순수 GitHub 화면에서는 HTML이 소스로 표시될 수 있습니다.)

---

## 1. 병원 업무 자동화 데모

의뢰·회송 문서, 통계 보고서, 교육자료 자동화를 탭으로 시연하는 인터랙티브 페이지입니다.

**▶ [데모 열기 (hospital_ai_demo.html)](./hospital_ai_demo.html)**

<details>
<summary>📄 HTML 일부 미리보기 (펼쳐 보기)</summary>

```html
<header class="top">
  <div class="wrap">
    <div class="eyebrow">Hospital Workflow Automation · AI Demo</div>
    <h1>병원 업무 자동화 AI 시연</h1>
    <p>의뢰·회송 문서 작성, 통계 보고서 생성, 교육자료 제작 —
       어느 조직에서나 쓰이는 자동화를 병원 업무에 적용한 예제입니다.</p>
    <div class="demo-badge">● 시연용 데모 · 가상 샘플 데이터</div>
  </div>
</header>

<div class="tabs">
  <div class="tab active" onclick="showTab(0)">의뢰·회송 문서 자동화</div>
  <div class="tab" onclick="showTab(1)">데이터 분석·보고서 자동화</div>
  <div class="tab" onclick="showTab(2)">맞춤형 교육자료 제작</div>
</div>
```

</details>

---

## 2. 바이브코딩 따라하기

챗봇에 말 거는 것부터 시작해 미니앱으로 키워가는 5단계 과정을 보여줍니다.

**▶ [따라하기 열기 (vibe_coding_walkthrough.html)](./vibe_coding_walkthrough.html)**

<details>
<summary>📄 HTML 일부 미리보기 (펼쳐 보기)</summary>

```html
<!-- STEP 1: 챗봇에 그냥 물어보기 -->
<div class="prompt">
  <button class="copy" onclick="cp(this)">복사</button>
  <pre>아래 환자 메모를 진료의뢰서로 작성해줘.

환자: 김정호, 58세 남
메모: 운동 시 흉부 압박감, 좌측 어깨 방사통.
흡연 30갑년, 고혈압 병력.</pre>
</div>
```

</details>

---

## 3. 함께 보면 좋은 자료

| 자료 | 형식 | 링크 |
|------|------|------|
| 발표용 슬라이드 (11장) | PPTX | [열기](./hospital_ai_slides.pptx) |
| 한 장 요약 | DOCX | [열기](./hospital_ai_onepager.docx) |

---

<!--
방법 2) 스크린샷 이미지를 '클릭하면 열리는 링크'로 만들기
이미지 파일(preview.png)을 준비한 뒤, 아래처럼 [![...](이미지)](링크) 형태로 감쌉니다.

[![데모 미리보기](./preview.png)](./hospital_ai_demo.html)
-->

---

## 📌 이 문서에 쓰인 마크다운 패턴 (복사해서 재사용)

````markdown
<!-- (1) 클릭하면 파일이 열리는 링크 — 상대경로 사용 -->
**▶ [데모 열기](./hospital_ai_demo.html)**

<!-- (2) HTML 일부를 접었다 펴는 미리보기 -->
<details>
<summary>📄 HTML 일부 미리보기</summary>

```html
<h1>병원 업무 자동화 AI 시연</h1>
```

</details>

<!-- (3) 스크린샷 이미지를 통째로 링크로 (이미지 클릭 → 파일 열림) -->
[![미리보기](./preview.png)](./hospital_ai_demo.html)

<!-- (4) 표로 여러 파일 정리 -->
| 자료 | 링크 |
|------|------|
| 슬라이드 | [열기](./hospital_ai_slides.pptx) |
````

> 핵심 3가지 — ① 상대경로 링크 `[텍스트](./파일.html)` 로 파일 연결, ② 코드 일부는 코드펜스로 표시, ③ 길면 `<details>` 로 접기.
