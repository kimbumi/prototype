# Color

Semantic과 Palette 두 레이어로 구성. Semantic 우선 사용, 필요 시 Palette에서 직접 선택 (디자이너만).

---

## Palette

### Constant

| Token | Value |
|---|---|
| White | FFFFFF |
| Black | 000000 |

### Gray

| Token | Value |
|---|---|
| Gray5 | F9F9FA |
| Gray10 | F6F7F8 |
| Gray20 | E9ECEE |
| Gray30 | CBCDD2 |
| Gray40 | B3B5BA |
| Gray50 | 9EA1A7 |
| Gray60 | 838589 |
| Gray70 | 6E6E72 |
| Gray80 | 5E5E61 |
| Gray90 | 464648 |
| Gray100 | 2E2E31 |

### Violet

| Token | Value |
|---|---|
| Violet5 | F5F4FF |
| Violet10 | EEEDFF |
| Violet20 | E5E2FF |
| Violet30 | CFCDFF |
| Violet40 | B6B3FF |
| Violet50 | A4A1F5 |
| Violet60 | 837AFF |
| Violet70 | 6B62ED |
| Violet80 | 5148CF |
| Violet90 | 422AAE |
| Violet100 | 220F84 |

### Blue

| Token | Value |
|---|---|
| Blue5 | F3F6FF |
| Blue10 | ECF0FF |
| Blue20 | D0DBFF |
| Blue30 | 9FB5FF |
| Blue40 | 7B99FF |
| Blue50 | 6285FF |
| Blue60 | 4269F5 |
| Blue70 | 274ED9 |
| Blue80 | 183AB7 |
| Blue90 | 0C2B9C |
| Blue100 | 001479 |

### Red

| Token | Value |
|---|---|
| Red5 | FDEFEC |
| Red10 | FEE2E2 |
| Red20 | FFB8B8 |
| Red30 | FF8484 |
| Red40 | FF6060 |
| Red50 | F44141 |
| Red60 | E80000 |
| Red70 | C80000 |
| Red80 | 9E0000 |
| Red90 | 7F1D1D |
| Red100 | 690000 |

### Green

| Token | Value |
|---|---|
| Green5 | F7FEE7 |
| Green10 | ECFCCB |
| Green20 | D9F99D |
| Green30 | BEF264 |
| Green40 | 9EEE36 |
| Green50 | 51E33A |
| Green60 | 00C944 |
| Green70 | 00B33E |
| Green80 | 009F37 |
| Green90 | 007F2C |
| Green100 | 006322 |

### Orange

| Token | Value |
|---|---|
| Orange5 | FFF7ED |
| Orange10 | FFEDD5 |
| Orange20 | FED7AA |
| Orange30 | FDBA74 |
| Orange40 | FB923C |
| Orange50 | FF9641 |
| Orange60 | EA580C |
| Orange70 | D84A00 |
| Orange80 | C2410C |
| Orange90 | 9A3412 |
| Orange100 | 7C2D12 |

---

## Semantic

### 네이밍 규칙

패턴: property.role-variant-state

- property: bg, fg, stroke
- role: neutral, brand, critical, positive, caution, informative 등
- variant: strong, subtle, muted, weak
- state: hover, pressed 등 (컴포넌트 단계에서 확장)

### Variant 정의

- strong — 기본보다 강한 강조 (타이틀, 핵심 수치)
- subtle — 한 단계 낮춤 (보조 역할, 약한 강도)
- muted — 두 단계 낮춤 (거의 안 읽어도 되는 정보)
- weak — 컬러 계열 배경 tint 전용 (Red5, Green5, Violet5 등)

### 사용 가이드

- disabled는 컬러 토큰이 아닌 opacity로 컴포넌트 단계에서 처리
- 아이콘은 같은 맥락의 텍스트보다 한 단계 낮은 fg 토큰 사용 권장

### Background

| Token | Palette | 용도 |
|---|---|---|
| bg.base | Gray10 | 페이지 배경 |
| bg.surface | White | 카드/콘텐츠 배경 |
| bg.surface-subtle | Gray5 | 카드 안 구분 영역 |
| bg.neutral | Gray100 | CTA 버튼, 가장 주요한 행동 |
| bg.neutral-subtle | Gray20 | 보조 버튼, 보조 요소 배경 |
| bg.brand | Violet60 | 브랜드 강조 |
| bg.brand-weak | Violet5 | 브랜드 약한 배경 |
| bg.critical | Red50 | 삭제 버튼 |
| bg.critical-weak | Red5 | 에러 배경 |
| bg.positive-weak | Green5 | 성공 배경 |
| bg.caution-weak | Orange5 | 경고 배경 |
| bg.informative-weak | Blue10 | 정보 배경 |
| bg.overlay | Black 60% | 모달 딤 |

### Foreground

| Token | Palette | 용도 |
|---|---|---|
| fg.neutral-strong | Gray100 | 타이틀, 강조 수치, 입력값 |
| fg.neutral | Gray90 | 일반적 기본 색상 |
| fg.neutral-subtle | Gray60 | 보조 텍스트 |
| fg.neutral-muted | Gray40 | 거의 안 읽어도 되는 정보 (메타, 날짜 등) |
| fg.inverse | White | 어두운 배경 위 |
| fg.brand | Violet60 | 브랜드 강조 |
| fg.critical | Red50 | 에러/삭제 |
| fg.positive | Green50 | 성공 |
| fg.caution | Orange50 | 경고 |
| fg.informative | Blue50 | 정보 |

### Stroke

| Token | Palette | 용도 |
|---|---|---|
| stroke.neutral | Gray30 | 카드, 인풋, 테이블 |
| stroke.neutral-subtle | Gray20 | 약한 구분선 |
| stroke.brand | Violet60 | 포커스, 선택 |
| stroke.critical | Red50 | 에러 인풋 |
