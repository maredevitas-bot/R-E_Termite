# 모델 유도형 연구설계 (Model-Guided Experimental Design)

> 이 문서는 **공개 흰개미 행동 데이터로 1차 계산모형을 먼저 구축하고, 우리 실험에서 얻는 실제 trophallaxis 물류망 데이터로 그 모형을 반복 보정하면서 다음 실험을 설계하는 연구 방식**을 정리한다.

---

## 1. 왜 이 구조가 필요한가

과학전람회 등은 실험 가능 시간이 짧기 때문에 다음과 같은 직렬 구조는 위험하다.

```text
사육 안정화
→ 장기 개체추적
→ trophallaxis 검출
→ 물류 규칙 발견
→ 수학적 모델링
→ 알고리즘 개발
→ benchmark 비교
```

앞 단계가 늦어지면 뒤의 계산 산출물이 모두 밀린다.

따라서 생물 실험과 컴퓨팅을 **병렬 진행**한다.

```text
[컴퓨팅 트랙]
기존 공개 데이터
→ V0 계산모형
→ simulator / baseline 구축

                +

[생물 트랙]
우리 실험
→ 개체추적
→ trophallaxis
→ 실제 물류망

                ↓

V1 실측 보정 물류모형
→ 다음 실험 설계
→ 추가 데이터
→ 모델 재보정
```

---

## 2. 핵심 방법론

전체 연구를 일방향이 아니라 다음 순환 구조로 진행한다.

```text
Observation
→ Model
→ Prediction
→ Experiment
→ Model Revision
→ 다음 Prediction
```

즉 알고리즘은 마지막에 붙이는 응용물이 아니라,

> **연구 중간단계에서 어떤 변수를 더 정확하게 측정해야 하는지, 어떤 경쟁 가설을 구분해야 하는지, 어떤 조건을 다음 실험에서 우선 검증해야 하는지를 결정하는 도구**

로 사용한다.

---

## 3. V0 — 공개 데이터 기반 1차 모델

### 목표

자체 trophallaxis 데이터가 충분하지 않은 초기 단계에서, 기존 실제 흰개미 행동 데이터와 문헌을 이용해 **행동 네트워크 기반 자원배분 가설 모델**을 만든다.

### 활용 가능한 선행 데이터

#### Paiva et al. (2021)
- 집단 크기와 밀도 변화
- 개체 이동 궤적
- 반복적 사회 접촉
- preferential interaction
- 희소한 선택적 연결 구조

이 데이터로 다음을 추정할 수 있다.

- 접촉 가능성
- 반복 파트너 구조
- 집단 규모에 따른 network sparsity
- interaction persistence

#### Manduca et al. (2025)
- worker–worker / soldier–soldier / mixed interaction
- 위치·속도 시계열
- transfer entropy
- interaction time lag

이 데이터로 다음을 검토할 수 있다.

- 계급 조합별 상호작용 차이
- 방향성 있는 행동 영향
- 중요한 시간척도

#### Royal food / uric acid 연구
- 왕과 여왕이 서로 다른 royal food를 공급받음
- 수혜 생식계급에 따른 discriminative trophallaxis 존재
- 생식개체의 질소·요산 이용이 번식과 연결됨

단, 이 문헌 결과를 **실제 개체별 자원 우선순위 값으로 간주하지 않는다.**

---

## 4. V0에서 할 수 있는 것과 할 수 없는 것

### 할 수 있는 것

- 실제 흰개미의 사회망 구조를 반영한 가설모델 구축
- 완전연결망 대신 희소한 local interaction 모델 구축
- 계급·반복상호작용·시간척도 등 후보 변수 선정
- simulator와 baseline 알고리즘 사전 구축
- 어떤 데이터가 실제 자원배분 모델에 가장 필요한지 판단

### 아직 할 수 없는 것

- V0를 ‘실제 흰개미 물류 알고리즘’이라고 부르기
- contact network를 실제 food logistics network로 동일시하기
- transfer entropy를 먹이 흐름으로 해석하기
- 왕/여왕의 실제 자원 우선순위를 수치로 확정하기

따라서 V0는 다음처럼 부른다.

> **Literature/Data-Constrained Termite Model**

---

## 5. 자체 데이터가 들어오면 V1으로 보정

우리 실험에서 실제 trophallaxis 데이터가 확보되면 다음을 추정한다.

\[
P(i\rightarrow j \mid
\text{caste},
\text{past interaction},
\text{recipient state},
\text{colony state})
\]

즉,

> **어떤 공급자가 어떤 수혜자에게 실제 자원을 전달할 확률이 어떤 변수에 의해 설명되는가?**

를 추정한다.

V1에서는 특히 다음을 비교한다.

- 단순 접촉 빈도만으로 trophallaxis가 예측되는가?
- 반복 상호작용을 추가하면 얼마나 개선되는가?
- 계급 정보를 추가하면 얼마나 개선되는가?
- 왕/여왕 주변 위치만으로 설명되는가?
- 실제 물류망에는 contact network에 없는 선택성이 존재하는가?

V1은 다음처럼 정의한다.

> **Empirically Calibrated Termite Logistics Model**

---

## 6. V0 → V1 비교 자체가 연구 결과가 된다

중요한 통합 질문:

> ## **“사회적 행동 네트워크만으로 실제 자원 물류를 얼마나 예측할 수 있는가?”**

### V0

```text
movement
+ contact
+ repeated interaction
+ caste
+ information-flow features
        ↓
resource-transfer prediction
```

### V1

```text
V0 features
+ actual trophallaxis data
        ↓
improved logistics model
```

따라서 다음을 정량적으로 비교할 수 있다.

- prediction accuracy
- log-loss / likelihood
- calibration
- ranking accuracy
- network reconstruction accuracy

만약 V0와 실제 물류망의 차이가 크다면 그것도 실패가 아니다.

> **“접촉망과 실제 물류망 사이에 추가적인 선택 규칙이 존재한다.”**

라는 생물학적 발견 후보가 된다.

---

## 7. 모델을 이용해 실험 정확도를 높이는 방법

### 7.1 변수 선택

초기 후보 변수 예:

- 개체 간 거리
- 접촉시간
- 반복 접촉
- 이동속도
- trophallaxis 횟수
- caste
- king/queen distance
- group size
- transfer entropy
- network centrality

모델 sensitivity / feature importance를 통해

> **어떤 변수를 다음 실험에서 더 정밀하게 측정해야 하는가?**

를 결정한다.

---

### 7.2 촬영 조건 최적화

파일럿 영상에서 중요한 행동 시간척도를 분석하여

- 필요한 fps
- 실험당 촬영시간
- 저장 주기
- ROI

를 결정한다.

예를 들어 interaction time lag가 매우 짧다면 높은 temporal resolution이 필요하고, 장시간 관계 지속성이 더 중요하다면 낮은 fps의 장기촬영이 더 유리할 수 있다.

---

### 7.3 경쟁 가설을 구분하는 실험 설계

예: Worker A가 Queen에게 trophallaxis를 많이 보였다고 하자.

가능한 설명:

1. A가 queen provisioning에 전문화됨
2. A가 단순히 여왕 주변에 오래 머묾
3. A가 원래 모든 개체에게 먹이를 많이 줌
4. A가 먹이원과 가까움

이를 각각 모델 \(M_1, M_2, M_3, M_4\)로 만들어,

> **모델 예측이 가장 크게 갈리는 조건을 다음 실험으로 선택**한다.

즉 데이터를 무작정 많이 모으는 것이 아니라 **가설을 가장 잘 구분하는 실험**을 우선한다.

---

### 7.4 샘플 수와 반복 설계

파일럿 데이터에서 관찰된 효과크기와 변동성을 이용해 시뮬레이션하고,

- 독립 군체 수
- 개체 수
- 관찰 시간
- 반복 횟수

가 증가할 때 불확실성이 어떻게 줄어드는지 평가한다.

목표는 단순히 ‘최대한 많이 촬영’이 아니라 **필요한 biological replicate를 확보하는 것**이다.

---

### 7.5 희귀 trophallaxis event 탐색

장시간 영상 전체를 사람이 확인하는 대신,

```text
V0 detector
→ trophallaxis 가능성이 높은 짧은 구간 선별
→ 사람이 검증
→ 새 label 추가
→ 모델 재학습
```

하는 **active learning / human-in-the-loop** 구조를 사용한다.

이 과정으로 라벨링 시간을 크게 줄이면서 실제 데이터셋을 확장한다.

---

## 8. 모델 오차를 새로운 생물학적 질문으로 사용

핵심 아이디어:

\[
Residual = Observed - Predicted
\]

모델이 반복적으로 틀리는 조건은 단순 오류가 아니라

> **기존 행동 네트워크 설명으로 포착되지 않는 생물학적 선택 규칙**

일 수 있다.

예:

```text
접촉은 매우 많음
하지만 trophallaxis는 거의 없음
```

이라면,

> **contact network와 logistics network 사이에 선택 필터가 존재할 가능성**

을 새 가설로 설정할 수 있다.

---

## 9. V2 — 일반 분산 우선순위 할당 알고리즘

V1에서 여러 실험·군체에서 반복적으로 확인된 규칙만 일반 컴퓨팅 문제로 옮긴다.

### 목표

> **Distributed Dynamic Priority Allocation Algorithm**

### 적용 후보

- server resource allocation
- edge computing
- sensor network energy/bandwidth allocation
- warehouse multi-agent task allocation
- node failure 후 role reassignment

### 비교 기준

- random allocation
- round-robin
- fixed priority
- shortest-cost allocation
- centralized optimum
- existing distributed heuristics

### 평가 지표

- demand satisfaction
- unmet demand
- average waiting time
- total transfer cost
- communication count
- robustness
- recovery time
- fairness

V2 단계에 도달했을 때 비로소

> **Empirically Derived / Termite-Derived Allocation Algorithm**

이라는 표현을 사용할 수 있다.

---

## 10. 연구 흐름의 최종 형태

```text
기존 공개 데이터
        ↓
V0: Literature/Data-Constrained Model
        ↓
파일럿 예측
        ↓
우리 trophallaxis 실험
        ↓
V0의 오차 분석
        ↓
다음 실험 설계 수정
        ↓
추가 데이터
        ↓
V1: Empirically Calibrated Logistics Model
        ↓
반복 검증
        ↓
V2: Distributed Dynamic Priority Allocation Algorithm
```

즉 알고리즘은 **연구 마지막에 붙는 산출물이 아니라 연구 중간의 측정·가설검증·실험설계 도구이면서, 동시에 장기적으로 일반화 가능한 최종 컴퓨팅 산출물**이다.

---

## 11. 가장 중요한 원칙

1. **자체 trophallaxis 데이터 전에는 V0를 실제 물류 알고리즘이라고 부르지 않는다.**
2. **모델 예측과 biological ground truth를 분리한다.**
3. **모델을 만든 데이터와 검증 데이터를 가능하면 분리한다.**
4. **같은 군체의 프레임 수보다 독립 군체 반복을 중요하게 본다.**
5. **모델이 틀린 조건을 숨기지 않고 다음 실험 질문으로 사용한다.**
6. **컴퓨팅 규칙은 실제 생물 데이터에서 반복적으로 확인된 것만 일반화한다.**

---

## 12. 현재 가장 적합한 표현

### 연구 방법론
> **Model-Guided Experimental Design**

### V0
> **Literature/Data-Constrained Termite Model**

### V1
> **Empirically Calibrated Termite Logistics Model**

### V2
> **Empirically Derived Distributed Dynamic Priority Allocation Algorithm**

---

## 핵심 문장

> **기존 흰개미 데이터를 이용해 초기 계산모형을 먼저 구축하고, 그 모형이 우리 실험의 측정 변수와 실험 조건을 안내하도록 한다. 이후 실제 trophallaxis 물류망을 이용해 모형을 지속적으로 보정하며, 모델의 오차 자체를 새로운 생물학적 질문으로 사용한다. 최종적으로 반복 검증된 물류 규칙만 분산 자원 할당 알고리즘으로 일반화한다.**
