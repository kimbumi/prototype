# Typography

글꼴: Pretendard

폰트 크기, 줄 높이, 폰트 두께, 자간 각각을 Primitive로 정의하고, Semantic과 Scale로 조합하여 사용.

- Semantic: 역할/상황 기반 (PageTitle, Body 등). 우선 사용 권장.
- Scale: 크기+두께 축약 조합 (t5Bold 등). Semantic에 맞는 게 없을 때 사용.

---

## Primitive

### Font Size

rem 기준 (1rem = 16px)

| Token | Value | px |
|---|---|---|
| font-size.t1 | 0.6875rem | 11 |
| font-size.t2 | 0.75rem | 12 |
| font-size.t3 | 0.8125rem | 13 |
| font-size.t4 | 0.875rem | 14 |
| font-size.t5 | 1rem | 16 |
| font-size.t6 | 1.125rem | 18 |
| font-size.t7 | 1.25rem | 20 |
| font-size.t8 | 1.375rem | 22 |
| font-size.t9 | 1.5rem | 24 |
| font-size.t10 | 2rem | 32 |

### Line Height

| Token | Value | px |
|---|---|---|
| line-height.t1 | 0.875rem | 14 |
| line-height.t2 | 1rem | 16 |
| line-height.t3 | 1.125rem | 18 |
| line-height.t4 | 1.25rem | 20 |
| line-height.t5 | 1.375rem | 22 |
| line-height.t6 | 1.5rem | 24 |
| line-height.t7 | 1.75rem | 28 |
| line-height.t8 | 1.875rem | 30 |
| line-height.t9 | 2rem | 32 |
| line-height.t10 | 2.75rem | 44 |

### Font Weight

| Token | Value |
|---|---|
| font-weight.regular | 400 |
| font-weight.medium | 500 |
| font-weight.semibold | 600 |
| font-weight.bold | 700 |

### Letter Spacing

| Token | Value |
|---|---|
| letter-spacing.tight | -0.01em |
| letter-spacing.normal | 0em |
| letter-spacing.wide | +0.01em |

---

## Semantic

역할 기반. 우선 사용 권장. 계층: Page > Section > Container > Component

Semantic에 맞는 두께가 없을 때 (medium, semibold 등) Scale 조합으로 대체. 예: ContainerTitle 자리에 medium → t5Medium

| Token | fontSize | lineHeight | fontWeight | letterSpacing | 용도 |
|---|---|---|---|---|---|
| PageTitle | t9 | t9 | bold | tight | 페이지 최상위 제목 |
| SectionTitle | t7 | t7 | bold | tight | 페이지 내 영역 구분 제목 |
| ContainerTitle | t5 | t5 | bold | tight | 카드/패널 헤더 |
| ComponentTitle | t4 | t4 | bold | tight | 테이블 헤더, 설정 항목명 |
| Body1 | t5 | t5 | regular | tight | 안내/설명 텍스트 (한두 줄) |
| Body2 | t4 | t4 | regular | tight | 기본 본문 (가장 많이 쓰임) |
| Body1Paragraph | t5 | t6 | regular | tight | 여러 줄 읽기용 (3줄 이상 본문) |
| Body2Paragraph | t4 | t5 | regular | tight | 여러 줄 읽기용 (3줄 이상 본문) |
| Label | t3 | t3 | regular | normal | 부가 설명, 힌트 텍스트 |
| Caption | t2 | t2 | regular | normal | 날짜, 메타, 카운트 등 |

---

## Scale

Semantic에 맞는 게 없을 때 사용하는 자유 조합. 미리 전부 정의하지 않고, 규칙에 따라 필요할 때 생성.

### 규칙

- 네이밍: {사이즈}{두께} (예: t5Bold, t3Regular)
- 사이즈: t1~t10
- 두께: Bold, Semibold, Medium, Regular
- line-height: 동일 번호의 line-height 사용 (t5 → line-height.t5)
- letter-spacing: t4 이상은 tight, t3 이하는 normal

### 예시

| Token      | fontSize  | lineHeight | fontWeight | letterSpacing |
| ---------- | --------- | ---------- | ---------- | ------------- |
| t5Bold     | t5 (16px) | t5 (22px)  | bold       | tight         |
| t4Medium   | t4 (14px) | t4 (20px)  | medium     | tight         |
| t3Regular  | t3 (13px) | t3 (18px)  | regular    | normal        |
| t2Semibold | t2 (12px) | t2 (16px)  | semibold   | normal        |
