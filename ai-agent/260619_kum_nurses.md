---
marp: true
theme: godel
paginate: true
size: 16:9
header: "개념부터 실전까지: AI 활용 실습"
footer: ©2026 From Insight Inc. All right reserved.
info: |
  ## 생성형 AI와 진료협력 업무 효율
  고려대 안암병원 진료협력 간담회
author: 프롬인사이트
---

<style> 
   .font-family {
    font-family: 'Pretendard', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen;
  }
  h2 {
    color: #1a5276;
  }
   .cite-author { 
      text-align        : right; 
   }
   .cite-author:after {   
      color             : #f87ca1;
      font-size         : 130%;
      font-style        : italic;
      font-weight       : bold;
      font-family       : Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
      padding-right     : 130px;
   }
   .cite-author[data-text]:after {
      content           : " - "attr(data-text) " - ";      
   }
   .cite-author p {    
      padding-bottom : 40px
   } 
   .classReact rect {
    fill: #61dafb;
    stroke: #000;
    stroke-width: 2px;
    rx: 10;
    ry: 10;
    max-width: 350px;
  }
  {
   -webkit-user-select: none;  /* Chrome, Safari, Opera */
    -moz-user-select: none;     /* Firefox */
    -ms-user-select: none;      /* IE/Edge */
    user-select: none;          /* Standard */
  }

/* Marp column layout */
.columns {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}
.column {
  display: flex;
  flex-direction: column;
}
</style>   

![bg right:45%](./images/agent-title.png)

<!-- _class: titlepage -->

# 생성형 AI로 높이는 업무 효율  
## AX 개념부터 실전까지 <br> 고려대 안암병원 간담회
<br><br><br>

<!-- <div class="title"> HTML, CSS, Javascript  </div>
<div class="subtitle"> 웹과 가까워지기  </div> -->
<div class="author"> 권 수 정 <a href="https://suekwon.github.io/about/" target="_blank" style="color: #aed6f1;"> <img src="./images/GitHub_Invertocat_Black.svg" width="7%" height="7%" /> 
</a></div>

<div class="organization">AI전략 컨설턴트 | <div style="display: inline;">  <a href="http://www.from-insight.com" target="_blank"> From Insight Inc. </a> </div>

<!--
오늘 강의의 핵심은 "AI가 무엇인가"가 아니라 "내 업무 방식이 어떻게 바뀌는가"입니다.
건강보험공단 리더 업무는 민원, 지표, 현장보고, 법령, 회의자료가 결합된 복합 업무입니다.
따라서 단순 챗봇이 아니라 리더의 판단을 보조하는 업무 Agent 관점으로 접근합니다.
-->


---

<!-- _class: center -->

# "AI에게 일을 맡기기" vs. "AI가 처리할 수 있는 형태로 재설계"


### 1. 이해
생성형 AI가 왜 그럴듯하게 답하고, 왜 틀릴 수 있는지 이해한다.

### 2. 적용
현제 업무 중 바로 적용 가능한 예시를 발견한다.


### 3. 확장
의료협력 현안 처리 Agent와 의료업무 특성에 맞는 안전한 Agent 설계한다.

---

# 최신 AI 흐름: 챗봇에서 Agent로

<div class="columns">
<div >

### 과거: 질문하면 답하는 AI

- "이 문서 요약해줘"
- "회의자료 초안 써줘"
- "민원 답변문 만들어줘"

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

<div style = "width:90%; margin: 0 auto;">

![alt text](nhis-images/flows.png)

</div>


<!-- 
- Agentic, Harnessing the Power of AI
> OpenAI: Responses API와 Agents SDK에서 web search, file search, computer use 같은 도구 결합을 Agent 구축의 핵심 기능
> Anthropic: MCP로 AI 애플리케이션과 외부 데이터·도구를 연결하는 표준으로 제시 -->

---

# 챗봇 vs AI Agent

<br> 
<div style="width:60%; margin: 0 auto;">

![alt text](../tf_team/images/samsung/agent.png)
</div>

---

<!-- _class: center -->

# 생성형 AI 구조를 확실히 알고 쓰기

##  "AI가 똑똑하다" → "AI가 어떤 방식으로 작동한다" 

---

# 생성형 AI는 어떻게 답을 만드는가

### AI는 "확률적으로 그럴듯한 초안 작성자",

<div style = "width:70%; margin: 0 auto;">

  ![alt text](./nhis-images/sentence2embmatrix1.png)  
    **토큰화**, **숫자벡터**,  **임베딩**, 다음 토큰 예측, 답변 생성, &nbsp; [변환기(Transformer)](https://www.google.com/search?q=transformer+abstract+diagram&newwindow=1&sca_esv=0941c5488d98d8af&udm=2&biw=1434&bih=1071&aic=0&sxsrf=ANbL-n4mFitsI2HLQ1YrqfhMGVtU7eNEug%3A1769868367139&ei=Twx-adCdCJfd2roP5b7F0Aw&ved=0ahUKEwiQgcq6-bWSAxWXrlYBHWVfEcoQ4dUDCBI&uact=5&oq=transformer+abstract+diagram&gs_lp=Egtnd3Mtd2l6LWltZyIcdHJhbnNmb3JtZXIgYWJzdHJhY3QgZGlhZ3JhbUidPFDOBFjKOnAGeACQAQCYAYgBoAGFFaoBBDAuMjO4AQPIAQD4AQGYAg2gAt4LwgIFEAAYgATCAgcQIxjJAhgnwgIEEAAYHsICBhAAGAgYHpgDAIgGAZIHBDEuMTKgB5E5sgcEMC4xMrgH2wvCBwcwLjMuOS4xyAc9gAgB&sclient=gws-wiz-img#sv=CAMSVhoyKhBlLVZzNHdNcDB2TTFuSmlNMg5WczR3TXAwdk0xbkppTToOYUxQX2YzdF94WkVvSU0gBCocCgZtb3NhaWMSEGUtVnM0d01wMHZNMW5KaU0YADABGAcg5_-0hQ8wAkoKCAEQAhgCIAIoAg) [LLM 모델은 몇 개나 될까? ](https://openrouter.ai/models)
    
</div>

---

# 생성형 AI 는 무엇을 잘하고 무엇을 못할까? 
## <b>  원칙: AI로 초안·분류·요약·비교 후, 최종 판단은 **사람**이 한다. </b>

<div class="columns">
<div>

### 적용 분야

- 긴 문서 요약
- 반복 민원 분류
- 회의록 정리
- 표 비교와 패턴 찾기
- 보고서 초안 작성
- 체크리스트 생성
- 쉬운 설명문 작성

</div>
<div>

### 잘하는 것
- 반복 작업
- 문서 초안 작성
- 요약
- 패턴 분석
- 각종 변환

###  못하는 것
- 맥락 없는 추정
- 법적 최종 판단
- 최신 정보(예. 보험수가 최신버전) 완벽 반영

</div>

</div>

---

<!-- __class: image -->

<div style="width:90%">

![alt text](../tf_team/images/hospitals/secure.png)

</div>

---

<!-- _class: center -->

# AI 활용 핵심 기술!

---
# 업무에 필요한 AI 활용 방식

<div class="columns">
<div>

### 진료협력  업무의 특징
<br>

- 공공성·책임성·보안성이 높은 업무
- 민원, 지표, 현장보고, 법령, 언론 동시 발생
- 최종 판단 전 방대한 자료 검토 시간을 요함

- **빠른 답변**과 **정확한 답변** 요구 민원

</div>
<div>

### AI가 먼저 도와줄 수 있는 일

   | 업무 | AI 활용 방식 |
   |---|---|
   | 현안 파악 | 여러 자료를 읽고 핵심 이슈 5개 추출 |
   | 민원 분석 | 유형·긴급도·반복성 분류 |
   | 지사 비교 | 유사 규모 지사와 지표 편차 분석 |
   | 회의 준비 | 안건, 쟁점, 질문 목록 작성 |
   | 보고 초안 | 1페이지 브리핑 초안 작성 |

</div>
</div>

---

# 업무용 프롬프트 템플릿

<div class="columns">
<div>

### 템플릿

```text
당신은 국민건강보험공단 지역본부 리더를 보좌하는 업무분석 담당자입니다.
아래 자료를 기준으로 핵심 이슈를 정리하세요.

분석 기준:
1. 민원 증가 가능성
2. 언론·대외 리스크
3. 처리 지연 가능성
4. 취약계층 영향
5. 내부 후속조치 필요성

출력 형식:
- 이번 주 위험 이슈 TOP 5
- 각 이슈별 근거
- 담당부서 확인사항
- 리더가 회의에서 물어볼 질문
- 확인 필요 정보

주의:
개인정보는 사용하지 말고, 자료에 없는 내용은 추정하지 마세요.
```

</div>
<div>

### 이 템플릿이 좋은 이유

- 역할이 명확하다
- 판단 기준이 있다
- 출력 형식이 정해져 있다
- "확인 필요"를 허용한다
- 개인정보 사용 금지를 명시한다

<br>

**질문에서 업무지시로 프롬프트 활용**

</div>
</div>

---

<!-- _class: center -->

# 진료협력 업무에 AI 적용하기
## 4가지 영역 · 오늘 바로 쓰는 예시

<!--
안암병원 진료협력 업무를 4개 영역으로 나눠
각 영역에서 AI가 무엇을 대신하고, 사람이 무엇을 판단하는지 보여줍니다.
모든 수치는 교육용 자리표시자([ ])이며, 실제(또는 교육용) 데이터로 교체합니다.
예제 데이터는 별도 파일로 생성합니다.
-->

---

# 한눈에 보는 4가지 적용 영역

<div class="columns">
<div>

### ① 의뢰·회송 자동화
의뢰서·회송문서 작성과 분류

### ② 데이터 분석
협력병원·진료과별 패턴 분석

</div>
<div>

### ③ 문서·보고서 자동화
간담회·협력병원 보고서 생성·시각화

### ④ 교육 지원
협력병원 의료진 맞춤 교육자료

</div>
</div>

<br>

### 공통 원칙: AI는 초안·분류·요약, 최종 판단은 의료진

---

<!-- _class: center -->

# ① 환자 의뢰·회송 자동화

<div style="font-size:330%; color:#f87ca1; font-weight:bold; line-height:1.1; margin-top:24px;">
[ 15분 → 3분 ]
</div>

<div style="font-size:130%; margin-top:14px;">
의뢰서 1건 작성시간 &nbsp;·&nbsp; 행정시간 <b style="color:#1a5276;">[ ▼ XX% ]</b> &nbsp;·&nbsp; 월 의뢰·회송 <b style="color:#1a5276;">[ XXX건 ]</b>
</div>

<!--
상황: 의사가 진료의뢰서·회송문서를 직접 작성해 행정 부담이 큼.
Hero Number는 제공해 주실 수치로 교체. (자리표시자: [ ])
-->

---

# ① AI 활용 방식 — 의뢰·회송

<div class="columns">
<div>

### AI가 하는 일
- 의뢰 사유 → 진료과 자동 분류
- 의뢰서·회송문서 초안 작성
- 필수 항목 누락 체크

### 사람이 하는 일
- 의학적 판단 · 최종 서명

</div>
<div>

### 프롬프트 (요약)
- **역할** 진료협력 문서 보조 AI
- **입력** 환자 의뢰 메모(비식별)
- **출력** 회송문서 초안 + 진료과 분류

<div class="card">
<b>예제 데이터</b><br>
[ 비식별 의뢰 메모 샘플 — 별도 생성 ]
</div>

</div>
</div>

<!--
[전체 프롬프트 원문 — 자리표시자]
당신은 진료협력센터의 문서 작성을 보조하는 AI입니다.
아래 비식별 의뢰 메모를 바탕으로 회송문서 초안과 진료과 분류를 작성하세요.
(제공/생성 예정)
-->

---

<!-- _class: center -->

# ② 데이터 분석

<div style="font-size:330%; color:#f87ca1; font-weight:bold; line-height:1.1; margin-top:24px;">
[ XX곳 · X,XXX건 ]
</div>

<div style="font-size:130%; margin-top:14px;">
협력병원 수 &nbsp;·&nbsp; 연간 의뢰 건수 &nbsp;·&nbsp; 진료과별 회송률 <b style="color:#1a5276;">[ XX% ]</b>
</div>

<!--
상황: 협력병원별 의뢰 패턴·진료과별 회송 현황을 수기로 파악하기 어려움.
-->

---

# ② AI 활용 방식 — 데이터 분석

<div class="columns">
<div>

### AI가 하는 일
- 협력병원별 의뢰 패턴 분석
- 진료과별 회송 현황 비교
- 이상치·증감 추세 탐지

### 사람이 하는 일
- 전략적 협력 방향 결정

</div>
<div>

### 프롬프트 (요약)
- **역할** 진료협력 데이터 분석가
- **입력** 의뢰·회송 통계표(비식별)
- **출력** 패턴 요약 + 협력 제안 3가지

<div class="card">
<b>예제 데이터</b><br>
[ 협력병원·진료과별 의뢰/회송 표 — 별도 생성 ]
</div>

</div>
</div>

<!--
[전체 프롬프트 원문 — 자리표시자]
-->

---

<!-- _class: center -->

# ③ 문서·보고서 자동화

<div style="font-size:330%; color:#f87ca1; font-weight:bold; line-height:1.1; margin-top:24px;">
[ X시간 → XX분 ]
</div>

<div style="font-size:130%; margin-top:14px;">
간담회·협력병원 보고서 작성시간 &nbsp;·&nbsp; 자동 생성 통계 <b style="color:#1a5276;">[ XX종 ]</b>
</div>

<!--
상황: 간담회·협력병원 대상 보고서와 통계 자료 작성에 시간이 많이 듦.
-->

---

# ③ AI 활용 방식 — 문서·보고서

<div class="columns">
<div>

### AI가 하는 일
- 통계 자료 표·차트 자동 생성
- 보고서 초안 작성
- 핵심 메시지 시각화

### 사람이 하는 일
- 사실 검증 · 최종 승인

</div>
<div>

### 프롬프트 (요약)
- **역할** 협력 보고서 작성 보조
- **입력** 의뢰·회송 통계(비식별)
- **출력** 1페이지 보고서 + 차트 설명

<div class="card">
<b>예제 데이터</b><br>
[ 분기 협력 실적 요약표 — 별도 생성 ]
</div>

</div>
</div>

<!--
[전체 프롬프트 원문 — 자리표시자]
-->

---

<!-- _class: center -->

# ④ 교육 지원

<div style="font-size:330%; color:#f87ca1; font-weight:bold; line-height:1.1; margin-top:24px;">
[ X일 → X시간 ]
</div>

<div style="font-size:130%; margin-top:14px;">
맞춤 교육자료 제작시간 &nbsp;·&nbsp; 대상 의료진 <b style="color:#1a5276;">[ XXX명 ]</b>
</div>

<!--
상황: 협력병원 의료진 대상 교육자료를 대상별로 맞춤 제작해야 함.
-->

---

# ④ AI 활용 방식 — 교육 지원

<div class="columns">
<div>

### AI가 하는 일
- 대상별 맞춤 교육자료 초안
- 난이도·분량 자동 조정
- 핵심 요약·퀴즈 생성

### 사람이 하는 일
- 의학적 정확성 검수

</div>
<div>

### 프롬프트 (요약)
- **역할** 의료진 교육자료 제작 보조
- **입력** 주제 · 대상 · 분량
- **출력** 슬라이드 개요 + 강의 노트

<div class="card">
<b>예제 데이터</b><br>
[ 교육 주제·대상 정의서 — 별도 생성 ]
</div>

</div>
</div>

<!--
[전체 프롬프트 원문 — 자리표시자]
-->

---

<!-- _class: center -->

# 실습 3. 안전한 AI 활용 

 공공기관에서 중요한 것은 "AI를 많이 쓰는 것" 보다,  
  "책임 있게 쓸 수 있는 경계선을 정하는 것" 이 우선

---

# AI 사용 금지·주의·실전

<div class="columns">
<div >

### 금지

- 주민등록번호, 계좌번호, 진료·요양 상세정보 
- 특정 민원인 개인정보를 외부 AI에 입력
- AI 답변을 검토 없이 민원인에게 발송
- 제재·불이익 판단을 AI에게 자동 결정시킴

### 주의

- 내부 결재 전 문서
- 국회·언론 대응자료
- 법령 해석
- 민감 민원

</div>
<div>

### 권장

- 가상 데이터 실습
- 비식별화된 통계 분석
- 공개 자료 요약
- 회의 안건 초안
- 직원 교육자료 초안
- 체크리스트 작성

<div class="card">
<b>리더의 원칙</b><br>
AI 활용의 책임은 AI가 아니라 조직과 사용자에게 있습니다. 따라서 "자동화"보다 "검토 가능한 보조"로 설계해야 합니다.
</div>

</div>
</div>

---

## 개인정보 제거 예시

| 원문 | AI 입력용 변환 |
|---|---|
| 홍길동, 580101-1******, 장기요양 등급 이의신청 | 70대 남성, 장기요양 등급 이의신청 사례 |
| 서울 ○○구 ○○아파트 101동 1203호 | 수도권 거주 고령 민원인 |
| 계좌번호 123-456-789 | 계좌정보 삭제 |
| 특정 병명과 진료내역 포함 | 건강정보 삭제 후 제도 문의 유형만 남김 |
| 담당 직원 실명 비판 | 담당부서 또는 업무유형으로 대체 |

---

## 실습용 데이터 만들기 규칙

```text
1. 사람 이름은 A민원인, B민원인으로 바꾼다.
2. 주민번호, 연락처, 주소, 계좌번호는 삭제한다.
3. 진료명, 병명, 요양 상세기록은 업무 유형으로 일반화한다.
4. 지사명은 A지사, B지사처럼 익명화한다.
5. 수치는 실제값이 아니라 교육용 범위로 변환한다.
6. AI 결과는 초안으로만 사용하고 최종 문서는 사람이 검토한다.
```

<div class="card">
<b>현장 팁</b><br>
AI 실습 자료는 "실제처럼 보이는 가상 데이터"가 가장 좋습니다. 실제 데이터보다 안전하고, 교육 효과는 충분합니다.
</div>

---

<!-- _class: center -->

# 마무리: 업무방식 변화

---

# Before → After

<div class="columns">
<div >

## Before

- 자료를 사람이 하나씩 읽는다
- 엑셀을 열어 직접 비교한다
- 보고서 초안을 처음부터 쓴다
- 회의 후 후속조치가 흩어진다
- 바쁜 리더가 맥락을 모두 떠안는다

</div>
<div>

## After

- AI가 먼저 읽고 분류한다
- Agent가 편차와 이상징후를 제시한다
- 리더는 초안을 검토하고 판단한다
- 회의 질문과 후속조치가 자동 정리된다
- 리더는 반복 업무보다 의사결정에 집중한다

</div>
</div>

<br> 

### 완벽한 AI 시스템보다 중요한 것은, 오늘 당장 업무 하나를 20% 줄이는 첫 실험입니다.

---

<!-- _class: center -->


<div class="text-3xl font-bold mt-4" style="color: #1a5276; line-height: 1.4em;">
  "AI를 쓰는 사람이<br>쓰지 않는 사람을 대체한다"
</div>

<div class="text-2xl mt-8 text-gray-500">
  <a href="https://www.nobelprize.org/prizes/physics/2024/hinton/speech/" target="_blank">AI를 세상에 준 사람이, 이제 세상에 AI를 조심하라고 말합니다.</a> 
</div>
<br>

<div align="right">by Geoffrey Hinton </div>
<br><br>

<div align="text-center">
"우리는 AI를 개발자들에게만 맡겨둘 수 없다" <br>
 (we cannot leave AI only to developers) <br>
 
<div align="right">by <a href="https://www.google.com/search?q=Lawrence+H.+Summers&oq=Lawrence+H.+Summers&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQLhhA0gEHMjIyajBqNKgCALACAQ&sourceid=chrome&ie=UTF-8" target="_blank">Lawrence H. Summers</a> </div>
</div>

---


# References

|      |
|------|
| OpenAI, New tools for building agents: Responses API, web search, file search, computer use, Agents SDK. |
| OpenAI API Docs, Computer use. |
| OpenAI, The next evolution of the Agents SDK. |
| Anthropic, Introducing the Model Context Protocol. |
| Model Context Protocol Specification. |
| 국민건강보험공단 홈페이지 및 공공기관 경영정보 공개자료. |
| 보건복지부, 사회보험징수통합 및 장기요양보험 관련 안내. |

<br> 

>본 강의자료의 실습 데이터는 교육용 가상 데이터입니다. 실제 민원, 개인 건강정보, 주민등록번호, 계좌정보, 내부 미공개 자료를 외부 AI 서비스에 입력하지 않습니다.
