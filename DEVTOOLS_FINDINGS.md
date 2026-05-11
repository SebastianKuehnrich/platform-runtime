# DevTools Findings — Sebastian's Showcase

## 1. .plan padding
- **Computed value:** 32px (2rem bei Standard-Font-Size 16px)
- **Cascaded from:** `.plan { padding: 2rem }` in `pages.css`

## 2. .plan background
- **Computed value:** rgb(255, 255, 255) (Light Mode) / rgb(51, 65, 85) (Dark Mode)
- **Cascaded from:** `.plan { background: var(--color-card) }` in `pages.css`, Token aufgeloest via `--color-card: var(--white)` in `tokens.css` Layer 2

## 3. .plan border-color
- **Computed value:** rgb(226, 232, 240) (Light Mode) / rgb(100, 116, 139) (Dark Mode)
- **Cascaded from:** `.plan { border: 1px solid var(--color-border) }` in `pages.css`, Token aufgeloest via `--color-border: var(--slate-200)` in `tokens.css` Layer 2

## 4. .plan-featured border-color (Bonus)
- **Computed value:** Berechnet via `color-mix(in oklch, var(--color-brand) 70%, white)` — ergibt einen hellen Indigo-Ton
- **Cascaded from:** `.plan-featured { border: 2px solid var(--color-featured-border) }` in `pages.css`, Token aus Layer 3

## Erkenntnis
Der Computed-Tab zeigt die aufgeloesten RGB-Werte, nicht die CSS-Variablen. Das ist der schnellste Weg, Token-Bugs zu finden — wenn der Computed-Wert nicht zum erwarteten Token passt, ist die Variable falsch definiert oder wird von einer hoeheren Specificity ueberschrieben.
