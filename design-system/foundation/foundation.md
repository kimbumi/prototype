# Foundation Tokens v2

v1 토큰 체계 기반 + 피그마 바텀업 분석에서 도출한 의사결정 트리/가이드 통합.

---

## Spacing

### Primitive Tokens

4px 기반 스케일. 네이밍이 숫자인 이유: spacing-4 = 4×2 = 8px.

| Token | Value |
|-------|-------|
| `spacing-0` | `0px` |
| `spacing-1` | `2px` |
| `spacing-2` | `4px` |
| `spacing-3` | `6px` |
| `spacing-4` | `8px` |
| `spacing-5` | `10px` |
| `spacing-6` | `12px` |
| `spacing-8` | `16px` |
| `spacing-10` | `20px` |
| `spacing-12` | `24px` |
| `spacing-16` | `32px` |
| `spacing-20` | `40px` |
| `spacing-24` | `48px` |
| `spacing-32` | `64px` |

### 적용 규칙 (의사결정 트리)

**위에서부터 순서대로 질문. 먼저 걸리는 게 정답.**

#### Gap — 두 요소 사이 간격

```
Q1. 하나의 컨트롤을 구성하는가? (아이콘+텍스트, 체크박스+라벨)
    → Yes: spacing-2 (4px). Stop.

Q2. 같은 컴포넌트의 자식인가? (같은 toolbar, 같은 input group)
    → Yes: spacing-4 (8px). Stop.

Q3. 같은 부모에서 같은 템플릿으로 반복되는가? (리스트 row, 카드 반복)
    → Yes: spacing-6 (12px). Stop.

Q4. 같은 섹션 안에서 기능이 다른 블록인가? (스코어카드 옆 스코어카드)
    → Yes: spacing-8 (16px). Stop.

Q5. 같은 종류의 그룹이 묶여서 반복되는가? (폼그룹 + 폼그룹)
    → Yes: spacing-10 (20px). Stop.

Q6. 서로 다른 섹션인가?
    → Yes: spacing-12 (24px). Stop.

나머지: spacing-16 (32px) — 페이지 구조 전환
```

#### Padding — 컨테이너 내부 여백

```
Q1. 부모 안에서 형제와 같은 구조로 반복되는가?
    → Yes:
        Q1-1. 내부에 2줄 이상의 복합 콘텐츠가 있는가? (프로필+본문+이미지)
              → Yes: 20px y, 24px x. Stop.
              → No:  12px y. Stop.
    → No: Q2.

Q2. 전체 너비를 차지하고 내부가 한 줄인가?
    → Yes: 16px y, 24px x. Stop. (바: 헤더, 필터, 페이지네이션)
    → No: Q3.

Q3. 내부에서 사용자가 입력/편집/분석하는가?
    → Yes: 24px all. Stop. (본문: 폼 섹션, 차트, 미리보기)
    → No:  20px y, 24px x. Stop. (카드: 스코어카드, 배너, 독립 블록)
```

#### 페이지 여백 (고정)

```
좌/우/상 = spacing-12 (24px)
하 = spacing-16 (32px)
x패딩 = 항상 24px (예외 없음)
```

#### 원칙

1. **가로는 항상 24px** — 세로만 바꿔서 밀도 조절
2. **위에서 먼저 걸리면 멈춤** — Q3에 해당하면 Q4는 보지 않음
3. **의심되면 한 단계 위** — 좁으면 다음 토큰으로 올림

### CRM 화면별 참고

```
사이드바
  메뉴 아이템 패딩        spacing-3 (6) 상하, spacing-4 (8) 좌우
  메뉴 아이템 간 갭       spacing-1 (2)
  섹션 그룹 간 갭         spacing-6 (12)

테이블
  셀 패딩               spacing-3 (6) 상하, spacing-4 (8) 좌우
  헤더-바디 간           spacing-0 (보더로 구분)

카드 (기본)
  내부 패딩              spacing-8 (16)
  내부 요소 간 갭         spacing-4 (8)

카드 (컴팩트)
  내부 패딩              spacing-6 (12)
  내부 요소 간 갭         spacing-3 (6)

모달
  내부 패딩              spacing-12 (24)
  섹션 간 갭             spacing-8 (16)

폼
  필드 간 갭             spacing-6 (12)
  라벨-인풋 간            spacing-2 (4)
  인풋 내부 패딩          spacing-4 (8) 좌우, spacing-3 (6) 상하

페이지
  좌우 패딩              spacing-12 (24)
  헤더-콘텐츠 간          spacing-10 (20)
  섹션 간                spacing-10 (20)

대시보드
  KPI 카드 간 갭          spacing-6 (12)
  KPI 카드 내부 패딩       spacing-8 (16)
```

### Layout

```
Sidebar (254px) + Main
```

| Type      | 설명                        | 판단               |
| --------- | ------------------------- | ---------------- |
| Fill      | Main 영역 전체 사용             | **기본값.** 대부분의 화면 |
| Contained | max-width: 1200px + 중앙 정렬 | 시선 분산을 막아야 할 때만  |

---

## Color

### Primitive Tokens

#### Gray (Blue-tinted Cool Gray)

| Token | Value |
|-------|-------|
| `gray-0` | `#FFFFFF` |
| `gray-25` | `#FAFBFC` |
| `gray-50` | `#F4F6F8` |
| `gray-100` | `#EDF0F3` |
| `gray-150` | `#E3E7EC` |
| `gray-200` | `#D5DAE1` |
| `gray-300` | `#B8C0CC` |
| `gray-400` | `#8D97A5` |
| `gray-500` | `#6B7685` |
| `gray-600` | `#525C6A` |
| `gray-700` | `#3D4654` |
| `gray-800` | `#2A3040` |
| `gray-900` | `#1A1F2B` |
| `gray-950` | `#111318` |

#### Purple (Brand)

| Token | Value |
|-------|-------|
| `purple-50` | `#F5F2FF` |
| `purple-100` | `#EBE5FF` |
| `purple-200` | `#D4C8FF` |
| `purple-300` | `#B5A1FF` |
| `purple-400` | `#9B82FC` |
| `purple-500` | `#7C5CFC` |
| `purple-600` | `#6644E5` |
| `purple-700` | `#5236BF` |
| `purple-800` | `#3E2A94` |
| `purple-900` | `#2B1D6B` |

#### Status & Extended Palette

| | light | default | dark |
|--|-------|---------|------|
| **red** | `#FEF2F2` | `#EF4444` | `#B91C1C` |
| **amber** | `#FFFBEB` | `#F59E0B` | `#B45309` |
| **green** | `#F0FDF4` | `#22C55E` | `#15803D` |
| **blue** | `#EFF6FF` | `#3B82F6` | `#1D4ED8` |
| **teal** | `#F0FDFA` | `#14B8A6` | `#0F766E` |
| **cyan** | `#ECFEFF` | `#06B6D4` | `#0E7490` |
| **indigo** | `#EEF2FF` | `#6366F1` | `#4338CA` |
| **pink** | `#FDF2F8` | `#EC4899` | `#BE185D` |
| **orange** | `#FFF7ED` | `#F97316` | `#C2410C` |
| **violet** | `#F5F3FF` | `#8B5CF6` | `#6D28D9` |

### Semantic Tokens

#### Background

| Token | → Primitive | 용도 |
|-------|-------------|------|
| `bg-app` | gray-25 | 앱 전체 배경 |
| `bg-surface` | gray-0 | 카드, 패널, 모달, 드롭다운 |
| `bg-surface-secondary` | gray-50 | 테이블 헤더, 사이드바, 중첩 표면 |
| `bg-brand` | purple-500 | CTA 버튼, 브랜드 강조 영역 |
| `bg-brand-subtle` | purple-50 | 선택된 필터, 활성 메뉴 배경 |
| `bg-danger` | red-default | 삭제 버튼, 위험 액션 |
| `bg-danger-subtle` | red-light | 에러 배너, 실패 알림 배경 |
| `bg-success-subtle` | green-light | 성공 배너, 완료 알림 배경 |
| `bg-warning-subtle` | amber-light | 경고 배너, 만료 임박 알림 배경 |
| `bg-info-subtle` | blue-light | 정보 배너, 안내 알림 배경 |

#### Text

| Token              | → Primitive | 용도                      |
| ------------------ | ----------- | ----------------------- |
| `text-primary`     | gray-800    | 제목, 이름, 핵심 데이터          |
| `text-secondary`   | gray-600    | 본문, 테이블 셀, 필드 값         |
| `text-tertiary`    | gray-400    | 보조 정보, 부가 설명            |
| `text-placeholder` | gray-300    | 인풋 placeholder, 빈 상태 안내 |
| `text-disabled`    | gray-200    | 비활성 텍스트, 잠긴 필드          |
| `text-brand`       | purple-500  | 링크, 브랜드 강조, 선택된 탭       |
| `text-on-brand`    | gray-0      | 브랜드 배경 위 텍스트            |
| `text-on-danger`   | gray-0      | 위험 배경 위 텍스트             |
| `text-danger`      | red-dark    | 에러 메시지, 실패 상태 텍스트       |
| `text-success`     | green-dark  | 성공 메시지, 완료 상태 텍스트       |
| `text-warning`     | amber-dark  | 경고 메시지, 만료 임박 텍스트       |
| `text-info`        | blue-dark   | 정보 메시지, 신규/진행중 텍스트      |

#### Border

| Token | → Primitive | 용도 |
|-------|-------------|------|
| `border-default` | gray-150 | 카드 보더, 인풋, 디바이더, 테이블 구분선 |
| `border-strong` | gray-200 | 강조 보더, 섹션 구분 |
| `border-brand` | purple-500 | focus ring, 선택된 카드/인풋 |
| `border-danger` | red-default | 에러 상태 인풋 보더 |

#### Icon

| Token            | → Primitive   | 용도                |
| ---------------- | ------------- | ----------------- |
| `icon-primary`   | gray-700      | 기본 아이콘, 네비게이션     |
| `icon-secondary` | gray-500      | 보조 아이콘, 인풋 prefix |
| `icon-tertiary`  | gray-400      | 비활성 아이콘, 빈 상태     |
| `icon-brand`     | purple-500    | 브랜드 강조 아이콘, 활성 메뉴 |
| `icon-on-brand`  | gray-0        | 브랜드 배경 위 아이콘      |
| `icon-danger`    | red-default   | 삭제, 에러 아이콘        |
| `icon-success`   | green-default | 완료 체크, 성공 아이콘     |
| `icon-warning`   | amber-default | 주의 아이콘            |
| `icon-info`      | blue-default  | 정보 아이콘            |

### 텍스트 컬러 적용 규칙

```
Q1. 이 텍스트가 가장 중요한 정보인가? (타이틀, 핵심 숫자)
    → Yes: text-primary (gray-800). Stop.

Q2. 이 텍스트를 안 읽으면 기능을 못 쓰는가? (본문, 상품명, 리뷰 내용)
    → Yes: text-secondary (gray-600). Stop.

Q3. 보조 설명인가? (읽으면 도움 되지만 안 읽어도 됨)
    → Yes: text-tertiary (gray-400). Stop.

나머지 (placeholder, 비활성):
    → text-placeholder (gray-300) 또는 text-disabled (gray-200)
```

### 설계 원칙

1. **Gray는 블루 틴트** — 순수 회색이 아닌 hsl(220, 10-12%, ...) 계열
2. **Purple은 브랜드 전용** — 데이터 표현용 보라 계열은 violet/indigo 사용
3. **확장 컬러는 light/default/dark 3단계** — badge(light bg + dark text) 패턴
4. **hover/pressed 등 상태는 컴포넌트 레벨에서 정의**

---

## Typography

### Primitive Tokens

#### Font Family

| Token | Value |
|-------|-------|
| `font-family-base` | `'Pretendard', -apple-system, BlinkMacSystemFont, sans-serif` |
| `font-family-mono` | `'Pretendard Mono', 'SF Mono', monospace` |

#### Font Size

| Token | Value |
|-------|-------|
| `font-size-2xs` | `11px` |
| `font-size-xs` | `12px` |
| `font-size-sm` | `13px` |
| `font-size-md` | `14px` |
| `font-size-lg` | `16px` |
| `font-size-xl` | `20px` |
| `font-size-2xl` | `24px` |
| `font-size-3xl` | `32px` |

#### Font Weight

| Token | Value |
|-------|-------|
| `font-weight-regular` | `400` |
| `font-weight-medium` | `500` |
| `font-weight-semibold` | `600` |
| `font-weight-bold` | `700` |

#### Line Height

| Token | Value |
|-------|-------|
| `line-height-tight` | `1.2` |
| `line-height-snug` | `1.4` |
| `line-height-normal` | `1.5` |
| `line-height-relaxed` | `1.7` |

#### Letter Spacing

| Token | Value |
|-------|-------|
| `letter-spacing-tighter` | `-0.03em` |
| `letter-spacing-tight` | `-0.02em` |
| `letter-spacing-normal` | `-0.01em` |
| `letter-spacing-wide` | `0em` |

### Semantic Tokens

#### Heading — 복합 토큰

| Token             | Size     | Weight         | Line Height | Letter Spacing    |
| ----------------- | -------- | -------------- | ----------- | ----------------- |
| `type-display`    | 3xl (32) | bold (700)     | tight (1.2) | tighter (-0.03em) |
| `type-display-sm` | 2xl (24) | bold (700)     | tight (1.2) | tighter (-0.03em) |
| `type-heading-lg` | xl (20)  | semibold (600) | tight (1.2) | tighter (-0.03em) |
| `type-heading-md` | lg (16)  | semibold (600) | tight (1.2) | tight (-0.02em)   |
| `type-heading-sm` | md (14)  | semibold (600) | snug (1.4)  | tight (-0.02em)   |

#### type-md — 14px

| Token             | Weight         | Line Height   | Letter Spacing   |
| ----------------- | -------------- | ------------- | ---------------- |
| `type-md`         | regular (400)  | normal (1.5)  | normal (-0.01em) |
| `type-md-medium`  | medium (500)   | normal (1.5)  | normal (-0.01em) |
| `type-md-strong`  | semibold (600) | normal (1.5)  | normal (-0.01em) |
| `type-md-reading` | regular (400)  | relaxed (1.7) | normal (-0.01em) |

#### type-sm — 13px

| Token            | Weight         | Line Height | Letter Spacing   |
| ---------------- | -------------- | ----------- | ---------------- |
| `type-sm`        | regular (400)  | snug (1.4)  | normal (-0.01em) |
| `type-sm-medium` | medium (500)   | snug (1.4)  | normal (-0.01em) |
| `type-sm-strong` | semibold (600) | snug (1.4)  | normal (-0.01em) |

#### type-xs — 12px

| Token | Weight | Line Height | Letter Spacing |
|-------|--------|-------------|---------------|
| `type-xs` | regular (400) | snug (1.4) | normal (-0.01em) |
| `type-xs-medium` | medium (500) | snug (1.4) | normal (-0.01em) |
| `type-xs-strong` | semibold (600) | snug (1.4) | normal (-0.01em) |

#### type-2xs — 11px

| Token | Weight | Line Height | Letter Spacing |
|-------|--------|-------------|---------------|
| `type-2xs` | regular (400) | snug (1.4) | normal (-0.01em) |
| `type-2xs-medium` | medium (500) | snug (1.4) | normal (-0.01em) |

### 사용 가이드

#### 사이즈 선택 기준

| 사이즈            | 언제 쓰는가                        |
| -------------- | ----------------------------- |
| **32px (3xl)** | KPI 히어로 숫자, 온보딩 타이틀           |
| **24px (2xl)** | 페이지 타이틀, 대형 모달 타이틀            |
| **20px (xl)**  | 섹션 제목                         |
| **16px (lg)**  | 아이템 제목, 사이드바 그룹 헤더            |
| **14px (md)**  | 본문 기본, 설정 라벨, 인풋 텍스트, 사이드바 메뉴 |
| **13px (sm)**  | 테이블 보조 셀, 설정 보조 설명, 서브텍스트     |
| **12px (xs)**  | 테이블 헤더, 폼 라벨, 배지/태그, 탭        |
| **11px (2xs)** | 타임스탬프, 메타정보, 카운터              |

#### 웨이트 선택 기준

| 웨이트 | 언제 쓰는가 |
|--------|-----------|
| **regular (400)** | 읽기 위한 텍스트 — 본문, 설명, 필드 값 |
| **medium (500)** | 살짝 강조 — 사이드바 메뉴, 인라인 강조, 활성 탭 |
| **semibold (600)** | 구조를 잡는 텍스트 — 제목, 설정 라벨, 테이블 헤더 |
| **bold (700)** | 시선을 잡는 텍스트 — KPI 숫자, 히어로 |

#### 설계 원칙

1. **Heading은 역할로, Text는 사이즈로 고른다** — 제목은 `type-heading-*`에서, 본문 이하는 `type-md/sm/xs/2xs`에서 사이즈 먼저 고르고 웨이트를 붙인다.
2. **같은 사이즈에서 웨이트로 위계를 만든다** — 사이즈 점프 없이 regular → medium → semibold로 정보 중요도를 표현한다.
3. **행간과 자간은 사이즈에 종속된다** — 개별 조정하지 않는다.
4. **Pretendard 한글 기준 자간** — 기본이 -0.01em. 0em은 영문/숫자 전용(모노스페이스)에서만.

---

## Radius

### Primitive Tokens

| Token         | Value    | 용도 힌트                 |
| ------------- | -------- | --------------------- |
| `radius-none` | `0px`    | 직각                    |
| `radius-xs`   | `2px`    | 최소형 요소 (체크박스, 인라인 코드) |
| `radius-sm`   | `4px`    | 소형 요소 (배지, 태그, 소형 버튼) |
| `radius-md`   | `6px`    | 기본 요소 (버튼, 인풋)        |
| `radius-lg`   | `8px`    | 중형 요소 (카드, 드롭다운)      |
| `radius-xl`   | `12px`   | 대형 요소 (모달, 팝오버)       |
| `radius-2xl`  | `16px`   | 특대형 요소 (패널, 온보딩 카드)   |
| `radius-3xl`  | `20px`   | 최대형 요소 (모바일 미리보기, 시트) |
| `radius-full` | `9999px` | 원형 (아바타, pill, dot)   |

### 설계 원칙

1. **"살짝 둥근" 기준점은 6px** — 데스크탑 CRM의 기본 인터랙션 요소(버튼, 인풋)에 적용
2. **요소가 커지면 radius도 커진다** — 시각적 비례감 유지
3. **같은 컴포넌트도 사이즈별로 다를 수 있다** — 소형 버튼 radius-sm, 기본 버튼 radius-md, 대형 버튼 radius-lg
