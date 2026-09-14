# Analysis

> AI 추적, 행동 검출, 네트워크 분석, 모델 유도형 실험설계, 분산 컴퓨팅 및 Physical AI 확장 코드를 정리하는 폴더.

## 예정 구조

```text
analysis/
├─ tracking/            # multi-object tracking / ID persistence
├─ behavior/            # trophallaxis / contact detection
├─ networks/            # contact / information / logistics networks
├─ transfer_entropy/    # information-flow analysis
├─ models/              # V0 interaction / V1 empirical logistics model
├─ simulation/          # social stomach / resource-homeostasis simulator
├─ optimization/        # distributed scheduler benchmarks
└─ physical_ai/         # embodied multi-agent simulation
```

## 분석 원칙

- raw video와 분석 결과를 분리한다.
- 자동 검출된 trophallaxis는 수동 검증 여부를 함께 기록한다.
- 사람이 안정적으로 구분하지 못하는 행동은 AI ground truth로 사용하지 않는다.
- transfer entropy를 실제 먹이 흐름으로 해석하지 않는다.
- Contact / Information / Logistics Network를 구분한다.
- 네트워크 지표는 생물학적 질문과 연결되는 최소한의 지표부터 사용한다.
- 공개 데이터의 다른 종에서 얻은 수치를 *R. speratus*에 그대로 적용하지 않는다.
- 같은 군체의 프레임 수를 biological replicate로 간주하지 않는다.
- 모델 개발 데이터와 독립 검증 데이터를 가능한 한 분리한다.
- 알고리즘 규칙을 먼저 만들고 흰개미 데이터에 끼워 맞추지 않는다.
- `priority allocation`을 기본 정답으로 고정하지 않고 실제 데이터가 지지하는 메커니즘을 선택한다.

## 계산모형 버전

### V0 — Literature/Data-Constrained Interaction Model

공개 행동 데이터와 문헌으로 local interaction, repeated partner, caste/state 후보 변수를 구성한다.

### V0.5 — Pilot / Human-in-the-loop

자체 소규모 영상으로 tracking reliability, labeling protocol, rare-event candidate detection을 검증한다.

### V1 — Empirically Calibrated Logistics Model

실제 trophallaxis로 donor→recipient 관계와 역할분담·전문화를 추정한다.

### V2 — Distributed Homeostatic Scheduler

여러 군체에서 재현된 국소 규칙을 분산 resource scheduling 문제로 일반화한다.

### V3 — Physical AI / Embodied Multi-Agent Evaluation

이동비용, 제한된 sensing/communication, physical handoff, congestion, dynamic workload, node failure를 포함한 simulator에서 평가한다.

## 1차 구현 목표

- [ ] trajectory CSV 입력
- [ ] contact network 생성
- [ ] trophallaxis edge 입력/시각화
- [ ] temporal network animation
- [ ] repeated-partner ratio 계산
- [ ] centrality 비교
- [ ] transfer entropy 재현
- [ ] V0 social-interaction model
- [ ] baseline resource simulator
- [ ] empirical donor→recipient model

## 이후 구현 목표

- [ ] specialization / role-discovery analysis
- [ ] Contact → Logistics prediction benchmark
- [ ] residual-based hypothesis discovery
- [ ] Distributed Homeostatic Scheduler
- [ ] centralized / random / fixed / local baseline 비교
- [ ] embodied multi-agent simulator interface
- [ ] failure recovery / resource handoff benchmark
