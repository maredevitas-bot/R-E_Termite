# 연구 통합 계획 — Social Stomach → Distributed Computing → Physical AI

> 이 문서는 2026-09-14까지의 연구 방향 변화와 앞으로의 장기 계획을 하나의 구조로 통합한다. 기존의 `RESEARCH_DIRECTION.md`, `MODEL_GUIDED_RESEARCH.md`, `PAPERS.md`, `EXPERIMENTS.md`를 대체하기보다는 **현재 시점의 상위 연구 프레임과 로드맵**을 제시한다.

---

## 1. 현재 연구의 가장 큰 질문

초기의 질문은 **“흰개미는 제한된 자원을 누구에게 먼저 배분하는가?”**였으며, 이를 분산형 동적 우선순위 자원 할당 알고리즘으로 확장하려 했다.

현재는 이보다 더 큰 질문으로 확장한다.

> ## **중앙 통제자가 없는 흰개미 군체의 ‘사회적 위장(social stomach)’은 어떻게 개체 간 처리·물질전달·역할분담을 조직하여 군체 전체의 자원 항상성을 유지하는가?**

여기서 `priority allocation`은 최종 결론으로 미리 가정하지 않는다. 실제 데이터에서 나타날 수 있는 여러 메커니즘 중 하나로 둔다.

가능한 메커니즘 예:

- 특정 계급에 대한 우선순위 배분
- 공급 일개미의 기능적 전문화
- 반복적인 donor–recipient 관계
- 희소한 communication / logistics topology
- 확산적·분산적 자원 균등화
- 군체 상태 변화에 따른 네트워크 재구성

즉 연구의 상위 개념은 **분산 생리(distributed physiology)와 자원 항상성(resource homeostasis)**이다.

---

## 2. 연구 방향의 변화

### 초기 구조

```text
페로몬 유사물질을 이용한 생식분화 조절
+
AI 행동 분석
+
질소 고정·요산·질소 배분
```

각 요소는 의미가 있었지만 서로 독립적인 소주제처럼 보였고, 하나의 중심 질문과 최종 산출물이 약했다.

### 1차 재구성 — 사회적 물류망

```text
질소가 제한된 목질 환경
→ 계급별 서로 다른 자원 수요
→ trophallaxis
→ 군체 물류망
→ 생식위계와 선택적 자원 배분
```

흰개미 군체를 단순한 social network가 아니라 **social logistics network**로 보기 시작했다.

### 2차 재구성 — 실측 기반 우선순위 할당

실제 개체 행동을 장기간 추적하여 donor→recipient 관계를 복원하고, 검증된 규칙만 컴퓨팅으로 옮기는 **termite-derived algorithm** 방향을 설정했다.

### 3차 재구성 — Model-Guided Experimental Design

과학전람회처럼 실험 시간이 짧은 상황에서 생물 실험과 알고리즘 개발을 직렬로 놓는 것은 위험하다.

따라서:

```text
공개 행동 데이터 → V0 계산모형
                      ↓
              다음 실험 설계
                      ↓
우리 trophallaxis 데이터 → V1 실측 보정
                      ↓
              추가 실험·재보정
```

형태의 모델–실험 순환 구조로 변경했다.

### 현재 — 사회적 위장과 분산 생리

우선순위 배분보다 더 근본적인 질문은:

> **여러 개체가 서로 다른 국소적 역할을 수행하고 물질을 전달하면서 어떻게 군체 전체가 하나의 대사·물류 시스템처럼 작동하는가?**

이다.

이 관점은 분산·병렬 컴퓨팅뿐 아니라 **Physical AI / embodied multi-agent system**과도 자연스럽게 연결된다.

---

## 3. 왜 ‘사회적 위장’인가

흰개미에서 trophallaxis는 단순 접촉이 아니라 실제 물질전달 행동이다. 또한 일본흰개미에서는 왕과 여왕이 서로 다른 조성의 royal food를 공급받고, 생식개체의 요산·질소 이용이 번식과 연결된다는 선행연구가 존재한다.

따라서 다음 연결을 검토할 수 있다.

```text
개체의 국소 행동
      ↓
먹이·대사물질 전달
      ↓
기능적 역할 분담
      ↓
계급별 수요 충족
      ↓
군체 수준 자원 항상성
```

이때 ‘사회적 위장’은 이미 증명된 하나의 기관을 의미하는 표현이 아니라, **군체 전체의 물질 처리·전달을 하나의 분산 생리계로 분석하기 위한 연구 프레임**으로 사용한다.

---

## 4. 핵심 네트워크 세 층

### 4.1 Contact Network

> 누가 누구와 만나는가?

- 거리
- 접촉 빈도
- 접촉 지속시간
- 반복 파트너

### 4.2 Information Network

> 누구의 과거 행동이 누구의 미래 행동을 예측하는가?

- transfer entropy
- time lag
- directional influence

### 4.3 Logistics Network

> 실제로 누가 누구에게 물질을 전달하는가?

- trophallaxis event
- donor / recipient
- 방향
- 빈도
- 계급
- 시간

핵심 비교:

```text
Contact Network ?= Information Network ?= Logistics Network
```

이 세 네트워크가 같다고 가정하지 않는다. 차이를 밝히는 것 자체가 중요한 결과가 될 수 있다.

---

## 5. 현재 핵심 생물학 질문

### Q1. 실제 trophallaxis 물류망은 선택적인가?

- 모든 개체가 거의 균등하게 교환하는가?
- 특정 donor–recipient 관계가 반복되는가?
- 물류 허브나 중계 개체가 존재하는가?

### Q2. 기능적 전문화가 존재하는가?

- 특정 일개미가 왕 또는 여왕에게 반복적으로 공급하는가?
- 특정 개체가 전달·중계·공급에 상대적으로 전문화되는가?
- 개체 수준의 반복 역할이 군체 수준의 ‘기능적 모듈’을 만드는가?

### Q3. 사회적 접촉망은 물류망을 얼마나 예측하는가?

- 많이 만나는 개체가 실제로 많이 전달하는가?
- 접촉만으로 설명되지 않는 선택 필터가 있는가?

### Q4. 군체 상태가 바뀌면 물류망도 재편되는가?

- 계급 구성
- 생식상태
- 집단 규모
- 자원 조건

등이 달라질 때 같은 물류 구조가 유지되는지 검토한다.

### Q5. ‘priority allocation’은 실제로 존재하는가?

우선순위 배분은 전제가 아니라 검증 대상이다.

실제 데이터가 다음 중 어느 구조를 지지하는지 확인한다.

- priority-based allocation
- specialist-agent allocation
- diffusion / consensus-like allocation
- adaptive network switching
- 기타 예상하지 못한 규칙

---

## 6. AI의 역할

AI의 목적은 단순히 개체를 분류하거나 여왕을 찾는 것이 아니다.

> **수십~수백 개체의 장시간 행동으로부터 군체의 물질 물류망을 정량적으로 복원하는 측정기술**

로 사용한다.

```text
Video
 ↓
Detection
 ↓
Long-term individual tracking
 ↓
Trajectory / contact candidates
 ↓
Trophallaxis candidate detection
 ↓
Human validation
 ↓
Temporal logistics network
 ↓
Role / specialization / state analysis
```

중요 원칙:

- 사람이 일관되게 구분할 수 없는 행동을 AI 정답으로 만들지 않는다.
- 자동 검출 결과와 biological ground truth를 분리한다.
- AI의 confidence를 실제 자원량으로 해석하지 않는다.

---

## 7. 모델 유도형 연구설계

연구는 다음 순환을 반복한다.

```text
Observation
→ Model
→ Prediction
→ Experiment
→ Model Revision
→ Next Experiment
```

모델은 최종 산출물뿐 아니라 중간 연구도구로 사용한다.

### 모델이 실험을 개선하는 방법

- 중요한 변수 선별
- 필요한 fps와 촬영시간 결정
- 경쟁 가설의 예측이 가장 크게 갈리는 조건 선택
- 필요한 독립 군체 수·반복 수 추정
- rare trophallaxis event active learning
- 모델 residual에서 새로운 생물학적 가설 탐색

---

## 8. 계산모델 버전 계획

### V0 — Literature/Data-Constrained Interaction Model

기존 공개 데이터와 선행연구를 이용한다.

활용 후보:

- Paiva et al.: 이동·집단크기·preferential interaction
- Manduca et al.: caste interaction·transfer entropy·time lag
- royal food / uric acid 연구: 계급별 물질 수요·전달 차이의 생물학적 근거

V0에서 가능한 것:

- sparse/local interaction topology
- repeated-partner structure
- caste/state 후보 변수 선정
- simulator와 baseline 구축

V0에서 불가능한 것:

- 실제 trophallaxis priority를 확정
- contact를 food flow로 해석
- 다른 종의 수치를 *R. speratus*에 그대로 대입

### V0.5 — Pilot / Human-in-the-loop Model

소규모 자체 영상을 이용하여:

- tracking reliability
- 행동 라벨 기준
- trophallaxis 후보 검출
- 필요한 영상 해상도·fps

를 검증한다.

### V1 — Empirically Calibrated Logistics Model

자체 trophallaxis 데이터가 확보되면:

- donor→recipient probability
- repeated relationship
- specialization
- contact vs logistics mismatch
- colony/state effects

를 추정한다.

### V2 — Distributed Homeostatic Scheduler

여러 군체에서 반복되는 규칙만 추상화한다.

중요한 점은 V2를 처음부터 `priority scheduler`로 고정하지 않는 것이다.

실제 데이터가 지지하는 메커니즘에 따라:

- dynamic priority
- specialist agent
- sparse message passing
- distributed load balancing
- adaptive role reassignment

등이 핵심 요소가 될 수 있다.

### V3 — Physical AI / Embodied Multi-Agent Evaluation

V2의 국소 규칙을 몸을 가진 다중 에이전트 환경에서 평가한다.

초기에는 실제 로봇보다 simulator를 우선한다.

후보 상황:

- 제한된 sensing / communication range
- 물리적 이동 비용
- 자원 handoff
- heterogeneous task
- dynamic workload
- node/robot failure
- congestion

평가지표:

- throughput
- task completion time
- energy / movement cost
- communication cost
- workload imbalance
- robustness
- failure recovery time

---

## 9. 병렬·분산 컴퓨팅과의 연결

사회적 위장은 단순 자원배분보다 더 넓은 계산 문제와 대응될 수 있다.

| 흰개미 군체 | 병렬·분산 컴퓨팅 |
|---|---|
| 개체 | processing node / worker |
| 개체 내부의 먹이 처리 | local computation |
| trophallaxis | message / resource passing |
| 반복적 관계 | communication topology |
| 역할·계급 차이 | heterogeneous processor / workload |
| 특정 공급자 전문화 | task specialization |
| 군체 상태 변화 | dynamic workload |
| 물류망 재편 | dynamic scheduling / load balancing |
| 일부 기능 상실 | node failure |
| 역할 재배치 | fault recovery / task reassignment |

핵심 계산 질문:

> **전체 상태를 알지 못하는 여러 노드가 국소 정보와 제한된 통신만으로 어떻게 전체 시스템의 자원 수요를 안정적으로 충족하는가?**

---

## 10. Physical AI와의 연결

흰개미는 추상적 계산 노드가 아니라 실제 공간에서 움직이는 embodied agent이다.

따라서 자원 전달에는:

- 이동거리
- 에너지 비용
- 충돌·혼잡
- 공간적 접근성
- 제한된 sensing
- 제한된 communication
- 직접적인 physical handoff

가 포함된다.

이는 다음 문제와 직접 연결된다.

> **Embodied decentralized task/resource allocation**

장기적으로는 흰개미에서 도출한 국소 규칙을 multi-robot / Physical AI 환경에서 검증할 수 있다.

가능한 확장:

- warehouse robot handoff
- decentralized task allocation
- energy/resource sharing
- heterogeneous robot specialization
- robot failure 후 local role reassignment

단, Physical AI 연결은 실측 생물학적 규칙이 충분히 검증된 뒤 진행하며, 단순한 생체모방 비유에 그치지 않도록 한다.

---

## 11. 가장 중요한 실현가능성 위험

### Risk 1. trophallaxis를 영상에서 신뢰성 있게 판별할 수 있는가?

접촉·grooming 등과 구별 가능한 명확한 행동 정의와 수동 ground truth가 필요하다.

### Risk 2. 장기 ID tracking이 가능한가?

전문화와 반복관계를 분석하려면 동일 개체 ID가 장기간 유지되어야 한다.

### Risk 3. event 수와 실제 자원량은 다르다

초기 Logistics Network는 `물질전달 이벤트망`으로 정의한다. 전달량 자체를 측정했다고 주장하지 않는다.

### Risk 4. 기존 공개 데이터의 종 차이

Paiva·Manduca 데이터는 우리 대상 종과 동일하지 않거나 실험 구조가 다르므로 V0의 구조적 prior와 방법론으로만 사용한다.

### Risk 5. pseudoreplication

프레임·개체 수보다 독립 원군체 수를 중요한 biological replicate로 본다.

### Risk 6. 관찰 챔버가 행동을 왜곡할 수 있다

AI 친화적 2D 공간과 자연스러운 행동 환경의 trade-off를 검증한다.

### Risk 7. 모델 유도형 연구의 자기확증

모델 개발 데이터와 독립 검증 데이터를 분리하고, 모델이 예측한 현상을 같은 데이터로 다시 증명하지 않는다.

### Risk 8. 연구 범위가 지나치게 커질 수 있다

질소 고정·페로몬·대사체·행동·AI·Physical AI를 모두 동시에 주 실험으로 만들지 않는다.

---

## 12. Go / No-Go Gate

### Gate 1 — 행동 측정 가능성

- 사람이 trophallaxis를 일관되게 판정할 수 있는가?
- 영상 조건이 충분한가?

실패 시: 행동 정의·카메라·관찰구역 수정.

### Gate 2 — ID tracking

- 실험에 필요한 시간 동안 개체 ID를 안정적으로 유지할 수 있는가?

실패 시: 개체 수 축소·관찰구역 재설계·tracking 전략 수정.

### Gate 3 — 반복 가능한 물류 구조

- 특정 donor–recipient 관계 또는 역할 차이가 반복되는가?
- 독립 군체에서도 재현되는가?

실패 시: `specialization / priority` 가설을 버리고 stochastic/emergent logistics 모델로 전환.

### Gate 4 — V0와 실제 물류망의 관계

- contact / information features가 logistics를 얼마나 예측하는가?

예측 실패 자체도 새로운 선택 필터의 존재를 탐색하는 결과로 사용.

### Gate 5 — 계산적 일반화

- 실측 규칙이 기존 baseline 대비 특정 trade-off에서 의미 있는 성능을 보이는가?

실패 시: 알고리즘의 우월성을 주장하지 않고 생물학적 결과와 모델링 결과에 집중.

---

## 13. 앞으로의 단계별 계획

### Phase 0 — 공개 데이터·기존 연구 재현

목표:

- Paiva / Manduca 분석방법 재현
- trajectory→network pipeline 구축
- V0 simulator 구축
- random / fixed / local baseline 준비

산출물:

- 재현 notebook / script
- 데이터 스키마
- V0 interaction model

### Phase 1 — 측정 가능성 검증

목표:

- 작은 집단에서 영상 촬영
- manual trophallaxis label protocol 작성
- ID tracking 정확도 측정
- 필요한 fps / 해상도 / 촬영시간 결정

산출물:

- pilot dataset
- labeling guideline
- tracking benchmark

### Phase 2 — 기본 Logistics Network 복원

목표:

- worker 중심 trophallaxis network 구축
- contact vs logistics 비교
- repeated partner / hub / specialization 후보 탐색

산출물:

- Termite Logistics Dataset v1
- network visualization
- V0→V1 첫 보정

### Phase 3 — 사회적 위장 기능 분석

목표:

- 왕·여왕 포함 가능 시 royal provisioning 분석
- 공급 일개미 전문화 여부
- 기능적 모듈 / social organ 후보 탐색
- 독립 군체 반복

산출물:

- specialization model
- social stomach network map

### Phase 4 — 상태 변화와 항상성

목표:

- 가능한 범위에서 계급 구성·집단 규모·자원 조건 변화에 대한 물류망 변화 관찰
- 네트워크 재구성·회복성 분석

산출물:

- dynamic logistics model
- homeostatic response model

### Phase 5 — 분산 컴퓨팅 모델

목표:

- 실제 데이터에서 반복된 국소 규칙 추출
- Distributed Homeostatic Scheduler 구현
- baseline과 benchmark 비교

산출물:

- termite-derived distributed scheduler
- benchmark report

### Phase 6 — Physical AI 확장

목표:

- embodied multi-agent simulator 적용
- sensing·movement·handoff·failure를 포함한 환경에서 평가

산출물:

- Physical AI simulation
- decentralized multi-agent scheduling comparison

---

## 14. 단기 우선순위

현재 당장 우선할 작업은 다음과 같다.

1. **기존 공개 데이터 접근성과 재현 가능성 확인**
2. **trophallaxis 수동 판정 기준 작성**
3. **소수 개체 pilot 영상 확보 및 tracking 안정성 측정**
4. **Contact / Logistics 공통 데이터 스키마 확정**
5. **V0 simulator와 baseline 구축**
6. **관찰 챔버의 촬영성·행동왜곡·탈출방지 조건 검토**
7. **왕/여왕 확보 여부와 무관하게 worker-only 기본 연구가 성립하도록 설계**

---

## 15. 장기 산출물 구조

### Biological Output

**Termite Social Stomach / Logistics Dataset**

- 개체 ID
- 계급
- trajectory
- contact
- trophallaxis
- donor / recipient
- state
- temporal network

### Measurement Output

**Collective Logistics Network Analyzer**

- long-term tracking
- trophallaxis candidate detection
- human-in-the-loop validation
- contact / information / logistics network generation

### Scientific Output

**Social Stomach / Distributed Physiology Model**

- 역할분담
- 전문화
- 물류 topology
- 상태 변화
- 항상성

### Computing Output

**Termite-derived Distributed Homeostatic Scheduler**

- local sensing
- limited communication
- dynamic resource scheduling
- fault recovery

### Physical AI Output

**Embodied Multi-Agent Resource Homeostasis Simulation**

- movement
- handoff
- congestion
- energy
- decentralized task reassignment

---

## 16. 현재 연구의 한 문장

> **“흰개미는 누구에게 먼저 밥을 줄까?”에서 출발해, 실제 군체의 사회적 위장이 어떻게 국소적 처리·물질전달·역할분담만으로 전체 자원 항상성을 만드는지 AI로 측정하고, 그 실측 규칙을 분산 컴퓨팅과 Physical AI의 자원 스케줄링 원리로 확장한다.**

---

## 17. 연구 원칙

1. `priority allocation`을 미리 결론으로 정하지 않는다.
2. contact, information, logistics network를 구분한다.
3. 공개 데이터는 V0의 구조적 prior로 사용하고 자체 종의 실제 물류 데이터로 검증한다.
4. 모델은 실험을 대신하지 않고 다음 실험을 더 정확하게 만드는 도구로 사용한다.
5. 모델 개발 데이터와 독립 검증 데이터를 가능한 한 분리한다.
6. 프레임 수보다 독립 군체 반복을 중요하게 본다.
7. 알고리즘이 기존 방식보다 반드시 우월할 것이라고 가정하지 않는다.
8. 실제 데이터가 지지하는 trade-off와 계산 문제를 선택한다.
9. Physical AI 연결은 실측 규칙을 기반으로 하며 단순 생체모방 비유에 그치지 않는다.
10. 어느 단계에서 멈추더라도 독립적인 생물학·측정·계산 결과가 남도록 연구를 설계한다.
