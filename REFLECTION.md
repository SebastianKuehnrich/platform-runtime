# Reflexion — Drei Fragen

## Frage 1
> Welches Feature aus dieser Woche werdet ihr in eurem naechsten Production-Project NICHT mehr ohne benutzen koennen — und warum?

Das 3-Layer Token-System mit `color-mix(in oklch)` — weil es Brand-Wechsel zu einer einzigen Zeile macht und alle abgeleiteten Farben automatisch korrekt bleiben, ohne dass man 30 Hex-Werte manuell anpassen muss.

## Frage 2
> Wenn ihr nur ein einziges Feature behalten duerftet, welches und warum?

`:has()` — weil es zum ersten Mal in CSS-Geschichte einen Parent-Selector gibt und damit State-Detection ohne JavaScript moeglich macht. Die Login-Form-Validation (`.login-form:has(input:placeholder-shown)`) zeigt, was vorher zwingend JS brauchte, jetzt in einer CSS-Zeile lebt.

## Frage 3
> Was kommt am Montag mit Motion, was Modern CSS NICHT abdecken kann?

CSS hat keine Springs (physikalisch korrekte Animationen), keine Exit-Animations bei DOM-Removal (AnimatePresence), keine deklarativen Drag/Touch-Gesten, und keine orchestrierten Multi-Element-Stagger-Animations. Die letzten 30% der Animation-Welt — state-getrieben, gestural, orchestriert — sind Motion-Territorium.
