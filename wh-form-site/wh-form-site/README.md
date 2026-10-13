# WH FORM

Statisk nettside for WH FORM — norsk produksjonsverksted for gravsteiner og monumenter. Minimalistisk, editorial, portfolio-first. Ingen rammeverk, ingen byggesteg — ren HTML og CSS.

## Struktur

```
wh-form-site/
├── index.html        # ARBEIDER (forside) — bildestrøm
├── prosess.html      # PROSESS — landskapsvideo dratt til høyre kant
├── om.html           # OM — tekst om WH FORM + kontakt
├── style.css         # Felles stil for alle tre sider
├── images/           # Gravsteinsrender
│   ├── 01-kirke.png  ✓ inkludert
│   ├── 02-over.png   ← må legges til
│   ├── 03-kors.png   ← må legges til
│   ├── 04-himmel.png ← må legges til
│   ├── 05-oval.png   ← må legges til
│   └── 06-skraa.png  ← må legges til
├── video/            # Prosessvideoer (opprett mappen, se under)
├── .nojekyll         # Lar GitHub Pages servere filene som de er
└── README.md
```

## Sider

- **ARBEIDER** (`index.html`) — sentral bildestrøm, metadata i margene.
- **PROSESS** (`prosess.html`) — landskapsformat dratt helt ut til høyre kant, referansetekst til venstre. Viser videoer.
- **OM** (`om.html`) — all tekst om WH FORM, grunnleggerne, kontakt og marked.

All tekst vises i VERSALER (styres av `text-transform:uppercase` i `style.css`).

## Video i PROSESS

Hvert prosess-element har et landskaps-placeholderfelt (16:9). Legg videoene i en `video/`-mappe og bytt ut placeholderen i `prosess.html`:

```html
<!-- erstatt denne -->
<div class="ph">Video — landskap 16:9</div>

<!-- med denne -->
<video src="video/01-kirke.mp4" autoplay muted loop playsinline></video>
```

## Bilder som mangler

Kun `01-kirke.png` er inkludert. De fem andre rendene ligger på WordPress-siden og må lastes ned og legges i `images/` med nøyaktig disse filnavnene:

| Filnavn | Motiv | Kilde (WordPress) |
|---|---|---|
| `02-over.png` | Over — blå naturstein | `chatgpt-image-jun-7-2026-at-06_56_43-pm.png` |
| `03-kors.png` | Kors | `chatgpt-image-jun-7-2026-at-06_16_48-pm.png` |
| `04-himmel.png` | Himmel | `16f9ce88-98e7-4a0d-ab64-1683d646a8bb.png` |
| `05-oval.png` | Oval | `chatgpt-image-jun-8-2026-at-08_46_17-pm.png` |
| `06-skraa.png` | Skrå — rød granitt | `chatgpt-image-jun-9-2026-at-11_58_36-am.png` |

Last ned fra WordPress-mediebiblioteket (eller bruk originalfilene) og gi dem navnene i tabellen. Da er siden fullstendig selvstendig uten eksterne avhengigheter.

## Publisere på GitHub Pages

1. Lag et nytt repo på GitHub (f.eks. `wh-form`).
2. Last opp innholdet i denne mappen til repoet:
   ```bash
   git init
   git add .
   git commit -m "WH FORM nettside"
   git branch -M main
   git remote add origin https://github.com/<brukernavn>/wh-form.git
   git push -u origin main
   ```
3. På GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, velg `main` / `root`, lagre.
4. Siden blir tilgjengelig på `https://<brukernavn>.github.io/wh-form/` etter et par minutter.

## Eget domene (whform.no)

I **Settings → Pages → Custom domain** legger du inn domenet, og setter opp DNS hos domeneleverandøren (CNAME mot `<brukernavn>.github.io`, eller A-records mot GitHub Pages sine IP-er). GitHub skriver da en `CNAME`-fil i repoet automatisk.

## Legge til nye prosjekter

Hvert prosjekt er en `<article class="project">`-blokk i `index.html`. Kopier en eksisterende blokk, oppdater løpenummer, tittel, material, referanse og bildefilen. Layoutsystemet trenger ingen endring.

## Designprinsipper

Svart bakgrunn, hvit tekst, flat typografi (Helvetica Neue), 12-kolonners editorial grid, metadata forankret i marginene, bildene i sentral kolonne. Ingen cards, shadows, gradienter eller border-radius. Whitespace er et aktivt virkemiddel.
