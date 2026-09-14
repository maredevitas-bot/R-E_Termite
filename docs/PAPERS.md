# 핵심 논문 정리

> 논문별로 **무엇을 실제로 보여줬는지**, **우리 연구에 어떤 의미가 있는지**, **어디까지는 말하면 안 되는지**를 분리해서 기록한다.

---

## 1. Paiva et al. (2021)
### *Scale-free movement patterns in termites emerge from social interactions and preferential attachments*

- Journal: *PNAS* 118(20), e2004369118
- DOI: `10.1073/pnas.2004369118`
- Species: *Cornitermes cumulans*

### 실험
- 집단 크기 1~29개체
- 31개 야생 군체
- 약 120만 개 위치 데이터 포인트
- 원형 arena와 annular arena 사용
- Lévy walk 분석
- 금속 장애물 대조실험
- 특정 상대와 반복적으로 접촉하는지 분석

### 핵심 결과
- 밀도가 증가하면 사회적 접촉이 늘고 이동 패턴이 변화했다.
- 단순 금속 장애물 충돌에서는 동일한 현상이 나타나지 않았다.
- 사회적 상호작용이 이동 양상 형성에 중요했다.
- 모든 상대와 균등하게 상호작용하지 않고 일부 상대와 반복적으로 접촉하는 **preferential attachment**가 나타났다.

### 우리 연구와의 연결
- 흰개미 관계망이 완전한 무작위·균등 네트워크가 아닐 수 있다는 근거.
- 물류망에서도 반복 전달 상대나 허브가 존재하는지 검증할 가치가 있다.
- 집단 크기가 커질 때 물류망 구조가 어떻게 달라지는지 연구할 근거가 된다.

### 주의
- 대상종은 *R. speratus*가 아니다.
- 실제 trophallaxis·질소 흐름을 측정한 연구가 아니다.
- 약 30분 실험에서의 선호관계를 평생 유지되는 ‘친구’라고 부르면 안 된다.

---

## 2. Manduca et al. (2025)
### *Transfer entropy analysis reveals interaction dynamics between termite castes*

- Journal: *Ecological Informatics* 92, 103416
- DOI: `10.1016/j.ecoinf.2025.103416`
- Species: *Reticulitermes lucifugus*

### 실험
세 조합 비교:
- worker–worker
- soldier–soldier
- worker–soldier

영상에서:
- occupied area
- speed

를 추출하고 transfer entropy 계산.

### 핵심 결과
- worker–worker 쌍이 가장 높은 total transfer entropy를 보였다.
- occupied area 최적 조건에서 약 1.04 bits vs 0.67/0.68 bits.
- speed에서도 worker–worker가 더 높은 값.
- 일부 조건에서 soldier → worker 정보흐름이 반대보다 유의하게 높았다.
- 하지만 방향성 결과는 모든 분석조건에서 일관되게 유의한 것은 아니었다.

### 우리 연구와의 연결
- 접촉량만이 아니라 **행동 영향의 방향성과 시간지연**을 정량화할 수 있다.
- Contact Network와 별도로 Information Network를 만들 수 있다.
- 군체 수준 확장은 논문 자체가 후속연구로 제안한다.

### 주의
- 2개체 수준 실험이다.
- transfer entropy ≠ 실제 먹이 이동.
- 높은 TE를 직접적인 명령·의사소통 경로라고 단정하면 안 된다.

---

## 3. Tasaki et al. (2023)
### *The royal food of termites shows king and queen specificity*

- Journal: *PNAS Nexus* 2(7), pgad222
- DOI: `10.1093/pnasnexus/pgad222`
- Species: *Reticulitermes speratus*

### 핵심 결과
- 왕과 여왕은 일개미에게 주로 stomodeal trophallaxis로 먹이를 공급받는다.
- 왕과 여왕에게 전달되는 royal food의 조성이 서로 다르다.
- 일개미는 왕과 여왕을 구분하여 먹이를 제공하는 **discriminative trophallaxis**를 보였다.
- 왕에게 먹이를 공급하던 일개미가 여왕의 begging을 거절하는 행동도 관찰되었다.

### 논문이 남긴 중요한 질문
저자들은 다음 두 가능성을 제시한다.
1. 한 일개미가 왕용/여왕용 먹이를 모두 만들고 상황에 따라 선택한다.
2. **왕 급식 담당과 여왕 급식 담당처럼 공급 일개미가 전문화되어 있다.**

이를 확인하려면 공급 개체의 추적이 필요하다고 논의한다.

### 우리 연구와의 연결
현재 가장 직접적인 gap 중 하나.

> **왕실 급식 일개미는 실제로 전문화되어 있는가?**

AI 장기 ID tracking과 trophallaxis 검출로 직접 검증할 수 있다.

---

## 4. King- and queen-specific degradation of uric acid contributes to reproduction in termites

- PMID: `36598016`
- PMCID: `PMC9811635`
- Species: *Reticulitermes speratus*

### 핵심 결과
- 요산은 중요한 질소 저장원이다.
- urate oxidase 유전자 `RsUAOX`가 성숙한 왕·여왕에서 높게 발현된다.
- 일개미가 neotenic reproductive로 분화할 때 RsUAOX 발현이 증가한다.
- 요산 분해를 억제하면 여왕의 산란수가 감소한다.
- 일개미가 생식개체에게 요산을 공급한다.

### 우리 연구와의 연결
- 생식계급은 사회적 지위뿐 아니라 **질소 자원 이용 능력이 다른 대사적 계급**임을 보여준다.
- 물류망의 수혜자별 중요도가 실제 생리와 연결됨을 보여주는 근거다.

### 주의
- 이 연구가 ‘어떤 사회관계가 요산 전달을 결정하는지’를 밝힌 것은 아니다.
- 행동망과 실제 질소 이동의 연결은 별도로 검증해야 한다.

---

## 5. Ohkuma et al. (1996)
### *Diversity of Nitrogen Fixation Genes in the Symbiotic Intestinal Microflora of the Termite Reticulitermes speratus*

- Journal: *Applied and Environmental Microbiology* 62(8), 2747–2752
- DOI: `10.1128/AEM.62.8.2747-2752.1996`
- Species: *Reticulitermes speratus*

### 핵심 결과
- 장내 미생물군에서 다양한 `nifH` 유전자가 확인되었다.
- 질소가 부족한 목질 환경에서 공생 미생물이 질소 획득에 기여할 가능성을 뒷받침한다.

### 우리 연구와의 연결
질소 고정 자체를 주실험으로 삼기보다:

> **왜 흰개미 사회가 희소한 질소 자원을 효율적으로 관리해야 하는가?**

를 설명하는 생태적 배경으로 사용한다.

### 주의
- `nifH` 다양성 확인 자체가 특정 실험조건에서 실제 질소고정량이 얼마나 변하는지 보여주는 것은 아니다.

---

## 6. 초기 queen pheromone 연구

*R. speratus*에서 주요 후보 성분으로:
- 2-methyl-1-butanol (2M1B)
- n-butyl-n-butyrate (nBnB)

가 보고되었다.

### 기존 연구 방향
초기 R&E에서는 자연추출물에서 유사성분을 찾아 생식분화를 억제하는 것을 중심 목표로 검토했다.

### 현재 위치
페로몬 자체를 최종 산출물로 두지 않는다.

필요할 경우:
- 생식상태를 변화시키는 perturbation
- 생식위계와 물류망의 인과관계를 확인하는 보조실험

으로 제한해서 사용한다.

---

# 논문 간 연결

```text
Ohkuma 1996
질소 부족 환경 + 공생 질소 획득
        ↓
Uric acid study
생식개체의 특이적 질소 이용
        ↓
Tasaki 2023
왕·여왕 특이적 trophallaxis / royal food
        ↓
Paiva 2021
선택적 사회관계 / preferential attachment
        ↓
Manduca 2025
방향성 있는 행동 정보흐름 정량화
        ↓
우리 연구
실제 Logistics Network 측정
        ↓
실측 기반 dynamic priority allocation 규칙 도출
```

---

# 아직 문헌상 확정되지 않은 핵심 gap

- 왕 급식/여왕 급식 공급 일개미가 실제로 전문화되어 있는가?
- 많이 접촉하는 개체가 실제로 많은 자원을 전달하는가?
- 사회적 허브와 물류 허브는 같은가?
- 생식위계가 바뀔 때 자원 배분 우선순위도 재편되는가?
- 집단 규모 변화가 trophallaxis network의 topology를 바꾸는가?
- 실측 흰개미 자원 배분 규칙이 일반 컴퓨팅 자원 할당 문제에서도 유용한가?
