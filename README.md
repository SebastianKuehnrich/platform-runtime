# Sebastian K. — Personal Platform-Runtime

## Was das ist
Ein Multi-Page-Personal-Showcase, gebaut mit Modern CSS Features (Mai 2026).
Kein Framework, kein Build-Step, fuenf Pages, ein Token-System.
Production-tauglich mit a11y-aware Animations.

## Pages
- **Home** — Hero + Feature-Cards
- **Pricing** — Subgrid-aligned Plan-Cards, Featured-Plan mit @property-Glow
- **Profile** — Stat-Cards mit Anchor-Positioned-Tooltips inkl. position-try
- **Projects** — Portfolio mit Projekt-Cards, Subgrid-Layout, @scope-Isolation
- **Login** — Form mit :has()-basierter Email-Validation

## Modern CSS Features (W1)
- 3-Layer Token-System (Primitives → Semantic → Component)
- `:has()` fuer State-Detection ohne JavaScript
- `@container` fuer Component-Level-Responsiveness
- `color-mix(in oklch)` fuer brand-derived Tokens
- View Transitions fuer smooth Page-Switches
- Subgrid fuer Card-Row-Alignment
- Anchor Positioning fuer JS-freie Tooltips
- `@supports` fuer progressive enhancement

## Production-Layer (Path B)
- `@property` mit angle-typed Custom Properties fuer animierte Conic-Gradients
- `@scope` fuer Component-Style-Isolation
- `position-try` fuer Edge-Aware Tooltip-Flipping
- `prefers-reduced-motion`-aware Animations (a11y-baseline)

## MicroSims (Interaktive Lern-Tools)
8 interaktive HTML-Simulationen im `/microsims/`-Ordner:
- **Specificity Calculator** — Live-Vergleich zweier CSS-Selektoren
- **Box Model Playground** — content-box vs border-box Visualisierung
- **Custom Property Cascade** — Vererbungs-Baum mit Live-Preview
- **DevTools Annotated Tour** — Tab-Erklaerungen + Quiz
- **@property Conic Lab** — Animierte Gradient-Parameter live anpassen
- **@scope Visualizer** — Scope-Grenzen an/aus togglen
- **Position-Try Demo** — Drag-basierte Edge-Detection
- **Reduced Motion Toggle** — a11y-Simulation aller Animationen

## Brand-Swap-Test
Eine Zeile in `tokens.css` aendern → ganzes System folgt automatisch.
Siehe `BRAND_SWAP_TEST.md` fuer die vollstaendige Anleitung.

## Stack
Vanilla HTML + CSS. Modern Browser-Features (Chrome 125+, Edge 125+, Safari 26+).
Anchor-Positioning braucht `@supports`-Wrapper fuer Firefox-Support.

## Deployment
- **Schritt 1:** GitHub Repo erstellen und pushen
- **Schritt 2:** `npm i -g vercel && vercel` fuer Vercel-Deployment
- **Schritt 3:** GitHub Settings → Pages → Deploy from branch main

## Dateistruktur
```
sebastian-platform-runtime/
├── index.html              Home-Page
├── pricing.html            Pricing mit Subgrid + @property Glow
├── profile.html            Profile mit Anchor-Tooltips
├── projects.html           Portfolio mit Subgrid + @scope
├── login.html              Login mit :has()-Validation
├── tokens.css              3-Layer Token-System
├── base.css                Reset + Nav + Buttons + Footer
├── pages.css               Page-spezifische Styles
├── transitions.css         View Transitions + reduced-motion
├── tooltips.css            Anchor Positioning + position-try
├── effects.css             @property Glow + @scope Isolation
├── microsims/              8 interaktive MicroSims
├── screenshots/            Brand-Swap-Test Screenshots
├── REFLECTION.md           3 Reflexionsfragen
├── DEVTOOLS_FINDINGS.md    Computed-Tab Analyse
├── BRAND_SWAP_TEST.md      Brand-Swap Anleitung
└── README.md               Diese Datei
```

## Author
Sebastian K. — Morphos Advanced CSS Cohort, Mai 2026
