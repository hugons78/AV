# Component Documentation — Assistente Virtual NOS (AV Chat)

Extracted from Figma file `gelKDCV6CKxnuhnZ7oEgcO`.

---

## `widget-header`

**Node ID:** `7842:4019`
**Type:** Instance
**Figma URL:** https://www.figma.com/design/gelKDCV6CKxnuhnZ7oEgcO/Assistente-Virtual-NOS--AV-Chat-?node-id=7842-4019

### Screenshot

> Turquoise header bar with a title on the left and two icons (chevron down, close) on the right.

```
┌──────────────────────────────────────────┐
│  Em que podemos ajudar?          ∨    ✕  │
└──────────────────────────────────────────┘
```

---

### Dimensions

| Property | Value |
|---|---|
| Width | 360px (full widget width) |
| Height | 102px |
| Padding top | 4px |
| Padding bottom | 24px |
| Padding horizontal | 20px |

---

### Anatomy

```
widget-header
└── Title Page + icons                (row, space-between)
    ├── Main title
    │   └── <p> title text
    └── Icons                         (row, gap 24px)
        ├── Navegação / Chevron       (24×24px, rotated 90°)
        │   └── icon (SVG/img)
        └── ic_close                  (32×32px, rotated 45°)
            └── Close (SVG/img)
```

---

### Tokens

| Property | Token | Value |
|---|---|---|
| Background | `--nos-color-brand-bg-turquoise-500` | `#4bdbc5` |
| Title color | `Neutral/Grey 900` | `#1e1f27` |
| Shadow | `level 1` | `drop-shadow(0 2px 8px #00000014)` |

---

### Typography

| Element | Style | Family | Weight | Size | Line Height |
|---|---|---|---|---|---|
| Title | `Title/2XS Medium` | Azo Sans | 500 (Medium) | 18px | 26px |

---

### Icons

| Name | Node | Size | Transform | Description |
|---|---|---|---|---|
| Navegação / Chevron | `I7842:4019;4002:3741` | 24×24px | `rotate(90deg)` | Collapse / minimise widget |
| ic_close | `I7842:4019;4002:3742` | 32×32px | `rotate(45deg)` | Close / dismiss widget |

> The chevron icon inner image is 8.12×13.41px; the close icon inner image is 21.33×21.33px.

---

### Shadow

| Token | Type | Color | Offset X | Offset Y | Blur | Spread |
|---|---|---|---|---|---|---|
| `level 1` | Drop Shadow | `#00000014` (8% opacity) | 0 | 2px | 8px | 0 |

---

### Layout Notes

- The header uses a **column flex** container (`flex-col`) centred horizontally.
- The inner row (`Title Page + icons`) uses `justify-between` to push the title left and icons right.
- Icons row uses a fixed `gap` of **24px**.
- The component spans the **full width** of the widget (360px) and is **absolutely positioned at the top** (y = 0) of the widget container.

---

### Reference Code (React + Tailwind)

```jsx
export default function WidgetHeader() {
  return (
    <div
      className="bg-[var(--nos-color-brand-bg-turquoise-500,#4bdbc5)]
                 flex flex-col items-center
                 pb-[24px] pt-[4px] px-[20px]
                 shadow-[0px_2px_8px_0px_rgba(0,0,0,0.08)]
                 w-full"
    >
      {/* Title + Icons row */}
      <div className="flex items-center justify-between w-full">

        {/* Title */}
        <p className="font-['Azo_Sans'] font-medium text-[18px] leading-[26px] text-[#1e1f27] whitespace-nowrap">
          Em que podemos ajudar?
        </p>

        {/* Icons */}
        <div className="flex items-center gap-[24px]">

          {/* Chevron — collapse */}
          <div className="size-[24px] overflow-clip">
            <img
              src={imgIcon}
              alt="Minimizar"
              className="w-[8.12px] h-[13.41px] rotate-90"
            />
          </div>

          {/* Close */}
          <div className="size-[32px] overflow-clip">
            <img
              src={imgClose}
              alt="Fechar"
              className="size-[21.33px] rotate-45"
            />
          </div>

        </div>
      </div>
    </div>
  );
}
```

> Adapt to the target stack — replace Tailwind utilities with the project's CSS/token system as needed.

---

## `Av Chat Buttons`

**Node ID:** `26477:10792`
**Type:** Frame (component set — 6 variants)
**Source file:** `-00MN- Experience myNOS` (`xw0F3wBnDmyjRLn4hk13xF`)
**Figma URL:** https://www.figma.com/design/xw0F3wBnDmyjRLn4hk13xF/-00MN--Experience-myNOS?node-id=26477-10792

### Overview

Selectable choice button used in the AV chat flow. Presents options to the user as bordered cards. Comes in two content types (title only, or title + description) and three interaction states (default, hover, disabled).

---

### Variants

The component has **2 axes** producing **6 combinations**:

| Node ID | State | Type | Width | Height |
|---|---|---|---|---|
| `26477:10786` | Default | Title and description | 320px | 72px |
| `26477:10787` | Hover | Title and description | 320px | 72px |
| `26477:10788` | Disabled | Title and description | 320px | 72px |
| `26477:10791` | Default | Title | max-w 320px | 50px |
| `26477:10790` | Hover | Title | max-w 320px | 50px |
| `26477:10789` | Disabled | Title | max-w 320px | 50px |

---

### Visual Reference

**Type = Title and description**
```
┌──────────────────────────────────────────┐
│ A. Casa de Lisboa                        │  ← bold title
│ Rua das Forças Armadas 56, 2º Esq...     │  ← regular description (truncated)
└──────────────────────────────────────────┘
```

**Type = Title**
```
┌──────────────────────────────┐
│ B. Rua Silva Porto, 23, 5.º B, Porto     │  ← bold title, wraps
└──────────────────────────────┘
```

---

### Anatomy

```
Av Chat Buttons                     (card container)
└── Content                         (flex col, gap 4px)
    ├── title                       (bold text — always present)
    └── description                 (regular text — Type="Title and description" only)
```

---

### Tokens

#### Container

| Property | Token | Default | Hover | Disabled |
|---|---|---|---|---|
| Background | `--nos-color-neutral-000` | `#ffffff` | `#ffffff` | `#ffffff` |
| Border colour | `--nos-color-border-neutral-1000` | `#000000` | — | — |
| Border colour | `--nos-color-border-neutral-600` | — | `#404149` | — |
| Border colour | `--nos-color-border-neutral-400` | — | — | `#74757d` |
| Border width | `--nos-border-width-1` (implied) | `1px` | `1px` | `1px` |
| Border radius | `--nos-spacing-fixed-4` | `16px` | `16px` | `16px` |
| Padding | `--nos-spacing-fixed-4` | `16px` (all sides) | `16px` | `16px` |

#### Content

| Property | Token | Default | Hover | Disabled |
|---|---|---|---|---|
| Title colour | `--nos-color-text-neutral-900` | `#1e1f27` | — | — |
| Title colour | `--nos-color-text-neutral-600` | — | `#404149` | — |
| Title colour | `--nos-color-text-neutral-400` | — | — | `#74757d` |
| Description colour | (same as title per state) | `#1e1f27` | `#404149` | `#74757d` |
| Content gap | `--nos-spacing-fixed-1` | `4px` | `4px` | `4px` |

---

### Typography

| Element | Style | Family | Weight | Size | Line Height |
|---|---|---|---|---|---|
| Title | `UI/Bold (700)/UI9` | Azo Sans Web | 700 | `--nos-font-size-ui-200` (14px) | `Font/Line-Height/ui-200` (18px) |
| Description | `UI/Regular (400)/UI9` | Azo Sans Web | 400 | `--nos-font-size-ui-200` (14px) | `Font/Line-Height/ui-200` (18px) |

> Description text truncates with `overflow: hidden` / `text-overflow: ellipsis` on a single line.

---

### State Behaviour

| State | Border | Text | Interactive |
|---|---|---|---|
| `Default` | Black (`#000000`) | Dark (`#1e1f27`) | Clickable |
| `Hover` | Dark grey (`#404149`) | Dark grey (`#404149`) | Hovered |
| `Disabled` | Light grey (`#74757d`) | Muted grey (`#74757d`) | Not clickable |

---

### Type Behaviour

| Type | Content shown | Width | Height |
|---|---|---|---|
| `Title` | Bold label only — wraps across lines | `max-w: 320px` | ~50px (auto) |
| `Title and description` | Bold label + regular one-line description | Fixed `320px` | ~72px |

---

### Layout Notes

- `Type=Title` uses `max-w-[320px]` and `shrink-0 w-[226px]` on the content — width adapts to text.
- `Type=Title and description` uses a fixed `w-[320px]` — always full width.
- The `Content` wrapper uses `flex-[1_0_0]` on `Title and description` to fill remaining space.
- Buttons are stacked vertically with a `gap` of `--nos-spacing-fixed-4` (16px) in the parent `CER_CTA` list container.

---

### Props (suggested interface)

```ts
type AvChatButtonsProps = {
  state?: "Default" | "Hover" | "Disabled";
  type?: "Title" | "Title and description";
  title: string;
  description?: string; // only used when type = "Title and description"
  onClick?: () => void;
};
```

---

### Reference Code (React + Tailwind)

```jsx
export default function AvChatButtons({
  state = "Default",
  type = "Title and description",
  title,
  description,
  onClick,
}: AvChatButtonsProps) {
  const borderColor =
    state === "Hover"     ? "border-[var(--nos-color-border-neutral-600,#404149)]"
    : state === "Disabled" ? "border-[var(--nos-color-border-neutral-400,#74757d)]"
                           : "border-[var(--nos-color-border-neutral-1000,black)]";

  const textColor =
    state === "Hover"     ? "text-[var(--nos-color-text-neutral-600,#404149)]"
    : state === "Disabled" ? "text-[var(--nos-color-text-neutral-400,#74757d)]"
                           : "text-[var(--nos-color-text-neutral-900,#1e1f27)]";

  const widthClass = type === "Title" ? "max-w-[320px]" : "w-[320px]";

  return (
    <div
      className={`bg-[var(--nos-color-neutral-000,white)]
                  border border-solid ${borderColor}
                  flex items-center
                  p-[16px] rounded-[16px]
                  ${widthClass}`}
      onClick={state !== "Disabled" ? onClick : undefined}
    >
      <div className="flex flex-col gap-[4px] items-start justify-center flex-1 overflow-hidden">

        {/* Title */}
        <p className={`font-['Azo_Sans_Web'] font-bold
                       text-[14px] leading-[18px] w-full
                       ${type === "Title" ? "whitespace-pre-wrap" : "overflow-hidden text-ellipsis whitespace-nowrap"}
                       ${textColor}`}>
          {title}
        </p>

        {/* Description — Title and description only */}
        {type === "Title and description" && description && (
          <p className={`font-['Azo_Sans_Web'] font-normal
                         text-[14px] leading-[18px] w-full
                         overflow-hidden text-ellipsis whitespace-nowrap
                         ${textColor}`}>
            {description}
          </p>
        )}

      </div>
    </div>
  );
}
```

> Adapt to the target stack — replace Tailwind utilities with the project's CSS/token system as needed.

---

## `message-user`

**Node ID:** `4007:22572`
**Type:** Symbol (component)
**Figma URL:** https://www.figma.com/design/gelKDCV6CKxnuhnZ7oEgcO/Assistente-Virtual-NOS--AV-Chat-?node-id=4007-22572

### Overview

Right-aligned chat bubble displaying a message sent by the user. Uses a light grey background with rounded corners on all sides except the bottom-right, following the standard "sent message" bubble convention.

---

### Visual Reference

```
                    ┌────────────────────────┐
                    │  Pergunta do utilizador │
                    └────────────────────────┘
                                              ↑ no bottom-right radius
```

---

### Dimensions

| Property | Value |
|---|---|
| Default width | 212px |
| Min width | 160px |
| Max width | 300px |
| Min height | 48px |
| Height | auto (grows with content) |

---

### Anatomy

```
message-user                    (bubble container)
└── text content                (flex, right-aligned)
    └── <p> message text
```

---

### Tokens

| Property | Token | Value |
|---|---|---|
| Background | `--nos-color-neutral-100` | `#dddee3` |
| Text colour | `--nos-color-text-neutral-900` | `#1e1f27` |
| Padding horizontal | `--nos-spacing-fixed-6` | `24px` |
| Padding vertical | `--nos-spacing-fixed-4` | `16px` |
| Border radius (TL, TR, BL) | `--nos-spacing-fixed-4` | `16px` |
| Border radius (BR) | — | `0` |

---

### Typography

| Element | Style | Family | Weight | Size | Line Height | Align |
|---|---|---|---|---|---|---|
| Message text | `UI/Regular (400)/UI8` | Azo Sans Web | 400 | `--nos-font-size-ui-300` (16px) | `Font/Line-Height/ui-300` (24px) | right |

---

### Border Radius

| Corner | Value |
|---|---|
| Top-left | `16px` (`--nos-spacing-fixed-4`) |
| Top-right | `16px` (`--nos-spacing-fixed-4`) |
| Bottom-left | `16px` (`--nos-spacing-fixed-4`) |
| Bottom-right | `0` |

> The missing bottom-right radius creates the "tail" that visually anchors the bubble to the right/user side.

---

### Layout Notes

- The bubble is **right-aligned** within its parent (`justify-end` on the parent row).
- Text is **right-aligned** inside the bubble.
- Width is fluid between `160px` and `300px` — the bubble wraps text naturally.
- Min height of `48px` ensures single-line messages don't appear too small.

---

### Reference Code (React + Tailwind)

```jsx
export default function MessageUser({ text }: { text: string }) {
  return (
    <div
      className="bg-[var(--nos-color-neutral-100,#dddee3)]
                 flex items-center justify-end
                 max-w-[300px] min-w-[160px] min-h-[48px]
                 px-[24px] py-[16px]
                 rounded-tl-[16px] rounded-tr-[16px]
                 rounded-bl-[16px] rounded-br-[0px]"
    >
      <p
        className="font-['Azo_Sans_Web'] font-normal
                   text-[16px] leading-[24px]
                   text-[var(--nos-color-text-neutral-900,#1e1f27)]
                   text-right"
      >
        {text}
      </p>
    </div>
  );
}
```

> Adapt to the target stack — replace Tailwind utilities with the project's CSS/token system as needed.
---

## `Input - Chat`

**Node ID:** `4002:7265`
**Type:** Frame (component set — 4 variants)
**Figma URL:** https://www.figma.com/design/gelKDCV6CKxnuhnZ7oEgcO/Assistente-Virtual-NOS--AV-Chat-?node-id=4002-7265

### Overview

Text input bar placed at the bottom of the AV widget. Adapts its appearance and size based on interaction state — idle, user typing (mobile with keyboard), user typing (web), and disabled.

---

### Variants

| State | Node ID | Width | Height | Description |
|---|---|---|---|---|
| `default` | `4002:7264` | 360px | 48px | Idle — placeholder text + microphone icon |
| `active` | `4002:7263` | 360px | 376px | Mobile typing — input with cursor + send icon + iOS keyboard |
| `active-web` | `4143:63460` | 320px | 48px | Web typing — input with cursor + send icon, no keyboard |
| `disable` | `4075:96436` | 320px | 48px | Disabled — grey background, muted placeholder, no icons |

---

### Visual Reference

**`default`**
```
┌─────────────────────────────────────────┐
│  Escrever para continuar a conversa  🎤 │
└─────────────────────────────────────────┘
```

**`active-web`**
```
┌──────────────────────────────────────┐
│  Qual o valor da minha fatura?|  ➤  │
└──────────────────────────────────────┘
```

**`active`** (mobile — includes keyboard)
```
┌──────────────────────────────────────┐
│  Qual o valor da minha fatura?|  ➤  │
└──────────────────────────────────────┘
┌──────────────────────────────────────┐
│  q  w  e  r  t  y  u  i  o  p       │
│   a  s  d  f  g  h  j  k  l        │
│  ⇧  z  x  c  v  b  n  m  ⌫        │
│  123  🌐  🎤     space      return  │
└──────────────────────────────────────┘
```

**`disable`**
```
┌──────────────────────────────────────┐
│  Escrever para continuar a conversa  │  ← grey bg, no icons
└──────────────────────────────────────┘
```

---

### Anatomy

```
Input - Chat
├── [default]  → "default with hint"
│   ├── hint-input
│   │   └── placeholder text
│   └── Microphone (24×24px icon)
│
├── [active-web]  → "default with hint"
│   ├── text-input
│   │   ├── typed text
│   │   └── _type-indicator (cursor, 2×24px)
│   └── Send (24×24px icon)
│
├── [active]  → Navigation Bar (gradient overlay) + Keyboard
│   ├── Input - Chat (inner, active-web layout)
│   │   ├── text-input
│   │   │   ├── typed text
│   │   │   └── _type-indicator (cursor)
│   │   └── Send icon
│   └── Keyboard/13 mini (279px iOS keyboard simulation)
│       ├── abc rows (26 letter keys)
│       ├── Key/Shift, Key/Remove
│       └── Input Type row (123, 🌐, 🎤, space, return)
│
└── [disable]  → Input - Text [V2]
    └── "default with hint"
        └── hint-input (placeholder, muted colour, no icons)
```

---

### Tokens per State

#### Input field

| Property | Token | Value | States |
|---|---|---|---|
| Background (default/active) | `--nos-color-neutral-000` | `#ffffff` | `default`, `active`, `active-web` |
| Background (disabled) | `--nos-color-neutral-075` | `#efeff1` | `disable` |
| Border colour | `--nos-color-border-neutral-200` | `#bbbcc4` | all |
| Border width | `--nos-border-width-1` | `1px` | all |
| Border radius | `--nos-spacing-fixed-2` | `8px` | all |
| Padding | `--nos-spacing-fixed-3` | `12px` | all |

#### Text

| Element | Token | Value | States |
|---|---|---|---|
| Placeholder colour | `--nos-color-text-neutral-400` | `#74757d` | `default`, `active`, `active-web` |
| Placeholder colour (disabled) | `--nos-color-text-neutral-500` | `#5b5c64` | `disable` |
| Typed text colour | `--nos-color-text-neutral-900` | `#1e1f27` | `active`, `active-web` |
| Font size | `--nos-font-size-ui-300` | `16px` | all |
| Line height | `Font/Line-Height/ui-300` | `24px` | all |
| Font family | Azo Sans Web | Regular (400) | all |

#### Spacing

| Token | Value | Usage |
|---|---|---|
| `--nos-spacing-fixed-1` | `4px` | Gap between text and cursor |
| `--nos-spacing-fixed-2` | `8px` | Gap between content sections |
| `--nos-spacing-fixed-3` | `12px` | Input field padding |
| `--nos-spacing-fixed-6` | `24px` | Navigation Bar vertical padding (active) |

---

### Sub-components

#### `Send` icon (`7070:37578`)
- Size: 24×24px
- Inner icon inset: 8.33% all sides (~2px)
- Shown in: `active`, `active-web`

#### `Microphone` (`2018:9089`)
- Size: 24×24px
- Inner icon inset: 12.5% top/bottom, 20.83% left/right
- Shown in: `default` only
- Keywords: mic, microphone, voice, voz, dictation, microfone

#### `_type-indicator` (cursor, `2001:12072`)
- Size: 2×24px
- Blinking text cursor rendered as an image asset
- Shown in: `active`, `active-web`

#### `Keyboard/13 mini` (`4002:4886`) — active only
- Size: 360×279.36px
- Background: `#d4d6dc`
- Includes: 26 letter keys, Shift, Remove, 123, Globe, Mic, Space, Return, Home bar
- Key background (action keys): `#aeb3be`; letter keys: `#ffffff`
- Font: SF Pro Text, Regular, 21.6px (letters), 15.36px (labels)

#### Navigation Bar gradient (`4147:61077`) — active only
- Sits above the keyboard
- Gradient: `rgba(255,255,255,0)` → `rgba(255,255,255,0.95)` top-to-bottom, breakpoint at 28.85%
- Contains the inner `Input - Chat` (active-web layout, 320px wide)

---

### Layout Notes

- `default` and `active` are **360px wide** (full widget width).
- `active-web` and `disable` are **320px wide** (widget width minus 2×20px horizontal padding).
- The input field is always **48px tall**.
- In `active` state, the component grows to **376px** to accommodate the gradient nav bar (72px) and keyboard (279px).
- The `active` state inner input uses the same visual layout as `active-web` but nested inside the gradient Navigation Bar.

---

### Props (suggested interface)

```ts
type InputChatProps = {
  state?: "default" | "active" | "active-web" | "disable";
  showKeyboard?: boolean;   // active only — show/hide iOS keyboard mock
  showMicrophone?: boolean; // default only — show/hide mic icon
  value?: string;           // typed text (active / active-web)
  placeholder?: string;     // override default placeholder
  onSend?: () => void;
  onChange?: (value: string) => void;
};
```

---

### Reference Code (React + Tailwind)

```jsx
function Send() {
  return (
    <div className="relative size-[24px]">
      <div className="absolute inset-[8.33%]">
        <img src={imgSend} alt="Enviar" className="absolute block size-full" />
      </div>
    </div>
  );
}

function Microphone() {
  return (
    <div className="relative size-[24px]">
      <div className="absolute inset-[12.5%_20.83%]">
        <img src={imgMic} alt="Microfone" className="absolute block size-full" />
      </div>
    </div>
  );
}

function TypeIndicator() {
  return <div className="h-[24px] w-[2px] relative shrink-0" />;
}

export default function InputChat({ state = "default" }) {
  const isDefault   = state === "default";
  const isActive    = state === "active";
  const isActiveWeb = state === "active-web";
  const isDisable   = state === "disable";

  const inputBg   = isDisable ? "bg-[var(--nos-color-neutral-075,#efeff1)]"
                              : "bg-[var(--nos-color-neutral-000,#ffffff)]";
  const textColor = isDisable ? "text-[var(--nos-color-text-neutral-500,#5b5c64)]"
                  : (isActive || isActiveWeb)
                              ? "text-[var(--nos-color-text-neutral-900,#1e1f27)]"
                              : "text-[var(--nos-color-text-neutral-400,#74757d)]";
  const width = (isActive || isDefault) ? "w-[360px]" : "w-[320px]";

  return (
    <div className={`flex flex-col items-start ${width}`}>

      {/* Active — gradient nav bar + keyboard */}
      {isActive && (
        <div className="flex flex-col items-start w-full">
          <div className="bg-gradient-to-b from-transparent to-[rgba(255,255,255,0.95)]
                          flex flex-col items-center py-[24px] w-[360px]">
            <InputField state="active-web" />
          </div>
          <Keyboard />
        </div>
      )}

      {/* Default, active-web, disable */}
      {!isActive && (
        <div className={`${inputBg} border border-[var(--nos-color-border-neutral-200,#bbbcc4)]
                         flex h-[48px] items-center overflow-clip
                         p-[12px] rounded-[8px] w-full`}>
          <div className="flex flex-1 items-center gap-[8px]">

            {/* Placeholder */}
            {(isDefault || isDisable) && (
              <p className={`flex-1 font-['Azo_Sans_Web'] font-normal
                             text-[16px] leading-[24px]
                             overflow-hidden text-ellipsis whitespace-nowrap
                             ${textColor}`}>
                Escrever para continuar a conversa
              </p>
            )}

            {/* Typed text + cursor */}
            {isActiveWeb && (
              <div className="flex flex-1 items-center gap-[4px] overflow-hidden">
                <p className={`font-['Azo_Sans_Web'] font-normal
                               text-[16px] leading-[24px]
                               overflow-hidden text-ellipsis whitespace-nowrap
                               ${textColor}`}>
                  Qual o valor da minha fatura?
                </p>
                <TypeIndicator />
              </div>
            )}

            {/* Right icon */}
            {isDefault  && <Microphone />}
            {isActiveWeb && <Send />}
          </div>
        </div>
      )}

    </div>
  );
}
```

> Adapt to the target stack — replace Tailwind utilities with the project's CSS/token system as needed.

---

## `AV_message`

**Node ID:** `4007:24754` (state=Default) · parent: `4465:78595`
**Type:** Symbol (single variant)
**Figma URL:** https://www.figma.com/design/gelKDCV6CKxnuhnZ7oEgcO/Assistente-Virtual-NOS--AV-Chat-?node-id=4007-24754

### Overview

Left-aligned text block rendering the AV bot's response. No background or border — plain body text sitting directly on the white widget surface. Always 320px wide, height grows with content.

---

### Visual Reference

```
┌────────────────────────────────────────┐
 Donec nec justo eget felis facilisis
 fermentum. Aliquam porttitor mauris sit
 amet orci. Aenean dignissim pellentesque
 felis.
```

> No bubble, no background — raw text only.

---

### Dimensions

| Property | Value |
|---|---|
| Width | 320px (fixed) |
| Height | auto (grows with content) |
| Min height | 96px (design frame baseline) |

---

### Anatomy

```
AV_message
└── state=Default               (flex row, items-start)
    └── <p> message text        (320px wide, multi-line)
```

---

### Tokens

| Property | Token | Value |
|---|---|---|
| Text colour | `--nos-color-text-neutral-900` | `#1e1f27` |
| Font size | `--nos-font-size-text-300` | `16px` |
| Line height | `Font/Line-Height/text-300` | `24px` |

---

### Typography

| Element | Style | Family | Weight | Size | Line Height | Align |
|---|---|---|---|---|---|---|
| Message text | `Text/Regular (400)/P1` | Azo Sans Web | 400 | `--nos-font-size-text-300` (16px) | `Font/Line-Height/text-300` (24px) | left |

---

### Layout Notes

- No background, border, or padding — the component is pure text.
- Width is fixed at **320px** (the inner content column of the widget, 360px − 2×20px padding).
- Text wraps naturally across multiple lines; the component height is driven by content.
- Left-aligned by default, consistent with the AV response side of the chat.
- In the full chat layout (`AV_response`), this component sits above any `CER_CTA` button list with a gap of `--nos-spacing-fixed-4` (16px).

---

### Reference Code (React + Tailwind)

```jsx
export default function AvMessage({ text }: { text: string }) {
  return (
    <div className="flex items-start">
      <p
        className="font-['Azo_Sans_Web'] font-normal
                   text-[length:var(--nos-font-size-text-300,16px)]
                   leading-[var(--font/line-height/text-300,24px)]
                   text-[color:var(--nos-color-text-neutral-900,#1e1f27)]
                   w-[320px]"
      >
        {text}
      </p>
    </div>
  );
}
```

> Adapt to the target stack — replace Tailwind utilities with the project's CSS/token system as needed.
