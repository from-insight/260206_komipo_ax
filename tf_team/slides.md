---
theme: default
pagination: true
aspectRatio: 16/9
title: "개념부터 실전까지: AI 활용 실습"
info: |
  ## HD엑셀 실습 
author: 프롬인사이트
class: text-center
drawings:
  persist: false
transition: slide-left
mdc: true
style: ../styles.css
---



<div class="columns">
  <div class="title-bg"></div>
  <div> </div>
  <div style="font-size: 2.2em; margin-top: -30px; color: #1a5276; text-align: center;"> AI 활용 엑셀
    <div class="mt-6 text-gray-200 text-lg" style="color: #1a5276;">
   개념부터 실전까지 : 실무 및 업무 자동화
</div>

  </div>
</div>


<div class="abs-br m-6 text-sm text-left">
  <h3 style="color: #1a5276;">
    <div>권수정 <a href="https://suekwon.github.io/about/" target="_blank" style="color: #1a5276;"> <carbon:logo-github /> </a></div>
    <div style="color: #3669ad; font-size: 0.85em">AI 전략 컨설턴트 | <a href="https://from-insight.com" target="_blank" style="color: #1a5276;">프롬인사이트 </a></div>
  </h3>
</div>


<!-- 
<div class="absolute bottom-2 right-4 text-xs opacity-80" style="color: #585a5dff;">
    <SlideCurrentNo /> / <SlidesTotal />
  </div>
   -->


---
layout: center
transition: fade
---

### 강사 소개

**권수정**
AI 전략 컨설턴트 | 프롬인사이트

- 산업공학 박사, 최적화 전공
- 생성형AI · 강화학습 · 머신러닝
  연구 및 실무 적용 전문
- 공공기관·금융·산업 현장
  AI 기반 의사결정 구현 경험

📧 [sue.kwon@from-insight.com](mailto:sue.kwon@from-insight.com)


---
layout: two-cols-header
title: AI Icebreaking
transition: fade-out
---

# 오늘 아침 업무 책상 위에는?

- 질문에 **해당되면 ☝️ 손가락 1개 접기**  
- 총 **5개** 질문

<br>


::left::

<v-click>

### 질문 ①  
최근 1주일 안에 **보고서·회의자료·답변 초안** 때문에 시간이 부족했다

</v-click>

<v-click>

### 질문 ②  
행정, 현장 보고 받을/할 것을 **따로따로 확인하다가** 중요한 이슈를 놓칠까 걱정한 적 있다


</v-click>

<v-click>

### 질문 ③  
"**어떤 AI**를 사용하지" 고민한 적이 있다

</v-click>

::right::

<v-click>

### 질문 ④  
비슷한 종류의 자료들을 비교해보고 싶은데, **엑셀 정리**에 시간이 많이 든다


</v-click>

<v-click>

### 질문 ⑤  
AI에게 **음성으로 질문**하거나 AI가 만든 **이미지·영상을** 본 적이 있다


</v-click>


<!--
멘트 예시:
5개 다 접으신 분은 이미 AI 전환의 핵심 문제를 정확히 알고 계신 분입니다.
0개이신 분은 축하드립니다. 오늘 강의가 끝나면 적어도 3개는 접게 됩니다.
-->


---
layout: center
transition: fade
---

# 오늘 목표
#### *"AI에게 일을 맡긴다" vs. "AI가 처리할 수 있는 형태로 일을 재설계한다"*


<div class="three-cols">
<div class="card">
<h3>1. 이해</h3>
생성형 AI가 왜 그럴듯하게 답하고, 왜 틀릴 수 있는지 이해한다.
</div>
<div class="card">
<h3>2. 적용</h3>
나의 업무 중 바로 적용 가능한 예시를 실습한다.
</div>
<div class="card">
<h3>3. 설계 및 확장</h3>
Agent를 설계하고, 나만의 Agent를 만든다.
</div>
</div>

---
layout: default
transition: fade
---

# 최신 AI 흐름: 챗봇에서 Agent로


<br>

<div class="columns">
<div>

### 과거: 질문하면 답하는 AI

- "이 문서 요약해줘"
- "회의자료 초안 써줘"
- "민원 답변문 만들어줘"
- "OO 정보에 대해서 알려줘"

</div>
<div>

### 현재: 도구를 쓰는 AI

- 파일을 읽는다
- 웹이나 내부 자료를 검색한다
- 표를 계산한다
- 시스템 화면을 보며 작업 순서를 제안한다
- 여러 단계를 나눠 실행한다

</div>
</div>

<div style="width:70%; margin: 0 auto;">

![alt text](./images/samsung/flows.png)

</div>

> OpenAI: Responses API와 Agents SDK에서 web search, file search, computer use 같은 도구 결합을 Agent 구축의 핵심 기능으로 설명 <br>
> Anthropic: **MCP**는 AI 애플리케이션과 외부 데이터·도구를 연결하는 표준으로 제시



---
layout: center
transition: fade
---

# 생성형 AI 구조를 확실히 알고 쓰기

  "AI가 똑똑하다" → "AI가 어떤 방식으로 작동한다"


---
layout: two-cols-header
transition: fade
---

# 생성형 AI는 어떻게 답을 만드는가

#### **AI는 "확률적으로 그럴듯한 초안 작성자"** &ensp;  <span v-click="1" v-mark.crossed-off.red> 데이터베이스 </span> &emsp; <span v-click="2" v-mark.crossed-off.red> 검색엔진 </span> 

<div style = "width:70%; margin: 0 auto;">

  ![alt text](./images/samsung/sentence2embmatrix1.png)  
    <b> *토큰화*, 숫자벡터, *임베딩*, 다음 토큰*예측*, 답변 *생성* , &nbsp;
    [변환기(Transformer)](https://www.google.com/search?q=transformer+abstract+diagram&newwindow=1&sca_esv=0941c5488d98d8af&udm=2&biw=1434&bih=1071&aic=0&sxsrf=ANbL-n4mFitsI2HLQ1YrqfhMGVtU7eNEug%3A1769868367139&ei=Twx-adCdCJfd2roP5b7F0Aw&ved=0ahUKEwiQgcq6-bWSAxWXrlYBHWVfEcoQ4dUDCBI&uact=5&oq=transformer+abstract+diagram&gs_lp=Egtnd3Mtd2l6LWltZyIcdHJhbnNmb3JtZXIgYWJzdHJhY3QgZGlhZ3JhbUidPFDOBFjKOnAGeACQAQCYAYgBoAGFFaoBBDAuMjO4AQPIAQD4AQGYAg2gAt4LwgIFEAAYgATCAgcQIxjJAhgnwgIEEAAYHsICBhAAGAgYHpgDAIgGAZIHBDEuMTKgB5E5sgcEMC4xMrgH2wvCBwcwLjMuOS4xyAc9gAgB&sclient=gws-wiz-img#sv=CAMSVhoyKhBlLVZzNHdNcDB2TTFuSmlNMg5WczR3TXAwdk0xbkppTToOYUxQX2YzdF94WkVvSU0gBCocCgZtb3NhaWMSEGUtVnM0d01wMHZNMW5KaU0YADABGAcg5_-0hQ8wAkoKCAEQAhgCIAIoAg)
    </b>
    <br> [LLM 모델은 몇 개나 될까? ](https://openrouter.ai/models)
</div>


---
layout: two-cols-header
transition: fade
---

# 생성형AI는 무엇을 잘하고 무엇을 못하는가

<br>

::left::

### <span v-mark.circle.red> **잘하는 것** </span>
  - 반복 작업
  - 문서 초안 작성
  - 요약
  - 패턴 분석
  - 각종 변환 

<br>

### <span v-mark.circle.red> **못하는 것** </span>
  - 맥락 없는 추정
  - 법적 최종 판단
  - <span v-mark.strike-through.orange> 데이터 최신 정보(예. 보험수가 최신버전) 완벽 반영 </span>
  
::right::

<br><br>

- 예시 업무
  ![bg](./images/hospitals/pros1.png)  

  <!-- 
  잘하는 것의 예시: 알파고 2016
  - 경우의 수가 많은 복잡한 게임
  - 4:1 승리
  - 사람의 통찰력?
  - 글쓰기??
  - 사람이 더 잘하는 영역? -->


---
layout: two-cols-header
transition: fade
---

# 적용해 볼 수 있는 업무와 위험한 분야


<div class="card"  v-mark.after.box.red>

#### **원칙**: AI로 <span class="ok">초안·분류·요약·비교</span>후, 최종 판단은 <span style="color:red">사람</span>이 한다.

</div>

<br>

::left::

### 적용 분야

- 긴 문서 요약, 정리(ex. 회의록)
- 표 비교 및 패턴 찾기 및 경중 업무 분류
- 초안 작성
- 체크리스트 생성
- 동시다발 처리해야하는 업무
- 잦은 반복 + 오랜 시간 업무
- “빠르게” “정확한" 답변

::right::

###  <span v-mark.undeline.orange > 조심해야 하는 일</span>

- 개인정보 포함 자료 입력
- 민감 자료 최종 분석
- 법적 최종 판단
- 최신 법령·정보를 확인하지 않은 내용
- 내부 규정과 다르게 자동 처리
- 자동 결정
  

---
layout: image
transition: fade
---


<div style="width:90%">

![alt text](./images/hospitals/secure.png)

</div>


---
layout: two-cols-header
transition: fade
---

# 업무용 AI 사용 원칙(체크리스트 예시)

<br>

::left::

### 입력 전 확인 사항

<br>

<div class="checklist-table">

| 질문 | 판단 |
| --- | --- |
| 주민번호, 계좌, 진료정보가 있는가? | 있으면 입력 금지 |
| 특정 개인이 식별되는가? | 비식별 처리 |
| 내부 결재 전 자료인가? | 내부 규정 확인 |
| 최신 법령 확인이 필요한가? | 출처 확인 필수 |
| ... | ... |

</div>

::right::

### 출력 후 확인 사항

<br>

<div class="checklist-table">

| 질문 | 판단 |
| --- | --- |
| 근거가 명확한가? | 출처 확인 |
| 과장된 표현은 없는가? | 문장 조정 |
| 기관 입장처럼 단정했는가? | 책임 표현 수정 |
| 부서 간 이해관계 및 불리한 판단인가? | 사람 검토 필수 |
| ... | ... |

</div>


---
layout: center
transition: fade
---

# 몸풀기 실습. 프롬프트 작성하기
| 실습준비: 구글계정, 브라우저



---
layout: default
transition: fade
---

# 좋은 프롬프트 구성 요소

<br>

<div class="columns">
<div class="checklist-table">

| 요소 | 질문 |
|:---:|---|
| 역할 | AI가 어떤 역할을 해야 하는가? |
| 목표 | 무엇을 만들어야 하는가? |
| 자료 | 어떤 입력자료를 기준으로 할 것인가? |
| 기준 | 어떤 관점으로 판단할 것인가? |
| 예시 | **예시 혹은 절차를 검토**하고 있는가? |
| 출력 | 어떤 형식으로 내보낼 것인가? |

</div>
<div>

<br> 
당신은 <strong style="color:blue">[역할]</strong>입니다.
목표는 <strong style="color:blue">[목표]</strong>입니다.
아래 <strong style="color:blue">[자료]</strong>를 기준으로 <strong style="color:blue">[기준]</strong>에 따라 분석하세요.
출력은 <strong style="color:blue">[형식]</strong>으로 작성하세요.
모르는 내용은 추정하지 말고 <strong style="color:blue">"확인 필요"</strong>라고 표시하세요.

</div>
</div>


--- 
layout: default
src: ./pages/nhis-subpage.md
---


---
layout: center
transition: fade
---

# 챗봇 vs AI Agent

<br> 
<div style="width:60%; margin: 0 auto;">

![alt text](./images/samsung/agent.png)
</div>



---
layout: default
transition: fade
---

# 에이전트의 일하는 방식 — 추론 : 도구호출 : 메모리

<div class="card">
<b>Agentic Workflow</b><br>
Agent ~ LLM + 업무목표 + 자료접근 + 도구사용 + 검토절차
</div>

<div style = "width:70%; margin: 0 auto">

![alt text](./images/samsung/react.png)

</div>


<!-- > **발표자 노트:**
> ReAct는 AI 에이전트가 작동하는 핵심 원리입니다. 생각하고(Think), 행동하고(Act), 결과를 보고(Observe), 다시 생각합니다. 이 루프가 목표를 달성할 때까지 반복됩니다. 사람이 문제를 해결할 때와 동일한 방식입니다. -->

---
layout: default
transition: fade
---

# 싱글 vs. 멀티 에이전트

![alt text](./images/samsung/multi-single.png){width=80%}



--- 
layout: default
src: ./pages/begin-agent.md
---



---
layout: center
transition: fade
---

# 도구 연결하기

## 준비물: 생성형 + 배포사이트


> #### 재고 관리 대시보드 만들고 배포하기  



---
layout: center
transition: fade
---

# Agent 설계 실습

## 내 업무/취미 Agent로 바꿔보기



---
layout: center
transition: fade
---

# 실무 예시 상황 5개


---
layout: default
transition: fade
---

## 예시 1. 월요일 아침 지사장 회의자료 초안

<br>

### 상황

- 지난주 민원 증가
- 장기요양 인정조사 지연
- 건강검진 수검률 부진
- 언론 취재 문의 발생

### 프롬프트

```text
당신은 지사장 회의자료를 작성하는 업무보좌관입니다.
아래 메모를 바탕으로 회의자료 초안을 작성하세요.

출력 형식:
1. 이번 주 핵심 이슈 3개
2. 지사장 모두에게 공유할 메시지
3. 담당부서별 확인사항
4. 다음 회의까지 후속조치
5. 대외 표현 주의사항

문체는 공공기관 내부 회의자료 문체로 작성하세요.
```

---
layout: default
transition: fade
---


## 예시 2. 민원 급증 원인 가설 정리

<br>

### 상황

본인부담상한제 환급 문의가 갑자기 늘었습니다.

### 프롬프트

```text
아래 민원 증가 상황을 보고 가능한 원인 가설을 정리하세요.

주의:
- 자료에 없는 원인을 사실처럼 단정하지 마세요.
- 확인해야 할 데이터와 담당부서를 함께 제시하세요.
- 민원 응대 현장에서 바로 쓸 수 있는 안내문 초안도 작성하세요.

출력:
[가능 원인 가설] [확인 데이터] [담당부서] [민원 안내문 초안]
```

---
layout: default
transition: fade
---

## 예시 3. 법령·지침 변경 영향분석

<br>

### 상황

새로운 고시나 내부 지침이 내려왔습니다.

### 프롬프트

```text
당신은 법령·지침 변경 영향분석 담당자입니다.
아래 변경 내용을 읽고 현장 업무에 미치는 영향을 분석하세요.

출력 형식:
1. 변경 내용 요약
2. 영향받는 업무
3. 영향받는 민원 유형
4. 수정이 필요한 서식·안내문·시스템 항목
5. 직원 교육 필요사항
6. 현장 혼선 가능성과 예방 메시지

불명확한 내용은 “추가 확인 필요”라고 표시하세요.
```

---
layout: default
transition: fade
---

## 예시 4. 취약계층 안내문 쉽게 바꾸기

<br>

### 상황

고령 민원인에게 제도를 안내해야 합니다.

### 프롬프트

```text
아래 제도 설명문을 고령 민원인이 이해하기 쉬운 안내문으로 바꾸세요.

작성 기준:
- 한 문장은 40자 이내로 짧게 작성
- 어려운 행정용어는 쉬운 말로 바꾸기
- 필요한 준비물과 문의처를 먼저 제시
- 불안감을 줄이는 친절한 문체 사용
- 법적 판단이나 확정 표현은 피하기

출력 형식:
문자 안내문 / 전화 상담 스크립트 / 창구 안내문 3가지로 작성하세요.
```

---
layout: default
transition: fade
---

## 예시 5. 회의록에서 후속조치 뽑기

<br>

### 상황

회의는 길었고, 누가 무엇을 언제까지 해야 하는지 흐릿합니다.

### 프롬프트

```text
아래 회의 메모에서 후속조치를 추출하세요.

출력 형식:
표로 작성하세요.
열은 [결정사항, 담당자/담당부서, 기한, 필요한 자료, 리스크, 다음 확인일]입니다.

주의:
- 담당자가 명확하지 않으면 “지정 필요”라고 쓰세요.
- 기한이 없으면 “기한 확인 필요”라고 쓰세요.
- 실행 불가능해 보이는 항목은 별도 표시하세요.
```


---
layout: two-cols-header
transition: fade
---

## 실습: 내 업무 Agent 카드 작성

<br>

::left::

|   | 내용 |
|---|---|
| 업무명 | 어떤 업무인가 |
| 입력자료 | 무엇을 넣는가 |
| 판단기준 | 어떤 기준으로 분석하는가 |
| 출력물 | 무엇을 만들어야 하는가 |
| 사람 검토 | 누가 무엇을 확인하는가 |
| 금지사항 | AI가 하면 안 되는 것은 무엇인가 |

<br>

- 1순위 후보
  - 주간·월간 보고서 초안
  - 민원 유형 분류
  - 지표 편차 분석
  - 회의록 후속조치 추출
  - 법령·지침 변경 요약

::right::

<div class="card">
 
 ### **예시: 지역 현안 브리핑 Agent** 
<b>입력</b>: 민원 현황, 언론 이슈, 현장보고, 지표<br>
<b>기준</b>: 민원 증가, 대외 리스크, 처리 지연, 취약계층 영향<br>
<b>출력</b>: 위험 이슈 TOP 5, 회의 질문, 후속조치<br>
<b>검토</b>: 지역본부장·담당부서장<br>
<b>금지</b>: 개인정보 입력, 자동 대외답변, 최종 책임 판단
</div>
<br>

- 신중한 후보
  - 고난도 민원 최종답변
  - 처분·불이익 판단
  - 개인정보 포함 상담자료
  - 인사·갈등관리
