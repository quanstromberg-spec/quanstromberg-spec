---
name: husqvarna-design
description: Apply Husqvarna brand design system to any frontend work. Use this skill whenever building UI components, prototypes, pages, or any visual interface for Husqvarna — including when the user mentions Fleet, prototyping, dashboards, or any Husqvarna product UI. Ensures all output follows official Husqvarna color tokens, typography, spacing, and border radius rules.
---

# Husqvarna UI Design System

You are building a Husqvarna-branded interface. Always apply the following design tokens and rules. Do not deviate from these values. Do not introduce colors, fonts, or spacing that are not defined here.

## 1. Color Tokens

| Token          | Value                | CSS Variable         | Apply To                                                                 |
|----------------|----------------------|----------------------|--------------------------------------------------------------------------|
| text-primary   | #3D3D3C              | --foreground         | All headings, body text, labels                                          |
| button-primary | #227730              | --primary            | Primary CTA buttons (background)                                         |
| surface-1      | #F4F4F3              | --background         | Page background, card background                                         |
| surface-2      | #FFFFFF              | --card               | Cards, modals, input fields, dropdowns, secondary button background      |
| border-default | rgba(0, 0, 0, 0.08)  | --border             | All strokes — always 1px solid                                           |
| text-on-brand  | #FFFFFF              | --primary-foreground | Text and icons placed on top of button-primary                           |

Always declare these as CSS variables on `:root`:

```css
:root {
  --foreground: #3D3D3C;
  --primary: #227730;
  --background: #F4F4F3;
  --card: #FFFFFF;
  --border: rgba(0, 0, 0, 0.08);
  --primary-foreground: #FFFFFF;
}
```

## 2. Typography

### 2a. Headings — Husqvarna Gothic Bold

HusqvarnaGothic is a proprietary font. Always use `font-family: 'HusqvarnaGothic'` directly — if it is installed on the user's local machine, the browser will find it automatically with no extra setup needed.

If the font does not render correctly, ask the user: "It looks like HusqvarnaGothic may not be installed on your machine. Could you provide the font file (.woff2 or .otf) so I can load it via @font-face?"

Never silently fall back to another font without informing the user.

| Token | font-size | line-height | font-weight | font-family     |
|-------|-----------|-------------|-------------|-----------------|
| h1    | 56px      | 56px        | 700         | HusqvarnaGothic |
| h2    | 44px      | 48px        | 700         | HusqvarnaGothic |
| h3    | 36px      | 40px        | 700         | HusqvarnaGothic |
| h4    | 28px      | 32px        | 700         | HusqvarnaGothic |

### 2b. Body — Roboto

Load Roboto from Google Fonts:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@100..900&display=swap" rel="stylesheet">
```

```css
body {
  font-family: 'Roboto', sans-serif;
  font-weight: 350;
  -webkit-font-smoothing: antialiased;
}
```

| Token     | font-size | line-height | font-weight | Usage                              |
|-----------|-----------|-------------|-------------|------------------------------------|
| body-1    | 18px      | 28px        | 350         | Primary body, descriptions         |
| body-2    | 16px      | 24px        | 350         | Secondary body, text inside cards  |
| microcopy | 14px      | 20px        | 350         | Captions, hints, metadata, labels  |

## 3. Shape & Spacing

**Border radius:** 32px — apply to all cards, buttons, modals, and overlays. This is a signature Husqvarna UI trait; do not reduce it.

**Spacing system:** All padding and spacing values must be multiples of 4px.
Valid values: 4, 8, 12, 16, 20, 24, 28, 32, 40, 48, 64...
Never use arbitrary values like 15px, 22px, or 10px.

## 4. Rules to Always Follow

- Never introduce colors outside the token set above.
- Never use system fonts (Arial, Helvetica, system-ui) for headings.
- All borders are always `1px solid var(--border)`.
- Button backgrounds use `var(--primary)` with `var(--primary-foreground)` for text.
- Secondary/ghost buttons use `var(--card)` as background with `var(--foreground)` text and `1px solid var(--border)` stroke.
- Page backgrounds use `var(--background)`. Card surfaces use `var(--card)`.
