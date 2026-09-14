# R-E_Termite

## AI로 읽는 흰개미의 사회적 위장과 분산 자원 항상성

이 저장소는 **일본흰개미(*Reticulitermes speratus*)의 trophallaxis 기반 물질전달망을 장기간 정량화하고, 여러 개체의 국소 행동이 어떻게 군체 전체의 자원 항상성을 만드는지 분석한 뒤 그 실측 규칙을 분산 컴퓨팅과 Physical AI로 확장하는 R&E 프로젝트**를 기록한다.

### 현재 핵심 질문

> **중앙 통제자가 없는 흰개미 군체의 ‘사회적 위장(social stomach)’은 어떻게 개체 간 처리·물질전달·역할분담을 조직하여 군체 전체의 자원 항상성을 유지하는가?**

```text
질소가 제한된 목질 환경
        ↓
계급별 서로 다른 자원 수요
        ↓
trophallaxis 기반 물질 전달
        ↓
Contact / Information / Logistics Network
        ↓
역할분담 · 전문화 · 선택적 배분 · 네트워크 재구성
        ↓
군체 수준의 분산 자원 항상성
        ↓
분산·병렬 컴퓨팅 스케줄러
        ↓
Physical AI / embodied multi-agent system
```

---

## 현재 연구 방향

연구의 중심은 흰개미 행동을 단순 모방하는 것이 아니라 **실제 군체의 분산 생리(distributed physiology)를 측정하고 규칙을 추출하는 것**이다.

1. 실제 개체를 장시간 추적한다.
2. 접촉망과 실제 trophallaxis 물류망을 구분해 복원한다.
3. 반복 donor–recipient 관계와 기능적 전문화가 존재하는지 검증한다.
4. 왕·여왕·집단규모·군체상태에 따라 물류망이 어떻게 달라지는지 분석한다.
5. `priority allocation`을 미리 가정하지 않고 실제 데이터가 지지하는 배분 메커니즘을 찾는다.
6. 공개 데이터 기반 V0 모델과 자체 실험을 반복 결합하는 **Model-Guided Experimental Design**을 사용한다.
7. 여러 군체에서 검증된 국소 규칙만 분산 컴퓨팅 및 Physical AI로 일반화한다.

핵심 차별점은 기존의 단순 `termite-inspired` 방식보다 **실제 행동·물류 데이터에서 규칙을 도출하는 empirically derived / termite-derived 접근**을 지향한다는 것이다.

---

## 모델 유도형 연구 구조

```text
[컴퓨팅 트랙]
공개 행동 데이터
→ V0 Literature/Data-Constrained Model
→ simulator / baseline

                +

[생물 트랙]
자체 영상
→ tracking
→ trophallaxis
→ 실제 Logistics Network

                ↓

V1 Empirically Calibrated Logistics Model
→ 다음 실험 설계
→ 추가 데이터·독립 검증
→ Distributed Homeostatic Scheduler
→ Physical AI simulation
```

알고리즘은 최종 산출물일 뿐 아니라 **변수 선정, 촬영조건 최적화, 경쟁 가설 구분, 표본설계, rare-event 탐색을 돕는 중간 연구도구**로 사용한다.

---

## Repository 구조

```text
R-E_Termite/
│
├─ README.md
│   └─ 프로젝트 홈과 현재 핵심 방향
│
├─ docs/
│   ├─ MASTER_PLAN.md
│   │   └─ 현재 상위 프레임, 장기 로드맵, Physical AI 확장
│   ├─ RESEARCH_LOG.md
│   │   └─ 날짜별 탐구 과정·의사결정 기록
│   ├─ RESEARCH_DIRECTION.md
│   │   └─ 사회적 물류망·우선순위 할당 중심의 상세 연구 기둥
│   ├─ MODEL_GUIDED_RESEARCH.md
│   │   └─ V0→V1→V2 모델-실험 반복 방법론
│   ├─ PAPERS.md
│   │   └─ 핵심 논문별 결과·한계·연구 연결
│   └─ EXPERIMENTS.md
│       └─ 실험 설계, 단계별 계획, 수행 기록
│
├─ analysis/
│   └─ tracking · behavior · network · modeling · optimization
│
└─ hardware/
    └─ 관찰 챔버 · Raspberry Pi · 카메라 · 센서
```

---

## 문서 바로가기

- **[통합 연구계획](docs/MASTER_PLAN.md)** — 사회적 위장 → 분산 컴퓨팅 → Physical AI 전체 로드맵
- **[현재 연구 방향](docs/RESEARCH_DIRECTION.md)** — 기존 물류망·생식위계·우선순위 할당 상세 논리
- **[모델 유도형 연구설계](docs/MODEL_GUIDED_RESEARCH.md)** — 공개 데이터 V0 → 자체 실측 V1 → 계산모형 반복 구조
- **[연구 기록](docs/RESEARCH_LOG.md)** — 아이디어 변화와 주요 의사결정
- **[논문 정리](docs/PAPERS.md)** — Paiva, Manduca, royal food, uric acid, nitrogen fixation 등
- **[실험 설계](docs/EXPERIMENTS.md)** — Phase별 실험 계획과 기록
- **[분석 코드 계획](analysis/README.md)** — tracking, network, modeling, optimization
- **[하드웨어 계획](hardware/README.md)** — 모듈형 관찰 챔버 및 촬영 시스템

---

## 장기 산출물 목표

### 1. Termite Social Stomach / Logistics Dataset
개체 ID, 계급, 궤적, 접촉관계, trophallaxis 방향·빈도·시간을 포함한 실측 데이터.

### 2. Collective Logistics Network Analyzer
영상에서 개체를 추적하고 Contact / Information / Logistics Network를 생성하는 분석 플랫폼.

### 3. Social Stomach / Distributed Physiology Model
역할분담, 전문화, 선택적 배분, 물류 topology, 상태 변화와 항상성을 설명하는 실측 기반 모델.

### 4. Termite-derived Distributed Homeostatic Scheduler
실제 흰개미에서 반복 확인된 국소 규칙을 이용한 분산형 자원 스케줄링 모델.

### 5. Physical AI / Embodied Multi-Agent Simulation
이동비용, 제한된 sensing·communication, physical handoff, workload 변화와 node failure를 포함한 환경에서 흰개미 유래 규칙을 평가한다.

### 6. Modular Termite Observation Chamber
장기 ID tracking과 trophallaxis 분석을 위한 관찰 시스템.

---

## 현재 대표 연구 질문

- 흰개미의 trophallaxis 물류망은 균등한가, 선택적인가?
- 접촉망과 실제 물질전달망은 얼마나 다른가?
- 왕·여왕에게 먹이를 공급하는 일개미는 전문화되어 있는가?
- 군체 안에 반복적인 역할분담으로 형성되는 기능적 ‘사회적 장기’가 존재하는가?
- 군체 상태와 자원 수요가 달라지면 물류망은 재구성되는가?
- 우선순위 배분은 실제 메커니즘인가, 여러 가능한 메커니즘 중 하나인가?
- 국소적인 sensing과 interaction만으로 군체 수준의 resource homeostasis가 가능한가?
- 그 규칙은 분산 컴퓨팅 및 embodied multi-agent system에서도 유용한가?

---

## 발표용 한 문장

> **“흰개미는 누구에게 먼저 밥을 줄까?”에서 출발해, 군체의 ‘사회적 위장’이 어떻게 국소적 처리와 물질전달만으로 전체 자원 항상성을 만드는지 AI로 측정하고, 그 실측 규칙을 분산 컴퓨팅과 Physical AI로 확장한다.**
