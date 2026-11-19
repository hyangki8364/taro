# 오늘의 타로 (Today's Tarot) — Style & Design System Guide
> **Celestial Twilight over Parchment.**  
> 깊은 우주의 미드나잇 잉크와 따뜻한 양피지 캔버스 위에, 볼드한 활자와 단 하나의 테라코타 앰버 액센트가 절제된 신비로움을 완성합니다.

**Theme:** Mystic Modern Editorial (모던 에디토리얼 타로)  
**Target:** 20대 대학생 및 사회초년생을 위한 모바일 퍼스트 웹 서비스  
**Framework Target:** Tailwind CSS v4 (`@theme`), shadcn/ui (CVA 기반 컴포넌트)

---

## 1. 디자인 철학 및 비주얼 아이덴티티

- **Editorial Restraint (절제된 신비감)**  
  조잡한 네온 보라색이나 클립아트풍 그래픽을 배제하고, 고급 오라클 카드 및 킨포크/에디토리얼 매거진의 감성을 담았습니다.
- **Typographic Gravity (무게감 있는 타이포그래피)**  
  헤드라인은 단단하고 굵은 자간(-0.02em)으로 돌에 새긴 듯한 권위를 부여하고, 본문은 1.61의 넉넉한 줄간격으로 깊은 호흡을 선사합니다.
- **Pill & Monolith Contrast (실루엣 대비)**  
  손에 닿는 모든 인터랙션 요소는 유려한 완전 타원형 필(`rounded-full`), 정적인 타로 카드와 결과 프레임은 각진 모놀리스 형태(`rounded-xl` / `rounded-none`)로 구성하여 긴장감과 몰입감을 줍니다.
- **Single Focal Accent (단 하나의 온기)**  
  전체 시스템은 딥 잉크와 퓨어 화이트의 모노크롬을 유지하며, 단 하나의 온기인 **클레이 앰버(Clay Ember, `#bc7155`)**로 뽑힌 카드와 핵심 전환 액션(CTA)을 밝힙니다.

---

## 2. 디자인 토큰 — 컬러 (Colors)

### 2.1 브랜드 컬러 팔레트 (Brand Palette)

| 명칭 (Token Name) | Hex | Role & Usage |
|---|---|---|
| **Deep Ink** | `#000d10` | 텍스트 기본색, 메인 다크 액션 버튼, 푸터, 아이콘 스트로크 |
| **Midnight Cosmic** | `#0f0f1c` | 타로 카드 뒷면 배경, 다크 테마 섹션, 우주적 깊이감 |
| **Charcoal Deck** | `#151623` | 다크 섹션 내 카드/패널 표면 |
| **Clay Ember** | `#bc7155` | **핵심 포인트 컬러** (선택된 주제 태그, 메인 뽑기 CTA, 강조 문구) |
| **Pure White** | `#ffffff` | 기본 페이지 배경, 카드 표면, 다크 버튼 위의 텍스트 |
| **Parchment Light**| `#fbfaf8` | 결과 카드 배경, 입력 폼 배경 (종이의 질감 느낌) |
| **Pebble Border** | `#d5d3d4` | 헤어라인 구분선, 카드 테두리, 비활성 버튼 보더 |
| **Cool Ash** | `#8e8e95` | 보조 설명 텍스트, 안내 문구, 미선택 토글 상태 |

### 2.2 시맨틱 컬러 매핑 (shadcn / Tailwind v4 Semantic Tokens)

```css
@theme {
  --color-background: #ffffff;
  --color-foreground: #000d10;

  /* Primary: 신뢰감 있고 단단한 Deep Ink */
  --color-primary: #000d10;
  --color-primary-foreground: #ffffff;

  /* Accent: 타로의 신비로운 불씨를 상징하는 Clay Ember */
  --color-accent: #bc7155;
  --color-accent-foreground: #ffffff;

  /* Secondary & Muted: 안정적인 그레이 계열 */
  --color-secondary: #fbfaf8;
  --color-secondary-foreground: #000d10;
  --color-muted: #f4f3f1;
  --color-muted-foreground: #8e8e95;

  /* Surface & Border */
  --color-card: #ffffff;
  --color-card-foreground: #000d10;
  --color-border: #d5d3d4;
  --color-ring: #bc7155;

  /* Destructive */
  --color-destructive: #d93d3d;
  --color-destructive-foreground: #ffffff;
}
```

---

## 3. 디자인 토큰 — 타이포그래피 (Typography)

### 3.1 서체 지정
- **영문 / 숫자 / 디스플레이**: `HelveticaNowDisplay`, `Pretendard`, `Inter`, `sans-serif`
- **한글 본문**: `Pretendard`, `-apple-system`, `BlinkMacSystemFont`, `sans-serif`
- **타로 상징 (로마자/별자리)**: Serif 계열 또는 Classical Roman Display (`Cinzel`, `Didot`, `Georgia`)

### 3.2 타입 스케일 (Type Scale)

| Role | 크기 (Size) | 자간 (Tracking) | 줄간격 (Leading) | 굵기 (Weight) | 용도 |
|---|---|---|---|---|---|
| **Hero Display** | 44px / 52px | -0.03em | 1.1 | 700 (Bold) | 시작 화면 타이틀 (`오늘의 타로`) |
| **Card Roman** | 30px / 36px | +0.05em | 1.0 | 700 (Bold) | 카드 로마자 및 이름 (`XIX 태양`) |
| **Heading** | 24px / 28px | -0.02em | 1.2 | 700 (Bold) | 스크린 헤더, 질문 섹션 헤딩 |
| **Subheading** | 18px / 20px | -0.01em | 1.3 | 600 (SemiBold) | 주제 선택 라벨, 사용자 결과 타이틀 |
| **Body (해석)** | 16px / 18px | 0 | **1.61 (넉넉함)** | 400 / 500 | 3줄 맞춤 해석 (가독성 최우선) |
| **Button / Nav** | 15px / 16px | 0 | 1.0 | 600 (SemiBold) | 필 버튼, 토글 칩 라벨 |
| **Caption / Legal**| 12px / 13px | 0 | 1.4 | 400 (Regular) | 개인정보 폐기 안내문, 오락용 경고 |

---

## 4. 디자인 토큰 — 간격, 레이아웃 및 쉐이프

### 4.1 모바일 뷰포트 레이아웃
- **최대 너비 (Max Width)**: `440px` (모바일 디바이스 최적화, 데스크톱 접속 시 중앙 카드형 뷰)
- **페이지 여백 (Padding X)**: `20px` (좌우 기본 패딩)
- **섹션 간격 (Section Gap)**: `32px` ~ `48px`

### 4.2 쉐이프 & 보더 반경 (Border Radius)

| 요소 | 토큰 값 | Tailwind 클래스 | 형태적 의미 |
|---|---|---|---|
| **Buttons & Action Pills** | `9999px` | `rounded-full` | 누르고 싶은 부드러운 알약 모양 |
| **Topic Selector Chips** | `9999px` | `rounded-full` | 6개 주제 선택 태그 버튼 |
| **Tarot Card Object** | `16px` | `rounded-2xl` | 전통적인 타로 카드의 안정적 라운딩 |
| **Form Inputs** | `12px` | `rounded-xl` | 모던하고 단정한 인풋 박스 |
| **Result Snapshot Card** | `20px` | `rounded-3xl` | 이미지 저장용 1080×1350 카드 캔버스 |

---

## 5. 컴포넌트 규격 (Component Specifications)

### 5.1 버튼 (Button - CVA Variants)

1. **Primary Action Pill (`variant: "default"`)**
   - 배경: Deep Ink (`#000d10`) 또는 활성화 시 Clay Ember (`#bc7155`)
   - 텍스트: Pure White (`#ffffff`), 16px, font-semibold
   - 반경: `rounded-full`, 높이: `h-14` (56px, 엄지손가락 터치 최적화)
   - 용도: `[타로 시작]`, `[카드 한 장 뽑기]`, `[이미지 저장]`
2. **Secondary Outline Pill (`variant: "outline"`)**
   - 배경: 투명, 테두리: 1px `#d5d3d4`, 텍스트: Deep Ink (`#000d10`)
   - 용도: `[결과 공유]`, `[다시 뽑기]`
3. **Ghost / Tertiary Link (`variant: "ghost"`)**
   - 배경: 없음, 텍스트: Cool Ash (`#8e8e95`), `text-sm underline`
   - 용도: `[처음으로] (정보 지우기)`

### 5.2 6개 주제 선택 칩 (Topic Chips)
- **주제 목록**: `💼 커리어`, `💰 재물`, `💕 연애`, `🌿 건강`, `📚 학업`, `✨ 종합`
- **미선택 상태**: 배경 `#fbfaf8`, 테두리 1px `#d5d3d4`, 텍스트 `#8e8e95`
- **선택된 상태**: 배경 `#bc7155` (Clay Ember), 테두리 1px `#bc7155`, 텍스트 `#ffffff`, 살짝 확대(`scale-[1.02]`)

### 5.3 개인정보 안심 안내 박스 (Privacy Reassurance Box)
- **배경**: `#fbfaf8` (미세한 웜그레이 틴트)
- **보더**: 1px `#e2e0dc`
- **아이콘**: 🔒 자물쇠 (Deep Ink `#000d10`)
- **문구**: *"입력한 이름 · 생년월일 · 전공은 해석을 만드는 데만 쓰고, 서버로 보내거나 저장하지 않아요. 창을 닫거나 [처음으로]를 누르면 바로 지워져요."*

### 5.4 타로 카드 및 3D 플립 애니메이션 (Tarot Card & Flip)
- **비율**: 가로 1 : 세로 1.65 (황금비율 타로 카드)
- **앞면 (Front)**: 22장 메이저 아르카나 일러스트레이션 + 황금빛/화이트 프레임
- **뒷면 (Back)**: Midnight Cosmic (`#0f0f1c`) 배경에 섬세한 기하학적 성운/달/별 은박 문양
- **애니메이션**: 1초 이내 부드러운 3D Y축 회전 (`transform-style: preserve-3d; transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1)`)

### 5.5 결과 저장 카드 (1080×1350 Instagram Story Card)
- **비율**: 4:5 고해상도 규격 (1080px × 1350px)
- **배경**: Parchment Light (`#fbfaf8`) 단색 바탕에 미세한 테두리
- **포함 요소**:
  1. 헤더: `{이름}님의 타로 · {주제}` (예: *지민님의 타로 · 커리어*)
  2. 중앙: 타로 카드 일러스트 & 명칭 (*XIX 태양 · ♌ 사자자리*)
  3. 해석 본문: 정갈한 3줄 해석 (줄간격 1.61)
  4. 하단: `※ 오락용 타로 해석입니다` + 로고 워터마크 `오늘의 타로 (Today's Tarot)`
- **제외 요소 (원칙 준수)**: 생년월일 및 전공 원문 텍스트는 절대 포함하지 않음.

---

## 6. Tailwind CSS v4 `@theme` 설정 (app.css)

```css
@import "tailwindcss";

@theme {
  /* 색상 토큰 */
  --color-deep-ink: #000d10;
  --color-pure-white: #ffffff;
  --color-cool-ash: #8e8e95;
  --color-pebble: #d5d3d4;
  --color-midnight-hull: #0f0f1c;
  --color-charcoal-deck: #151623;
  --color-clay-ember: #bc7155;
  --color-parchment: #fbfaf8;

  /* 시맨틱 매핑 */
  --color-background: var(--color-pure-white);
  --color-foreground: var(--color-deep-ink);
  --color-primary: var(--color-deep-ink);
  --color-primary-foreground: var(--color-pure-white);
  --color-accent: var(--color-clay-ember);
  --color-accent-foreground: var(--color-pure-white);
  --color-muted: var(--color-parchment);
  --color-muted-foreground: var(--color-cool-ash);
  --color-border: var(--color-pebble);

  /* 폰트 패밀리 */
  --font-sans: 'Pretendard', -apple-system, BlinkMacSystemFont, system-ui, sans-serif;
  --font-serif: 'Cinzel', 'Georgia', serif;

  /* 타이포그래피 줄간격 */
  --leading-editorial: 1.618;

  /* 애니메이션 키프레임 (카드 뒤집기) */
  --animate-card-flip: card-flip 0.8s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;

  @keyframes card-flip {
    from {
      transform: rotateY(180deg) scale(0.95);
      opacity: 0.8;
    }
    to {
      transform: rotateY(0deg) scale(1);
      opacity: 1;
    }
  }
}
```

---

## 7. shadcn/ui 기반 컴포넌트 패턴 (CVA 예시)

```typescript
// components/ui/button.tsx
import { cva, type VariantProps } from 'class-variance-authority'

export const buttonVariants = cva(
  'inline-flex items-center justify-center whitespace-nowrap rounded-full text-base font-semibold transition-all duration-200 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-accent focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-40 active:scale-[0.98]',
  {
    variants: {
      variant: {
        default: 'bg-deep-ink text-pure-white hover:bg-black',
        accent: 'bg-clay-ember text-pure-white hover:bg-[#a66147] shadow-sm',
        outline: 'border border-pebble bg-transparent text-deep-ink hover:bg-parchment',
        ghost: 'text-cool-ash hover:text-deep-ink underline-offset-4 hover:underline',
      },
      size: {
        default: 'h-14 px-6 py-3',
        sm: 'h-10 px-4 text-sm',
        lg: 'h-16 px-8 text-lg',
        icon: 'size-12 rounded-full',
      },
    },
    defaultVariants: {
      variant: 'default',
      size: 'default',
    },
  }
)
```

---

## 8. 디자인 원칙 및 Do's & Don'ts

### ✅ Do (권장 사항)
- **3줄 해석의 리듬 유지**: 3줄 해석은 최대 90자 이내로 구성하며, `leading-[1.61]`을 적용해 시선이 편안하게 머무르도록 합니다.
- **오락용 및 안심 안내 표기**: 결과 카드와 입력 화면에 오락용 타로임을 밝히고, 저장이 없음을 명시하여 신뢰도를 유지합니다.
- **알약 버튼(Pill) 일관성**: 모든 인터랙션 버튼은 `rounded-full`을 유지하여 모바일에서 자연스럽게 터치할 수 있도록 합니다.
- **클레이 앰버(`#bc7155`)의 절제된 사용**: 화면당 시선이 머물러야 하는 핵심 요소(예: 활성화된 버튼, 선택된 태그) 1~2곳에만 포인트로 사용하여 시각적 피로를 방지합니다.

### ❌ Don't (금지 사항)
- **과도한 그림자나 그라디언트 금지**: 싸구려 앱 느낌을 주는 무지개빛 그라디언트나 짙은 드롭 섀도를 지양하고, 맑은 단색 면 분할과 미세한 헤어라인으로 깊이를 표현합니다.
- **건강·재물에 대한 단정적 어조 금지**: 디자인 텍스트 배치 시 "돈을 법니다" 대신 "지출을 점검할 시기예요"와 같은 조언형 문구로 구성합니다.
- **결과 이미지에 민감 정보 삽입 금지**: 1080×1350 카드 이미지에 사용자의 주민등록번호나 생년월일 원문이 찍혀 나오지 않도록 엄격히 차단합니다.
