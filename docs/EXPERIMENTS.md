# 실험 설계 및 진행 기록

> 실제 수행 전에는 각 실험의 목적, 독립변수, 종속변수, 대조군, 반복수, 제외기준을 이 문서에서 먼저 확정한다.

---

## 전체 단계

```text
Phase 0  선행데이터·코드 재현
   ↓
Phase 1  관찰 챔버 + 장기 ID tracking
   ↓
Phase 2  기본 trophallaxis 물류망
   ↓
Phase 3  왕·여왕 급식망과 공급자 전문화
   ↓
Phase 4  생식위계 변화에 따른 동적 배분
   ↓
Phase 5  실측 기반 분산 자원 할당 알고리즘
```

---

# Phase 0. 공개 데이터와 분석 pipeline 재현

## 목적
실제 흰개미 실험 전에 다중개체 추적·네트워크 분석 방법을 검증한다.

## 할 일
- [ ] Paiva et al. 공개 데이터/코드 확보
- [ ] Manduca et al. 공개 데이터/코드 확보
- [ ] 궤적 데이터 형식 통일
- [ ] contact network 생성
- [ ] repeated-partner / preferential interaction 재현
- [ ] transfer entropy 계산 재현
- [ ] 시각화 prototype 제작

## 성공 기준
- 논문에서 보고한 경향을 대략 재현할 수 있음
- 우리 코드에서 개체 궤적 → 네트워크 생성까지 자동 수행 가능

---

# Phase 1. 관찰 챔버와 장기 ID tracking

## 목적
일본흰개미의 trophallaxis를 장시간 추적할 수 있는 촬영 조건을 확보한다.

## 하드웨어 가설
- 넓고 높은 일반 사육장보다 **얕은 2D 관찰 공간**이 ID tracking에 유리하다.
- core colony와 observation/feeding zone을 분리한다.
- transit corridor를 통해 출입 개체를 관찰할 수 있게 한다.

## 확인할 항목
- [ ] IR/NoIR 환경에서 충분한 영상 품질
- [ ] 개체 겹침 빈도
- [ ] 카메라 초점·시야
- [ ] 온·습도 안정성
- [ ] 흰개미가 observation zone을 실제 사용함
- [ ] 탈출 방지 구조
- [ ] 동일 개체 ID 유지 시간

## 기록
| 날짜 | 챔버 버전 | 집단 크기 | 촬영 시간 | ID 유지율 | 주요 문제 | 수정사항 |
|---|---:|---:|---:|---:|---|---|
| | | | | | | |

---

# Phase 2. 기본 trophallaxis 물류망

## 핵심 질문
> **일개미 사이의 먹이전달은 균등한가, 선택적인가?**

## 측정값
- 개체별 trophallaxis 횟수
- donor → recipient 방향
- repeated partner ratio
- donor out-degree
- recipient in-degree
- edge persistence
- 전체 contact network와의 차이

## 기본 분석
1. Contact Network 생성
2. Logistics Network 생성
3. 두 네트워크의 edge overlap 계산
4. degree / centrality 비교
5. 특정 개체에 전달이 집중되는지 null model과 비교

## Null model 후보
- 같은 개체수에서 무작위 edge 재배선
- 각 개체의 총 전달 횟수는 유지하고 recipient만 shuffle

## 아직 확정하지 않은 사항
- 집단 크기
- 촬영 시간
- 반복 수
- 개체 마킹 방법
- trophallaxis 자동검출 기준

---

# Phase 3. 왕·여왕 급식망과 공급자 전문화

## 핵심 질문
> **왕과 여왕에게 먹이를 공급하는 일개미는 전문화되어 있는가?**

## 가설 후보
- H0: 공급 일개미는 왕/여왕을 가리지 않고 기회적으로 먹이를 준다.
- H1: 일부 일개미가 왕 또는 여왕에 반복적으로 특화된다.

## 필요한 데이터
- 공급 일개미 ID
- 수혜자: king / queen
- 전달 시각
- 전달 지속시간
- 이전/이후 행동
- 같은 개체의 반복 공급 여부

## 지표 후보
- king provisioning ratio per worker
- queen provisioning ratio per worker
- specialization index
- role persistence over time

## 중요한 해석 제한
- 특정 개체가 몇 번 더 공급했다고 즉시 ‘전담’으로 부르지 않는다.
- random expectation과 반복성 검증이 필요하다.

---

# Phase 4. 생식위계와 동적 물류 우선순위

## 핵심 질문
> **군체의 생식 상태가 변할 때 자원 배분 우선순위도 재편되는가?**

## 가능한 조건
- 안정된 왕·여왕 존재 상태
- 생식위계 변화가 발생하는 자연 조건
- 필요 시 선행연구가 충분히 뒷받침된 perturbation 조건

## 측정
- 계급별 trophallaxis 수혜량
- 공급 네트워크 topology 변화
- 특정 recipient로의 집중도
- logistics centrality 변화
- change point

## 주의
이 단계는 현재 **가설 검증**이며, ‘생식위계가 바뀌면 반드시 우선순위가 바뀐다’고 전제하지 않는다.

---

# Phase 5. 실측 기반 분산 자원 할당 알고리즘

## 목적
실제 흰개미 물류 데이터에서 확인된 규칙만 추출해 컴퓨팅 문제에 적용한다.

## 기본 절차
1. 관찰 데이터에서 candidate feature 생성
2. 실제 donor → recipient 선택을 설명하는 변수 분석
3. empirical transition/allocation rule 모델링
4. agent-based allocation simulator 구현
5. 기존 baseline과 비교

## Baseline 후보
- random allocation
- round-robin
- fixed priority
- shortest-cost allocation
- centralized optimum
- 기존 distributed heuristic

## Benchmark scenario 후보
- 제한된 CPU/메모리 자원 할당
- 센서 네트워크 에너지 배분
- multi-robot task allocation
- node failure 이후 dynamic role reassignment

## 평가 지표
- demand satisfaction rate
- unmet demand
- average waiting time
- total transfer cost
- communication count
- congestion
- recovery time
- robustness
- fairness

---

# 공통 데이터 스키마 초안

## Individual table
| field | description |
|---|---|
| individual_id | 개체 ID |
| caste | worker / soldier / king / queen / etc. |
| colony_id | 원군체 |
| experiment_id | 실험 ID |

## Trajectory table
| field | description |
|---|---|
| timestamp | 시간 |
| individual_id | 개체 ID |
| x, y | 위치 |
| speed | 속도 |

## Interaction table
| field | description |
|---|---|
| timestamp | 시간 |
| donor_id | 공급자 |
| recipient_id | 수혜자 |
| interaction_type | contact / trophallaxis / etc. |
| duration | 지속시간 |
| confidence | 자동검출 신뢰도 |
| manually_verified | 수동 검증 여부 |

---

# 다음 실험 회의에서 확정해야 할 것

- [ ] 왕·여왕 포함 *R. speratus* 군체 확보 가능성
- [ ] 개체 장기 ID tracking 방법
- [ ] trophallaxis 영상 판정 기준
- [ ] 마킹 필요 여부와 안전성
- [ ] 파일럿 집단 크기
- [ ] 관찰시간
- [ ] 반복 수
- [ ] 챔버 V1 치수
- [ ] 질소 관련 직접 측정을 어느 단계에 포함할지
- [ ] Phase 5 benchmark를 무엇으로 할지
