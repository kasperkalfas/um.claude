# Zadanie 3: Średnia, mediana, „który wiersz spełnia warunek" – Claude pisze formuły do komórek

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok B: Praca na komórkach i strukturze danych w Excelu**;
kontynuacja [zadania 2](02-pierwsze-wnioski-z-danych.md)).

**Cel:** poprosić Claude o konkretne statystyki (średnia, mediana) i o
znalezienie wiersza spełniającego warunek – i zobaczyć, że dodatek
**wpisuje do arkusza formułę, nie liczbę**, podaje adres komórki z
wynikiem i pozwala do niej skoczyć jednym kliknięciem. Po drodze: jak
sprawdzić, że formuła liczy to, o co prosiliście.
**Poziom:** podstawowy
**Czas:** ok. 12 minut
**Wymaga:** dodatek Claude w Excelu, otwarty `Human_Resources.xlsx`
(kopia!), model Opus lub Sonnet – to zadanie jest na tyle proste, że
Sonnet wystarczy.

## Problem, który to rozwiązuje

W zadaniu 2 Claude liczył „u siebie" (kodem) i tylko opowiadał o
wynikach. W codziennej pracy chcecie, żeby wynik **został w arkuszu**:
jako formuła, którą można sprawdzić, skopiować, która przeliczy się po
zmianie danych. Do tego dochodzi typowe pytanie „która pozycja ma
największą wartość / spełnia warunek" – w 1 470 wierszach ręcznie to
filtr i sortowanie, a Claude ma to zrobić i **wskazać adres**.

## Materiały

- `Human_Resources.xlsx` – **świeża kopia** (np.
  `Human_Resources_zad3.xlsx`), bo od tego zadania Claude pisze do
  komórek.
- Ściągawka kolumn: `A` = `Age` (wiek), `B` = `MonthlyIncome`
  (wynagrodzenie miesięczne), `E` = `DailyRate` (stawka dzienna),
  `Q` = `JobRole`, `W` = `OverTime`, `AC` = `TotalWorkingYears` (lata
  pracy ogółem), `AF` = `YearsAtCompany` (lata w firmie). Dane w
  wierszach 2–1471.

## Kroki

1. **Średnia.** W panelu: *„Policz średni wiek pracowników (kolumna
   Age) i wpisz wynik pod danymi, z etykietą."*
   Claude powinien: (a) napisać, że znalazł kolumnę `Age` w `A`, (b)
   wpisać formułę typu `=ŚREDNIA(A2:A1471)` w komórce pod danymi (np.
   `A1473`) z etykietą obok, (c) podać wynik **i adres komórki jako
   link**. Kliknijcie link – Excel skoczy do tej komórki. Kliknijcie w
   nią: na pasku formuły ma być **formuła**, nie wpisana liczba.
   Klucz: **36,92**.
2. **Mediana.** *„Policz medianę stawki dziennej (DailyRate) i wpisz
   obok poprzedniego wyniku."* Klucz: **802**. Sprawdźcie, czy formuła
   to `=MEDIANA(E2:E1471)` – a nie średnia (to częsta pomyłka
   przy „typowej wartości").
3. **Wiersz z warunkiem.** *„Znajdź pracownika z najdłuższym stażem w
   firmie (YearsAtCompany). Podaj numer wiersza, EmployeeNumber i stanowisko."*
   Claude powinien wskazać **wiersz 128** (`EmployeeNumber` 165,
   `YearsAtCompany` = 40, `Healthcare Representative`) i dać link do
   tej komórki. Kliknijcie, przewińcie do kolumny `AF` – ma być 40.
   Dopytajcie: *„Czy ktoś jeszcze ma 40 lat w firmie?"* (klucz: nie,
   ale **dwie osoby** mają 40 lat pracy ogółem w `TotalWorkingYears` –
   to inna kolumna; sprawdźcie, czy Claude ich nie pomylił).
4. **Warunek złożony – Wasze pytanie.** Zadajcie jedno pytanie, na
   które odpowiedź musi być **liczbą w komórce**, np.:
   - *„Ile osób z nadgodzinami (OverTime = Yes) odeszło (Attrition =
     Yes)? Wpisz formułę."* – klucz **127**, formuła typu
     `=LICZ.WARUNKI(W2:W1471;"Yes";C2:C1471;"Yes")`;
   - *„Ile osób mieszka dalej niż 20 km od pracy (DistanceFromHome > 20)?"*
     – klucz **204**;
   - *„Ile osób ma 55 lat lub więcej?"* – klucz **69**.
5. **Sprawdzian „przelicz się sam".** Zmieńcie w komórce `A2` wiek z 41
   na 141 i patrzcie na komórkę ze średnią z kroku 1: powinna się
   zmienić (na ok. 36,99). Cofnijcie (`Ctrl+Z`). Gdyby w komórce była
   wpisana liczba zamiast formuły – nic by się nie stało. To jest
   różnica między „Claude policzył" a „Claude zbudował arkusz".

## Na co zwrócić uwagę

- **Formuła, nie wartość – zawsze.** Jeśli Claude wpisze gołą liczbę,
  poproście: *„Zamień na formułę, żeby przeliczała się po zmianie
  danych."* Ta sama zasada obowiązuje w Claude Code przy Procesie 2
  (`../../day-1/claude-code-cli/`) – wpisujemy `=SUMA()`, nie wynik.
- **Link do komórki to Wasza kontrola.** Każdą liczbę z odpowiedzi
  klikacie i patrzycie na pasek formuły: zakres (`A2:A1471`, nie `A:A`
  z nagłówkiem, nie `A2:A1000`), funkcja (średnia vs mediana), warunki.
  Trzy sekundy na liczbę.
- **Zakres kończy się na 1471.** Jeśli dopiszecie wiersze pod danymi,
  formuła ich nie obejmie. Dla rosnących zestawień lepiej poprosić:
  *„Zamień zakres na tabelę Excela i użyj odwołań strukturalnych."*
- **Mediana vs średnia.** Wynagrodzenie: średnia 6 505, mediana 4 908
  (zadanie 2) – kilka wysokich pensji ciągnie średnią w górę. Przy
  pytaniu o „typową" wartość proście o **obie**; dla banku i Rady
  różnica bywa argumentem.
- **Wiersz ≠ pracownik.** Claude podaje numer wiersza arkusza (128) –
  po posortowaniu albo usunięciu wiersza 8 numer się zmieni. Do
  identyfikacji używajcie `EmployeeNumber` (165), nigdy numeru wiersza.
- **Copilot obok Claude.** Jeśli w Waszym Excelu jest też przycisk
  Copilot – to inny asystent, inne modele i inna umowa na dane. Na
  szkoleniu pracujemy Claude; zasada „tylko dane fikcyjne" dotyczy obu.

## Notatki własne

- Czy Claude za pierwszym razem wpisał formuły, czy liczby?
- Które pytanie z kroku 4 zadaliście i czy wynik zgadzał się z kluczem?
- Jakie pytanie „który wiersz…" zadajecie najczęściej w swoich
  zestawieniach – i ile dziś zajmuje Wam odpowiedź?
