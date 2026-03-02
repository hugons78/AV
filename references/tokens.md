# Design Tokens — Assistente Virtual NOS (AV Chat)

Extracted from Figma file `gelKDCV6CKxnuhnZ7oEgcO`, node `7842:3999`.

---

## Colors

### Brand
| Token | Value | Usage |
|---|---|---|
| `--nos-color-brand-bg-turquoise-500` | `#4bdbc5` | Widget header background |

### Neutral
| Token | Value | Usage |
|---|---|---|
| `--nos-color-neutral-000` | `#ffffff` | Card/widget background, input background, CTA button background |
| `--nos-color-neutral-100` | `#dddee3` | User message bubble background |
| `--nos-color-neutral-1000` | `#000000` | — |

### Text
| Token | Value | Usage |
|---|---|---|
| `--nos-color-text-neutral-900` | `#1e1f27` | Body text, user message text, CTA label text, header title |
| `--nos-color-text-neutral-1000` | `#000000` | — |
| `--nos-color-text-neutral-400` | `#74757d` | Input placeholder text |

### Border
| Token | Value | Usage |
|---|---|---|
| `--nos-color-border-neutral-1000` | `#000000` | CTA button border |
| `--nos-color-border-neutral-200` | `#bbbcc4` | Input field border |

### Raw / Alias
| Name | Value |
|---|---|
| `Neutral/Grey 900` | `#1e1f27` |
| `Neutrals/Grey 400` | `#74757d` |
| `Grey/600` | `#404149` |
| `black` | `#35363e` |

---

## Typography

### Font Families
| Usage | Family | Style |
|---|---|---|
| Body / UI text | `Azo Sans Web` | Regular (400), Bold (700) |
| Header title | `Azo Sans` | Medium (500) |

### Font Sizes
| Token | Value (px) | Usage |
|---|---|---|
| `--nos-font-size-ui-300` | `16` | User message, input placeholder |
| `--nos-font-size-ui-200` | `14` | CTA button labels |
| `--nos-font-size-text-300` | `16` | AV response body text |
| *(raw)* | `18` | Widget header title |

### Font Weights
| Token | Value | Alias |
|---|---|---|
| `Font/Weight/400` | `Regular` | Normal |
| `Font/Weight/500` | `Medium` | — |
| `Font/Weight/700` | `Bold` | — |

### Line Heights
| Token | Value (px) | Paired with |
|---|---|---|
| `Font/Line-Height/ui-300` | `24` | UI/Regular UI8 — 16px body |
| `Font/Line-Height/ui-200` | `18` | UI/Bold UI9 — 14px labels |
| `Font/Line-Height/text-300` | `24` | Text/Regular P1 — 16px body |
| *(raw)* | `26` | 18px header title |

### Text Styles (composite)
| Name | Family | Weight | Size | Line Height |
|---|---|---|---|---|
| `UI/Regular (400)/UI8` | Azo Sans Web | 400 | `--nos-font-size-ui-300` (16px) | `Font/Line-Height/ui-300` (24px) |
| `UI/Bold (700)/UI9` | Azo Sans Web | 700 | `--nos-font-size-ui-200` (14px) | `Font/Line-Height/ui-200` (18px) |
| `Text/Regular (400)/P1` | Azo Sans Web | 400 | `--nos-font-size-text-300` (16px) | `Font/Line-Height/text-300` (24px) |
| `Title/2XS Medium` | Azo Sans | 500 | 18px | 26px |

---

## Spacing

| Token | Value (px) | Usage |
|---|---|---|
| `--nos-spacing-fixed-1` | `4` | Tight internal gaps (e.g. CTA content gap) |
| `--nos-spacing-fixed-2` | `8` | Input border-radius, small gaps |
| `--nos-spacing-fixed-3` | `12` | Input padding |
| `--nos-spacing-fixed-4` | `16` | Message bubble padding, response/CTA gaps, CTA card padding, border-radius |
| `--nos-spacing-fixed-6` | `24` | Message bubble horizontal padding, chat top padding, header bottom padding, icon gaps |
| `--nos-spacing-fixed-15` | `0` | — |

---

## Border Widths

| Token | Value (px) |
|---|---|
| `--nos-border-width-1` | `1` |
| `--nos-border-width-3` | `3` |

---

## Effects / Shadows

| Name | Type | Color | Offset | Radius | Spread | Usage |
|---|---|---|---|---|---|---|
| `level 1` | Drop Shadow | `#00000014` (8% opacity) | (0, 2) | 8px | 0 | Input bar shadow |
| `Exports` | Drop Shadow | `#0000001F` (12% opacity) | (0, 14) | 40px | 0 | Widget container shadow |

---

## Border Radius (contextual)

| Context | Token / Value |
|---|---|
| User message bubble | `--nos-spacing-fixed-4` (16px) — TL, TR, BL; no BR |
| CTA buttons | `--nos-spacing-fixed-4` (16px) — all corners |
| Input field | `--nos-spacing-fixed-2` (8px) — all corners |

---

## Layout

| Element | Width | Height |
|---|---|---|
| Widget container | 360px | 800px |
| Header bar | 360px | ~102px |
| Content area | 360px | 698px |
| Inner chat column | 320px | — |
| User message bubble | 212px (max 300px) | min 48px |
| Input bar | 360px | 48px |
