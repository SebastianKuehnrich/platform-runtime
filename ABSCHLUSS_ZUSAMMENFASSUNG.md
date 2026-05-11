# Abschluss-Zusammenfassung — Hausaufgabe W1 Wochenende

**Datum:** 11.05.2026
**Student:** Sebastian K.
**Path:** A (Fundamentals) + B (Advanced) — beide Paths vollstaendig bearbeitet
**Projekt:** sebastian-platform-runtime

---

## 1. Ueberblick

Diese Zusammenfassung dokumentiert die vollstaendige Bearbeitung beider Hausaufgaben-Paths (A: Fundamentals + B: Advanced) des Advanced CSS Moduls, Woche 1, Tag 4. Das Endprodukt ist ein Personal Showcase mit 5 Pages, 8 MicroSims, und allen geforderten Features.

---

## 2. Path A — Fundamentals (4 Topics)

### F1: CSS-Selektoren und Specificity
- **MicroSim:** `microsims/specificity-calculator.html` — Interaktiver Rechner mit Live-Vergleich zweier Selektoren, farbcodierte Specificity-Digits (inline/ID/class/type), Breakdown-Anzeige
- **Tiny-Task:** 3 Specificity-Kommentare in `base.css` eingefuegt:
  - `.site-nav` → (0, 0, 1, 0)
  - `.site-nav nav a:hover` → (0, 0, 2, 2)
  - `.btn-primary` → (0, 0, 2, 0) (als Teil von `.btn.btn-primary`)
- **Erkenntnis:** `:has()` fuehrt keine eigene Specificity ein — die Specificity ist die des staerksten inneren Selektors

### F2: Box Model und box-sizing
- **MicroSim:** `microsims/box-model-playground.html` — Slider fuer Content/Padding/Border/Margin, Toggle content-box vs border-box, Live-Visualisierung der 4 Schichten
- **Tiny-Task:** Box-Model-Kommentar in `pages.css` bei `.plan`:
  - Bei content-box waere die Card 326px statt 260px breit (260 + 64 padding + 2 border)
  - Das Grid wuerde ueberlaufen
- **Erkenntnis:** `box-sizing: border-box` ist nicht optional — es ist die Basis jedes modernen Layouts

### F3: CSS Custom Properties Basics
- **MicroSim:** `microsims/custom-property-cascade.html` — Tree-Struktur mit 4 Ebenen (:root → section → card → button), Live-Farb-Preview, Fallback-Mode
- **Tiny-Task:** Cascade-Kommentar in `tokens.css` bei Layer 3:
  - `--color-brand` ist auf Layer 2 (Semantic) definiert
  - Lokales Ueberschreiben in `.login-card` wuerde alle Layer-3-Tokens mitziehen
  - Gut fuer bewusste lokale Varianten, gefaehrlich wenn unbewusst
- **Erkenntnis:** Custom Properties sind Strings — erst `@property` macht sie zu typisierten CSS-Werten

### F4: DevTools Computed-Tab
- **MicroSim:** `microsims/devtools-tour.html` — Tab-Navigation (Elements/Computed/Layout/Network/Console), annotierte Erklaerungen, 3-Fragen-Quiz
- **DEVTOOLS_FINDINGS.md:** Computed-Werte fuer `.plan`:
  - padding: 32px (2rem)
  - background: rgb(255, 255, 255)
  - border-color: rgb(226, 232, 240)
- **Erkenntnis:** Computed-Tab zeigt aufgeloeste RGB-Werte, nicht CSS-Variablen — schnellster Weg fuer Token-Debugging

---

## 3. Path B — Advanced (4 Topics)

### A1: @property Animated Conic-Gradient Border
- **Implementation:** `effects.css` mit `@property --pro-glow-angle` (syntax: `<angle>`, inherits: false)
- **MicroSim:** `microsims/property-conic-lab.html` — Slider fuer Duration/Hue/Saturation/Lightness, inherits-Toggle, Play/Pause, copy-paste-faehiger Code-Output
- **Angewandt auf:** `.plan-featured::before` — rotierender Brand-Glow auf der Pro-Pricing-Card
- **Erkenntnis:** `inherits: false` verhindert, dass nested Cards die Animation erben — Production-Standard

### A2: @scope Deep + Nested Scoping
- **Implementation:** `effects.css` mit `@scope (.glow-card)` — Hover-Glow isoliert innerhalb der Component
- **MicroSim:** `microsims/scope-visualizer.html` — Toggle @scope ON/OFF, to-Klausel-Checkbox, Live-Darstellung welche Links gestyled werden
- **Angewandt auf:** `.project-card.glow-card` — Projects-Page Cards haben isolierte Hover-Effekte
- **Erkenntnis:** `@scope` ist die Browser-native Antwort auf CSS-Modules — null Build-Step, volle Isolation

### A3: Anchor Positioning: position-try
- **Implementation:** `tooltips.css` erweitert um `position-try-fallbacks: flip-block, flip-inline, flip-block flip-inline`
- **MicroSim:** `microsims/position-try-demo.html` — Draggable Card, Tooltip flippt automatisch am Viewport-Rand, Toggle ON/OFF zum Vergleich
- **Erkenntnis:** `position-try` ist synchron im Layout-Pass — kein Frame-Lag wie bei JS-Libraries (Floating-UI)

### A4: prefers-reduced-motion
- **Implementation:** `transitions.css` erweitert um:
  - View-Transition-Deaktivierung bei reduce
  - Globales Safety-Net (`animation-duration: 0.01ms !important`)
- **MicroSim:** `microsims/reduced-motion-toggle.html` — 4 Animation-Demos (Conic Glow, Hover, Bounce, View Transition Sim), Toggle reduce ON/OFF
- **Erkenntnis:** Animation ist Opt-In (`no-preference`), nicht Opt-Out — das ist der Senior-Standard

---

## 4. Personal Showcase (8 Schritte)

| Schritt | Status | Details |
|---|---|---|
| 1. Cloning + Renaming | Erledigt | Eigenes Repo `sebastian-platform-runtime`, git init |
| 2. Profile personalisieren | Erledigt | "Sebastian K.", Frontend Developer, 12 Projects / 3 Years / 8 CSS Features |
| 3. Neue Page (projects.html) | Erledigt | 4 Projekt-Cards mit Subgrid, @scope-Isolation, glow-card, Tags |
| 4. Brand-Swap-Test | Vorbereitet | `BRAND_SWAP_TEST.md` mit Anleitung, Screenshots-Ordner bereit |
| 5. Vercel Deployment | Bereit | `npm i -g vercel && vercel` — manuell ausfuehren |
| 6. GitHub Pages | Bereit | Settings → Pages → main branch |
| 7. README.md | Erledigt | Vollstaendige Dokumentation aller Features und Dateistruktur |
| 8. Push final | Bereit | `git add . && git commit && git push` |

---

## 5. Feature-Checkliste (Mindestanforderungen)

### W1-Features auf Projects-Page (min. 3 gefordert):
- [x] Tokens aus `tokens.css` (kein Hex-Wert direkt)
- [x] Subgrid fuer Card-Row-Alignment
- [x] `@scope` fuer Component-Style-Isolation (Path B)
- [x] `color-mix(in oklch)` via Token-System

### Path-B Advanced Features (min. 2 gefordert):
- [x] `@property`-Glow auf Featured-Pricing-Card
- [x] `@scope` auf Projects-Page Cards
- [x] `position-try` auf Profile-Tooltips
- [x] `prefers-reduced-motion` globales Safety-Net

---

## 6. Erstellte Dateien

### HTML (5 Pages)
- `index.html` — Home mit Hero + Feature-Cards
- `pricing.html` — Pricing mit Subgrid + @property Glow
- `profile.html` — Profile mit Anchor-Tooltips + position-try
- `projects.html` — NEU: Portfolio mit Subgrid + @scope
- `login.html` — Login mit :has()-Validation

### CSS (6 Stylesheets)
- `tokens.css` — 3-Layer Token-System + Cascade-Kommentare
- `base.css` — Reset + Nav + Buttons + Specificity-Kommentare
- `pages.css` — Page-Styles + Projects-Styles + Box-Model-Kommentar
- `transitions.css` — View Transitions + reduced-motion Safety-Net
- `tooltips.css` — Anchor Positioning + position-try
- `effects.css` — NEU: @property Glow + @scope Isolation

### MicroSims (8 interaktive Simulationen)
- `microsims/specificity-calculator.html`
- `microsims/box-model-playground.html`
- `microsims/custom-property-cascade.html`
- `microsims/devtools-tour.html`
- `microsims/property-conic-lab.html`
- `microsims/scope-visualizer.html`
- `microsims/position-try-demo.html`
- `microsims/reduced-motion-toggle.html`

### Dokumentation (5 MD-Dateien)
- `README.md` — Projekt-Dokumentation
- `REFLECTION.md` — 3 Reflexionsfragen beantwortet
- `DEVTOOLS_FINDINGS.md` — Computed-Tab Analyse
- `BRAND_SWAP_TEST.md` — Brand-Swap Anleitung
- `ABSCHLUSS_ZUSAMMENFASSUNG.md` — Diese Datei

---

## 7. Optimierungsphase (8 Production-Ready Features)

Nach Abschluss beider Paths wurden 8 zusaetzliche Optimierungen implementiert:

| # | Optimierung | Dateien | Details |
|---|---|---|---|
| 1 | Responsive Hamburger-Nav | `base.css`, alle 5 HTML | CSS-only via `:has(.nav-toggle:checked)`, animierte Span-Rotation zu X, `@media (max-width: 640px)` |
| 2 | @container Queries | `pages.css` | `container-type: inline-size` auf `.feature-card` + `.project-card`, Layout-Switch bei 320px |
| 3 | Hero Gradient-Text | `effects.css` | `background-clip: text` mit oklch-Gradient, `@property --hero-hue` Animation, radial-gradient Hintergrund |
| 4 | Login Live-Validation | `pages.css` | `:has(input:valid:not(:placeholder-shown))` fuer Email + Passwort, gruene/rote Border, Button-Opacity reaktiv |
| 5 | Skip-to-Content Link | `base.css`, alle 5 HTML | `<a href="#main" class="skip-link">`, visuell versteckt bis `:focus`, a11y-Baseline |
| 6 | SEO Meta-Tags | alle 5 HTML | `<meta description>`, `<meta theme-color>`, Open Graph (index), SVG data-URI Favicon |
| 7 | Dark-Mode Persistence | alle 5 HTML | `localStorage.setItem('theme-dark')`, Preload-Script verhindert Flash (`dark-preload` Klasse) |
| 8 | prefers-reduced-motion | `effects.css` | Alle Animationen (Glow, Hero-Pulse) in `@media (prefers-reduced-motion: no-preference)` gewrappt |

---

## 8. Naechste Schritte (manuell)

1. **Brand-Swap Screenshots:** `tokens.css` oeffnen, `--color-brand` aendern, Screenshots machen
2. **GitHub Repo:** Neues Public Repo erstellen, Remote hinzufuegen, pushen
3. **Vercel:** `npm i -g vercel && vercel` ausfuehren
4. **GitHub Pages:** Settings → Pages → Deploy from main
5. **Live-URLs** in README.md eintragen
6. **Abgabe:** Path (A+B), GitHub-URL, Vercel-URL, GitHub-Pages-URL im Chat posten

---

*Bearbeitet am 11.05.2026 | Advanced CSS Modul, Woche 1, Tag 4 | Morphos GmbH*
