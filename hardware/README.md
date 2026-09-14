# Hardware

> 흰개미 사육·촬영·먹이전달 분석을 위한 모듈형 관찰 챔버와 카메라 시스템 기록 폴더.

## 기본 개념

```text
[Core Colony]
      │
[Transit Corridor]
      │
[Observation / Feeding Module]
      │
[Top-view IR / NoIR Camera]
```

## 설계 목표

- AI tracking을 위해 관찰부는 가능한 한 얕은 2D 구조
- core colony와 observation zone 분리
- 먹이 제공부 교체 가능
- transit corridor에서 출입 개체 관찰 가능
- 온·습도 측정
- IR/NoIR 촬영
- 모듈 교체가 가능한 구조
- 1차 챔버 외부에 2차 격리 구조를 두어 탈출 위험 최소화

## 개발 순서

### V0 — 배치 모형
- 종이/간단한 판재로 구조 검토

### V1 — 저가 프로토타입
검증 항목:
- [ ] 카메라 초점과 시야
- [ ] 개체 겹침 빈도
- [ ] 통로 이용 여부
- [ ] 습도 유지
- [ ] 먹이부 접근성
- [ ] 탈출 취약점

### V2 — 연구용 주문제작
- V1 결과를 바탕으로 아크릴/가공 부품 치수 확정

### V3 — 전시/장기실험형
- 배선·센서·카메라 고정까지 정리

## 현재 보유/활용 예정 장비

- Raspberry Pi
- Raspberry Pi NoIR camera
- IR illumination
- 온·습도 센서
- 영상 저장 및 Google Drive 업로드 파이프라인

## 주의

최종 주문제작 전에 반드시 V1에서 실제 흰개미의 이동과 영상추적 가능성을 검증한다. 사육·격리 구조는 지도교사와 학교 실험실 관리 기준에 맞춰 확정한다.
