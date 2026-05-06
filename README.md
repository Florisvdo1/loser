# Kuur — Flucloxacilline 500 mg

Een privé, mobiel-first PWA voor het bijhouden van de antibiotica­kuur van Floris.
4 × per dag, 1 capsule, gedurende 10 dagen — `40 ST FLUCLOXACILLINE CAPS 500MG`.

> Privé project. Niet voor openbare publicatie. Alle gegevens blijven lokaal in de
> browser (`localStorage`) — er is geen backend, geen tracking, geen account.

---

## ✦ Wat zit erin

- **Methode 1** — Vaste dagklokken: **07:00 · 12:00 · 18:00 · 23:00**
  (uit de bijsluiter: *"Bij 4 keer per dag bijvoorbeeld om 7, 12, 18 en 23 uur"*)
- **Methode 2** — Strikte 6-uurs intervallen: **06:00 · 12:00 · 18:00 · 00:00**
  (klinisch gelijkmatige spiegel — vraag eerst de apotheek bij twijfel)
- **Info** — Nederlandse samenvatting van de bijsluiter (werking, gebruik, dosering, vergeten dosis, bewaren, bijwerkingen, kenmerken, contact apotheek).
- **Toggle per inname** — tik op een capsule-cel om af te vinken; haptische feedback + zachte chime.
- **Native iOS-alarmen** — exporteer alle aangevinkte tijdstippen als `.ics`-bestand. iOS importeert dit als Agenda-events met alarmen op het exacte tijdstip én 5 minuten vooraf.
- **In-app alarm** — als de app open is wanneer een dosering valt, klinkt er een rustig-maar-luid bel-tonenrij.
- **PWA** — installeer via *Deel → Zet op beginscherm*. Werkt offline.

## ✦ Bestandsstructuur

```
kuur-app/
├── index.html              ← alles geïntegreerd (HTML + CSS + JS)
├── manifest.webmanifest    ← PWA manifest
├── sw.js                   ← service worker, offline-first
├── icons/
│   ├── icon.svg
│   ├── icon-192.png
│   ├── icon-512.png
│   ├── maskable-512.png
│   ├── apple-touch-icon.png
│   ├── favicon.svg
│   ├── favicon-16.png
│   └── favicon-32.png
└── README.md
```

---

## ✦ Deploy naar GitHub Pages

1. Maak een (privé) repository, bv. `kuur-app`.
2. Upload de inhoud van deze map naar de `main`-branch (root).
3. Ga naar **Settings → Pages**, kies **Source: Deploy from a branch**, branch **`main`**, folder **`/ (root)`**.
4. Wacht ~1 minuut. Je app staat op `https://<jouw-username>.github.io/kuur-app/`.
5. Open die URL op je iPhone in **Safari** → **Deel-knop** → **Zet op beginscherm**.

> Tip: Voor een volledig privé installatie kun je de repo *private* houden en
> in plaats van GitHub Pages een tool als [Cloudflare Pages](https://pages.cloudflare.com)
> gebruiken met een niet-vermeld subdomein.

## ✦ iOS — alarmen instellen

1. Open de app, ga naar **Methode 1** of **Methode 2**.
2. Tik op het **belletje** naast elke dosering die je wilt laten herinneren (standaard staan ze allemaal aan).
3. Tik onderaan op **Exporteer alarmen (.ics)**.
4. iOS opent het bestand → **Voeg toe aan Agenda**.
5. Elk event heeft een alarm op het exacte tijdstip én een waarschuwing 5 min vooraf.
6. (Aanbevolen) Stel je iPhone in op **Stille modus uit** of gebruik **Focus → Slaap** met *medicatie* als toegestane melding voor de 23:00/00:00 dosering.

## ✦ Privacy

- 100 % lokaal. Geen analytics, geen externe API-calls behalve Google Fonts (CSS).
- Alle voortgang staat in `localStorage` onder de sleutel `kuur-state-v1`.
- Niets verlaat je telefoon.

---

## ✦ Bronnen & disclaimer (NL)

De inneemtijden komen rechtstreeks uit de officiële bijsluiter ("Bij 4 keer per dag
bijvoorbeeld om 7, 12, 18 en 23 uur") en uit standaard apothekersadvies voor
4 × daagse antibiotica. **Volg altijd het advies van je apotheek of arts** als
dat afwijkt — dit is een persoonlijke hulptool, geen medisch advies.

> ⚠️ Audio-transcriptie van `Opname_medicatie_innemen.m4a` was niet mogelijk in
> de buildomgeving (modeldownload geblokkeerd). De twee methodes zijn afgeleid
> van de bijsluiter en gangbare apothekersrichtlijnen.

---

## ✦ Tech

- Vanilla HTML / CSS / JS — geen build step, geen dependencies.
- Service worker met cache-first strategie voor offline gebruik.
- Web Audio API voor alarm-tonen (geen audiobestanden vereist).
- iCalendar (RFC 5545) export met `VALARM`-blokken voor native iOS-alarmen.
- Fonts: *Instrument Serif*, *Geist*, *Geist Mono* (Google Fonts).
- Optimaal voor iPhone 15 Pro portrait (393 × 852 pt). Werkt op alle moderne mobiele browsers.

---

## ✦ Built for Floris — privé · 2026
