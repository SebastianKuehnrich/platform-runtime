# Platform Runtime

Multi-Page Personal Showcase, gebaut mit Modern CSS Features.
Kein Framework, kein Build-Step — fuenf Pages, ein Token-System.

**Live:** [GitHub Pages](https://sebastiankuehnrich.github.io/platform-runtime/)

---

## Pages

| Page | Beschreibung | Kern-Features |
|------|-------------|---------------|
| **Home** | Hero mit Gradient-Text, Feature-Cards | `@container`, `background-clip: text`, `@property` |
| **Pricing** | Drei Plan-Cards, Pro mit Knockout-Glow | Subgrid, 3-Layer Glow-Card, `color-mix()` |
| **Profile** | Stats mit Anchor-Tooltips | Anchor Positioning, `position-try-fallbacks` |
| **Projects** | Portfolio-Grid mit Knockout-Glow-Cards | 3-Layer Glow-Card, `@scope`, `@container` |
| **Login** | Formular mit Live-Validation | `:has()` Email/Passwort-Validation, reaktiver Button |

---

## CSS Features

### Token-System (3-Layer)
```
Layer 1 — Primitives    --slate-700, --indigo-500
Layer 2 — Semantic      --color-brand: var(--indigo-500)
Layer 3 — Component     --card-bg: color-mix(in oklch, ...)
```
Brand-Swap = eine Zeile in `tokens.css` aendern. Siehe [BRAND_SWAP_TEST.md](BRAND_SWAP_TEST.md).

### Modern CSS (W1 Features)
- `:has()` — Dark Mode, Login-Validation, Hamburger-Nav (kein JS)
- `@container` — Component-Level Responsiveness
- `color-mix(in oklch)` — brand-derived Tokens
- View Transitions — smooth Page-Navigation
- Subgrid — Card-Row-Alignment
- Anchor Positioning — JS-freie Tooltips mit Edge-Detection
- `@supports` — Progressive Enhancement

### Glow-Card (Warmup-Technik)
3-Layer-Stack mit Knockout-Text via `mix-blend-mode: multiply`:
```
z: -1  ::before          Rotierender Border-Glow (conic-gradient)
z:  0  .glow-card__beam  Weisse Basis + farbiger Strahl
z:  0  .glow-card__surface  Dunkle Card + weisser Text → Knockout
```
4 `@property`-Deklarationen: `--gradient-angle`, `--glow-hue`, `--glow-spread`, `--beam-angle`
3 Animationen: `rotate-glow` (4s), `rotate-beam` (4s), `shift-hue` (8s)

### Production Layer
- `@property` — 5 Typed Custom Properties fuer animierte Gradients + Glow
- `@scope` — Component-Style-Isolation ohne Build-Step
- `position-try-fallbacks` — Edge-Aware Tooltip-Flipping
- `prefers-reduced-motion` — Alle Animationen in `no-preference`-Guard
- Responsive Hamburger-Nav — CSS-only via `:has(.nav-toggle:checked)`
- Skip-to-Content Link — a11y-Baseline auf allen Pages
- Dark-Mode Persistence — `localStorage` seitenuebergreifend
- SEO — Meta-Tags, Open Graph, SVG Favicon, Theme-Color

---

## MicroSims

8 interaktive Lern-Simulationen in [`/microsims/`](microsims/):

| MicroSim | Was es zeigt |
|----------|-------------|
| Specificity Calculator | Live-Vergleich zweier Selektoren |
| Box Model Playground | `content-box` vs `border-box` |
| Custom Property Cascade | Vererbungs-Baum mit Live-Preview |
| DevTools Tour | Annotierte Tab-Erklaerung + Quiz |
| @property Conic Lab | Gradient-Parameter live anpassen |
| @scope Visualizer | Scope-Grenzen togglen |
| Position-Try Demo | Drag-basierte Edge-Detection |
| Reduced Motion Toggle | a11y-Simulation aller Animationen |

---

## Dateistruktur

```
platform-runtime/
├── index.html           Home
├── pricing.html         Pricing
├── profile.html         Profile
├── projects.html        Projects
├── login.html           Login
├── tokens.css           3-Layer Token-System
├── base.css             Reset, Nav, Hamburger, Skip-Link
├── pages.css            Page-Styles, @container Queries
├── transitions.css      View Transitions, reduced-motion
├── tooltips.css         Anchor Positioning, position-try
├── effects.css          @property Glow, @scope, Hero-Gradient
├── microsims/           8 interaktive MicroSims
├── REFLECTION.md        3 Reflexionsfragen
├── DEVTOOLS_FINDINGS.md Computed-Tab Analyse
├── BRAND_SWAP_TEST.md   Brand-Swap Anleitung
└── ABSCHLUSS_ZUSAMMENFASSUNG.md
```

## Browser-Support

Chrome 125+, Edge 125+, Safari 26+.
Anchor Positioning hat `@supports`-Fallback fuer Firefox.

## Author

Sebastian K. — Morphos Advanced CSS Cohort, Mai 2026
