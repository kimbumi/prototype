# Radius & Shadow

---

## Radius

가이드:
- 여기 없는 값이 필요하면 Primitive 직접 사용
- 요소 크기가 클수록 radius도 크게

### Primitive

| Token | Value |
|---|---|
| radius.2 | 2px |
| radius.4 | 4px |
| radius.6 | 6px |
| radius.8 | 8px |
| radius.12 | 12px |
| radius.16 | 16px |
| radius.20 | 20px |
| radius.9999 | 9999px |

### Semantic

| Token       | Value  | 용도        |
| ----------- | ------ | --------- |
| radius.xs   | 2px    | 체크박스, 아이콘 |
| radius.sm   | 6px    | 버튼, 인풋, 탭 |
| radius.md   | 8px    | 범용 기본값    |
| radius.lg   | 12px   | 카드, 패널    |
| radius.xl   | 16px   | 모달, 시트    |
| radius.xxl  | 20px   | 모바일 미리보기  |
| radius.full | 9999px | 뱃지, 칩, 토글 |

---

## Shadow

### Primitive

| Token    | Value                           |
| -------- | ------------------------------- |
| shadow.1 | 0px 4px 12px rgba(0,0,0, 0.04)  |
| shadow.2 | 0px 4px 12px rgba(0,0,0, 0.15)  |
| shadow.3 | 0px 4px 20px rgba(0,0,0, 0.20)  |
| shadow.4 | 4px 16px 30px rgba(0,0,0, 0.20) |

### Semantic

| Token           | Primitive | 용도           |
| --------------- | --------- | ------------ |
| shadow.subtle   | shadow.1  | 배경과 약하게 분리되는 요소 (카드, 위젯) |
| shadow.elevated | shadow.2  | 배경 위로 떠있는 요소 (드롭다운, 툴팁, 토스트) |
| shadow.strong   | shadow.3  | 인터랙션 강조 (호버, 활성 상태) |
| shadow.modal    | shadow.4  | 화면 위를 덮는 레이어 (모달, 사이드 패널) |
