# Render — HTML→PDF dla karuzeli LinkedIn

## Zasada działania

Skill generuje jeden plik `.html` zawierający wszystkie slajdy jako osobne sekcje z `@media print` zoptymalizowane pod PDF. Każdy slajd = jedna strona A4 poziomo (lub kwadrat 1080×1080px przy ustawieniu niestandardowym).

---

## Szablon HTML (bazowy)

Wstaw poniższy kod jako strukturę pliku. Wypełnij `SLAJDY` na podstawie specyfikacji JSON z Kroku 2.

```html
<!DOCTYPE html>
<html lang="pl">
<head>
<meta charset="UTF-8">
<title>Karuzela LinkedIn — {{TEMAT}}</title>
<style>
  /* ── Reset i zmienne ── */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --brand:   {{KOLOR_MARKI}};        /* np. #0A66C2 */
    --brand-dark: color-mix(in srgb, var(--brand) 70%, black);
    --slide-w: 1080px;
    --slide-h: 1080px;
    --safe:    80px;                   /* bezpieczna strefa */
    --font-xl: 64px;
    --font-lg: 48px;
    --font-md: 32px;
    --font-sm: 24px;
    --font-xs: 18px;
  }

  /* ── Slajd — jednostka bazowa ── */
  .slide {
    width: var(--slide-w);
    height: var(--slide-h);
    padding: var(--safe);
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    overflow: hidden;
    page-break-after: always;
    break-after: page;
    font-family: 'Segoe UI', 'Inter', Arial, sans-serif;
  }

  /* ── Warianty tła ── */
  .slide.dark  { background: #0f0f0f; color: #ffffff; }
  .slide.light { background: #f8f9fa; color: #1a1a1a; }
  .slide.brand { background: var(--brand); color: #ffffff; }
  .slide.white { background: #ffffff; color: #1a1a1a; }

  /* ── Typografia ── */
  .headline {
    font-size: var(--font-lg);
    font-weight: 800;
    line-height: 1.15;
    margin-bottom: 28px;
    letter-spacing: -0.02em;
  }
  .headline.xl { font-size: var(--font-xl); }

  .body { font-size: var(--font-md); line-height: 1.5; }

  ul.body-list {
    list-style: none;
    font-size: var(--font-md);
    line-height: 1.5;
    display: flex;
    flex-direction: column;
    gap: 16px;
  }
  ul.body-list li::before {
    content: "→ ";
    color: var(--brand);
    font-weight: 700;
  }

  .quote {
    font-size: var(--font-lg);
    font-weight: 700;
    font-style: italic;
    line-height: 1.3;
    border-left: 6px solid var(--brand);
    padding-left: 32px;
  }

  /* ── Akcent kolorowy ── */
  .accent { color: var(--brand); }
  .slide.dark .accent,
  .slide.brand .accent { color: #FFD700; }

  /* ── Numer slajdu (prawy górny róg) ── */
  .slide-num {
    position: absolute;
    top: 32px;
    right: 40px;
    font-size: var(--font-xs);
    opacity: 0.45;
    font-weight: 600;
    letter-spacing: 0.05em;
  }

  /* ── Branding (lewy dolny róg) ── */
  .brand-tag {
    position: absolute;
    bottom: 32px;
    left: var(--safe);
    font-size: var(--font-xs);
    opacity: 0.55;
    font-weight: 500;
  }

  /* ── Linia dekoracyjna ── */
  .divider {
    width: 60px;
    height: 5px;
    background: var(--brand);
    border-radius: 3px;
    margin-bottom: 28px;
  }
  .slide.brand .divider,
  .slide.dark  .divider { background: #FFD700; }

  /* ── Duża liczba dekoracyjna (dla hooków liczbowych) ── */
  .big-num {
    font-size: 200px;
    font-weight: 900;
    opacity: 0.08;
    position: absolute;
    bottom: -20px;
    right: 40px;
    line-height: 1;
    color: var(--brand);
    pointer-events: none;
  }

  /* ── CTA button ── */
  .cta-btn {
    display: inline-block;
    margin-top: 40px;
    padding: 20px 48px;
    background: var(--brand);
    color: #fff;
    font-size: var(--font-sm);
    font-weight: 700;
    border-radius: 8px;
    text-align: center;
  }
  .slide.brand .cta-btn { background: #fff; color: var(--brand); }

  /* ── Print / PDF ── */
  @media print {
    html, body { margin: 0; padding: 0; background: white; }
    .slide { page-break-after: always; break-after: page; }
    .slide:last-child { page-break-after: avoid; break-after: avoid; }
  }

  /* ── Podgląd w przeglądarce ── */
  @media screen {
    body {
      background: #e5e5e5;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 24px;
      padding: 40px;
    }
    .slide {
      box-shadow: 0 8px 40px rgba(0,0,0,0.18);
      border-radius: 4px;
    }
  }
</style>
</head>
<body>

<!-- ═══════════════════════════════════════════
     SLAJD 1 — HOOK (ciemne tło, duża typografia)
     ═══════════════════════════════════════════ -->
<div class="slide dark">
  <span class="slide-num">1 / {{TOTAL}}</span>
  <div class="divider"></div>
  <h1 class="headline xl">{{NAGLOWEK_1}}</h1>
  <p class="body">{{BODY_1}}</p>
  <div class="big-num">{{LICZBA_SLAJDOW}}</div>
  <span class="brand-tag">{{AUTOR}}</span>
</div>

<!-- ═══════════════════════════════════════════
     SLAJD 2 — OBIETNICA (jasne tło)
     ═══════════════════════════════════════════ -->
<div class="slide light">
  <span class="slide-num">2 / {{TOTAL}}</span>
  <div class="divider"></div>
  <h2 class="headline">{{NAGLOWEK_2}}</h2>
  <ul class="body-list">
    <li>{{PUNKT_1}}</li>
    <li>{{PUNKT_2}}</li>
    <li>{{PUNKT_3}}</li>
  </ul>
  <span class="brand-tag">{{AUTOR}}</span>
</div>

<!-- ═══════════════════════════════════════════
     SLAJDY 3–8 — WARTOŚĆ (białe tło)
     Kopiuj ten blok dla każdego slajdu wartości
     ═══════════════════════════════════════════ -->
<div class="slide white">
  <span class="slide-num">3 / {{TOTAL}}</span>
  <div class="divider"></div>
  <h2 class="headline">{{NAGLOWEK_3}}</h2>
  <ul class="body-list">
    <li>{{PUNKT_A}}</li>
    <li>{{PUNKT_B}}</li>
    <li class="accent">{{KONKLUZJA}}</li>
  </ul>
  <span class="brand-tag">{{AUTOR}}</span>
</div>

<!-- ═══════════════════════════════════════════
     SLAJD PODSUMOWANIE — cytat / esencja
     ═══════════════════════════════════════════ -->
<div class="slide dark">
  <span class="slide-num">{{NR_PODSUM}} / {{TOTAL}}</span>
  <blockquote class="quote">
    "{{CYTAT_ESENCJA}}"
  </blockquote>
  <span class="brand-tag">{{AUTOR}}</span>
</div>

<!-- ═══════════════════════════════════════════
     SLAJD CTA — kolor marki jako tło
     ═══════════════════════════════════════════ -->
<div class="slide brand">
  <span class="slide-num">{{TOTAL}} / {{TOTAL}}</span>
  <h2 class="headline xl">{{CTA_NAGLOWEK}}</h2>
  <p class="body">{{CTA_BODY}}</p>
  <div class="cta-btn">{{CTA_AKCJA}}</div>
  <span class="brand-tag">{{AUTOR}}</span>
</div>

</body>
</html>
```

---

## Mapowanie JSON → HTML

Przy generowaniu pliku HTML ze specyfikacji JSON zastosuj to mapowanie:

| Pole JSON | Placeholder HTML |
|---|---|
| `meta.kolor` | `{{KOLOR_MARKI}}` |
| `meta.temat` | `{{TEMAT}}` |
| `meta.autor` | `{{AUTOR}}` |
| `slajdy.length` | `{{TOTAL}}` |
| `slajdy[i].naglowek` | `{{NAGLOWEK_N}}` |
| `slajdy[i].body[0..2]` | `{{PUNKT_X}}`, `{{PUNKT_Y}}`, `{{KONKLUZJA}}` |

**Typ tła per typ slajdu:**

| `typ` w JSON | Klasa CSS |
|---|---|
| `hook` | `dark` |
| `obietnica` | `light` |
| `wartosc` | `white` (nieparzyste) / `light` (parzyste) |
| `podsumowanie` | `dark` |
| `cta` | `brand` |
| `branding` | `dark` |

---

## Eksport do PDF — instrukcja dla użytkownika

### Metoda A: Drukowanie w przeglądarce (zero instalacji)

1. Otwórz plik w **Chrome** lub **Edge** (inne przeglądarki mogą obcinać marginesy)
2. `Ctrl+P` (Windows) lub `Cmd+P` (Mac)
3. Ustaw:
   - **Drukarka:** Zapisz jako PDF / Save as PDF
   - **Rozmiar papieru:** Niestandardowy → `1080 × 1080 px` lub A4 poziomo
   - **Marginesy:** Brak / None
   - **Tło graficzne:** ✓ włączone (Więcej ustawień → Grafika tła)
4. Kliknij **Zapisz**

### Metoda B: Python + WeasyPrint (linia poleceń)

```bash
pip install weasyprint
python -c "from weasyprint import HTML; HTML('karuzela.html').write_pdf('karuzela.pdf')"
```

### Metoda C: Python + Puppeteer (Node.js, najlepsza jakość)

```bash
npm install puppeteer
node -e "
const puppeteer = require('puppeteer');
(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();
  await page.goto('file://' + process.cwd() + '/karuzela.html', {waitUntil: 'networkidle0'});
  await page.pdf({
    path: 'karuzela.pdf',
    width: '1080px',
    height: '1080px',
    printBackground: true
  });
  await browser.close();
  console.log('PDF gotowy: karuzela.pdf');
})();
"
```

---

## Wgrywanie PDF na LinkedIn

1. Zaloguj się na LinkedIn
2. Utwórz nowy post → kliknij ikonę **dokumentu** (nie zdjęcia)
3. Wgraj plik `.pdf`
4. LinkedIn automatycznie zamieni strony PDF na slajdy karuzeli
5. Dodaj tytuł dokumentu (pojawi się pod karuzelą)
6. Wklej tekst posta z hookiem i CTA
7. Opublikuj

**Limit:** LinkedIn akceptuje PDF do **300 MB** i **max 300 slajdów**. Standardowa karuzela 10-slajdowa to zwykle 1–5 MB.

---

## Rozszerzone możliwości renderera

### Wariant jasny (light mode)

Zmień `.slide.dark` na `.slide.light` dla całej karuzeli jeśli temat jest pozytywny/aspiracyjny.

### Ikony (bez zewnętrznych zasobów)

Używaj emoji jako ikon — są wbudowane w system i działają w PDF:
```html
<span style="font-size:48px">🎯</span>
```

### Numery slajdów z postępem

```html
<div class="progress" style="
  position:absolute; bottom:0; left:0;
  height:4px; background:var(--brand);
  width: calc({{NR}} / {{TOTAL}} * 100%);
"></div>
```

### Zdjęcie autora

```html
<img src="avatar.jpg" style="
  position:absolute; bottom:32px; right:80px;
  width:60px; height:60px;
  border-radius:50%; object-fit:cover;
  border:2px solid var(--brand);
">
```
