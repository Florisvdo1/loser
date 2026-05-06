# Kuur App — v2.1

Een privé, mobiel-first PWA voor een 10-daagse medicatiekuur met 4 innamemomenten per dag.
Premium iPhone 15 Pro portrait design, volledig statisch, geen externe libraries, offline-first.

## Inhoud

```
.
├── index.html              ← single-file app (HTML + CSS + JS)
├── manifest.webmanifest    ← PWA manifest
├── sw.js                   ← service worker (offline-first)
├── README.md               ← deze file
├── .gitignore
└── icons/                  ← favicon + alle PWA icons
```

## Functies

- **Vandaag** — dag X / 10, 4 innamemomenten, status per dosis, voortgang.
- **Wekkers** — iOS Wekker Assistent: 4 wekkerlabels, kopieerknop, stap-voor-stap uitleg.
- **Guide** — korte regels: 4 × per dag, glas water, lege maag, 10 dagen, kuur afmaken.
- **Voortgang** — 10-dagen overzicht, totaal ingenomen, voltooide dagen.
- **Instellingen** — startdatum, voorbeeldschema, reset, lokale data wissen.

Alle voortgang staat in `localStorage` onder de sleutel `kuur-v2-state`. Geen analytics, geen netwerk-calls, geen account.

## Deploy via Working Copy + GitHub Pages

1. Pak de ZIP uit.
2. Kopieer **alle bestanden** (incl. `icons/`) naar de root van je GitHub-repo.
3. Commit in **Working Copy**.
4. Push naar GitHub.
5. **Settings → Pages** → branch `main`, folder `/ (root)` → Save.
6. Open de Pages-URL in **Safari** op je iPhone → **Deel** → **Zet op beginscherm**.

## iOS — wekkers instellen

Deze app maakt **geen** wekkers automatisch aan (een statische webapp mag dat niet beloven). Gebruik in plaats daarvan de in-app **Wekker Assistent**:

1. Open de app → tab **Wekkers**.
2. Tik **Kopieer wekkerlabels** of bekijk de 4 labels in de kaarten.
3. Open de standaard **Wekker** app op je iPhone.
4. Tik op +, kies tijd, zet **Herhaal: Elke dag**, plak het label, **Bewaar**.
5. Herhaal voor alle 4 momenten.

## Tech

- Native iOS font stack (`-apple-system`).
- 100 dvh layout, safe-area-inset support.
- 4-px / 8-px grid, max-width 430 px, 44 pt touch targets.
- Service worker met cache-first voor de app shell.
- Geen build step, geen npm.
- Respecteert `prefers-reduced-motion`.

---

Privé · v2.1 · 2026
