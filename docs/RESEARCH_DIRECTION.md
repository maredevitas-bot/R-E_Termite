# 현재 연구 방향
## 질소 자원경제 · 생식위계 · 군체 물류망 · AI 행동 네트워크 · 분산 우선순위 할당

> 이 문서는 현재 팀이 가장 유력하게 보는 연구 방향을 정리한다. 과거 아이디어의 변화 과정은 [`RESEARCH_LOG.md`](./RESEARCH_LOG.md), 논문별 정리는 [`PAPERS.md`](./PAPERS.md), 실제 실험 설계는 [`EXPERIMENTS.md`](./EXPERIMENTS.md)에 기록한다.

---

## 1. 현재 연구를 한 문장으로

> **질소가 부족한 목질 환경에서 흰개미 군체가 제한된 자원을 어떤 개체·계급에 우선적으로 배분하는지를 실제 행동 데이터로 규명하고, 그 물류 규칙을 AI로 추출하여 중앙 통제 없는 동적 우선순위 자원 할당 알고리즘으로 확장한다.**

```text
질소가 부족한 목질 자원
        ↓
질소 획득·저장·재활용의 필요
        ↓
일개미 중심의 먹이 가공·전달
        ↓
왕·여왕·병정·유충 등 계급별 서로 다른 수요
        ↓
선택적 trophallaxis(먹이 전달)
        ↓
동적 군체 물류망
        ↓
생식위계 변화에 따른 우선순위 재편?
        ↓
AI로 실제 배분 규칙 추출
        ↓
분산형 동적 우선순위 자원 할당 알고리즘
```

---

## 2. 왜 기존 방향을 바꾸었는가

초기에는 다음 세 연구를 병렬적으로 진행하려 했다.

1. 페로몬 유사물질을 이용한 생식분화 억제
2. AI 영상분석을 이용한 군체 상태·상호작용 분석
3. 질소 고정·요산·질소 배분 연구

각 파트는 독립적으로는 의미가 있었지만, **왜 세 연구를 반드시 함께 해야 하는가**에 대한 답이 약했다. 또한 방제·농업·가축화 같은 직접 응용을 붙일수록 기초 연구와 최종 제품 사이에 검증되지 않은 단계가 늘어났다.

따라서 현재는 페로몬, AI, 질소를 각각의 독립 주제로 보지 않는다.

- **질소**: 왜 자원 배분이 중요한가를 설명하는 희소자원·대사적 배경
- **생식위계**: 계급별 자원 수요와 우선순위가 달라질 수 있는 사회적 상태
- **trophallaxis**: 실제 자원 할당이 일어나는 행동
- **AI**: 수십~수백 개체의 물류 관계를 장시간 복원하는 측정 도구
- **최적화 알고리즘**: 실제 생물 데이터에서 도출된 규칙의 범용적 산출물

---

## 3. 왜 흰개미인가

단순한 집단행동 연구라면 개미·벌·물고기 등도 가능하다. 그러나 일본흰개미 *Reticulitermes speratus*는 다음 요소가 한 군체 안에서 연결된다는 점이 중요하다.

1. 질소가 부족한 목재를 주식으로 한다.
2. 장내 공생미생물이 질소 자원 확보에 관여한다.
3. 요산 등으로 질소를 저장·재활용한다.
4. 일개미가 다른 계급에게 먹이를 공급한다.
5. 왕과 여왕에게 전달되는 royal food의 조성이 서로 다르다.
6. 왕·여왕은 요산 질소를 이용하는 능력이 강하며 번식과 연결된다.
7. 보충생식개체 형성을 통해 생식위계 자체가 재편될 수 있다.
8. 개체 간 사회적 상호작용이 균등하지 않을 가능성이 있다.

따라서 흰개미는 단순한 social network가 아니라 다음과 같은 **social–metabolic network**로 볼 수 있다.

```text
사회 관계
   ↕
자원 배분
   ↕
대사
   ↕
생식위계
```

---

## 4. 질소 고정의 위치

질소 고정 자체를 독립적인 주 실험축으로 삼지는 않는다.

Ohkuma et al. (1996)은 *R. speratus* 장내 미생물군에서 다양한 `nifH` 유전자를 확인했다. 이는 질소가 부족한 목질 환경에서 장내 공생계가 질소 획득에 기여한다는 생태적 배경을 제공한다.

우리 연구에서 생식위계와 더 직접적으로 연결되는 것은 다음이다.

- 요산 저장과 질소 재활용
- 일개미 → 생식개체 질소 공급
- 왕·여왕 특이적 요산 이용
- 왕·여왕별 서로 다른 royal food

즉 **질소 고정은 ‘왜 자원 배분이 중요한가’를 설명하는 출발점**, 질소 재활용·배분은 **군체 물류망의 기능적 의미를 검증하는 층**으로 둔다.

---

## 5. 대표 행동: trophallaxis

벌의 proboscis extension처럼 복잡한 연구를 한 장면으로 보여줄 행동으로 **먹이 전달(trophallaxis)**을 사용한다.

대중적인 시작 질문은 다음과 같다.

> **“흰개미는 누구에게 먼저 밥을 줄까?”**

여기서 자연스럽게 다음 질문으로 확장한다.

- 아무에게나 균등하게 먹이를 주는가?
- 왕과 여왕은 서로 다르게 대우받는가?
- 특정 일개미가 반복적으로 왕 또는 여왕에게 먹이를 공급하는가?
- ‘왕실 급식 담당’처럼 행동 전문화가 존재하는가?
- 생식위계가 바뀌면 물류 우선순위도 바뀌는가?

---

## 6. 세 종류의 네트워크

### 6.1 Contact Network
**누가 누구와 만나는가?**

- 거리
- 접촉 횟수
- 접촉 지속시간
- 반복 상대

### 6.2 Information Network
**누구의 과거 행동이 누구의 미래 행동을 예측하는가?**

- transfer entropy
- time lag
- 방향성

### 6.3 Logistics Network
**실제로 누가 누구에게 자원을 전달하는가?**

- trophallaxis 발생
- 전달 방향
- 빈도
- 공급자/수혜자
- 계급

핵심 질문은 세 네트워크가 같은 구조인지 여부이다.

\[
Contact\ Network \stackrel{?}{=} Information\ Network \stackrel{?}{=} Logistics\ Network
\]

이들을 같다고 가정하지 않는다. **차이를 밝히는 것 자체가 연구 결과**가 될 수 있다.

---

## 7. 현재 핵심 생물학 질문

### Q1. 먹이 전달망은 선택적인가?
- 모든 개체에게 균등하게 전달되는가?
- 특정 상대에게 반복적으로 전달되는가?
- 물류 허브 개체가 존재하는가?

### Q2. 왕·여왕 급식 일개미는 전문화되어 있는가?
- king provisioning worker와 queen provisioning worker가 나뉘는가?
- 같은 개체가 장기간 특정 생식개체에 반복적으로 공급하는가?

### Q3. 사회적 중심성과 물류 중심성은 같은가?
- 많이 만나는 개체가 실제로 많은 자원을 전달하는가?

### Q4. 생식위계 변화에 따라 물류 우선순위가 바뀌는가?
- 안정된 생식위계와 전환 중인 상태에서 공급 대상과 네트워크 구조가 달라지는가?

### Q5. 집단 규모에 따라 물류 구조가 어떻게 달라지는가?
- 집단이 커질수록 관계 수가 단순 증가하는가?
- 소수 선호관계나 subnet/community가 유지되는가?

---

## 8. AI의 역할

AI의 목적은 ‘여왕을 찾아내는 것’이 아니다.

> **수십~수백 개체의 장시간 영상으로부터 실제 군체 물류망을 복원하는 측정기술**

이 핵심이다.

```text
영상
 ↓
다중개체 탐지
 ↓
장기 ID 추적
 ↓
위치·속도 시계열
 ↓
접촉 후보 추출
 ↓
trophallaxis 행동 검출
 ↓
수동 검증
 ↓
Contact / Information / Logistics Network 생성
 ↓
계급·생식상태와 비교
```

후보 분석 지표:

- degree / weighted degree
- betweenness centrality
- eigenvector centrality
- community structure
- edge persistence
- repeated-partner ratio
- trophallaxis in/out-degree
- transfer entropy
- network entropy
- temporal change point

지표를 먼저 많이 넣고 의미를 끼워 맞추는 방식은 피한다.

---

## 9. 컴퓨팅으로의 확장: 분산형 동적 우선순위 할당

흰개미 군체의 자원배분 문제를 계산적으로 추상화하면 다음 질문이 된다.

> **“중앙 관리자 없이, 제한된 자원을 서로 다른 수요와 역할을 가진 여러 노드에 어떻게 배분할 것인가?”**

이는 **Distributed Dynamic Priority Allocation** 문제와 연결된다.

| 흰개미 군체 | 컴퓨팅 시스템 |
|---|---|
| 일개미 | worker node / agent |
| 먹이·질소 | CPU, memory, bandwidth, energy 등 제한 자원 |
| 왕·여왕·유충·병정 | 서로 다른 수요/중요도를 가진 task |
| trophallaxis | resource transfer |
| 선택적 상호작용 | limited communication neighbors |
| 생식위계 | dynamic priority structure |
| 생식개체 소실 | critical node/service failure |
| 보충생식개체 형성 | role reassignment / failover |
| 군체 상태 변화 | workload / demand shift |

흰개미에서 흥미로운 것은 ‘가장 짧은 경로’보다 **‘한정된 자원을 누구에게 먼저 배분하는가’**라는 문제이다.

---

## 10. 알고리즘 도출 원칙

알고리즘을 먼저 만든 뒤 흰개미 이름을 붙이지 않는다.

### 올바른 순서

1. 실제 영상에서 먹이전달 데이터 수집
2. 공급자–수혜자–계급–상태 관계 추출
3. 실제 전달 확률 추정
4. 어떤 변수가 배분을 설명하는지 확인
5. 검증된 규칙만 계산모델로 추상화

개념적으로 다음을 추정할 수 있다.

\[
P(i\rightarrow j \mid caste,\ past\ interaction,\ recipient\ state,\ colony\ state)
\]

예시적인 점수식은 다음처럼 쓸 수 있지만, 계수는 임의로 정하지 않는다.

\[
S_{ij}=\alpha D_j+\beta H_{ij}+\gamma R_j-\delta C_{ij}
\]

- \(D_j\): 현재 수요
- \(H_{ij}\): 과거 관계
- \(R_j\): 역할 중요도
- \(C_{ij}\): 전달 비용

실제 흰개미 데이터가 어떤 항과 관계를 지지하는지 먼저 검증한다.

---

## 11. 기존 termite-inspired algorithm과의 차별점

이미 다음과 같은 흰개미 모방 알고리즘이 존재한다.

- TERMITE routing
- Termite-hill routing
- Termite Colony Optimization
- Termite Alate Optimization

대표적인 기존 방식은 대체로 다음 흐름이다.

```text
흰개미의 알려진 특성/비유
→ 계산 규칙 설계
→ 컴퓨팅 문제 적용
```

예: stigmergy, pheromone-like weight, probabilistic search, local interaction.

우리 연구가 목표로 하는 흐름은 다르다.

```text
실제 흰개미 영상
→ 실제 먹이전달망 측정
→ 실제 우선순위 규칙 추정
→ 계산 알고리즘 도출
```

즉 단순한 **Termite-inspired**보다 **Empirically Derived / Termite-derived** 접근에 가깝다는 점이 핵심 차별성이다.

---

## 12. 알고리즘 검증 방향

실제 흰개미에서 도출한 규칙을 다음과 비교한다.

- random allocation
- fixed priority
- round-robin
- shortest-cost allocation
- centralized optimization
- 기존 distributed heuristic
- termite-derived dynamic allocation

평가지표 후보:

- demand satisfaction rate
- unmet demand
- average waiting time
- total transfer cost
- communication/message count
- congestion
- node failure 후 recovery time
- robustness
- fairness

응용 후보:

- edge computing의 CPU/메모리 자원 분배
- sensor network의 에너지·대역폭 할당
- warehouse multi-robot task allocation
- distributed server load balancing
- node failure 후 role reassignment
- emergency-priority allocation

---

## 13. 최종 산출물

### A. 생물학적 산출물 — Termite Logistics Dataset
- 개체 ID
- caste
- 시간별 위치
- 접촉관계
- trophallaxis 방향·빈도
- 생식개체와의 관계
- 군체 상태

### B. AI/분석 산출물 — Collective Logistics Network Analyzer
- 다중개체 추적
- trophallaxis 검출
- 동적 물류망 생성
- 정보흐름 분석
- 계급별 물류분석

### C. 컴퓨팅 산출물 — Empirically Derived Distributed Dynamic Priority Allocation Algorithm
- 실제 흰개미 배분 규칙에서 도출
- 일반 자원 할당 benchmark에서 성능 비교

### D. 실험 장치 — Modular Termite Observation Chamber
- top-view 추적에 유리한 얕은 구조
- core colony / observation zone 분리
- 먹이 제공부 교체 가능
- 온습도 기록
- 이중 격리 및 탈출 방지

---

## 14. 선행연구에서 확인된 사실 vs 우리가 검증할 가설

### 이미 확인된 사실
- 사회적 상호작용이 흰개미 이동 패턴을 바꿀 수 있다.
- 특정 상대와 반복적인 상호작용이 나타날 수 있다.
- 계급 조합에 따라 행동 정보흐름 특성이 달라질 수 있다.
- 왕과 여왕은 일개미에게 서로 다른 먹이를 공급받는다.
- 일개미는 왕/여왕을 구분하여 먹이 제공 행동을 한다.
- 왕·여왕의 요산 이용 능력은 번식과 연결된다.
- 일개미가 생식개체에게 요산을 공급한다.

### 우리가 새롭게 검증해야 하는 가설
- 특정 일개미가 왕/여왕 급식에 전문화되어 있다.
- 물류 허브 개체가 존재한다.
- contact centrality와 logistics centrality가 일치한다.
- 생식위계 변화 시 자원 우선순위가 동적으로 재편된다.
- 집단 크기에 따라 자원 배분 규칙이 바뀐다.
- 실측 흰개미 규칙이 컴퓨팅 자원 할당 문제에서 유용하다.

---

## 15. 피해야 할 과장

현재 근거 없이 다음을 단정하지 않는다.

- 흰개미는 최적의 물류 알고리즘을 사용한다.
- 왕/여왕이 항상 최우선 자원 수혜자다.
- 많이 만나는 개체가 가장 많은 자원을 전달한다.
- transfer entropy가 실제 먹이 흐름을 뜻한다.
- preferential attachment가 평생 친구 관계다.
- 생식위계 변화가 반드시 질소고정률을 변화시킨다.
- termite-derived algorithm이 기존 방법보다 우수하다.

---

## 16. 현재 가장 유력한 제목

### 연구보고서형
**AI 다중개체 추적을 이용한 일본흰개미 자원 물류망의 동적 우선순위 배분 규명 및 분산 자원 할당 알고리즘 개발**

### 간결형
**일본흰개미의 사회적 자원 물류망에서 나타나는 동적 우선순위 배분 규칙과 실측 기반 분산 최적화 알고리즘**

### 전시형
**흰개미는 누구에게 먼저 밥을 줄까? — 자연에서 배우는 분산형 자원 배분 알고리즘**

---

## 17. 현재 연구 단계

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

구체 실험 설계와 진행상황은 [`EXPERIMENTS.md`](./EXPERIMENTS.md)에 기록한다.
