# Brand-Swap-Test — Architektur-Beweis

## Anleitung

Der Brand-Swap-Test beweist, dass das 3-Layer Token-System production-tauglich ist.
Eine einzige Zeile in `tokens.css` aendern — das gesamte System folgt automatisch.

### Schritt 1: Ausgangszustand (before)
Aktueller Brand-Token in `tokens.css`, Layer 2:
```css
--color-brand: var(--indigo-500);  /* #6366f1 */
```
Screenshot speichern als `screenshots/before.png`.

### Schritt 2: Brand-Farbe aendern (after)
In `tokens.css`, Layer 1 ein neues Primitive hinzufuegen:
```css
--emerald-500: oklch(0.696 0.17 162.48);
```
Dann in Layer 2 den Brand-Token aendern:
```css
--color-brand: var(--emerald-500);
```
Reload. Screenshot speichern als `screenshots/after.png`.

### Schritt 3: Reduced-Motion Screenshot (Path B Bonus)
In DevTools: Rendering-Tab → "Emulate CSS media feature prefers-reduced-motion" → "reduce".
Screenshot speichern als `screenshots/reduced-motion.png`.

## Was sich automatisch aendert

Durch die Cascade-Architektur folgen alle abgeleiteten Tokens automatisch:

| Token (Layer 3) | Abhaengigkeit | Effekt |
|---|---|---|
| `--color-featured-tint` | `color-mix(in oklch, brand 8%, white)` | Featured-Card-Hintergrund |
| `--color-featured-border` | `color-mix(in oklch, brand 70%, white)` | Featured-Card-Border |
| `--color-button-hover` | `color-mix(in oklch, brand 85%, black)` | Button-Hover-State |
| `.price` color | `var(--color-brand)` direkt | Pricing-Zahlen |
| `.stat-value` color | `var(--color-brand)` direkt | Profile-Stat-Werte |
| `.avatar` color + border | `var(--color-brand)` + featured-border | Avatar-Circle |
| `.plan .features li::before` | `var(--color-brand)` | Checkmark-Farbe |
| `@property --pro-glow-angle` | Conic-Gradient mit brand | Animierter Glow |
| `.project-tags li` | featured-tint + featured-border | Tag-Badges |
| Nav hover + aria-current | `var(--color-brand)` | Aktiver Nav-Link |

## Ergebnis

Wenn ALLE oben genannten Elemente die neue Farbe uebernehmen:
Das Token-System ist production-tauglich. Kein Hardcoded Hex, keine vergessenen Stellen.
