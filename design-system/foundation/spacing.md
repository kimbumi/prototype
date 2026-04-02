# Spacing

모든 spacing은 dimension 기반. 방향(x/y) 구분 없이 역할 기반 정의. 코드는 rem (1rem = 16px), 피그마는 px.

---

## Primitive

| Token | Value | px |
|---|---|---|
| dimension.x0 | 0 | 0 |
| dimension.x0_5 | 0.125rem | 2 |
| dimension.x1 | 0.25rem | 4 |
| dimension.x1_5 | 0.375rem | 6 |
| dimension.x2 | 0.5rem | 8 |
| dimension.x2_5 | 0.625rem | 10 |
| dimension.x3 | 0.75rem | 12 |
| dimension.x3_5 | 0.875rem | 14 |
| dimension.x4 | 1rem | 16 |
| dimension.x5 | 1.25rem | 20 |
| dimension.x6 | 1.5rem | 24 |
| dimension.x7 | 1.75rem | 28 |
| dimension.x8 | 2rem | 32 |
| dimension.x10 | 2.5rem | 40 |
| dimension.x12 | 3rem | 48 |
| dimension.x14 | 3.5rem | 56 |
| dimension.x16 | 4rem | 64 |
| dimension.x20 | 5rem | 80 |
| dimension.x24 | 6rem | 96 |
| dimension.x32 | 8rem | 128 |

---

## Semantic

계층: Page > Section > Container > Component

- Page — 화면 가장자리 여백
- Section — 기능/맥락이 다른 큰 덩어리 간 간격
- Container — 배경/border가 있는 시각적 박스의 내부 여백
- Component — 박스 안 요소들 사이 간격

| Token                           | Value     | 용도                                    |
| ------------------------------- | --------- | ------------------------------------- |
| spacing.page-inset              | x6 (24px) | 페이지 좌우 여백                             |
| spacing.page-bottom             | x8 (32px) | 페이지 하단 여백                             |
| spacing.section-gap             | x6 (24px) | 큰 영역 간 간격 (배너 ↔ 카드, 폼 섹션 간)           |
| spacing.container-inset         | x6 (24px) | 카드/패널 기본 여백                           |
| spacing.container-inset-compact | x4 (16px) | 가로로 긴 카드 등 축소 여백                      |
| spacing.component-gap           | x4 (16px) | 다른 기능 그룹 사이 (카드 ↔ 카드, 필터 ↔ 테이블)       |
| spacing.inline-gap              | x2 (8px)  | 같은 그룹 안 요소 사이 (input ↔ 버튼, 아이콘 ↔ 텍스트) |

---

## 적용 규칙

1. inset은 컨테이너에만 — 배경/border가 있는 시각적 박스만. 내부 요소는 부모 패딩 상속.
2. 컨테이너 판단 기준 — 배경/border 있으면 컨테이너, 없으면 내부 요소.
3. container-inset 기준 — 큰 컨테이너: 24px / 작고 가로 긴 컨테이너: 16px 24px
4. 내부 간격은 gap으로 — 다른 그룹이면 component-gap, 같은 그룹이면 inline-gap
5. 확장 — -tight / -wide suffix. 필요할 때만 추가.

---

## Layout

배치 방식을 결정. spacing과 별개. Page뿐 아니라 Section 단위에서도 정의 가능.

```
Page (Layout + Width)
 └ Layout Section (Layout + Width)
      └ Content Section (Layout + Width)
```

### Layout Type

| Type  | 설명      | 사용        |
| ----- | ------- | --------- |
| Stack | 위→아래 쌓기 | 대부분의 화면   |
| Split | 좌/우 분할  | 설정 + 미리보기 |

### Width Type

| Type      | 설명              | 사용            |
| --------- | --------------- | ------------- |
| Fill      | 가로 폭 최대 사용      | 테이블/리스트       |
| Contained | 최대 폭 제한 + 중앙 정렬 | 홈, 대시보드, 설정/폼 |

### 페이지 유형별 조합

| 사용자 행동       | Layout | Width                     | 예시            |
| ------------ | ------ | ------------------------- | ------------- |
| 데이터 목록 조회/검색 | Stack  | Fill                      | 상품 검색, 캠페인 목록 |
| 단순 설정/폼 입력   | Stack  | Contained 600px           | 작성 조건, 포인트 설정 |
| 설정 + 미리보기    | Split  | Fill (left 600px + right) | 키워드 리뷰        |
| 데이터 요약/대시보드  | Stack  | Contained 1200px          | 캠페인 통계        |
| 단계별 빌더/편집    | Stack  | Contained 1200px          | 캠페인 빌더        |
| 홈/랜딩/피드      | Stack  | Contained 1200px          | 홈 화면          |

### 판단 기준

1. 데이터를 훑고 찾는가? → Fill
2. 읽고 입력하는가? → Contained 600px
3. 한눈에 파악하는가? → Contained 1200px
4. 입력하면서 결과를 봐야 하는가? → Split (Fill, left 600px)
