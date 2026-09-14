# R&E Termite 연구 기록

이 파일은 `README.md`와 분리하여 **연구 방향의 변화, 회의 내용, 가설 수정, 실험 아이디어, 논문 검토 결과**를 누적 기록하기 위한 문서입니다.

## 사용 원칙

- `README.md`: 저장소의 짧은 소개와 현재 연구 목표
- `docs/MASTER_PLAN.md`: 현재 상위 연구 프레임과 장기 로드맵
- `docs/RESEARCH_LOG.md`: 날짜별 탐구 과정과 의사결정 기록
- `docs/RESEARCH_DIRECTION.md`: 사회적 물류망·생식위계·우선순위 할당 중심의 상세 연구 방향
- `docs/MODEL_GUIDED_RESEARCH.md`: 공개 데이터 → 계산모형 → 실험설계 → 실측 보정의 반복 구조
- `docs/SHORTEST_PATH_PLAN.md`: 첫 완결 연구 루프를 가장 빠르게 만드는 최단경로 계획
- `docs/PAPERS.md`: 주요 논문별 핵심 내용과 우리 연구와의 연결
- `docs/EXPERIMENTS.md`: 실험 설계 및 수행 기록
- `analysis/`: AI 추적·네트워크·모델링·최적화 코드
- `hardware/`: 관찰 챔버·카메라·센서 설계

---

## 현재 핵심 방향

> **흰개미 군체의 trophallaxis 기반 물질전달을 ‘사회적 위장(social stomach)’이라는 분산 생리계로 보고, 여러 개체의 국소 행동·처리·역할분담이 군체 전체의 자원 항상성을 어떻게 만드는지 AI로 정량화한 뒤 실제로 검증된 규칙을 분산 컴퓨팅과 Physical AI로 확장한다.**

### 핵심 연결

```text
질소가 제한된 목질 환경
→ 계급별 자원 수요 차이
→ trophallaxis 기반 물질 전달
→ Contact / Information / Logistics Network
→ 역할분담 · 전문화 · 선택적 배분 · 네트워크 재구성
→ 군체 수준의 resource homeostasis
→ Distributed Homeostatic Scheduler
→ Physical AI / embodied multi-agent system
```

`priority allocation`은 더 이상 최종 결론으로 미리 가정하지 않고, 실제 데이터가 지지할 수 있는 여러 배분 메커니즘 중 하나로 둔다.

---

## 기록

### 2026-09-14 — 최단경로 연구계획 추가

- 연구기간을 줄이기 위해 `군체 확보 → 촬영 → 추적 → 행동검출 → 모델링 → 알고리즘`을 순차적으로 기다리는 구조를 피하기로 함.
- **공개 데이터 기반 V0 계산모형**, **소규모 자체 흰개미 파일럿**, **tracking/contact/trophallaxis 데이터 파이프라인**을 병렬 진행하도록 계획.
- 초기 최소 완성선을 `Contact Network + 실제 trophallaxis Logistics Network + V0 예측 비교`로 설정.
- 첫 통합 질문을 **“사회적 접촉망만으로 실제 trophallaxis 물류망을 얼마나 예측할 수 있는가?”**로 둠.
- 초기에는 왕·여왕, 질소 직접 분석, 생식위계 변화, 완전 자동 AI, 복잡한 GNN/강화학습, 실제 Physical AI 로봇 구현을 필수 경로에서 제외.
- AI는 처음부터 완전자동 행동 판별기로 만들기보다 `근접/상호작용 후보 추출 → 짧은 영상 클립 → 사람 검증`의 Human-in-the-Loop 방식으로 사용.
- 첫 파일럿 Go/No-Go 기준을 다음 세 가지로 설정:
  1. 개체 ID를 필요한 시간 동안 유지할 수 있는가?
  2. 영상에서 trophallaxis를 사람이 일관되게 판별할 수 있는가?
  3. 분석 가능한 빈도로 trophallaxis event가 발생하는가?
- 촬영은 `30분 → 2시간 → 반나절 → 장기 촬영` 식으로 단계적으로 확대하고, 각 단계에서 문제를 즉시 수정하기로 함.
- 8주 기준 예시 계획을 작성하되 절대적인 기간이 아니라 **첫 Observation → Model → Prediction → Experiment → Revision 루프를 최대한 빨리 완성하는 순서**로 사용.
- 세부 계획을 `docs/SHORTEST_PATH_PLAN.md`에 별도 기록.

### 2026-09-14 — 상위 프레임을 ‘사회적 위장·분산 생리’로 확장

- 기존 `분산형 동적 우선순위 할당` 방향은 흰개미 사회의 기능 중 **자원을 누구에게 먼저 줄 것인가**에 초점이 맞춰져 있었음.
- 그러나 trophallaxis 기반 물질전달은 단순 배분뿐 아니라 **개체별 처리, 역할분담, 중계, 제한된 communication topology, 상태 변화에 따른 재구성**을 포함할 가능성이 있다고 판단.
- 이에 따라 상위 연구 질문을 **“중앙 통제자가 없는 흰개미의 사회적 위장은 어떻게 군체 전체의 자원 항상성을 유지하는가?”**로 확장.
- `priority allocation`은 검증 대상인 하위 메커니즘으로 이동.
- 실제 데이터가 priority 외에 specialist-agent, diffusion/consensus, adaptive network switching 등의 구조를 지지할 가능성도 열어둠.
- 이 방향은 현대 병렬·분산 컴퓨팅의 다음 문제와 직접 연결될 수 있다고 판단:
  - local processing
  - message/resource passing
  - heterogeneous task specialization
  - sparse communication topology
  - dynamic scheduling / load balancing
  - fault tolerance / role reassignment
- 흰개미가 실제 공간에서 움직이고 직접 자원을 전달하는 embodied agent라는 점에서 **Physical AI / multi-agent robotics**로의 확장도 설정.
- 장기 계산 산출물을 특정 `priority algorithm` 하나로 고정하지 않고 **Termite-derived Distributed Homeostatic Scheduler**로 넓힘.
- 추가 장기 단계로 이동비용·제한된 sensing/communication·physical handoff·node failure가 포함된 **Physical AI simulation**을 계획.
- 전체 현재 방향과 향후 Phase 0~6 계획, Go/No-Go Gate, 실현가능성 위험을 `docs/MASTER_PLAN.md`에 통합 기록.

### 2026-09-14 — 모델 유도형 실험설계 방향 추가

- 과학전람회처럼 실험 시간이 짧은 상황에서 `생물 실험 완료 → 규칙 발견 → 알고리즘 개발`의 직렬 구조는 리스크가 크다고 판단.
- 기존 공개 흰개미 행동 데이터(Paiva, Manduca 등)로 **V0 계산모형**을 먼저 구축하고, 자체 trophallaxis 데이터가 들어올 때마다 모델을 보정하는 병렬 구조로 변경.
- V0는 실제 물류 알고리즘이 아니라 **Literature/Data-Constrained Termite Model**로 명확히 구분.
- 자체 먹이전달 데이터가 확보되면 **V1: Empirically Calibrated Termite Logistics Model**로 보정.
- 여러 군체에서 반복적으로 확인된 규칙만 일반화하여 계산모형으로 확장하기로 함.
- 알고리즘을 단순 최종 산출물이 아니라 **연구 정확도를 높이는 중간 도구**로 사용하기로 함.
- 모델을 이용해 다음을 수행할 계획:
  - 중요한 측정 변수 선별
  - 필요한 fps·촬영시간 등 촬영조건 최적화
  - 경쟁 가설이 가장 크게 갈리는 실험조건 선택
  - 필요한 독립 군체·반복 수 추정
  - 희귀 trophallaxis event를 우선 선별하는 active learning
  - 모델 residual을 이용한 새로운 생물학적 질문 탐색
- 전체 방법론을 **Model-Guided Experimental Design**으로 정리하고 `docs/MODEL_GUIDED_RESEARCH.md`에 별도 문서화함.

### 2026-09-14 — 저장소 구조 재정리

- 긴 연구 정리문을 `README.md` 하나에 모두 넣는 방식에서 분리형 구조로 변경.
- `README.md`는 프로젝트 홈과 핵심 질문만 남김.
- `docs/RESEARCH_DIRECTION.md`: 현재 연구 방향과 전체 논리.
- `docs/PAPERS.md`: 핵심 선행연구의 결과·한계·연결.
- `docs/EXPERIMENTS.md`: Phase 0~5 실험 계획.
- `analysis/README.md`: AI/네트워크/최적화 분석 공간.
- `hardware/README.md`: 관찰 챔버와 촬영 시스템 개발 공간.
- 연구 기록은 앞으로 날짜별로 이 문서에 누적하기로 함.

### 2026-09 — 연구 방향 재정립

- 초기의 `페로몬 유사물질 + AI + 질소` 병렬 구조는 각 파트의 연결성과 최종 산출물이 약하다고 판단.
- 베이트 방제, 군체 파편화, 기계 신호 제어 등 여러 응용 방향을 검토했으나 실용성 연결에 불확실성이 큼.
- 흰개미 군체를 **사회적 물류망(social logistics network)** 으로 보는 관점으로 전환.
- 먹이전달(trophallaxis)을 대표 행동으로 설정.
- Paiva et al.의 preferential interaction과 Manduca et al.의 transfer entropy 분석을 군체 물류망 분석의 방법론적 기반으로 검토.
- 일본흰개미의 왕·여왕 특이적 royal food와 요산/질소 이용 연구를 통해 `사회관계–자원배분–생식위계`의 연결 가능성을 확인.
- 당시에는 실제 흰개미 물류 데이터를 기반으로 **분산형 동적 우선순위 자원 할당 알고리즘**을 도출하는 방향을 가장 유력한 산출물로 설정했으나, 이후 이를 더 큰 `사회적 위장·자원 항상성` 프레임의 하위 메커니즘으로 확장함.

### 다음 기록 항목

- 최단경로 Track A/B/C 실제 시작일과 진행 상태
- 첫 30분 / 2시간 pilot 결과
- Paiva / Manduca 공개 데이터 접근 및 재현 가능성
- V0 interaction model과 baseline simulator 구축
- trophallaxis 수동 판정 기준 및 라벨링 일치도
- 소수 개체 pilot의 장기 ID tracking 정확도
- 관찰 챔버의 행동왜곡·촬영성·탈출방지 검토
- Contact / Logistics 공통 데이터 스키마
- worker-only 기본 물류망 실험
- 왕/여왕 확보 시 provisioning specialization 분석
- 독립 군체 반복 및 V0 → V1 검증 데이터 분리
- 실제 데이터가 지지하는 resource homeostasis 메커니즘 결정
- Distributed Homeostatic Scheduler benchmark 설계
- Physical AI simulator 후보 선정
