# Zadanie 3: Średnia, mediana, „który wiersz spełnia warunek" – Claude pisze formuły do komórek

**Dzień 2, Blok B** · ok. 12 min · dodatek Claude w Excelu, **świeża kopia**
`materialy/Human_Resources_zad3.xlsx` (z
[`materialy/Human_Resources.xlsx`](materialy/Human_Resources.xlsx)), Sonnet wystarczy.

**Cel:** wynik ma **zostać w arkuszu jako formuła** (nie liczba), z adresem
komórki do kliknięcia.

**Ściągawka kolumn:** `A` Age · `B` MonthlyIncome · `C` Attrition ·
`E` DailyRate · `Q` JobRole · `W` OverTime · `AC` TotalWorkingYears ·
`AF` YearsAtCompany. Dane w wierszach 2–1471.

## Polecenia

### 1. Średnia

> Policz średni wiek pracowników (kolumna Age) i wpisz wynik pod danymi,
> z etykietą.

Kliknijcie link do komórki → na pasku formuły ma być `=ŚREDNIA(A2:A1471)`,
nie liczba. Klucz: **36,92**.

### 2. Mediana

> Policz medianę stawki dziennej (DailyRate) i wpisz obok poprzedniego
> wyniku.

Klucz: **802**, formuła `=MEDIANA(E2:E1471)` (nie średnia).

### 3. Wiersz z warunkiem

> Znajdź pracownika z najdłuższym stażem w firmie (YearsAtCompany). Podaj
> numer wiersza, EmployeeNumber i stanowisko.

Klucz: **wiersz 128**, `EmployeeNumber` 165, 40 lat, `Healthcare
Representative`.

> Czy ktoś jeszcze ma 40 lat w firmie?

Klucz: nie – ale **dwie osoby** mają 40 lat w `TotalWorkingYears` (inna
kolumna). Sprawdźcie, czy Claude ich nie pomylił.

### 4. Warunek złożony – jedno do wyboru

> Ile osób z nadgodzinami (OverTime = Yes) odeszło (Attrition = Yes)?
> Wpisz formułę.

Klucz: **127**, `=LICZ.WARUNKI(W2:W1471;"Yes";C2:C1471;"Yes")`.

> Ile osób mieszka dalej niż 20 km od pracy (DistanceFromHome > 20)?

Klucz: **204**.

> Ile osób ma 55 lat lub więcej?

Klucz: **69**.

### 5. Sprawdzian „przelicz się sam"

Zmieńcie `A2` z 41 na 141 → średnia z kroku 1 ma się zmienić (ok. 36,99).
`Ctrl+Z`. Gdyby w komórce była liczba – nic by się nie stało.

## Pamiętaj

- Jeśli Claude wpisze gołą liczbę:
  > Zamień na formułę, żeby przeliczała się po zmianie danych.
- Każdą liczbę z odpowiedzi klikacie i patrzycie na zakres (`A2:A1471`,
  nie `A:A`), funkcję i warunki.
- Przy „typowej wartości" proście o **średnią i medianę** (6 505 vs 4 908).
- **Numer wiersza ≠ identyfikator.** Do identyfikacji `EmployeeNumber`.
