# Bē Convention 2026 Katowice — pełna struktura strony (brief dla AI)

Dokument opisuje istniejącą stronę WWW (statyczny HTML) zbierającą nagrania z konwencji
doTERRA Bē Convention 2026 w Katowicach. Cel: przekazać innemu AI pełną treść + strukturę,
żeby mógł ją przeprojektować / zbudować nowy mockup.

**Paleta:** akcent zielony `#0d674a` (ciemny `#094d36`, tło akcentu `#e6f0ec`), tło strony `#fafaf8`,
przyciski YouTube czerwone `#cc0000`. Font systemowy (-apple-system / system-ui). Język interfejsu: PL.

Strona składa się z **1 strony-hub** (`index.html`) + **4 podstron sesji** o wspólnym szablonie.

---

## CZĘŚĆ A — Strona-hub (`index.html`)

Typ: landing / hub zbierający wszystkie sesje.

### Header
- **Tag (pill badge):** doTERRA Bē Convention 2026
- **Tytuł (H1):** Katowice · nagrania konwencji
- **Podtytuł:** Spodek Arena · maj 2026 · EN · wszystkie sesje w jednym miejscu
- **Przycisk CTA (czerwony, YouTube):** ▶ Cała konwencja (playlista)
  → https://www.youtube.com/playlist?list=PL2CEwcCp6FQbauNNi_bFPFyt7OssgpaYN

### Card Grid (4 karty, 2 kolumny / 1 na mobile)
Każda karta = jedna sesja. Cała karta klikalna → podstrona. Zawiera: number badge, tytuł (H2),
linię daty/godziny/liczby wystąpień, listę prelegentów, link „Wejdź →" + osobny link „▶ playlista".

| # | Tytuł karty | Data / godziny | Podstrona | Playlista YT |
|---|---|---|---|---|
| 1 | Empowerment Day · Sesja 1 | 28 maja 2026 · 10:00–12:45 · 5 wystąpień | `sesja1.html` | …list=PL2CEwcCp6FQa5JQ8RpkCus-w7HqSP---m |
| 2 | Empowerment Day · Sesja 2 | 28 maja 2026 · 14:45–17:00 · 7 wystąpień | `Sesja 2/index.html` | …list=PL2CEwcCp6FQaokWGX162KjEXaRC4F9lNl |
| 3 | General Session · piątek | 29 maja 2026 · 09:30–12:30 · 10 wystąpień | `General Session/index.html` | …list=PL2CEwcCp6FQaN75P3ZBR6HX7MzjS-rddp |
| 4 | General Session · sobota | 30 maja 2026 · poranek + GS · 10 wystąpień | `Sobota/index.html` | …list=PL2CEwcCp6FQaQ6bsg1R1MR-c6VzuUN8nx |

**Listy prelegentów (tekst pod tytułem karty):**
- Karta 1: Michele Farace, Dani Lauer, Melina Ilia-Philmon, Panel (Oliver Zabania), Tammy Marti.
- Karta 2: Eniko Gecsenyi, Helena Olearska, Kristin Schindhelm, Russell Buttars, Patrycja Dębska, Panel (Mika Paciorek + Nowosielskie), Jessica Moultrie.
- Karta 3: David Stirling, Mihaela Oprea, Michael Schluchter, Russell Osguthorpe, Scott Johnson (RevitaZen + OnGuard), Abby Stopher, Olga Mazur, Alexandra Nitsche, Angela Kersten.
- Karta 4: Dr Mariza Snyder (poranek), Mark Wolfert, Russell Osguthorpe, Anastassia Lempert, Emilie Bell, Murray Smith, Elena Doandesi, Ionut Nitulescu, Daniela Huelsen, David Stirling (zamknięcie).

### Footnote
Filmy na YouTube jako unlisted (widoczne dla osób z linkiem). Playlista „Cała konwencja"
zbiera wszystkie nagrania w kolejności.

### Hierarchia
```
Page (Hub / Landing)
├── Header
│   ├── Eyebrow tag
│   ├── Page title (H1)
│   ├── Subtitle (meta)
│   └── Primary CTA button → YouTube playlist (cała konwencja)
├── Card Grid (4 × Session Card, 2-column)
│   └── Session Card
│       ├── Number badge
│       ├── Card title (H2)
│       ├── Date/Time line
│       ├── Speaker list
│       └── Card footer (Enter link → podstrona, Playlist link → YouTube)
└── Footnote
```

---

## CZĘŚĆ B — Szablon podstrony sesji (wspólny dla 4 stron)

Typ: strona szczegółowa jednej sesji. Lista wystąpień + nawigacja + sekcja merytoryczna.

### Komponenty (od góry)
1. **Header sesji** — tag (pill), tytuł (H1), meta (miejsce · data · liczba wystąpień · czas · język),
   pasek 3 przycisków nawigacji:
   - „← Wszystkie sesje" (outline → hub `index.html`)
   - „▶ Playlista …" (czerwony → playlista YT sesji)
   - „Sesja N →" (zielony → następna podstrona)
2. **Intro box** (zielone tło) — krótki opis bloku, znacznik „Jesteś tutaj".
3. **Lista wystąpień** (H2 „Wystąpienia") — seria kart wystąpienia (Talk Card), każda:
   - Tytuł (H3): numer + nazwisko + temat
   - Meta: „Sesja N [nr] · czas trwania · język" (na stronach 3–4 dochodzi stanowisko/ranga)
   - 3 przyciski: „▶ Film" (YouTube), „Notatki" (lokalny `notatki.html`), „Transkrypcja" (lokalny `transkrypcja.html`)
4. **Sekcja merytoryczna „O sesji — czerwona nić"** (po poziomej linii):
   - linia metadanych (lokalizacja, data, liczba speakerów, czas, język, link playlisty)
   - „O sesji" — kilka akapitów
   - „Czerwona nić" — N wspólnych tez (H3 + cytaty per speaker)
   - „Spis wystąpień" — lista linków + jednozdaniowe opisy
   - „Kluczowe call-to-action" — lista numerowana
   - „Cytaty" — blockquote, po jednym z każdego wystąpienia
   - stopka techniczna (materiały lokalne, Reflect, cięcia) — robocza, do pominięcia w mockupie

### Hierarchia
```
Session Page
├── Session Header (tag, H1, meta, nav bar: Hub / Playlist / Next)
├── Intro box
├── Talk List (H2)
│   └── Talk Card ×N (H3 title, meta, buttons: Film / Notatki / Transkrypcja)
└── "Red thread" content section (metadata, O sesji, tezy, spis, CTA, cytaty, stopka)
```

---

## CZĘŚĆ C — Pełna lista wystąpień (wszystkie 4 strony)

### Strona 1 — Empowerment Day · Sesja 1 (28.05, 10:00–12:45, 5 wystąpień)
1. Michele Farace nie pracuj na cudze marzenie — [01] · 22:08 · EN
2. Dani Lauer stop overthinking — [02] · 18:13 · EN
3. Melina Ilia-Philmon LRP i sciezka do 500 — [03] · 17:56 · EN
4. Panel rekrutacja przez polaczenie (Oliver Zabania + 4 liderki) — [04] · 27:30 · EN
5. Tammy Marti stop chasing create spaces — [05] · 24:30 · EN

### Strona 2 — Empowerment Day · Sesja 2 (28.05, 14:45–17:00, 7 wystąpień)
1. Eniko Gecsenyi typy osobowosci — [01] · 19:30 · EN
2. Helena Olearska personal brand — [02] · 15:42 · EN
3. Kristin Schindhelm poza plateau — [03] · 22:47 · EN
4. Russell Buttars leadership growth — [04] · 10:59 · EN
5. Patrycja Debska presence identity — [05] · 21:10 · EN
6. Panel Mika Paciorek + Nowosielskie duplikacja — [06] · 14:40 · EN
7. Jessica Moultrie silne systemy — [07] · 14:39 · EN

### Strona 3 — General Session · piątek (29.05, 09:30–12:30, 10 wystąpień)
1. David Stirling — otwarcie i legacy — [01] · Founding Executive & CEO · 29:29 · EN
2. Mihaela Oprea — otwarcie + zbiórka Feminoteca — [02] · MD of Leadership Experience · 10:52 · EN
3. Michael Schluchter — corporate i liderzy — [03] · MD of Business Operations · 10:50 · EN
4. Dr Russell Osguthorpe — wprowadzenie medyczne — [04] · Chief Medical Officer · 05:45 · EN
5. Dr Scott Johnson — RevitaZen — detoks — [05] · Director, Research Substantiation · 13:07 · EN
6. Abby Stopher — olej rycynowy (castor oil) — [06] · Product Marketing Manager · 08:23 · EN
7. Olga Mazur — doTERRA Fiber — [07] · Senior Product Manager EMEA · 14:49 · EN
8. Alexandra Nitsche — błonnik i trawienie — [08] · MD, Representative of SMEC Europe · 27:21 · EN
9. Dr Scott Johnson — OnGuard + Echinacea — [09] · Director, Research Substantiation · 18:43 · EN
10. Angela Kersten — sprzedaż Convention Kit — [10] · Presidential Diamond, Germany Founder · 33:58 · EN

### Strona 4 — General Session · sobota (30.05, poranek + GS, 10 wystąpień)
1. Dr Mariza Snyder — poranek: hormony i energia kobiet — [01] · Gość, zdrowie kobiet · 50:40 · EN
2. Mark Wolfert Jr. — duma i powołanie — [02] · Vice President, Europe · 11:03 · EN
3. Dr Russell Osguthorpe — jakość vs konkurencja + dowody kliniczne — [03] · Chief Medical Officer · 28:07 · EN
4. Anastassia Lempert — od IT do transformacji — [04] · Diamond · 16:32 · EN
5. Emilie Bell — Co-Impact Sourcing i Healing Hands — [05] · Director of Strategic Sourcing · 23:24 · EN
6. Murray Smith — ludzie w centrum (Lesbos) — [06] · President · 24:47 · EN
7. Elena Doandesi — serce i środki, bądź obecny — [07] · Blue Diamond, Romania & Moldova · 17:03 · EN
8. Ionut Nitulescu — historia przyjaciela — [08] · Diamond · 16:21 · EN
9. Daniela Huelsen — alignment, miłość ponad strach — [09] · Double Diamond, Germany Founder · 26:43 · EN
10. David Stirling — zamknięcie — being i becoming — [10] · Founding Executive & CEO · 14:31 · EN

---

## CZĘŚĆ D — Wzorce zachowań / linków

- Cała karta sesji (hub) jest klikalna → podstrona. „Wejdź →" to etykieta, nie osobny przycisk.
- „▶ playlista" na karcie = osobny link z `event.stopPropagation()` (nie odpala wejścia na podstronę).
- Wszystkie linki YouTube otwierają się w nowej karcie (`target="_blank"`).
- Na podstronie każde wystąpienie ma 3 akcje: Film (YT), Notatki (lokalny HTML), Transkrypcja (lokalny HTML).
- Nawigacja między podstronami: „← Wszystkie sesje" (hub) i „Sesja N →" (następna).
- Wszystkie filmy YouTube są unlisted.
