# R-E_Termite

## AI로 읽는 흰개미 군체의 자원 물류망

이 저장소는 **일본흰개미(*Reticulitermes speratus*)의 먹이전달(trophallaxis)과 생식위계에 따른 자원 배분 규칙을 실제 행동 데이터로 분석하고, 이를 실측 기반 분산 자원 할당 알고리즘으로 확장하는 R&E 프로젝트**를 기록한다.

### 핵심 질문

> **흰개미는 제한된 자원을 누구에게 먼저 배분하며, 그 우선순위는 군체 상태와 생식위계에 따라 어떻게 달라지는가?**

```text
질소가 부족한 목질 자원
        ↓
계급별 서로 다른 자원 수요
        ↓
trophallaxis 기반 자원 전달
        ↓
동적 군체 물류망
        ↓
AI로 실제 배분 규칙 추출
        ↓
분산형 동적 우선순위 자원 할당 알고리즘
```

---

## 현재 연구 방향

연구의 중심은 흰개미를 단순히 관찰하거나 기존 행동을 모방하는 데 있지 않다.

1. **실제 흰개미 개체를 장시간 추적**하고
2. **누가 누구에게 먹이를 전달하는지 물류망을 복원**하며
3. **왕·여왕과 다른 계급에 대한 자원 배분이 선택적인지 검증**하고
4. **생식위계 변화에 따라 물류 우선순위가 재편되는지 분석**한 뒤
5. 확인된 규칙만 이용해 **분산형 동적 우선순위 할당 알고리즘**으로 확장한다.

핵심 차별점은 기존의 단순 `termite-inspired` 알고리즘보다 **실제 행동 데이터에서 규칙을 도출하는 empirically derived / termite-derived 접근**을 지향한다는 것이다.

### 연구 방법론

생물 실험이 모두 끝난 뒤 계산을 시작하는 직렬 구조 대신, **Model-Guided Experimental Design**을 사용한다.

```text
기존 공개 데이터 → V0 계산모형
                      ↓
              다음 실험 설계
                      ↓
우리 trophallaxis 데이터 → V1 실측 보정
                      ↓
              추가 실험·재보정
                      ↓
      V2 분산 우선순위 할당 알고리즘
```

즉 알고리즘은 최종 응용일 뿐 아니라, **중요 변수 선정·촬영조건 조정·경쟁 가설 구분·희귀 행동 탐색 등 연구 정확도를 높이는 중간 도구**로도 사용한다.

---

## Repository 구조

```text
R-E_Termite/
│
├─ README.md
│   └─ 프로젝트 개요와 현재 핵심 방향
│
├─ docs/
│   ├─ RESEARCH_LOG.md
│   │   └─ 날짜별 탐구 과정·의사결정 기록
│   ├─ RESEARCH_DIRECTION.md
│   │   └─ 현재 연구 기둥과 최종 산출물 방향
│   ├─ MODEL_GUIDED_RESEARCH.md
│   │   └─ V0→V1→V2 모델-실험 반복 구조
│   ├─ PAPERS.md
│   │   └─ 핵심 논문별 결과·한계·우리 연구와의 연결
│   └─ EXPERIMENTS.md
│       └─ 실험 설계, 단계별 계획, 수행 기록
│
├─ analysis/
│   └─ AI tracking · network analysis · optimization 코드
│
└─ hardware/
    └─ 관찰 챔버 · Raspberry Pi · 카메라 시스템
```

---

## 문서 바로가기

- **[현재 연구 방향](docs/RESEARCH_DIRECTION.md)** — 연구의 전체 논리와 산출물
- **[모델 유도형 연구설계](docs/MODEL_GUIDED_RESEARCH.md)** — 공개 데이터 V0 → 실측 V1 → 일반화 V2 구조
- **[연구 기록](docs/RESEARCH_LOG.md)** — 아이디어 변화와 회의 기록
- **[논문 정리](docs/PAPERS.md)** — Paiva, Manduca, royal food, uric acid, nitrogen fixation 등
- **[실험 설계](docs/EXPERIMENTS.md)** — Phase 0~5 실험 계획과 기록
- **[분석 코드 계획](analysis/README.md)** — tracking, network, optimization
- **[하드웨어 계획](hardware/README.md)** — 모듈형 관찰 챔버 및 촬영 시스템

---

## 최종 산출물 목표

### 1. Termite Logistics Dataset
개체 ID, 계급, 궤적, 접촉관계, trophallaxis 방향과 빈도를 포함한 실측 데이터.

### 2. Collective Logistics Network Analyzer
영상에서 개체를 추적하고 Contact / Information / Logistics Network를 생성하는 분석 플랫폼.

### 3. Termite-derived Dynamic Priority Allocation Algorithm
실제 흰개미 자원 배분 규칙에서 도출한 분산형 동적 우선순위 할당 알고리즘.

### 4. Modular Termite Observation Chamber
장기 ID tracking과 먹이전달 분석에 최적화된 실험용 관찰 챔버.

---

## 현재 대표 연구 질문

- 흰개미의 먹이전달망은 균등한가, 선택적인가?
- 왕·여왕에게 먹이를 공급하는 일개미는 전문화되어 있는가?
- 많이 접촉하는 개체와 실제 물류 허브는 같은가?
- 생식위계가 달라지면 자원 배분 우선순위도 바뀌는가?
- 사회적 행동망만으로 실제 물류망을 얼마나 예측할 수 있는가?
- 실제 흰개미에서 확인된 국소 자원배분 규칙은 일반적인 분산 컴퓨팅 문제에서도 유용한가?

---

## 발표용 한 문장

> **“흰개미는 누구에게 먼저 밥을 줄까? 실제 군체의 자원 물류망을 AI로 측정하고, 공개 데이터와 자체 실험을 반복적으로 결합해 그 규칙을 분산형 자원 할당 알고리즘으로 발전시킨다.”**
