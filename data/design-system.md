# Design System — Default

Source of truth for tokens and visual patterns of the project.
Generated from the base CSS. Fill in the [FILL] fields during each project setup.

---

## Project visual identity

- **Primary font:** [FILL — e.g. Poppins | Inter | Nunito]
- **Primary color:** [FILL — e.g. #f97316]
- **Secondary color:** [FILL — e.g. #16a34a]
- **Overall style:** [FILL — ex: institucional sóbrio | moderno vibrante | editorial minimalista]

---

## 1. Tokens de cor

```css
/* Brand */
--c-primary:         [FILL];   /* main color — buttons, highlights, icons */
--c-primary-hover:   [FILL];   /* primary darkened ~10% */
--c-secondary:       [FILL];   /* support color — badges, lists, links */
--c-secondary-hover: [FILL];   /* secondary darkened ~10% */

/* Text */
--c-text:            #111827;  /* main body text */
--c-muted:           #6b7280;  /* secondary text, paragraphs */

/* Background */
--c-bg:              #ffffff;  /* default background */
--c-bg-alt:          #f5f5f5;  /* alternating sections */
--c-dark:            #0f172a;  /* dark sections, hero overlay, footer */

/* Interface */
--c-border:          #e5e7eb;  /* input borders, dividers */
```

**Rule:** never use hex values directly in project CSS. Always use var(--c-*).

---

## 2. Typography

```css
/* Family */
--ff-base: "[FILL]", system-ui, -apple-system, Segoe UI, Roboto, sans-serif;

/* Scale */
--fs-xs:   0.75rem;    /*  12px — tags, badges, labels */
--fs-sm:   0.875rem;   /*  14px — captions, buttons, nav */
--fs-md:   1rem;       /*  16px — base body text */
--fs-lg:   1.25rem;    /*  20px — subtitles, intro */
--fs-xl:   2rem;       /*  32px — default h2 */
--fs-hero: 2.25rem;    /*  36px — h1 mobile (scales with clamp on desktop) */

/* Weight */
--fw-regular:  400;
--fw-medium:   500;
--fw-semibold: 600;
--fw-bold:     700;

/* Line height */
--lh-base:  1.6;   /* body */
--lh-tight: 1.2;   /* headings */
```

**Heading hierarchy:**
- `h1` → `var(--fs-hero)` → scales to `3rem` on desktop via media query  
- `h2` → `var(--fs-xl)` → scales to `2.25rem` / `2.5rem` on tablet/desktop  
- `h3` → `var(--fs-lg)`

**Google Fonts:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=[FILL]:wght@400;500;600;700&display=swap" rel="stylesheet">
```

---

## 3. Spacing

```css
--space-1:  8px;
--space-2:  16px;
--space-3:  24px;
--space-4:  40px;
--space-5:  64px;
--space-6:  96px;
```

**Default usage:**
- Section padding: `var(--space-5) 0` (mobile)
- Grid gap: `var(--space-3)`
- Card padding: `var(--space-3)` or `var(--space-4)`
- Container padding: `0 var(--space-2)` (mobile) → `0 var(--space-4)` (768px+)

**Rule:** never use arbitrary values (e.g: `margin: 37px`). Always use the scale.

---

## 4. Layout

```css
--container: 1200px;   /* max-width padrão */
```

**Default container:**
```css
.secao__container {
  max-width: var(--container);
  margin: 0 auto;
  padding: 0 var(--space-2);
}

@media (min-width: 768px) {
  .secao__container {
    padding: 0 var(--space-4);
  }
}
```

**Default grid:**
```css
/* 2 colunas */
@media (min-width: 768px) {
  .grid-2 { grid-template-columns: repeat(2, 1fr); }
}

/* 3 colunas */
@media (min-width: 768px) {
  .grid-3 { grid-template-columns: repeat(3, 1fr); }
}

/* 4 colunas */
@media (min-width: 1024px) {
  .grid-4 { grid-template-columns: repeat(4, 1fr); }
}
```

---

## 5. Bordas e sombras

```css
/* Border radius */
--radius-sm:  6px;    /* buttons, inputs, tags */
--radius-md:  10px;   /* cards */
--radius-lg:  16px;   /* images, highlighted sections */

/* Shadow */
--shadow-sm:  0 2px 8px rgba(0,0,0,0.06);    /* cards at rest */
--shadow-md:  0 8px 24px rgba(0,0,0,0.10);   /* cards on hover */

/* Transição */
--transition:        0.25s ease;   /* UI interactions — buttons, links, cards */
--transition-reveal: 0.6s ease;    /* Scroll entrance animations */
```

---

## 6. Breakpoints

| Nome | Valor | Uso |
|------|-------|-----|
| Mobile | < 480px | base (mobile-first) |
| Small | 480px | ajustes pontuais |
| Tablet | 768px | grid 2 colunas, nav desktop |
| Laptop | 1024px | grid 3–4 colunas, ajuste de tipografia |
| Desktop | 1280px+ | refinamentos opcionais |

---

## 7. Componentes base

### Botões

```css
/* Primário */
.btn-primary {
  background: var(--c-primary);
  color: #fff;
  border: 2px solid var(--c-primary);
  padding: 12px 24px;
  font-size: var(--fs-sm);
  font-weight: var(--fw-semibold);
  border-radius: var(--radius-sm);
  transition: background var(--transition), border-color var(--transition);
}
.btn-primary:hover {
  background: var(--c-primary-hover);
  border-color: var(--c-primary-hover);
}

/* Secundário (outline) */
.btn-secondary {
  background: transparent;
  color: var(--c-secondary);
  border: 2px solid var(--c-secondary);
}
.btn-secondary:hover {
  background: var(--c-secondary);
  color: #fff;
}

/* Outline branco — uso em fundos escuros */
.btn-outline-white {
  background: transparent;
  color: #fff;
  border: 2px solid rgba(255,255,255,0.70);
}
.btn-outline-white:hover {
  background: rgba(255,255,255,0.12);
  border-color: #fff;
}
```

### Card padrão

```css
.card {
  background: #fff;
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-sm);
  padding: var(--space-3);
  transition: box-shadow var(--transition), transform var(--transition);
}
.card:hover {
  box-shadow: var(--shadow-md);
  transform: translateY(-2px);
}
```

### Seção padrão

```css
/* Fundo claro */
.secao { padding: var(--space-5) 0; background: var(--c-bg); }

/* Fundo alternado */
.secao-alt { padding: var(--space-5) 0; background: var(--c-bg-alt); }

/* Fundo escuro */
.secao-dark { padding: var(--space-5) 0; background: var(--c-dark); color: #fff; }
```

### Input / Textarea

```css
.input, .textarea {
  width: 100%;
  padding: 12px var(--space-2);
  border: 1px solid var(--c-border);
  border-radius: var(--radius-sm);
  font-family: var(--ff-base);
  font-size: var(--fs-sm);
  color: var(--c-text);
  background: #fff;
  transition: border-color var(--transition);
}
.input:focus, .textarea:focus {
  outline: none;
  border-color: var(--c-primary);
}
```

---

### Parallax section

Fixed background image effect — image stays still while content scrolls over it.

```css
.parallax-section {
  background-attachment: fixed;
  background-size: cover;
  background-position: center;
  padding: var(--space-6) 0;
}

.parallax-section__overlay {
  background: rgba(0, 0, 0, 0.55);
  padding: var(--space-6) 0;
  text-align: center;
}
```

HTML pattern (background image set via inline style — approved exception):
```html
<section class="parallax-section" style="background-image: url('./images/[filename]');">
  <div class="parallax-section__overlay">
    <div class="container">
      <h2 class="parallax-section__title reveal">[TITLE]</h2>
      <p class="parallax-section__text reveal reveal-delay-1">[TEXT]</p>
      <a href="[URL]" class="btn btn-outline-white reveal reveal-delay-2">[CTA]</a>
    </div>
  </div>
</section>
```

**Rules:**
- Max 2 parallax sections per page
- Use only on low-density sections (title + short text + CTA)
- Do NOT apply to hero, forms, cards, or grids
- iOS fallback: `background-attachment: scroll` on mobile (already in CSS)
- Always combine with `.reveal` for scroll entrance animation

---

### Scroll reveal

```css
.reveal {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity var(--transition-reveal), transform var(--transition-reveal);
}

.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}

.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.3s; }
.reveal-delay-4 { transition-delay: 0.4s; }
```

**Usage:**
- Apply `.reveal` to section titles, cards, images, and CTA blocks
- Use `.reveal-delay-N` on grid items for stagger effect
- Do NOT apply to hero, header, or navigation elements
- `.visible` class is added automatically by `initScrollReveal()` in `main.js`

---

## 8. Ícones

Biblioteca: **Lucide Icons** via CDN.

```html
<script src="https://unpkg.com/lucide@latest"></script>
```

Uso:
```html
<i data-lucide="check"></i>
<i data-lucide="arrow-right"></i>
<i data-lucide="instagram"></i>
```

Inicialização: called inside `assets/main.js` via `initIcons()` — do NOT use inline script in HTML.

**Default sizes:**
- UI icons (lists, features): `20px × 20px`
- Section/card icons: `28px × 32px`
- Button icons: `16px × 18px`
- Footer/social icons: `18px × 18px`

---

## 9. Acessibilidade

```css
/* Focus visível — WCAG AA */
:focus-visible {
  outline: 2px solid var(--c-primary);
  outline-offset: 3px;
}
```

**Minimum contrast:**
- Body text on white background: ≥ 4.5:1
- Large text (18px+ bold) on background: ≥ 3:1
- Never use `--c-muted` (`#6b7280`) on `--c-bg-alt` without checking contrast

---

## 10. Performance

- Images with `width` and `height` always defined (prevents CLS)
- `loading="lazy"` on all below-the-fold images
- Hero image must NOT use `loading="lazy"` — use `fetchpriority="high"` instead
- CSS linked in `<head>`, JS with `defer`
- Google Fonts with `display=swap`
- No external CSS frameworks

---

## 11. Nomenclatura de classes (BEM)

```
.bloco {}
.bloco__elemento {}
.bloco--modificador {}
```

**Project examples:**
```
.hero__title
.header__nav-link
.footer__social-link
.programas__card-title
.contato__form-group
```

---

## 12. Paleta de cores do projeto atual

> Replace the [FILL] fields above when starting a new project.

| Token | Valor | Uso |
|-------|-------|-----|
| `--c-primary` | `#f97316` | orange — buttons, icons, highlights |
| `--c-primary-hover` | `#ea580c` | dark orange — hover |
| `--c-secondary` | `#16a34a` | green — secondary CTAs, badges |
| `--c-secondary-hover` | `#15803d` | dark green — hover |
| `--c-text` | `#111827` | near black — headings, body |
| `--c-muted` | `#6b7280` | medium gray — paragraphs |
| `--c-bg` | `#ffffff` | white — default background |
| `--c-bg-alt` | `#f5f5f5` | light gray — alternating sections |
| `--c-dark` | `#0f172a` | dark blue — dark sections |
| `--c-border` | `#e5e7eb` | soft gray — borders |
