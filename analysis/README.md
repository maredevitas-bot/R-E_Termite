# Analysis

> AI 추적, 네트워크 분석, 통계, 분산 자원 할당 알고리즘 코드를 정리하는 폴더.

## 예정 구조

```text
analysis/
├─ tracking/          # multi-object tracking
├─ behavior/          # trophallaxis / contact detection
├─ networks/          # contact / information / logistics networks
├─ transfer_entropy/  # 정보흐름 분석
├─ models/            # empirical allocation model
└─ optimization/      # distributed priority allocation benchmarks
```

## 분석 원칙

- raw video와 분석 결과를 분리한다.
- 자동 검출된 trophallaxis는 수동 검증 여부를 함께 기록한다.
- transfer entropy를 실제 먹이 흐름으로 해석하지 않는다.
- 네트워크 지표는 생물학적 질문과 연결되는 최소한의 지표부터 사용한다.
- 알고리즘 규칙을 먼저 만들고 흰개미 데이터에 끼워 맞추지 않는다.

## 1차 구현 목표

- [ ] trajectory CSV 입력
- [ ] contact network 생성
- [ ] trophallaxis edge 입력/시각화
- [ ] temporal network animation
- [ ] repeated-partner ratio 계산
- [ ] centrality 비교
- [ ] transfer entropy 재현
- [ ] empirical donor→recipient model
