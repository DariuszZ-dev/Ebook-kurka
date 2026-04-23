# 📋 Plan budowy HTML Ebooka - "Kompleksowy Poradnik Hodowcy Kur"
## Etapy realizacji krok po kroku

---

> Każdy etap można oznaczyć jako wykonany `[x]` po jego zakończeniu.
> Kolejność etapów jest ważna - każdy następny bazuje na poprzednim.

---

## ETAP 1 – Szkielet HTML i fundament CSS
**Cel:** Stworzyć kompletny plik HTML z podstawową strukturą dokumentu i wszystkimi zmiennymi CSS.

- [x] 1.1. Utworzyć plik `index.html` z poprawną deklaracją `<!DOCTYPE html>`, `<html lang="pl">`, `<head>`, `<body>`
- [x] 1.2. Dodać meta tagi (`charset`, `viewport`, `title`)
- [x] 1.3. Zaimportować fonty Google: Playfair Display, Lora, Nunito Sans
- [x] 1.4. Zdefiniować w `<style>` (lub osobnym `style.css`) wszystkie zmienne CSS w `:root`:
  - [x] Paleta kolorów tła (5 zmiennych)
  - [x] Paleta kolorów tekstu (4 zmienne)
  - [x] Paleta akcentów (4 zmienne)
  - [x] Obramowania (3 zmienne)
  - [x] Cienie (3 zmienne)
  - [x] Fonty (3 zmienne)
  - [x] Skala typograficzna (8 zmiennych)
  - [x] Zaokrąglenia, przejścia, spacje
- [x] 1.5. Dodać style bazowe `body` (font-family, font-size, line-height, kolory, wygładzanie)
- [x] 1.6. Dodać style nagłówków `h1-h4` (font-family, line-height, font-weight)
- [x] 1.7. Zdefiniować klasy kontenerów: `.ebook-wrapper`, `.content-column`, `.content-column--wide`, `.content-column--full`

**Weryfikacja:** Plik otwiera się w przeglądarce, tło ma kolor `#FAF7F2`, fonty ładują się poprawnie.

---

## ETAP 2 – Okładka (Cover Page)
**Cel:** Zbudować sekcję okładki zajmującą pełny ekran.

- [x] 2.1. Dodać `<section class="cover-page">` z teksturą tła `.cover-page__texture`
- [x] 2.2. Dodać tag kompendium, tytuł z elementem `<em>`, podtytuł, separator ozdobny `✦ ✦ ✦`
- [x] 2.3. Dodać metadane (50 Rozdziałów · 600+ Stron · Wydanie 2026)
- [x] 2.4. Dodać ilustrację (emoji 🐔)
- [x] 2.5. Napisać pełne style CSS dla okładki (pełnoekranowa, flex, ciemne tło, faktura drewna)

**Weryfikacja:** Okładka zajmuje cały viewport, tytuł jest wycentrowany, tekstura tła widoczna, kolory zgodne z dokumentacją.

---

## ETAP 3 – Pasek górny (Topbar) i pasek postępu czytania
**Cel:** Zbudować sticky topbar z przyciskiem menu i paskiem postępu.

- [x] 3.1. Dodać `<div class="topbar">` z przyciskiem hamburger, tytułem książki i wskaźnikiem bieżącego rozdziału
- [x] 3.2. Dodać `<div class="reading-progress">` dla paska postępu
- [x] 3.3. Napisać style CSS (sticky, backdrop-filter blur, przezroczystość)
- [x] 3.4. Napisać JavaScript - aktualizacja paska postępu przy scrollowaniu

**Weryfikacja:** Pasek górny jest przyklejony do góry, pasek postępu rośnie podczas przewijania strony.

---

## ETAP 4 – Nawigacja boczna (Sidebar)
**Cel:** Zbudować panel boczny z pełnym spisem treści.

- [x] 4.1. Dodać `<nav class="sidebar">` z nagłówkiem (logo 🐔, tytuł, przycisk zamknięcia)
- [x] 4.2. Dodać pasek postępu czytania w sidebarze
- [x] 4.3. Dodać `<ul class="sidebar__nav">` z podziałem na Części (I-XV) i linkami do rozdziałów (1-49)
- [x] 4.4. Dodać `<div class="sidebar-overlay">` 
- [x] 4.5. Napisać style CSS (fixed, transform, animacja wjazdu, style linków, stan aktywny)
- [x] 4.6. Napisać JavaScript - otwieranie/zamykanie sidebara, zamykanie przez overlay

**Weryfikacja:** Sidebar wysuwa się od lewej po kliknięciu hamburgera, zamyka się po kliknięciu ✕ lub overlay.

---

## ETAP 5 – Strona tytułowa / Wstęp (Front Matter)
**Cel:** Zaimplementować stronę wstępną przed rozdziałami.

- [x] 5.1. Dodać `<section class="front-matter">` z krótkim wstępem do ebooka
- [x] 5.2. Napisać treść wstępną (kilka akapitów w stylu opisanym w `styl_pisania_ebooka.md`)
- [x] 5.3. Ostylować sekcję (kolumna 720px, marginesy, typografia)

**Weryfikacja:** Wstęp wyświetla się po okładce, tekst jest czytelny, w kolumnie 720px.

---

## ETAP 6 – Spis treści (TOC Page)
**Cel:** Zbudować interaktywny spis treści z numerami stron i nawigacją.

- [x] 6.1. Dodać `<section class="toc-page">` z tytułem "Spis treści"
- [x] 6.2. Dodać bloki `.toc-part` dla każdej Części (I-XV)
- [x] 6.3. W każdym bloku dodać elementy `.toc-list__item` z nazwami rozdziałów, kropkami i numerami stron
- [x] 6.4. Dodać linki `<a href="#chapter-X">` do każdego rozdziału
- [x] 6.5. Napisać style CSS (etykiety części, linia kropek, numery stron, hover)

**Weryfikacja:** Spis treści wyświetla wszystkie 49 rozdziałów z podziałem na części, kliknięcie przenosi do rozdziału.

---

## ETAP 7 – Komponenty wielokrotnego użytku
**Cel:** Zaimplementować i przetestować wszystkie komponenty wizualne, zanim zostaną użyte w rozdziałach.

- [x] 7.1. **Nagłówek rozdziału** `.chapter-header` - ciemne tło, wzór siatki, numer, tytuł, lead, meta
- [x] 7.2. **Akapit i tekst główny** - drop cap (inicjał), max-width 68ch, powiększony akapit po nagłówku
- [x] 7.3. **Cytat wyróżniony** `.pull-quote` - lewy border złoty, cudzysłów dekoracyjny, kursywa
- [x] 7.4. **Ramki z poradami** `.tip-box` - 4 warianty:
  - [x] 7.4.1. `tip-box--tip` (💡 Wskazówka - zielona)
  - [x] 7.4.2. `tip-box--warning` (⚠️ Uwaga - pomarańczowa)
  - [x] 7.4.3. `tip-box--important` (📌 Ważne - terakotowa)
  - [x] 7.4.4. `tip-box--fact` (🌾 Ciekawostka - beżowa)
- [x] 7.5. **Listy stylizowane** - `ul` z kółkami w kolorze złota, `ol` z numerami w kółkach
- [x] 7.6. **Tabela** `.data-table` - ciemny nagłówek, zebra stripes, hover, caption
- [x] 7.7. **Separator** `.section-divider` - linia z ornamentem ✦

**Weryfikacja:** Każdy komponent wyświetla się poprawnie na stronie testowej, kolory i fonty są zgodne z dokumentacją.

---

## ETAP 8 – Rozdział 1: "Dlaczego warto hodować kury?"
**Cel:** Napisać i zaimplementować pierwszy pełny rozdział jako wzorzec.

- [x] 8.1. Dodać `<article class="chapter" id="chapter-1">` z nagłówkiem rozdziału
- [x] 8.2. Napisać treść podrozdziałów 1.1-1.7 zgodnie ze stylem z `styl_pisania_ebooka.md`:
  - [x] 1.1. Historia domestykacji kury domowej
  - [x] 1.2. Korzyści z hodowli przydomowej
  - [x] 1.3. Hodowla jako hobby vs. zarobkowa
  - [x] 1.4. Wpływ na środowisko i zrównoważone rolnictwo
  - [x] 1.5. Psychologiczne aspekty
  - [x] 1.6. Aspekty prawne w Polsce
  - [x] 1.7. Hodowla w mieście vs. na wsi
- [x] 8.3. Użyć w treści komponentów: pull-quote, tip-box (min. 2 warianty), lista, separator
- [x] 8.4. Sprawdzić checklist edytora z `styl_pisania_ebooka.md`

**Weryfikacja:** Rozdział 1 wyświetla się poprawnie, wszystkie komponenty działają, treść spełnia kryteria stylistyczne.

---

## ETAP 9 – Rozdział 2: "Planowanie hodowli"
**Cel:** Napisać i zaimplementować Rozdział 2.

- [x] 9.1. Dodać `<article class="chapter" id="chapter-2">` z nagłówkiem
- [x] 9.2. Napisać treść podrozdziałów 2.1-2.8
- [x] 9.3. Użyć tabeli (np. porównanie budżetów), checklisty startowej, tip-boxów
- [x] 9.4. Sprawdzić checklist edytora

---

## ETAP 10 – Rozdziały 3-6 (CZĘŚĆ II – Rasy i genetyka)
**Cel:** Napisać i zaimplementować rozdziały o rasach i genetyce.

- [x] 10.1. Rozdział 3: Rasy jajeczne (3.1-3.9) - z tabelą porównawczą ras
- [x] 10.2. Rozdział 4: Rasy mięsne (4.1-4.7) - z zestawieniem czasu odchowu
- [x] 10.3. Rozdział 5: Rasy ogólnoużytkowe i ozdobne (5.1-5.9)
- [x] 10.4. Rozdział 6: Podstawy genetyki drobiu (6.1-6.10)

---

## ETAP 11 – Rozdziały 7-9 (CZĘŚĆ III – Infrastruktura)
**Cel:** Napisać i zaimplementować rozdziały o infrastrukturze.

- [x] 11.1. Rozdział 7: Projektowanie i budowa kurnika (7.1-7.12)
- [x] 11.2. Rozdział 8: Wyposażenie kurnika (8.1-8.10) - z podrozdziałami zagnieżdżonymi
- [x] 11.3. Rozdział 9: Wybieg i pastewnik (9.1-9.8)

---

## ETAP 12 – Rozdziały 10-13 (CZĘŚĆ IV – Żywienie)
**Cel:** Napisać i zaimplementować rozdziały o żywieniu.

- [x] 12.1. Rozdział 10: Podstawy żywienia (10.1-10.7)
- [x] 12.2. Rozdział 11: Rodzaje pasz (11.1-11.12)
- [x] 12.3. Rozdział 12: Naturalne żywienie (12.1-12.10) - z zagnieżdżonymi podrozdziałami
- [x] 12.4. Rozdział 13: Bilansowanie diety (13.1-13.6) - z recepturami

---

## ETAP 13 – Rozdziały 14-16 (CZĘŚĆ V – Nieśność i produkcja jaj)

- [x] 13.1. Rozdział 14: Fizjologia nieśności (14.1-14.8)
- [x] 13.2. Rozdział 15: Optymalizacja produkcji jaj (15.1-15.7)
- [x] 13.3. Rozdział 16: Zbieranie i przechowywanie jaj (16.1-16.10)

---

## ETAP 14 – Rozdziały 17-19 (CZĘŚĆ VI – Rozmnażanie i wylęganie)

- [x] 14.1. Rozdział 17: Rozmnażanie naturalne (17.1-17.7)
- [x] 14.2. Rozdział 18: Kwoczenie (18.1-18.9)
- [x] 14.3. Rozdział 19: Inkubacja sztuczna (19.1-19.14)

---

## ETAP 15 – Rozdziały 20-22 (CZĘŚĆ VII – Odchów piskląt)

- [x] 15.1. Rozdział 20: Pierwsze dni pisklęcia (20.1-20.7)
- [x] 15.2. Rozdział 21: Odchów do 8 tygodnia (21.1-21.8) - z podrozdziałami zagnieżdżonymi
- [x] 15.3. Rozdział 22: Młode kury 8-18 tydzień (22.1-22.6)

---

## ETAP 16 – Rozdziały 23-30 (CZĘŚĆ VIII – Zdrowie i weterynaria)
**Uwaga:** Najdłuższa część - 8 rozdziałów, wiele zagnieżdżonych podrozdziałów.

- [x] 16.1. Rozdział 23: Podstawy zdrowia (23.1-23.6)
- [x] 16.2. Rozdział 24: Choroby wirusowe (24.1-24.9) - rozbudowane podrozdziały
- [x] 16.3. Rozdział 25: Choroby bakteryjne (25.1-25.9)
- [x] 16.4. Rozdział 26: Choroby pasożytnicze (26.1-26.3) - głęboko zagnieżdżone
- [x] 16.5. Rozdział 27: Choroby niedoborowe (27.1-27.9)
- [x] 16.6. Rozdział 28: Problemy behawioralne (28.1-28.6)
- [x] 16.7. Rozdział 29: Apteczka i pierwsza pomoc (29.1-29.10)
- [x] 16.8. Rozdział 30: Szczepienia i profilaktyka (30.1-30.8)

---

## ETAP 17 – Rozdziały 31-33 (CZĘŚĆ IX – Zarządzanie kurnikiem)

- [x] 17.1. Rozdział 31: Higiena i biosekuryta (31.1-31.8)
- [x] 17.2. Rozdział 32: Zarządzanie odchodami (32.1-32.8)
- [x] 17.3. Rozdział 33: Sezonowe zarządzanie (33.1-33.4) - z podrozdziałami sezonowymi

---

## ETAP 18 – Rozdziały 34-36 (CZĘŚĆ X – Ekonomika)

- [x] 18.1. Rozdział 34: Rachunkowość (34.1-34.7)
- [x] 18.2. Rozdział 35: Sprzedaż produktów (35.1-35.8)
- [x] 18.3. Rozdział 36: Skalowanie hodowli (36.1-36.6)

---

## ETAP 19 – Rozdziały 37-39 (CZĘŚĆ XI – Hodowla ekologiczna)

- [x] 19.1. Rozdział 37: Hodowla ekologiczna (37.1-37.5)
- [x] 19.2. Rozdział 38: Permakultura i kury (38.1-38.6)
- [x] 19.3. Rozdział 39: Alternatywne systemy utrzymania (39.1-39.7)

---

## ETAP 20 – Rozdziały 40-42 (CZĘŚĆ XII – Hodowla wystawowa)

- [x] 20.1. Rozdział 40: Wystawy drobiu (40.1-40.5)
- [x] 20.2. Rozdział 41: Przygotowanie kur do wystawy (41.1-41.7)
- [x] 20.3. Rozdział 42: Sędziowanie i ocenianie (42.1-42.5)

---

## ETAP 21 – Rozdziały 43-46 (CZĘŚĆ XIII – Zaawansowane techniki)

- [x] 21.1. Rozdział 43: Zaawansowana selekcja (43.1-43.6)
- [x] 21.2. Rozdział 44: Zaawansowana reprodukcja (44.1-44.4) - z podrozdziałami
- [x] 21.3. Rozdział 45: Żywienie precyzyjne (45.1-45.8)
- [x] 21.4. Rozdział 46: Diagnostyka laboratoryjna (46.1-46.7)

---

## ETAP 22 – Rozdziały 47-48 (CZĘŚĆ XIV – Kontekst globalny)

- [ ] 22.1. Rozdział 47: Światowa produkcja drobiu (47.1-47.5)
- [ ] 22.2. Rozdział 48: Zmiany klimatyczne a hodowla (48.1-48.4)

---

## ETAP 23 – Rozdział 49 (CZĘŚĆ XV – Zasoby) + Załączniki

- [ ] 23.1. Rozdział 49: Nauka i doskonalenie się (49.1-49.3)
- [ ] 23.2. Załącznik A: Tabele i normy (A.1-A.7)
- [ ] 23.3. Załącznik B: Wzory dokumentów (B.1-B.7)
- [ ] 23.4. Załącznik C: Słownik pojęć (C.1-C.2)
- [ ] 23.5. Załącznik D: Przepisy prawne (D.1-D.4)
- [ ] 23.6. Indeks rzeczowy
- [ ] 23.7. Sekcja "O Autorze"

---

## ETAP 24 – Stopka ebooka (Footer)

- [ ] 24.1. Dodać `<footer class="ebook-footer">` z informacjami o prawach autorskich
- [ ] 24.2. Dodać informacje o wersji i formatach
- [ ] 24.3. Ostylować stopkę

---

## ETAP 25 – JavaScript: Interaktywność
**Cel:** Dodać pełną interaktywność ebooka.

- [ ] 25.1. IntersectionObserver - animacje wjazdu rozdziałów (`.is-visible`)
- [ ] 25.2. IntersectionObserver - aktywny link w sidebarze (`.is-active`)
- [ ] 25.3. Aktualizacja nazwy rozdziału w topbarze przy scrollowaniu
- [ ] 25.4. Toggle sidebar - otwieranie (hamburger), zamykanie (✕), zamykanie (overlay)
- [ ] 25.5. Pasek postępu czytania - aktualizacja przy scrollowaniu
- [ ] 25.6. Smooth scroll po kliknięciu linków w TOC i sidebarze

**Weryfikacja:** Wszystkie elementy interaktywne działają płynnie, sidebar otwiera/zamyka się, pasek postępu rośnie.

---

## ETAP 26 – Responsywność (RWD)
**Cel:** Zapewnić poprawne wyświetlanie na wszystkich urządzeniach.

- [ ] 26.1. Media queries dla tabletu (`max-width: 1024px`)
- [ ] 26.2. Media queries dla mobile (`max-width: 768px`):
  - [ ] Zmniejszone paddingi nagłówków rozdziałów
  - [ ] Mniejsze tytuły rozdziałów
  - [ ] Tip-boxy w kolumnie (flex-direction: column)
  - [ ] Mniejsze pull-quote
  - [ ] Cover meta wrap
- [ ] 26.3. Testowanie na różnych szerokościach ekranu

**Weryfikacja:** Ebook wygląda dobrze na desktop (1920px), tablet (768px) i mobile (375px).

---

## ETAP 27 – Animacje i przejścia
**Cel:** Dodać subtelne animacje.

- [ ] 27.1. Animacja wejścia rozdziałów (opacity + translateY)
- [ ] 27.2. Hover na linkach (zmiana koloru)
- [ ] 27.3. Animacja wjazdu sidebara (transform + cubic-bezier)
- [ ] 27.4. Smooth scroll (`scroll-behavior: smooth`)
- [ ] 27.5. `@media (prefers-reduced-motion: reduce)` - wyłączenie animacji dla użytkowników z taką preferencją

**Weryfikacja:** Animacje są subtelne i płynne, nie przeszkadzają w czytaniu.

---

## ETAP 28 – Style druku (Print Styles)
**Cel:** Zapewnić poprawne drukowanie/eksport do PDF.

- [ ] 28.1. Ukrycie sidebara, topbara, paska postępu, overlay
- [ ] 28.2. Białe tło, rozmiar czcionki 12pt
- [ ] 28.3. Page-break-before dla rozdziałów
- [ ] 28.4. Resetowanie opacity i transform
- [ ] 28.5. Uproszczenie linków i tip-boxów

**Weryfikacja:** Podgląd wydruku w przeglądarce (Ctrl+P) wygląda czytelnie i profesjonalnie.

---

## ETAP 29 – Końcowy przegląd i polerowanie
**Cel:** Ostateczna kontrola jakości.

- [ ] 29.1. Sprawdzić spójność kolorów ze zmiennymi CSS (brak hardkodów)
- [ ] 29.2. Sprawdzić poprawność wszystkich linków wewnętrznych (nawigacja)
- [ ] 29.3. Sprawdzić treść pod kątem checklisty edytora (`styl_pisania_ebooka.md`)
- [ ] 29.4. Walidacja HTML (brak zduplikowanych ID, poprawna semantyka)
- [ ] 29.5. Test wydajności przy dużym dokumencie (płynność scrollowania)
- [ ] 29.6. Sprawdzić dostępność (aria-labels, kontrast, focusowalność)
- [ ] 29.7. Optymalizacja rozmiaru pliku

---

## Podsumowanie

| Metryka | Wartość |
|---------|---------|
| **Łączna liczba etapów** | 29 |
| **Rozdziały treści** | 49 + Załączniki A-D |
| **Części tematyczne** | XV (15) |
| **Komponenty wizualne** | 7 (nagłówek, akapit, cytat, tip-box, lista, tabela, separator) |
| **Warianty tip-box** | 4 (wskazówka, uwaga, ważne, ciekawostka) |

---

*Plan na podstawie dokumentacji: `dokumentacja_html_ebook.md`, `hodowla_kur_ebook.md`, `styl_pisania_ebooka.md`*
