# Agent Design Guidelines

## Template Structure

```
gp/
├── index.html          # Main site - rebuild when assets change
├── assets/
│   ├── logo.*          # User-provided logo (svg/png/webp)
│   └── [other assets]  # Images, icons user drops in
├── styles.css          # Optional separate stylesheet
└── AGENTS.md           # This file
```

## Workflow

1. User drops assets into `/assets/` (logo, images, etc.)
2. Agent detects new assets and rebuilds `index.html` incorporating them
3. Commit and push: `git add -A && git commit -m "Update" && git push`

---

## Design Principles: Don't Look AI-Generated

### The Problem with AI Sites
- Gradient backgrounds with generic blobs
- "Welcome to [Brand]" hero text
- Perfectly centered everything
- Stock-looking illustrations
- Over-explained microcopy
- Cookie-cutter card layouts
- Excessive whitespace with no rhythm

### What Makes Sites Feel Human

**Asymmetry & Tension**
- Off-center layouts create visual interest
- Let elements breathe unevenly
- Use negative space intentionally, not uniformly

**Typography That Has Opinions**
- Pick ONE bold typeface choice (not safe system fonts)
- Vary font weights dramatically (200 vs 800)
- Tight letter-spacing on headlines, relaxed on body
- Consider: Inter, Satoshi, Cabinet Grotesk, Instrument Sans

**Color with Restraint**
- 2-3 colors max, not a gradient soup
- Dark modes: avoid pure #000, use #0a0a0a or #111
- Accent colors should feel intentional, not decorative
- Consider: off-whites (#fafaf9), warm blacks, single bold accent

**Micro-interactions That Feel Tactile**
```css
/* Subtle hover lift */
.card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.08);
}

/* Smooth but not floaty */
* {
    transition: all 0.15s ease-out;
}

/* Button press */
button:active {
    transform: scale(0.98);
}
```

**Scroll Animations (Use Sparingly)**
```css
/* Fade up on scroll - vanilla CSS */
@keyframes fadeUp {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.animate-in {
    animation: fadeUp 0.5s ease-out forwards;
}
```

```js
// Intersection Observer for scroll triggers
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.classList.add('animate-in');
        }
    });
}, { threshold: 0.1 });

document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
```

---

## Modern Patterns (2024-2025)

**Layout**
- CSS Grid for complex layouts, Flexbox for alignment
- `clamp()` for fluid typography: `font-size: clamp(1rem, 2.5vw, 1.5rem);`
- Container queries where appropriate
- Full-bleed sections with contained content

**Effects That Don't Scream "Template"**
- Subtle grain/noise textures on backgrounds
- Blur effects on overlays: `backdrop-filter: blur(8px);`
- Border radius: either sharp (0) or noticeably rounded (12-16px), not 4px
- Borders: 1px solid with low-opacity colors

**What to Avoid**
- Parallax (overused, often janky)
- Hamburger menus on desktop
- "Scroll to explore" prompts
- Floating chat widgets
- Carousels (just show the content)
- Lorem ipsum (write real copy or leave blank)

---

## Logo Integration

When a logo is added to `/assets/`:

```html
<!-- SVG preferred - inline for color control -->
<header>
    <a href="/" class="logo">
        <img src="assets/logo.svg" alt="Site" height="32">
    </a>
</header>
```

```css
.logo img {
    height: 32px;
    width: auto;
}

/* Dark mode invert if needed */
@media (prefers-color-scheme: dark) {
    .logo img {
        filter: invert(1);
    }
}
```

---

## Code Style

**HTML**
- Semantic elements: `<header>`, `<main>`, `<section>`, `<article>`
- No div soup
- Meaningful class names (not `.container-wrapper-inner`)

**CSS**
- CSS custom properties for theming
- Mobile-first with `min-width` breakpoints
- Logical properties where sensible (`inline`, `block`)

```css
:root {
    --bg: #fafaf9;
    --fg: #111;
    --accent: #2563eb;
    --radius: 12px;
    --transition: 0.15s ease-out;
}

@media (prefers-color-scheme: dark) {
    :root {
        --bg: #0a0a0a;
        --fg: #fafaf9;
    }
}
```

---

## Commit Messages

Keep them tight:
- `Update logo`
- `Rebuild with new assets`
- `Style refinements`
- `Add animations`

## Deploy Command

```bash
git add -A && git commit -m "Update" && git push
```

Site live at: `https://[user].github.io/gp/`
