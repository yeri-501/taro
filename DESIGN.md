# Tarot (타로) — Design System & Style Guide
> Midnight Tarot — 미드나잇 시네마와 신비로운 타로의 만남. 불 꺼진 심야의 방, 프로젝터의 불빛처럼 칠흑 같은 암흑(Void) 속에서 타로 카드와 당신만을 위한 텍스트만이 순수하게 빛납니다.

**Theme:** Dark (Universal Black Canvas)  
**Target Platform:** Mobile Web (360px ~ 430px 기준, 최대 480px 컨테이너)  
**Architecture:** Tailwind CSS v4 + shadcn/ui (Base UI & Radix Primitives)

---

## 1. 디자인 철학 및 비주얼 아이덴티티

- **Cinematic Void Canvas**: 불필요한 장식, 그라디언트 UI, 그림자(box-shadow)를 완전히 배제한 절대적인 블랙(`#000000`) 캔버스.
- **Typographic Gravity**: 볼드하고 절제된 타이포그래피. 산세리프(Helvetica/Inter/Pretendard)의 구조적 명확함, 세리프(Times New Roman/Myeongjo)의 서사적 깊이, 모노스페이스(Courier New)의 인덱스 텍스처를 조화롭게 사용합니다.
- **Card-Centric Illumination**: UI 크롬이 아닌 **타로 카드 그림**과 **엠버 코랄(Ember Coral)** 액센트만이 온기와 감정을 전달합니다.
- **Privacy & Transience (쓰고 바로 지우는 경험)**: 개인정보를 절대 보관하지 않는 서비스 원칙을 신뢰감 주는 하이콘트라스트 타이포그래피와 절제된 알림(Alert)으로 명확히 드러냅니다.

---

## 2. 디자인 토큰 (Tokens)

### 2.1 Color Tokens

| Name | Hex | Token | Shadcn Mapping | Role & Description |
|------|-----|-------|----------------|-------------------|
| **Void** | `#000000` | `--color-void` | `--background`, `--popover` | 전체 캔버스 바닥색, 모바일 배경 |
| **Soot** | `#0a0a0a` | `--color-soot` | `--card`, `--muted` | 카드 영역, 입력창 배경, 미세한 서피스 분리 |
| **Soot Light**| `#141414` | `--color-soot-light`| `--secondary` | 토글 버튼 비활성 상태, 보조 컨테이너 |
| **Bone** | `#ffffff` | `--color-bone` | `--foreground`, `--primary` | 메인 텍스트, 헤드라인, 고대비 버튼 배경, 카드 테두리 |
| **Ash** | `#8e8e93` | `--color-ash` | `--muted-foreground` | 보조 텍스트, 플레이스홀더, 비활성 캡션 |
| **Hairline Border** | `#262626` | `--color-hairline` | `--border`, `--input` | 1px 미세 구분선 및 외곽선 |
| **Ember Coral** | `#e1695e` | `--color-ember-coral` | `--accent-foreground` | 별자리 심볼, 카드 뒤집기 하이라이트 (UI 크롬에는 사용 금지) |
| **Burnt Sienna** | `#573332` | `--color-burnt-sienna`| (Content Only) | 타로 카드 후면 및 결과 카드 웜톤 백그라운드 |

### 2.2 Typography Scale & Families

- **Primary Sans (`--font-sans`)**: `Helvetica Neue`, `Inter`, `Pretendard`, system-ui
  - 일상 텍스트, 입력 필드, 내비게이션, 기본 본문
- **Display Serif (`--font-serif`)**: `Times New Roman`, `Playfair Display`, `Batang`, `Nanum Myeongjo`
  - 대 타이틀, 타로 카드 로마 숫자 및 카드 명칭, 에디토리얼 인용구
- **Texture Mono (`--font-mono`)**: `Courier New`, `JetBrains Mono`, monospace
  - 별자리 인덱스, 날짜 표기, 안내 뱃지, 슬레이트 마킹 텍스처

| Role | Family | Weight | Size | Line Height | Letter Spacing | Token |
|------|--------|--------|------|-------------|----------------|-------|
| **Display Large** | Serif | 400 | 44px ~ 52px | 0.95 | `-0.04em` (`-2.0px`) | `--text-display` |
| **Heading Hero** | Sans | 300 | 32px ~ 36px | 1.05 | `-0.03em` (`-1.0px`) | `--text-heading-hero` |
| **Heading Section** | Serif | 400 | 22px ~ 24px | 1.15 | `-0.02em` (`-0.5px`) | `--text-heading` |
| **Subheading** | Sans | 500 | 18px ~ 19px | 1.25 | `-0.01em` (`-0.2px`) | `--text-subheading` |
| **Body (해석 본문)** | Sans | 400 | 15px ~ 16px | 1.45 | `0` | `--text-body` |
| **Caption / Notice**| Sans | 400 | 13px ~ 14px | 1.40 | `0` | `--text-caption` |
| **Micro / Mono Tag** | Mono | 400 | 12px ~ 13px | 1.40 | `+0.10em` (`+1.3px`)| `--text-mono-tag` |

### 2.3 Spacing & Layout

- **Base Grid**: 4px
- **Mobile Container**: max-width `440px`, margin `0 auto`, horizontal padding `20px`
- **Section Gap**: 40px ~ 60px
- **Item / Component Gap**: 16px ~ 20px
- **Element Inner Gap**: 8px ~ 12px

### 2.4 Radius & Elevation

- **Card Radius**: `0px` (정통 시네마 프레임 및 포스터 룩, 결과 카드 1080×1350 기준)
- **Input Radius**: `8px` ~ `10px` (손끝 접촉 면적에 안정감을 주는 미세 라운딩)
- **Button Radius**: `0px` (샤프한 건축적 플랫 버튼)
- **Badge / Tag Radius**: `9999px` (Pill) 또는 `0px`
- **Elevation**: **0 (No Shadows)**. 그림자 일체 배제, 1px 헤어라인(`--border`)과 면 분할(`--card`)로만 레이어 형성.

---

## 3. Tailwind CSS v4 & Theme 설정

```css
/* app.css */
@import "tailwindcss";

@theme {
  /* Color Mappings */
  --color-void: #000000;
  --color-soot: #0a0a0a;
  --color-soot-light: #141414;
  --color-bone: #ffffff;
  --color-ash: #8e8e93;
  --color-hairline: #262626;
  --color-ember-coral: #e1695e;
  --color-burnt-sienna: #573332;

  /* Semantic Theme Tokens */
  --color-background: var(--color-void);
  --color-foreground: var(--color-bone);

  --color-card: var(--color-soot);
  --color-card-foreground: var(--color-bone);

  --color-popover: var(--color-soot);
  --color-popover-foreground: var(--color-bone);

  --color-primary: var(--color-bone);
  --color-primary-foreground: var(--color-void);

  --color-secondary: var(--color-soot-light);
  --color-secondary-foreground: var(--color-bone);

  --color-muted: var(--color-soot);
  --color-muted-foreground: var(--color-ash);

  --color-accent: var(--color-soot-light);
  --color-accent-foreground: var(--color-ember-coral);

  --color-destructive: #ef4444;
  --color-destructive-foreground: #ffffff;

  --color-border: var(--color-hairline);
  --color-input: var(--color-hairline);
  --color-ring: var(--color-bone);

  /* Radius Tokens */
  --radius-sm: 4px;
  --radius-md: 6px;
  --radius-lg: 8px;
  --radius-xl: 10px;
  --radius-2xl: 0px;
  --radius-full: 9999px;

  /* Typography */
  --font-sans: 'Pretendard', 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  --font-serif: 'Times New Roman', 'Playfair Display', 'Nanum Myeongjo', serif;
  --font-mono: 'Courier New', 'JetBrains Mono', monospace;

  /* 3D Card Animation */
  --animate-flip: flip-card 0.8s cubic-bezier(0.4, 0, 0.2, 1) forwards;
  --animate-fade-in: fade-in 0.3s ease-out forwards;

  @keyframes flip-card {
    0% {
      transform: rotateY(0deg);
    }
    100% {
      transform: rotateY(180deg);
    }
  }

  @keyframes fade-in {
    from {
      opacity: 0;
      transform: translateY(6px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
}
```

---

## 4. shadcn/ui 컴포넌트 규칙 및 설계

### 4.1 Buttons (`Button`)

- **원칙**: 높이 52px(모바일 터치 최적화), 0px radius, 플랫한 고대비 디자인.
- **Variants**:
  - `default` (Primary CTA): `bg-white text-black hover:bg-neutral-200 active:scale-[0.99] font-medium tracking-tight rounded-none h-13`
  - `secondary`: `bg-neutral-900 text-white border border-neutral-800 hover:bg-neutral-800 rounded-none h-13`
  - `outline`: `border border-white/60 text-white bg-transparent hover:border-white hover:bg-white/10 rounded-none h-13`
  - `ghost`: `text-neutral-400 hover:text-white bg-transparent h-auto py-2 hover:border-b hover:border-white rounded-none`
- **아이콘 규칙**: 버튼 내 아이콘은 `data-icon="inline-start"` 또는 `data-icon="inline-end"` 사용.

### 4.2 Forms & Inputs (`FieldGroup`, `Field`, `Input`)

- **구조**: `FieldGroup` + `Field` + `FieldLabel` + `Input` + `FieldError` 구조 준수.
- **Input 스타일**:
  - 배경: `#0a0a0a`
  - 테두리: `1px solid #262626`
  - 포커스: 테두리가 `#ffffff`로 1px 유지되며 미세한 백색 아웃라인(ring 없이 순수 보더 강조)
  - 폰트: `16px font-sans` (iOS 자동 줌 방지 필수 조건 16px 이상)
  - Radius: `rounded-lg` (8px~10px)

### 4.3 Topic Selector (`ToggleGroup`)

- **주제 6개 (F-2)**: `💼 커리어`, `💰 재물`, `💕 연애`, `🌿 건강`, `📚 학업`, `✨ 종합`
- **구조**:
  ```tsx
  <ToggleGroup type="single" value={selectedTopic} onValueChange={setSelectedTopic} className="grid grid-cols-3 gap-2.5">
    {TOPICS.map((topic) => (
      <ToggleGroupItem
        key={topic.id}
        value={topic.id}
        className="h-12 border border-neutral-800 bg-neutral-950 text-neutral-300 data-[state=on]:border-white data-[state=on]:bg-white data-[state=on]:text-black rounded-none transition-colors"
      >
        {topic.label}
      </ToggleGroupItem>
    ))}
  </ToggleGroup>
  ```

### 4.4 Result Card Frame & 3D Flip (`Card`)

- **결과 카드 컴포넌트 (F-4, F-5)**:
  - 1080×1350(4:5 비율) 저장 규격에 대응하는 세로형 프레임.
  - 테두리: `1px solid #262626`, 배경 `#0a0a0a`, 패딩 `24px`.
  - **Flip Mechanism**:
    ```tsx
    <div className="perspective-1000 w-full max-w-[280px] aspect-[2/3] mx-auto">
      <div className={cn("relative w-full h-full transition-transform duration-700 transform-style-3d", isFlipped && "rotate-y-180")}>
        {/* 카드 뒷면 (S-01 및 플립 전) */}
        <div className="absolute inset-0 backface-hidden border border-neutral-800 bg-[#0c0c0e] flex items-center justify-center">
          <CardBackArtwork />
        </div>
        {/* 카드 앞면 (타로 일러스트) */}
        <div className="absolute inset-0 backface-hidden rotate-y-180 border border-white/20 bg-black">
          <TarotArtwork src={card.image} alt={card.name} />
        </div>
      </div>
    </div>
    ```

### 4.5 Badges & Tags (`Badge`)

- **별자리 및 메타 라벨 (F-4)**:
  - `font-mono uppercase tracking-[0.12em] text-[12px] py-1 px-2.5 border border-neutral-800 text-neutral-300 bg-neutral-950 rounded-full`
  - 예시: `♌ LEO · 사자자리`, `ARCANUM XIX`

### 4.6 Notice Callouts (`Alert`)

- **개인정보 안내 (원칙 1) & 오락용 안내 (원칙 4)**:
  ```tsx
  <Alert className="border-neutral-800 bg-neutral-950/80 text-neutral-400 rounded-none p-3.5">
    <AlertDescription className="text-xs leading-relaxed flex items-center gap-2">
      <LockIcon className="size-3.5 text-neutral-500 shrink-0" />
      <span>입력한 정보는 해석 제작 후 즉시 폐기되며 서버로 전송·저장되지 않습니다.</span>
    </AlertDescription>
  </Alert>
  ```

### 4.7 Toast Feedback (`toast` from sonner)

- **피드백 상태 (F-5, F-6)**:
  - 이미지 저장 성공: `toast("이미지를 저장했어요")`
  - 이미지 저장 불가 인앱: 다이얼로그로 이미지 팝업 + "길게 눌러 저장해 주세요"
  - 결과 복사 완료: `toast("결과를 복사했어요. 원하는 앱에 붙여 넣어 주세요")`

---

## 5. 화면별 상세 UI 스펙 (Screen Specifications)

### S-01 시작 화면 (F-1)
- **배경**: Full-bleed `#000000`
- **헤더/타이틀**:
  - `font-serif text-[42px] leading-none text-white tracking-[-0.04em]` → `🔮 오늘의 타로`
  - 서브 카피: `font-sans text-[15px] text-neutral-400 mt-3` → "내 정보를 넣고 카드 한 장으로 나만의 해석을 받아 봐요"
- **중앙 비주얼**:
  - 신비로운 패턴의 타로 카드 뒷면 (가로 180px × 세로 270px)
- **하단 액션**:
  - `Button default h-13 w-full` → `[ 타로 시작 ]`
  - 푸터 안내: `text-[12px] text-neutral-500 font-mono text-center` → "※ 오락용 타로 · 정보는 저장 안 해요"

### S-02 내 정보 & 주제 선택 화면 (F-2)
- **상단 내비게이션**: 뒤로가기 화살표 (`← 나에 대해 알려 주세요`)
- **입력 폼**:
  - 이름 (닉네임 가능, 최대 10자)
  - 생년월일 (YYYY . MM . DD — 숫자 키패드 지원 및 유효 날짜 검증)
  - 전공 (선택 사항, 플레이스홀더: "예: 경영학과, 디자인과")
- **주제 선택 그리드**:
  - 6개 토글 아이템 (2행 3열)
- **개인정보 폐기 안내 배너**:
  - 헤어라인 보더의 컴팩트 Alert (잠금 아이콘 + 파기 원칙)
- **하단 CTA**:
  - `[ 카드 한 장 뽑기 ]` (이름, 생년월일, 주제 미입력 시 `disabled` 상태 유지)

### S-03 맞춤 해석 결과 화면 (F-4 ~ F-7)
- **중앙 결과 카드 영역 (1080×1350 캡처 캔버스 대상)**:
  1. Header: `{이름}님의 타로 · {주제}` (`font-sans font-medium text-16 text-white`)
  2. Visual: 1초 플립 효과와 함께 드러난 타로 카드 정방향 일러스트
  3. Index: `XIX 태양 · ♌ 사자자리` (`font-serif text-20 text-white` + `font-mono tag`)
  4. Interpretation (3줄 이내, 90자 안팎):
     - Line 1 (기본): `준비한 것을 드러낼 때예요.`
     - Line 2 (별자리): `사자자리의 자신감이 무기가 돼요.`
     - Line 3 (전공): `경영학도다운 기획력이 빛나요.`
  5. Footer Notice: `※ 오락용 타로 해석입니다`
- **하단 액션 버튼 그룹**:
  - Row 1: `[ 이미지 저장 ]` (Primary White) + `[ 결과 공유 ]` (Secondary Dark)
  - Row 2: `[ 다시 뽑기 ]` (Outline) + `[ 처음으로 ]` (Ghost Text - 정보 삭제 강조)
- **하단 안내**: "🔒 정보는 저장되지 않아요. [처음으로]를 누르면 바로 지워져요."

---

## 6. Do's & Don'ts (규칙)

### Do
- **Do**: 전체 캔버스를 `#000000`으로 고정하고 모바일 뷰포트 높이(100dvh)에 최적화합니다.
- **Do**: 타이포그래피 계층을 엄격히 분리합니다 (Serif: 타이틀/카드명, Sans: 본문/폼, Mono: 별자리/안내).
- **Do**: 결과 카드 영역은 정밀하게 4:5 비율을 유지하여 인스타그램 스토리 및 이미지 저장이 깨끗하게 되도록 합니다.
- **Do**: 버튼과 폼 상태 변경 시 150ms 이내의 절제된 트랜지션만 사용합니다.
- **Do**: 개인정보 미저장 원칙을 사용자가 안심할 수 있도록 입력 전후에 반복해서 고지합니다.

### Don't
- **Don't**: 버튼, 뱃지, 배경에 컬러풀한 그라디언트나 채도 높은 원색을 절대 적용하지 마십시오 (UI는 모노크롬 유지).
- **Don't**: 컴포넌트에 입체 그림자(`box-shadow`, `drop-shadow`)를 넣지 마십시오. 오직 1px 선과 면 대비로만 표현합니다.
- **Don't**: 카드 컨테이너 모서리를 둥글게 깎지 마십시오 (`rounded-0`).
- **Don't**: 건강·재물 운세 문구에 절대적인 예언 단정형 표현(예: "돈을 벌게 됩니다")을 쓰지 마십시오.
- **Don't**: 이미지 저장 시나 공유 링크에 생년월일이나 전공 원문을 외부에 노출하지 마십시오.
