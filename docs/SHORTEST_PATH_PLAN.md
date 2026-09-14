# 최단경로 연구계획 (Shortest-Path Research Plan)

> 이 문서는 **연구의 장기 목표를 유지하면서도 첫 번째 완결된 연구 결과를 가장 짧은 시간 안에 확보하기 위한 최소 경로**를 정리한다. 핵심 원칙은 생물 실험·AI 분석·계산모형을 직렬로 기다리지 않고 병렬 진행하며, 왕·여왕·질소 분석·완전 자동화·Physical AI를 초기 필수조건에서 제외하는 것이다.

---

## 1. 최단경로의 목표

장기 목표 전체를 단기간에 끝내는 것이 아니라, 다음 한 사이클을 최대한 빨리 완성한다.

```text
Observation
→ Model
→ Prediction
→ Experiment
→ Revision
```

초기 최소 완성선은 다음과 같다.

```text
공개 데이터 기반 V0
        +
소규모 자체 흰개미 영상
        ↓
Contact Network + Trophallaxis/Logistics Network
        ↓
V0가 실제 물류망을 얼마나 예측하는지 비교
        ↓
모델 오차를 이용한 다음 실험 설계
```

이 단계까지만 성공해도 **실제 흰개미 사회망과 자원전달망의 관계를 정량적으로 비교한 하나의 완결된 연구 루프**가 성립한다.

---

## 2. 초기 단계에서 의도적으로 제외할 것

다음 항목은 장기적으로 중요하지만 첫 번째 연구 루프의 필수조건으로 두지 않는다.

- 왕·여왕 확보 및 royal provisioning specialization
- 생식위계 인위적 변화
- 질소 고정률·요산·대사체·RNA 등의 직접 생화학 분석
- 수십~수백 개체의 완전 자동 장기 tracking
- trophallaxis 완전 자동 검출
- Transfer Entropy, GNN, 강화학습 등 복잡한 방법의 초기 필수 사용
- 실제 로봇 기반 Physical AI 구현
- 최종 범용 Distributed Homeostatic Scheduler 완성

이 항목들은 기본 물류망 측정과 V0→V1 검증이 성공한 뒤 확장한다.

---

## 3. 병렬 진행 구조

### Track A — 공개 데이터 / 계산모형

```text
Paiva / Manduca 등 공개 데이터
→ 데이터 포맷 정리
→ Contact / Interaction Network 재현
→ V0 Literature/Data-Constrained Model
→ baseline simulator
```

초기 V0는 단순하게 시작한다.

\[
P(i\rightarrow j)
=f(\text{distance},\text{contact history},\text{interaction features})
\]

목표는 실제 물류 규칙을 미리 정하는 것이 아니라, **사회적 상호작용만으로 자원 전달을 어디까지 예측할 수 있는지 비교할 기준모형을 만드는 것**이다.

### Track B — 생물 실험

```text
소수 개체 관찰
→ 안정적 촬영
→ ID tracking
→ contact event
→ trophallaxis 후보
→ 사람의 ground-truth 판정
→ 실제 Logistics Network
```

초기 집단은 추적 정확도를 우선하여 약 5~20개체 규모에서 시작한다.

### Track C — AI / 데이터 파이프라인

```text
video
→ trajectory
→ proximity/contact candidate
→ short clip extraction
→ human validation
→ network table
```

초기에는 AI가 trophallaxis를 완전히 판별할 필요가 없다. **AI는 사람이 검토해야 할 후보 구간을 줄이는 도구**로 사용한다.

---

## 4. 첫 파일럿의 세 가지 Go/No-Go 질문

첫 파일럿에서 가장 먼저 다음 세 항목만 확인한다.

### Gate 1. 개체 ID를 필요한 시간 동안 유지할 수 있는가?

- 실패 시: 개체 수 감소, 관찰영역 축소, 영상조건 수정
- 성공 시: 반복 donor–recipient 관계 분석 가능

### Gate 2. 영상에서 trophallaxis를 사람이 일관되게 판별할 수 있는가?

- 실패 시: 촬영배율·각도·해상도·행동 정의 수정
- 성공 시: ground-truth dataset 구축

### Gate 3. 분석 가능한 빈도로 trophallaxis event가 발생하는가?

- 실패 시: 관찰시간, 집단구성, 먹이조건, observation zone 수정
- 성공 시: Contact vs Logistics 비교 진행

이 세 Gate를 통과하기 전에는 대규모 촬영이나 복잡한 AI 개발을 진행하지 않는다.

---

## 5. 촬영을 짧은 반복으로 확대

처음부터 며칠짜리 장기영상을 찍지 않는다.

```text
30분 테스트
→ 2시간 테스트
→ 반나절 촬영
→ 장기 촬영
```

각 단계마다 다음을 확인한다.

- 초점 / 조명 / 프레임 안정성
- ID switch 빈도
- 개체 겹침과 cluster 발생
- trophallaxis 판독 가능성
- 저장·업로드 자동화
- 행동 왜곡 여부

문제를 발견하면 즉시 이전 단계에서 수정하여, 잘못된 조건으로 장시간 데이터를 쌓는 것을 피한다.

---

## 6. 완전 자동화보다 Human-in-the-Loop 우선

장시간 영상을 전부 사람이 검토하지 않는다.

```text
두 개체가 근접
→ 일정 시간 이상 상호작용
→ 후보 클립 자동 추출
→ 사람이 trophallaxis 여부 확인
→ label 누적
→ detector 개선
```

이를 통해 처음부터 완벽한 행동검출 AI를 만드는 시간을 줄이고, 실제 데이터가 쌓일수록 자동화를 높인다.

---

## 7. 첫 통합 연구 질문

최단경로에서 가장 먼저 답할 질문은 다음으로 둔다.

> **“흰개미의 사회적 접촉망만으로 실제 trophallaxis 물류망을 얼마나 예측할 수 있는가?”**

비교 대상:

- Contact frequency
- Contact duration
- Repeated partner history
- Distance / spatial proximity
- 기본 activity features

관찰 대상:

- 실제 trophallaxis edge
- donor–recipient direction
- edge persistence
- 반복 partner 비율

가능한 결과는 모두 연구적 의미가 있다.

1. Contact Network가 Logistics Network를 잘 예측한다.
2. 일부 변수만 예측력이 있다.
3. Contact Network로는 충분하지 않다.

특히 3번이면 **접촉과 물질전달 사이에 추가적인 선택 규칙이 존재할 가능성**이 다음 연구 질문이 된다.

---

## 8. 8주 기준의 빠른 진행 예시

### 1~2주차

병렬 수행:

- 공개 데이터 접근 및 재현 시작
- 공통 trajectory / interaction 데이터 스키마 정의
- V0 baseline 코드 작성
- 작은 observation chamber / 촬영조건 테스트
- 5~20개체 파일럿 영상 확보

### 3~4주차

- tracking 안정화
- proximity/contact event 자동 추출
- trophallaxis 수동 판정 기준 확정
- candidate clip 기반 라벨링
- 첫 Contact / Logistics Network 작성

### 5~6주차

- V0 예측과 실제 trophallaxis 비교
- residual 분석
- 가장 중요한 설명변수와 실패조건 선정
- 독립 반복 확대
- 다음 실험 조건을 모델 기반으로 결정

### 7~8주차

- V1 초기 보정
- 독립 데이터에서 재검증
- 첫 번째 Observation→Model→Experiment→Revision 루프 완성
- 이후 확장 여부 결정

이 일정은 절대적인 기간이 아니라 **연구 순서를 최소화하기 위한 기준**이다.

---

## 9. 첫 루프가 성공한 뒤에만 확장할 것

다음 단계는 결과가 지지할 때 선택한다.

### A. 반복적 donor–recipient 관계가 강함
→ specialization / functional social organ 분석

### B. 계급별 선택성이 강함
→ 왕·여왕 provisioning 및 priority allocation 확장

### C. 군체 상태에 따라 network가 크게 변함
→ adaptive logistics / homeostasis 분석

### D. 국소 규칙이 반복적으로 검증됨
→ Distributed Homeostatic Scheduler 개발

### E. 이동·물리적 handoff·failure를 포함할 가치가 있음
→ Physical AI / multi-agent simulation

즉 결과에 맞춰 다음 경로를 선택하며, 처음부터 모든 확장을 필수 목표로 두지 않는다.

---

## 10. 기간 단축을 위한 핵심 원칙

1. **직렬 의존성을 없애고 생물·AI·모델링을 병렬 진행한다.**
2. **소수 개체에서 측정 가능성을 먼저 증명한다.**
3. **완전 자동화보다 Human-in-the-Loop를 먼저 사용한다.**
4. **공개 데이터로 코드와 V0를 자체 실험 전에 검증한다.**
5. **첫 연구 질문은 Contact Network vs Logistics Network 비교로 제한한다.**
6. **왕·여왕·질소 분석·Physical AI는 초기 필수조건에서 제외한다.**
7. **짧은 파일럿 → 즉시 수정 → 확대 방식으로 진행한다.**
8. **모델이 틀리는 조건을 다음 실험의 우선순위로 사용한다.**
9. **프레임 수보다 독립 반복과 ground-truth 정확도를 우선한다.**
10. **첫 번째 완전한 연구 루프를 가장 빨리 돌리는 것을 초기 성공 기준으로 둔다.**

---

## 현재 최단경로 한 문장

> **공개 흰개미 행동 데이터로 V0를 먼저 구축하는 동시에 소규모 자체 영상에서 contact와 trophallaxis를 정량화하고, 둘의 차이를 이용해 모델을 보정함으로써 가장 짧은 시간 안에 첫 Model-Guided Research 루프를 완성한다.**
