# Dokumentacja Techniczna HTML Ebooka
## Styl: Nowoczesny Rustyk / Modern Farmhouse

---

# 1. FILOZOFIA WIZUALNA

Ebook ma łączyć dwie pozornie sprzeczne rzeczy: ciepło wiejskiej kuchni i czytelność nowoczesnego medium cyfrowego. Nie chodzi o udawanie, że strona wygląda jak pergamin albo stara drewniana tablica. Chodzi o to, żeby czytającemu było ciepło w środku i żeby chciał czytać dalej. Styl Modern Farmhouse to szlachetne materiały, naturalne barwy, gruba typografia i dużo oddechu między elementami.

Słowa klucze dla całego projektu: **drewno, len, ziemia, mleko, zioła, luz, spokój, jakość**.

---

# 2. PALETA KOLORÓW

Wszystkie kolory definiujemy jako zmienne CSS na poziomie `:root`. Nigdy nie używamy hardkodowanych wartości heksadecymalnych w komponentach.

```css
:root {
  /* Tła */
  --color-bg-primary:     #FAF7F2;  /* ciepła biel, jak ściana z wapna */
  --color-bg-secondary:   #F2EDE4;  /* lniany beż */
  --color-bg-card:        #FFFFFF;  /* czysta biel dla kart treści */
  --color-bg-dark:        #2C2416;  /* ciemna czekolada, nagłówki sekcji */
  --color-bg-accent:      #4A3728;  /* ciemny brąz mahoniowy */

  /* Tekst */
  --color-text-primary:   #2C2416;  /* prawie czarny, ciepły */
  --color-text-secondary: #6B5744;  /* brązowa ziemia */
  --color-text-muted:     #9E8B7A;  /* wypłowiały brąz */
  --color-text-inverse:   #FAF7F2;  /* jasny tekst na ciemnym tle */

  /* Akcenty */
  --color-accent-primary: #8B6914;  /* złoto pszenicy */
  --color-accent-warm:    #C4722A;  /* terakota, kolor gliny */
  --color-accent-green:   #5C7A3E;  /* zieleń liści */
  --color-accent-red:     #8B3A2A;  /* ciemnoczerwony, kolor grzebienia */

  /* Obramowania i linie */
  --color-border-light:   #E0D5C5;  /* bardzo jasna kreska */
  --color-border-medium:  #C5B49A;  /* naturalne płótno */
  --color-border-dark:    #8B7355;  /* ciemniejsza linia */

  /* Cienie */
  --shadow-soft:  0 2px 12px rgba(44, 36, 22, 0.08);
  --shadow-card:  0 4px 24px rgba(44, 36, 22, 0.10);
  --shadow-hover: 0 8px 32px rgba(44, 36, 22, 0.15);
}
```

---

# 3. TYPOGRAFIA

## 3.1. Fonty

Importujemy trzy kroje pisma z Google Fonts. Każdy pełni inną rolę i nie wolno ich zamieniać.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400;1,600&family=Lora:ital,wght@0,400;0,500;0,600;1,400&family=Nunito+Sans:wght@300;400;600&display=swap" rel="stylesheet">
```

| Zmienna CSS             | Krój                | Zastosowanie                                  |
|-------------------------|---------------------|-----------------------------------------------|
| `--font-display`        | Playfair Display    | Tytuły rozdziałów, nagłówki H1, H2            |
| `--font-body`           | Lora                | Tekst główny - cały bieg narracyjny           |
| `--font-ui`             | Nunito Sans         | Etykiety, numery stron, spis treści, UI       |

```css
:root {
  --font-display: 'Playfair Display', Georgia, serif;
  --font-body:    'Lora', 'Times New Roman', serif;
  --font-ui:      'Nunito Sans', sans-serif;
}
```

## 3.2. Skala typograficzna

```css
:root {
  --text-xs:   0.75rem;   /* 12px - podpisy, etykiety */
  --text-sm:   0.875rem;  /* 14px - drobny UI */
  --text-base: 1.0625rem; /* 17px - tekst główny */
  --text-md:   1.25rem;   /* 20px - lead, pierwsze akapity */
  --text-lg:   1.5rem;    /* 24px - H3 */
  --text-xl:   2rem;      /* 32px - H2 */
  --text-2xl:  2.75rem;   /* 44px - H1 rozdziału */
  --text-3xl:  4rem;      /* 64px - tytuł okładki */
}
```

## 3.3. Właściwości tekstu głównego

```css
body {
  font-family:      var(--font-body);
  font-size:        var(--text-base);
  line-height:      1.85;
  color:            var(--color-text-primary);
  background-color: var(--color-bg-primary);
  font-weight:      400;
  -webkit-font-smoothing: antialiased;
  text-rendering:   optimizeLegibility;
}
```

Interlinia 1.85 to kluczowy wybór. Dla tekstu narracyjnego, który czytelnik czyta długo, jest to poziom, który nie męczy oczu.

## 3.4. Nagłówki

```css
h1, h2, h3, h4 {
  font-family: var(--font-display);
  color:       var(--color-text-primary);
  line-height: 1.2;
  font-weight: 700;
}

/* Numer i tytuł rozdziału */
.chapter-number {
  font-family:    var(--font-ui);
  font-size:      var(--text-sm);
  font-weight:    600;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color:          var(--color-accent-primary);
}

.chapter-title {
  font-family: var(--font-display);
  font-size:   var(--text-2xl);
  font-weight: 700;
  margin-top:  0.25em;
}

/* H2 - podrozdział */
h2.section-title {
  font-size:     var(--text-xl);
  font-weight:   600;
  margin-top:    3rem;
  margin-bottom: 1rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid var(--color-border-light);
}

/* H3 - podtytuł */
h3.subsection-title {
  font-size:     var(--text-lg);
  font-weight:   600;
  font-style:    italic;
  margin-top:    2rem;
  margin-bottom: 0.75rem;
  color:         var(--color-text-secondary);
}
```

---

# 4. UKŁAD STRONY (LAYOUT)

## 4.1. Kontener i szerokości

```css
.ebook-wrapper {
  max-width:  100%;
  min-height: 100vh;
  background: var(--color-bg-primary);
}

/* Kolumna tekstu - serce ebooka */
.content-column {
  max-width:     720px;
  margin:        0 auto;
  padding:       0 2rem;
}

/* Szeroka kolumna dla elementów wyróżnionych */
.content-column--wide {
  max-width: 960px;
  margin:    0 auto;
  padding:   0 2rem;
}

/* Pełna szerokość dla nagłówków rozdziałów */
.content-column--full {
  max-width: 100%;
  padding:   0;
}

@media (max-width: 768px) {
  .content-column,
  .content-column--wide {
    padding: 0 1.25rem;
  }
}
```

Kolumna 720px to klasyczna szerokość dla komfortowego czytania. Przy 17px tekstu i interlinie 1.85 daje to idealny rytm.

## 4.2. Struktura dokumentu HTML

```html
<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Kompleksowy Poradnik Hodowcy Kur</title>
  <!-- fonty, CSS -->
</head>
<body>

  <!-- NAWIGACJA BOCZNA (sidebar) -->
  <nav class="sidebar" id="sidebar">...</nav>

  <!-- OVERLAY dla mobilnego menu -->
  <div class="sidebar-overlay" id="sidebarOverlay"></div>

  <!-- GŁÓWNA TREŚĆ -->
  <main class="main-content" id="mainContent">

    <!-- OKŁADKA -->
    <section class="cover-page">...</section>

    <!-- STRONA TYTUŁOWA / WSTĘP -->
    <section class="front-matter">...</section>

    <!-- ROZDZIAŁY (powtarzalny blok) -->
    <article class="chapter" id="chapter-1">

      <!-- Nagłówek rozdziału - pełna szerokość -->
      <header class="chapter-header">...</header>

      <!-- Treść rozdziału - kolumna 720px -->
      <div class="chapter-body content-column">
        ...
      </div>

    </article>

    <!-- STOPKA EBOOKA -->
    <footer class="ebook-footer">...</footer>

  </main>

  <!-- PASEK POSTĘPU CZYTANIA -->
  <div class="reading-progress" id="readingProgress"></div>

</body>
</html>
```

---

# 5. KOMPONENTY

## 5.1. Nagłówek rozdziału (Chapter Header)

Nagłówek rozdziału zajmuje pełną szerokość ekranu. Ma ciemne tło, dekoracyjny wzór i dużą typografię.

```html
<header class="chapter-header">
  <div class="chapter-header__bg"></div>
  <div class="chapter-header__content content-column">
    <span class="chapter-number">Rozdział 7</span>
    <h1 class="chapter-title">Projektowanie i budowa kurnika</h1>
    <p class="chapter-lead">
      Kurnik to fundament całej hodowli. Można kupić najlepsze kury świata,
      ale jeśli mieszkają źle, nie dadzą ci ani jaja więcej niż przeciętna.
    </p>
    <div class="chapter-meta">
      <span class="chapter-meta__item">⏱ Czas czytania: ok. 18 minut</span>
      <span class="chapter-meta__item">📄 12 podrozdziałów</span>
    </div>
  </div>
</header>
```

```css
.chapter-header {
  position:   relative;
  background: var(--color-bg-dark);
  color:      var(--color-text-inverse);
  padding:    5rem 0 4rem;
  overflow:   hidden;
}

/* Dekoracyjny wzór w tle - siatka jak kurnik */
.chapter-header__bg {
  position:         absolute;
  inset:            0;
  background-image: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 39px,
    rgba(255,255,255,0.03) 39px,
    rgba(255,255,255,0.03) 40px
  ),
  repeating-linear-gradient(
    90deg,
    transparent,
    transparent 39px,
    rgba(255,255,255,0.03) 39px,
    rgba(255,255,255,0.03) 40px
  );
  pointer-events: none;
}

.chapter-header .chapter-number {
  color:          var(--color-accent-primary);
  display:        block;
  margin-bottom:  0.75rem;
}

.chapter-header .chapter-title {
  color:         var(--color-text-inverse);
  font-size:     clamp(2rem, 5vw, var(--text-2xl));
  margin-bottom: 1.25rem;
}

.chapter-lead {
  font-family:   var(--font-body);
  font-size:     var(--text-md);
  font-style:    italic;
  color:         rgba(250, 247, 242, 0.75);
  max-width:     58ch;
  line-height:   1.7;
  margin-bottom: 2rem;
}

.chapter-meta {
  display:   flex;
  gap:       1.5rem;
  flex-wrap: wrap;
}

.chapter-meta__item {
  font-family:    var(--font-ui);
  font-size:      var(--text-sm);
  color:          rgba(250, 247, 242, 0.55);
  letter-spacing: 0.02em;
}
```

## 5.2. Akapit i tekst główny

```css
.chapter-body p {
  margin-bottom: 1.5rem;
  max-width:     68ch;
}

/* Pierwsze zdanie akapitu po nagłówku - powiększone */
.chapter-body h2 + p,
.chapter-body h3 + p {
  font-size:   var(--text-md);
  font-weight: 500;
  color:       var(--color-text-secondary);
}

/* Pierwsze słowo / inicjał rozdziału (drop cap) */
.chapter-body > p:first-of-type::first-letter {
  font-family:   var(--font-display);
  font-size:     4.5em;
  font-weight:   700;
  float:         left;
  line-height:   0.75;
  margin-right:  0.1em;
  margin-top:    0.1em;
  color:         var(--color-accent-primary);
}
```

## 5.3. Cytat wyróżniony (Blockquote)

Stosujemy do mocnych zdań i wniosków, które chcemy, żeby czytelnik zapamiętał.

```html
<blockquote class="pull-quote">
  <p>Kurnik to nie koszt. To inwestycja, która zwraca się przez dziesięć lat.</p>
</blockquote>
```

```css
.pull-quote {
  position:     relative;
  margin:       3rem 0;
  padding:      2rem 2rem 2rem 3rem;
  background:   var(--color-bg-secondary);
  border-left:  4px solid var(--color-accent-primary);
  border-radius: 0 8px 8px 0;
}

.pull-quote::before {
  content:     '\201C';
  font-family: var(--font-display);
  font-size:   6rem;
  color:       var(--color-accent-primary);
  opacity:     0.25;
  position:    absolute;
  top:         -1rem;
  left:        1rem;
  line-height: 1;
}

.pull-quote p {
  font-family: var(--font-display);
  font-size:   var(--text-lg);
  font-style:  italic;
  line-height: 1.5;
  color:       var(--color-text-primary);
  margin:      0;
}
```

## 5.4. Ramka z poradą (Tip Box)

Cztery warianty: porada, ostrzeżenie, ważne, ciekawostka.

```html
<div class="tip-box tip-box--tip">
  <div class="tip-box__icon">💡</div>
  <div class="tip-box__content">
    <strong class="tip-box__label">Wskazówka</strong>
    <p>Orientuj kurnik wejściem na południe. Rano słońce wejdzie do środka i naturalnie osusza podściółkę.</p>
  </div>
</div>

<div class="tip-box tip-box--warning">
  <div class="tip-box__icon">⚠️</div>
  <div class="tip-box__content">
    <strong class="tip-box__label">Uwaga</strong>
    <p>Nigdy nie buduj kurnika w zagłębieniu terenu. Woda po deszczu musi mieć gdzie spłynąć.</p>
  </div>
</div>

<div class="tip-box tip-box--important">
  <div class="tip-box__icon">📌</div>
  <div class="tip-box__content">
    <strong class="tip-box__label">Ważne</strong>
    <p>Minimalna powierzchnia podłogi to 0,25 m² na kurę w systemie ściółkowym.</p>
  </div>
</div>

<div class="tip-box tip-box--fact">
  <div class="tip-box__icon">🌾</div>
  <div class="tip-box__content">
    <strong class="tip-box__label">Ciekawostka</strong>
    <p>Kury preferują spanie na grzędzie na wysokości 40-60 cm nad podłogą. Wyżej nie oznacza lepiej.</p>
  </div>
</div>
```

```css
.tip-box {
  display:       flex;
  gap:           1rem;
  margin:        2rem 0;
  padding:       1.25rem 1.5rem;
  border-radius: 8px;
  border:        1px solid transparent;
}

.tip-box__icon {
  font-size:   1.5rem;
  flex-shrink: 0;
  margin-top:  0.1em;
}

.tip-box__label {
  display:        block;
  font-family:    var(--font-ui);
  font-size:      var(--text-xs);
  font-weight:    600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  margin-bottom:  0.4rem;
}

.tip-box__content p {
  margin:      0;
  font-size:   0.9375rem;
  line-height: 1.65;
}

.tip-box--tip {
  background:   #F0F7E8;
  border-color: #A8CC7A;
}
.tip-box--tip .tip-box__label { color: var(--color-accent-green); }

.tip-box--warning {
  background:   #FEF3E2;
  border-color: #E8A84A;
}
.tip-box--warning .tip-box__label { color: #B87420; }

.tip-box--important {
  background:   #F5EDE8;
  border-color: #C4722A;
}
.tip-box--important .tip-box__label { color: var(--color-accent-warm); }

.tip-box--fact {
  background:   #F5F0E8;
  border-color: var(--color-border-medium);
}
.tip-box--fact .tip-box__label { color: var(--color-accent-primary); }
```

## 5.5. Lista stylizowana

Listy nie mają domyślnych punktorów. Używamy własnych znaczników.

```css
.chapter-body ul {
  list-style:    none;
  padding:       0;
  margin:        1.5rem 0;
}

.chapter-body ul li {
  position:      relative;
  padding-left:  1.75rem;
  margin-bottom: 0.6rem;
  line-height:   1.7;
}

.chapter-body ul li::before {
  content:     '';
  position:    absolute;
  left:        0;
  top:         0.6em;
  width:       8px;
  height:      8px;
  background:  var(--color-accent-primary);
  border-radius: 50%;
  transform:   translateY(-50%);
}

.chapter-body ol {
  counter-reset: list-counter;
  list-style:    none;
  padding:       0;
  margin:        1.5rem 0;
}

.chapter-body ol li {
  counter-increment: list-counter;
  position:          relative;
  padding-left:      2.5rem;
  margin-bottom:     0.75rem;
  line-height:       1.7;
}

.chapter-body ol li::before {
  content:         counter(list-counter);
  position:        absolute;
  left:            0;
  top:             0;
  width:           1.75rem;
  height:          1.75rem;
  background:      var(--color-accent-primary);
  color:           white;
  font-family:     var(--font-ui);
  font-size:       var(--text-xs);
  font-weight:     600;
  border-radius:   50%;
  display:         flex;
  align-items:     center;
  justify-content: center;
}
```

## 5.6. Tabela

```html
<div class="table-wrapper">
  <table class="data-table">
    <caption>Porównanie popularnych ras nieśnych</caption>
    <thead>
      <tr>
        <th>Rasa</th>
        <th>Jaja rocznie</th>
        <th>Masa ciała (kg)</th>
        <th>Odporność na zimno</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Australorp</td>
        <td>280-320</td>
        <td>2,7-3,0</td>
        <td>Dobra</td>
      </tr>
      <tr>
        <td>Leghorn</td>
        <td>280-300</td>
        <td>2,0-2,5</td>
        <td>Słaba</td>
      </tr>
    </tbody>
  </table>
</div>
```

```css
.table-wrapper {
  overflow-x:    auto;
  margin:        2.5rem 0;
  border-radius: 10px;
  border:        1px solid var(--color-border-light);
  box-shadow:    var(--shadow-soft);
}

.data-table {
  width:           100%;
  border-collapse: collapse;
  font-family:     var(--font-ui);
  font-size:       var(--text-sm);
}

.data-table caption {
  font-family:    var(--font-body);
  font-style:     italic;
  font-size:      var(--text-sm);
  color:          var(--color-text-muted);
  padding:        0.75rem 1rem;
  text-align:     left;
  caption-side:   top;
}

.data-table thead {
  background: var(--color-bg-dark);
  color:      var(--color-text-inverse);
}

.data-table thead th {
  padding:        0.9rem 1.25rem;
  text-align:     left;
  font-weight:    600;
  letter-spacing: 0.04em;
  font-size:      var(--text-xs);
  text-transform: uppercase;
}

.data-table tbody tr {
  border-bottom: 1px solid var(--color-border-light);
  transition:    background 0.15s ease;
}

.data-table tbody tr:last-child {
  border-bottom: none;
}

.data-table tbody tr:hover {
  background: var(--color-bg-secondary);
}

.data-table tbody td {
  padding:     0.85rem 1.25rem;
  color:       var(--color-text-primary);
  line-height: 1.5;
}

.data-table tbody tr:nth-child(even) {
  background: var(--color-bg-primary);
}
```

## 5.7. Separator rozdziałów

Dekoracyjna linia z ornamentem, zamiast zwykłego `<hr>`.

```html
<div class="section-divider">
  <span class="section-divider__ornament">✦</span>
</div>
```

```css
.section-divider {
  display:         flex;
  align-items:     center;
  justify-content: center;
  margin:          3.5rem 0;
  gap:             1rem;
}

.section-divider::before,
.section-divider::after {
  content:    '';
  flex:       1;
  height:     1px;
  background: linear-gradient(
    to right,
    transparent,
    var(--color-border-medium),
    transparent
  );
}

.section-divider__ornament {
  color:          var(--color-accent-primary);
  font-size:      1rem;
  flex-shrink:    0;
}
```

## 5.8. Nawigacja boczna (Sidebar)

```html
<nav class="sidebar" id="sidebar">
  <div class="sidebar__header">
    <div class="sidebar__logo">🐔</div>
    <div class="sidebar__title">Hodowla Kur</div>
    <button class="sidebar__close" id="sidebarClose" aria-label="Zamknij menu">✕</button>
  </div>

  <div class="sidebar__progress">
    <div class="sidebar__progress-label">
      <span>Postęp czytania</span>
      <span id="progressPercent">0%</span>
    </div>
    <div class="sidebar__progress-bar">
      <div class="sidebar__progress-fill" id="progressFill"></div>
    </div>
  </div>

  <ul class="sidebar__nav">
    <li class="sidebar__nav-part">Część I - Podstawy</li>
    <li><a href="#chapter-1" class="sidebar__nav-link">1. Dlaczego warto hodować kury?</a></li>
    <li><a href="#chapter-2" class="sidebar__nav-link">2. Planowanie hodowli</a></li>
    <li class="sidebar__nav-part">Część II - Rasy</li>
    <li><a href="#chapter-3" class="sidebar__nav-link">3. Rasy jajeczne</a></li>
    <!-- ...kolejne rozdziały -->
  </ul>
</nav>
```

```css
.sidebar {
  position:   fixed;
  top:        0;
  left:       0;
  height:     100vh;
  width:      300px;
  background: var(--color-bg-accent);
  color:      var(--color-text-inverse);
  overflow-y: auto;
  z-index:    100;
  transform:  translateX(-100%);
  transition: transform 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  display:    flex;
  flex-direction: column;
}

.sidebar.is-open {
  transform: translateX(0);
  box-shadow: 4px 0 30px rgba(0, 0, 0, 0.25);
}

.sidebar__header {
  display:         flex;
  align-items:     center;
  gap:             0.75rem;
  padding:         1.5rem 1.25rem;
  border-bottom:   1px solid rgba(255,255,255,0.1);
  position:        sticky;
  top:             0;
  background:      var(--color-bg-accent);
  z-index:         1;
}

.sidebar__logo {
  font-size:   1.75rem;
  flex-shrink: 0;
}

.sidebar__title {
  font-family: var(--font-display);
  font-size:   var(--text-base);
  font-weight: 600;
  flex:        1;
}

.sidebar__close {
  background:  none;
  border:      none;
  color:       rgba(255,255,255,0.5);
  cursor:      pointer;
  font-size:   1.1rem;
  padding:     0.25rem;
  line-height: 1;
  transition:  color 0.15s;
}

.sidebar__close:hover {
  color: white;
}

.sidebar__progress {
  padding: 1rem 1.25rem;
  border-bottom: 1px solid rgba(255,255,255,0.1);
}

.sidebar__progress-label {
  display:         flex;
  justify-content: space-between;
  font-family:     var(--font-ui);
  font-size:       var(--text-xs);
  color:           rgba(255,255,255,0.5);
  margin-bottom:   0.5rem;
}

.sidebar__progress-bar {
  height:        4px;
  background:    rgba(255,255,255,0.1);
  border-radius: 2px;
  overflow:      hidden;
}

.sidebar__progress-fill {
  height:        100%;
  background:    var(--color-accent-primary);
  border-radius: 2px;
  transition:    width 0.3s ease;
  width:         0%;
}

.sidebar__nav {
  list-style: none;
  padding:    1rem 0;
  margin:     0;
  flex:       1;
}

.sidebar__nav-part {
  font-family:    var(--font-ui);
  font-size:      var(--text-xs);
  font-weight:    600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color:          var(--color-accent-primary);
  padding:        1rem 1.25rem 0.4rem;
  margin-top:     0.5rem;
}

.sidebar__nav-link {
  display:     block;
  padding:     0.55rem 1.25rem;
  font-family: var(--font-ui);
  font-size:   var(--text-sm);
  color:       rgba(250, 247, 242, 0.65);
  text-decoration: none;
  transition:  all 0.15s;
  border-left: 3px solid transparent;
}

.sidebar__nav-link:hover {
  color:        var(--color-text-inverse);
  background:   rgba(255,255,255,0.06);
}

.sidebar__nav-link.is-active {
  color:        var(--color-text-inverse);
  border-color: var(--color-accent-primary);
  background:   rgba(139, 105, 20, 0.15);
}
```

## 5.9. Przycisk otwierania menu i pasek górny

```html
<div class="topbar">
  <button class="topbar__menu-btn" id="menuBtn" aria-label="Otwórz spis treści">
    <span></span><span></span><span></span>
  </button>
  <div class="topbar__title">Kompleksowy Poradnik Hodowcy Kur</div>
  <div class="topbar__chapter" id="currentChapter">Rozdział 1</div>
</div>
```

```css
.topbar {
  position:        sticky;
  top:             0;
  z-index:         50;
  display:         flex;
  align-items:     center;
  gap:             1rem;
  padding:         0.85rem 1.5rem;
  background:      rgba(250, 247, 242, 0.92);
  backdrop-filter: blur(12px);
  border-bottom:   1px solid var(--color-border-light);
}

.topbar__menu-btn {
  display:        flex;
  flex-direction: column;
  gap:            5px;
  background:     none;
  border:         none;
  cursor:         pointer;
  padding:        4px;
  flex-shrink:    0;
}

.topbar__menu-btn span {
  display:       block;
  width:         22px;
  height:        2px;
  background:    var(--color-text-primary);
  border-radius: 2px;
  transition:    all 0.2s;
}

.topbar__title {
  font-family:     var(--font-display);
  font-size:       var(--text-sm);
  font-weight:     600;
  color:           var(--color-text-secondary);
  flex:            1;
  white-space:     nowrap;
  overflow:        hidden;
  text-overflow:   ellipsis;
}

.topbar__chapter {
  font-family:    var(--font-ui);
  font-size:      var(--text-xs);
  color:          var(--color-text-muted);
  flex-shrink:    0;
}
```

## 5.10. Pasek postępu czytania

```css
.reading-progress {
  position:   fixed;
  top:        0;
  left:       0;
  height:     3px;
  background: var(--color-accent-primary);
  z-index:    200;
  width:      0%;
  transition: width 0.1s linear;
}
```

```javascript
// Pasek postępu - JS
window.addEventListener('scroll', () => {
  const scrollTop    = window.scrollY;
  const docHeight    = document.documentElement.scrollHeight - window.innerHeight;
  const progress     = (scrollTop / docHeight) * 100;
  const bar          = document.getElementById('readingProgress');
  const fill         = document.getElementById('progressFill');
  const percentLabel = document.getElementById('progressPercent');

  bar.style.width  = progress + '%';
  fill.style.width = progress + '%';
  percentLabel.textContent = Math.round(progress) + '%';
});
```

---

# 6. OKŁADKA

```html
<section class="cover-page">
  <div class="cover-page__texture"></div>
  <div class="cover-page__content">
    <div class="cover-page__tag">Kompendium wiedzy hodowcy</div>
    <h1 class="cover-page__title">
      Kompleksowy<br>
      <em>Poradnik</em><br>
      Hodowcy Kur
    </h1>
    <p class="cover-page__subtitle">
      Od pierwszego pisklęcia do pełnej hodowli
    </p>
    <div class="cover-page__divider">
      <span>✦ ✦ ✦</span>
    </div>
    <div class="cover-page__meta">
      <span>50 Rozdziałów</span>
      <span>·</span>
      <span>600+ Stron</span>
      <span>·</span>
      <span>Wydanie 2025</span>
    </div>
  </div>
  <div class="cover-page__footer">
    <div class="cover-page__illustration">🐔</div>
  </div>
</section>
```

```css
.cover-page {
  min-height:      100vh;
  background:      var(--color-bg-dark);
  color:           var(--color-text-inverse);
  display:         flex;
  flex-direction:  column;
  justify-content: center;
  align-items:     center;
  text-align:      center;
  position:        relative;
  overflow:        hidden;
  padding:         4rem 2rem;
}

/* Faktura drewna w tle */
.cover-page__texture {
  position:         absolute;
  inset:            0;
  background-image:
    repeating-linear-gradient(
      88deg,
      transparent 0px,
      transparent 18px,
      rgba(255,255,255,0.012) 18px,
      rgba(255,255,255,0.012) 19px
    ),
    repeating-linear-gradient(
      92deg,
      transparent 0px,
      transparent 35px,
      rgba(255,255,255,0.008) 35px,
      rgba(255,255,255,0.008) 36px
    );
  pointer-events: none;
}

.cover-page__tag {
  font-family:    var(--font-ui);
  font-size:      var(--text-xs);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color:          var(--color-accent-primary);
  margin-bottom:  1.5rem;
}

.cover-page__title {
  font-family: var(--font-display);
  font-size:   clamp(3rem, 8vw, 5.5rem);
  font-weight: 700;
  line-height: 1.05;
  margin:      0 0 1.5rem;
}

.cover-page__title em {
  font-style: italic;
  color:      var(--color-accent-primary);
}

.cover-page__subtitle {
  font-family: var(--font-body);
  font-size:   var(--text-md);
  font-style:  italic;
  color:       rgba(250, 247, 242, 0.6);
  margin:      0 0 2.5rem;
}

.cover-page__divider {
  color:         var(--color-accent-primary);
  font-size:     0.75rem;
  letter-spacing: 0.4em;
  margin-bottom: 2rem;
}

.cover-page__meta {
  display:        flex;
  gap:            1rem;
  align-items:    center;
  font-family:    var(--font-ui);
  font-size:      var(--text-sm);
  color:          rgba(250, 247, 242, 0.4);
}

.cover-page__illustration {
  font-size:  5rem;
  margin-top: 3rem;
  filter:     grayscale(0.3) opacity(0.6);
}
```

---

# 7. SPIS TREŚCI (TOC)

```html
<section class="toc-page content-column">
  <h2 class="toc-page__title">Spis treści</h2>
  <div class="toc-part">
    <h3 class="toc-part__label">Część I - Wprowadzenie i planowanie</h3>
    <ol class="toc-list">
      <li class="toc-list__item">
        <a href="#chapter-1" class="toc-list__link">
          <span class="toc-list__name">Dlaczego warto hodować kury?</span>
          <span class="toc-list__dots"></span>
          <span class="toc-list__page">12</span>
        </a>
      </li>
    </ol>
  </div>
</section>
```

```css
.toc-page {
  padding:    5rem 2rem;
}

.toc-page__title {
  font-family:   var(--font-display);
  font-size:     var(--text-2xl);
  margin-bottom: 3rem;
  color:         var(--color-text-primary);
}

.toc-part {
  margin-bottom: 2.5rem;
}

.toc-part__label {
  font-family:    var(--font-ui);
  font-size:      var(--text-xs);
  font-weight:    600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color:          var(--color-accent-primary);
  margin-bottom:  0.75rem;
  padding-bottom: 0.5rem;
  border-bottom:  1px solid var(--color-border-light);
}

.toc-list {
  list-style: none;
  padding:    0;
  margin:     0;
}

.toc-list__item {
  margin-bottom: 0.1rem;
}

.toc-list__link {
  display:         flex;
  align-items:     baseline;
  gap:             0.5rem;
  padding:         0.45rem 0;
  text-decoration: none;
  color:           var(--color-text-secondary);
  font-family:     var(--font-body);
  font-size:       var(--text-base);
  transition:      color 0.15s;
}

.toc-list__link:hover {
  color: var(--color-accent-primary);
}

.toc-list__name {
  flex-shrink: 0;
}

.toc-list__dots {
  flex:        1;
  border-bottom: 1px dotted var(--color-border-medium);
  margin-bottom: 0.2em;
}

.toc-list__page {
  font-family: var(--font-ui);
  font-size:   var(--text-sm);
  flex-shrink: 0;
  color:       var(--color-text-muted);
}
```

---

# 8. RESPONSYWNOŚĆ

```css
/* Tablet */
@media (max-width: 1024px) {
  .main-content {
    margin-left: 0;
  }
}

/* Mobile */
@media (max-width: 768px) {
  .chapter-header {
    padding: 3rem 0 2.5rem;
  }

  .chapter-header .chapter-title {
    font-size: var(--text-xl);
  }

  .chapter-lead {
    font-size: var(--text-base);
  }

  .content-column {
    padding: 0 1.25rem;
  }

  .chapter-body {
    padding-top:    2rem;
    padding-bottom: 3rem;
  }

  .tip-box {
    flex-direction: column;
    gap:            0.5rem;
  }

  .pull-quote {
    padding: 1.25rem 1.25rem 1.25rem 2rem;
  }

  .pull-quote p {
    font-size: var(--text-base);
  }

  .cover-page__meta {
    flex-wrap: wrap;
    justify-content: center;
  }
}
```

---

# 9. ANIMACJE I PRZEJŚCIA

Wszystkie animacje mają być subtelne. Ebook to narzędzie do czytania, nie pokaz efektów.

```css
/* Wejście rozdziału przy scrollowaniu */
.chapter {
  opacity:   0;
  transform: translateY(20px);
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.chapter.is-visible {
  opacity:   1;
  transform: translateY(0);
}

/* Hover na linkach i elementach interaktywnych */
a {
  color:      var(--color-accent-warm);
  transition: color 0.15s ease;
}

a:hover {
  color: var(--color-accent-primary);
}

/* Smooth scroll */
html {
  scroll-behavior: smooth;
}

/* Szanujemy ustawienia systemu */
@media (prefers-reduced-motion: reduce) {
  * {
    animation:  none !important;
    transition: none !important;
  }
  html {
    scroll-behavior: auto;
  }
}
```

```javascript
// Intersection Observer dla animacji rozdziałów
const chapters = document.querySelectorAll('.chapter');
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('is-visible');
    }
  });
}, { threshold: 0.05 });

chapters.forEach(ch => observer.observe(ch));

// Aktywny link w sidebarze
const navLinks  = document.querySelectorAll('.sidebar__nav-link');
const headings  = document.querySelectorAll('.chapter');
const headingObs = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      navLinks.forEach(link => link.classList.remove('is-active'));
      const active = document.querySelector(
        `.sidebar__nav-link[href="#${entry.target.id}"]`
      );
      if (active) active.classList.add('is-active');
      document.getElementById('currentChapter').textContent =
        entry.target.querySelector('.chapter-number')?.textContent || '';
    }
  });
}, { threshold: 0.3 });

headings.forEach(h => headingObs.observe(h));

// Toggle sidebar
document.getElementById('menuBtn').addEventListener('click', () => {
  document.getElementById('sidebar').classList.toggle('is-open');
  document.getElementById('sidebarOverlay').classList.toggle('is-visible');
});

document.getElementById('sidebarClose').addEventListener('click', () => {
  document.getElementById('sidebar').classList.remove('is-open');
  document.getElementById('sidebarOverlay').classList.remove('is-visible');
});

document.getElementById('sidebarOverlay').addEventListener('click', () => {
  document.getElementById('sidebar').classList.remove('is-open');
  document.getElementById('sidebarOverlay').classList.remove('is-visible');
});
```

```css
.sidebar-overlay {
  display:    none;
  position:   fixed;
  inset:      0;
  background: rgba(0, 0, 0, 0.4);
  z-index:    90;
}

.sidebar-overlay.is-visible {
  display: block;
}
```

---

# 10. PRINT STYLES

Ebook powinien wyglądać dobrze po wydrukowaniu.

```css
@media print {
  .sidebar,
  .topbar,
  .reading-progress,
  .sidebar-overlay {
    display: none !important;
  }

  body {
    background: white;
    font-size:  12pt;
  }

  .chapter-header {
    background:       var(--color-bg-dark) !important;
    -webkit-print-color-adjust: exact;
    print-color-adjust: exact;
  }

  .chapter {
    page-break-before: always;
    opacity:           1 !important;
    transform:         none !important;
  }

  a {
    color:           inherit;
    text-decoration: none;
  }

  .tip-box {
    border:     1px solid #ccc;
    background: #f9f9f9 !important;
    -webkit-print-color-adjust: exact;
    print-color-adjust: exact;
  }
}
```

---

# 11. ZMIENNE - KOMPLETNA LISTA REFERENCYJNA

```css
:root {
  /* Kolory tła */
  --color-bg-primary:     #FAF7F2;
  --color-bg-secondary:   #F2EDE4;
  --color-bg-card:        #FFFFFF;
  --color-bg-dark:        #2C2416;
  --color-bg-accent:      #4A3728;

  /* Kolory tekstu */
  --color-text-primary:   #2C2416;
  --color-text-secondary: #6B5744;
  --color-text-muted:     #9E8B7A;
  --color-text-inverse:   #FAF7F2;

  /* Akcenty */
  --color-accent-primary: #8B6914;
  --color-accent-warm:    #C4722A;
  --color-accent-green:   #5C7A3E;
  --color-accent-red:     #8B3A2A;

  /* Obramowania */
  --color-border-light:   #E0D5C5;
  --color-border-medium:  #C5B49A;
  --color-border-dark:    #8B7355;

  /* Cienie */
  --shadow-soft:          0 2px 12px rgba(44, 36, 22, 0.08);
  --shadow-card:          0 4px 24px rgba(44, 36, 22, 0.10);
  --shadow-hover:         0 8px 32px rgba(44, 36, 22, 0.15);

  /* Fonty */
  --font-display:         'Playfair Display', Georgia, serif;
  --font-body:            'Lora', 'Times New Roman', serif;
  --font-ui:              'Nunito Sans', sans-serif;

  /* Skala typograficzna */
  --text-xs:              0.75rem;
  --text-sm:              0.875rem;
  --text-base:            1.0625rem;
  --text-md:              1.25rem;
  --text-lg:              1.5rem;
  --text-xl:              2rem;
  --text-2xl:             2.75rem;
  --text-3xl:             4rem;

  /* Zaokrąglenia */
  --radius-sm:            4px;
  --radius-md:            8px;
  --radius-lg:            16px;

  /* Przejścia */
  --transition-fast:      0.15s ease;
  --transition-base:      0.25s ease;
  --transition-slow:      0.4s ease;

  /* Spacje */
  --space-section:        5rem;
  --space-block:          3rem;
  --space-element:        1.5rem;
}
```

---

*Dokumentacja wersja 1.0 - stosuj ją jako jedyne źródło prawdy dla wszystkich decyzji wizualnych ebooka.*
