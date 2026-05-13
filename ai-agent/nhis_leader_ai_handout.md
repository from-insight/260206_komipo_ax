---
marp: true
theme: godel
paginate: true
size: 16:9
header: "개념부터 실전까지: AI 활용 실습"
footer: ©2026 From Insight Inc. All right reserved.
info: |
  ## 예제 중심 AI 활용 업무방식 전환
  건강보험공단 리더 대상 실습형 강의안
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

# AI 기반 문제 해결 및 전략 수립
## 개념부터 실전까지: AI·활용 실습

<br><br><br><br><br>

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

# 오늘 아침 리더의 책상 위에는?


<div class="columns">
<div >

### 질문 ①  
최근 1주일 안에 **보고서·회의자료·답변 초안** 때문에 시간이 부족했다

### 질문 ②  
민원, 언론, 지표, 현장 보고를 **따로따로 확인하다가** 중요한 이슈를 놓칠까 걱정한 적 있다

### 질문 ③  
"어떤 AI를 사용히지" 고민한 적이 있다

</div>
<div>

### 질문 ④  
비슷한 규모의 지사끼리 비교해보고 싶은데, **엑셀 정리**에 시간이 많이 든다


### 질문 ⑤  
AI를 쓰고 싶지만 **개인정보·책임·보안** 때문에 어디까지 가능한지 애매하다


</div>
</div>

<!--
멘트 예시:
5개 다 접으신 분은 이미 AI 전환의 핵심 문제를 정확히 알고 계신 분입니다.
0개이신 분은 축하드립니다. 오늘 강의가 끝나면 적어도 3개는 접게 됩니다.
-->

---

<!-- _class: center -->

# 오늘 목표
## "AI에게 일을 맡긴다" vs. "AI가 처리할 수 있는 형태로 일을 재설계한다"


### 1. 이해
생성형 AI가 왜 그럴듯하게 답하고, 왜 틀릴 수 있는지 이해한다.

### 2. 적용
건보공단 리더 업무 중 바로 적용 가능한 예시를 실습한다.


### 3. 확장
지역 현안 브리핑 Agent와 지사 편차 분석 Agent를 설계한다.

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

<!-- _class: center -->

# 생성형 AI 구조를 확실히 알고 쓰기

##  "AI가 똑똑하다" → "AI가 어떤 방식으로 작동한다" 

---

# 생성형 AI는 어떻게 답을 만드는가

### AI는 "확률적으로 그럴듯한 초안 작성자"

<div style = "width:70%; margin: 0 auto;">

  ![alt text](./nhis-images/sentence2embmatrix1.png)  
    <b> **토큰화**, **숫자벡터**, 다음 토큰 예측, 답변 생성 </b>
</div>

---

# 생성형 AI 는 무엇을 잘하고 무엇을 못할까? 

<div class="columns">
<div>

![alt text](./nhis-images/ability.png)
</div>
<div style = "margin: 60px 10px 10px 10px;">

![alt text](./nhis-images/pros1.png)
</div>
</div>

---

# 적용해 볼 수 있는 업무와 위험한 분야

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

### 조심해야 하는 일

- 법적 최종 판단
- 민감 민원 최종 답변
- 개인정보 포함 자료 입력
- 최신 법령·고시를 확인하지 않은 답변
- 내부 규정과 다르게 자동 처리
- 불이익 처분 자동 결정
</div>
</div>

---

<!-- __class: image -->

<div style="width:90%">

![alt text](../tf_team/images/hospitals/secure.png)

</div>

---

# 업무에서 AI 활용 원칙

<div class="columns">
<div>

### 입력 전 확인 사항

| 질문 | 판단 |
|---|---|
| 주민번호, 계좌, 진료정보가 있는가? | 있으면 입력 금지 |
| 특정 개인이 식별되는가? | 비식별 처리 |
| 내부 결재 전 자료인가? | 내부 규정 확인 |
| 최신 법령 확인이 필요한가? | 출처 확인 필수 |

</div>
<div>

### 출력 후 확인 사항

| 질문 | 판단 |
|---|---|
| 근거가 명확한가? | 출처 확인 |
| 과장된 표현은 없는가? | 문장 조정 |
| 기관 입장처럼 단정했는가? | 책임 표현 수정 |
| 민원인에게 불리한 판단인가? | 사람 검토 필수 |

</div>
</div>

---

<!-- _class: center -->

# 몸풀기 실습. 프롬프트 작성하기

---

# 좋은 프롬프트 구성 요소

<div class="columns">
<div>

| 요소 | 질문 |
|---|---|
| 역할 | AI가 어떤 역할을 해야 하는가? |
| 목표 | 무엇을 만들어야 하는가? |
| 자료 | 어떤 입력자료를 기준으로 할 것인가? |
| 기준 | 어떤 관점으로 판단할 것인가? |
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

# 예시. 업무용 프롬프트 템플릿

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
# NHIS 업무의 특징

<div class="columns">
<div>

### 공단 업무의 특징
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

<!-- _class: center -->

# 간단한 활용 예시
## 임의 데이터 생성, 간단한 대시보드 작성하기


---

<!-- _class: center -->

# 오늘의 핵심 실습 1.

## 지역 현안 브리핑 AI

| 매주 지역별 민원, 언론, 지표, 현장 보고를 모아 
| "이번 주 위험 이슈 5개"를 정리하는 AI 

---

## [실습1. 가정]

<div class="columns">
<div >

### 상황

당신은 지역본부 리더입니다. 
월요일 오전 회의 전에 아래 자료를 10분 안에 정리해야 합니다.

- 지사별 민원 증가 현황
- 지역 언론 보도
- 장기요양 현장 보고
- 건강검진 수검률
- 징수 관련 지표

</div>
<div>

### AI에게 맡길 일과 사람의 일 구분하기

| AI의 일 | 사람의 일 |
|---|---|
| 자료 요약 | 최종 판단 |
| 위험도 분류 | 책임 있는 지시 |
| 회의 질문 초안 | 대외 메시지 결정 |
| 후속조치 목록화 | 조직 조정 |

</div>
</div>

---

## [실습1. 데이터] 지역 현안 브리핑용 가상 자료

아래 자료를 휴대폰 AI 앱에 그대로 복사해 사용합니다. 실제 개인정보나 내부자료가 아닌 **가상 데이터**입니다.

| 지역 | 민원 증감 | 언론·외부 이슈 | 현장 보고 | 주요 지표 |
|---|---:|---|---|---|
| A | +34% | 신문: 장기요양 대기기간 불만 기사 | 방문조사 차질(일정 지연,인력 결원) | 인정조사 평균 11.2일 |
| B | +8% | 특이사항 없음 | 고령 민원인 내방 증가 | 건강검진 수검률 61% |
| C | +27% | 온라인: 보험료 부과 불만 확산 | 피부양자 자격 관련 상담 급증 | 부과 민원 420건 |
| D | -3% | 특이사항 없음 | 민원처리 안정 | 처리기간 2.1일 |
| E | +19% | 지방의회 자료요구 예정 | 체납 안내문 반송 증가 | 체납 고지 반송률 14% |
| F | +41% | 지역방송: 취재 문의 | 본인부담상한제 환급 문의 폭증 | 환급 문의 680건 |

---

## [실습 1. 프롬프트 작성하기] (휴대폰 환경)

```text
당신은 국민건강보험공단 지역본부장을 보좌하는 지역 현안 브리핑 AI입니다.
아래 가상 자료를 기준으로 이번 주 지역본부 회의에서 다룰 위험 이슈 TOP 5를 정리하세요.

분석 기준:
1. 민원 증가율
2. 언론·외부 확산 가능성
3. 취약계층 영향
4. 처리 지연 가능성
5. 리더 의사결정 필요성

출력 형식:
표로 작성하세요.
열은 [순위, 이슈명, 관련 지역, 위험도, 근거, 오늘 회의 질문, 후속조치]로 구성하세요.

주의사항:
- 자료에 없는 내용은 추정하지 마세요.
- 개인정보는 포함하지 마세요.
- 최종 판단이 필요한 항목은 "리더 판단 필요"라고 표시하세요.

[자료]
A지사: 민원 +34%, 장기요양 대기기간 불만 기사, 방문조사 일정 지연, 조사인력 결원 2명, 인정조사 평균 11.2일
B지사: 민원 +8%, 특이 언론 없음, 고령 민원인 내방 증가, 건강검진 수검률 61%
C지사: 민원 +27%, 온라인 커뮤니티 보험료 부과 불만 확산, 피부양자 자격 상담 급증, 부과 민원 420건
D지사: 민원 -3%, 특이 이슈 없음, 민원처리 안정, 처리기간 2.1일
E지사: 민원 +19%, 지방의회 자료요구 예정, 체납 안내문 반송 증가, 체납 고지 반송률 14%
F지사: 민원 +41%, 지역방송 취재 문의, 본인부담상한제 환급 문의 폭증, 환급 문의 680건
```

---

## [실습 1. 좋은 결과물의 모습]

<div class="columns">
<div>

### AI 결과에서 확인할 점

- 단순 민원 증가율 순서로만 정리했는가?
- 언론·지방의회·지역방송 이슈를 반영했는가?
- "오늘 회의 질문"이 실제 리더 질문처럼 구체적인가?
- 후속조치가 담당부서 행동으로 바뀔 수 있는가?

</div>
<div class="column">

### 추가 진행 사항

```bash
> 위 결과를 기준으로 지역본부장 회의용 1페이지 브리핑 문안을 작성하세요.
> 문장은 보고용 문체로 작성하고, 각 이슈마다 담당부서 확인사항을 1개씩 붙이세요.
> 단, 외부 공개가 곤란한 표현은 완곡하게 바꾸세요.
```

</div>
</div>

<br>
<div class="card">
<b>포인트</b><br>
한 번에 완성본 요구 대신, 1차 분류 → 2차 회의자료 → 3차 메시지 조정 순서 권장
</div>

---

## [실습1. 지역 현안 브리핑 AI 확장 구조]

<div style="width: 70%; margin: 10px auto">

![alt text](./nhis-images/ex1-flow.png)
</div>

---

<!-- _class: center -->

# 오늘의 핵심 실습 2.

## 지사 편차 분석 AI

| 비슷한 규모 지사끼리 처리기간, 민원 증가율, 직원 1인당 업무량, 징수 실적 차이 비교 분석

---

## [실습2. 데이터] 지사 편차 분석용 가상 지표

| 지사 | 가입자 규모 | 월 민원 | 민원 증가율 | 평균 처리기간 | 직원 수 | 직원 1인당 민원 | 징수율 | 건강검진 수검률 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| A | 21만 | 1,420 | 34% | 4.8일 | 42 | 33.8 | 96.1% | 63% |
| B | 20만 | 980 | 8% | 3.1일 | 39 | 25.1 | 97.4% | 61% |
| C | 22만 | 1,310 | 27% | 4.2일 | 41 | 32.0 | 95.8% | 66% |
| D | 19만 | 760 | -3% | 2.1일 | 38 | 20.0 | 98.0% | 72% |
| E | 21만 | 1,080 | 19% | 3.9일 | 37 | 29.2 | 94.9% | 68% |
| F | 23만 | 1,690 | 41% | 5.3일 | 43 | 39.3 | 96.5% | 59% |

<div class="tiny">
주의: 위 데이터는 교육용 가상 데이터입니다. 실제 지사 평가나 성과판단에 사용할 수 없습니다.
</div>

---

## [실습 2. 시각화 결과] 비슷한 규모 지사의 편차 보기

<div class="columns">
<div>

![alt text](nhis-images/ex2-1.png)

</div>
<div>

![alt text](nhis-images/ex2-2.png)

</div>
</div>

---

## [실습 2. 확장] 품질 높이는 추가 질문해보기

<div class="columns">
<div>

### 1차 결과가 나왔을 때

```text
위 분석을 지역본부장 보고용으로 바꾸세요.
표현은 특정 지사를 비난하지 않는 방식으로 조정하고,
"지원 필요 영역" 중심으로 작성하세요.
```

### 비교 기준을 더 엄격하게

```text
가입자 규모가 19만~23만인 지사만 같은 그룹으로 보고,
그룹 평균 대비 편차를 계산해 표로 보여주세요.
```

<br>
</div>
<div>

### 회의 질문 만들기

```text
분석 결과를 바탕으로 지사장 회의에서 사용할 질문 7개를 작성하세요.
질문은 추궁형이 아니라 원인 파악과 지원 방안 도출형으로 작성하세요.


```


### 실행계획 만들기

```text
위 결과를 바탕으로 2주 안에 실행할 수 있는 조치와 3개월 구조개선 과제를 구분해 주세요.


```

</div>
</div>

---

## [실습2. 지사 편차 분석 AI 확장 구조]

<div style="width: 85%; margin: 10px auto">

![alt text](nhis-images/ag.png)

</div>

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
| OpenAI API Docs, Computer use. |
| Anthropic, Introducing the Model Context Protocol. |
| https://openrouter.ai/rankings|
| 국민건강보험공단 홈페이지 및 공공기관 경영정보 공개자료. |
| 보건복지부, 사회보험징수통합 및 장기요양보험 관련 안내. |

<br> 

>본 강의자료의 실습 데이터는 교육용 가상 데이터입니다. 실제 민원, 개인 건강정보, 주민등록번호, 계좌정보, 내부 미공개 자료를 외부 AI 서비스에 입력하지 않습니다.
