# Zadanie 2: „Daj mi ogólne wnioski" – pierwsza analiza danych i jej kontrola

**Dzień 2, Blok B** · ok. 15 min · dodatek Claude w Excelu (zad. 1),
`Human_Resources.xlsx`, model Opus.

**Cel:** jednym zdaniem uzyskać przegląd zbioru, a potem **sprawdzić trzy
liczby formułami** – Claude potrafi podać pewnie brzmiące, błędne
podsumowanie.

**Kontekst danych:** wiersz = pracownik; `Attrition` = czy odszedł
(`Yes`/`No`). Pytanie działu kadr: kto odchodzi i dlaczego?

## Polecenia

### 1. Jedno zdanie

> Podaj ogólne wnioski z tych danych.

Bez opisu kolumn, bez tłumaczenia `Attrition`. Claude czyta cały arkusz,
potem pisze i uruchamia kod (rozwińcie „pokaż więcej"). 2–4 min.

Typowa odpowiedź: przegląd (wiersze, kolumny, braki, typowe wartości) →
liczby o odejściach → 3–5 wniosków „do działania".

### 2. Kontrola – trzy formuły, bez Claude

W wolnej kolumnie (np. `AK`):

| Co | Formuła | Klucz |
|---|---|---|
| odsetek odejść | `=LICZ.JEŻELI(C2:C1471;"Yes")/ILE.NIEPUSTYCH(C2:C1471)` | **16,1 %** (237) |
| braki danych | `=LICZ.PUSTE(A2:AI1471)` | **13** |
| mediana wynagrodzenia | `=MEDIANA(B2:B1471)` | **4 908** |

Jeśli liczba się nie zgadza z podsumowaniem – **zapiszcie rozbieżność**,
nie poprawiajcie Claude. To najważniejszy wynik zadania.

### 3. Dopytanie o jeden wniosek

> Skąd ten wniosek? Podaj liczby: ile osób z nadgodzinami odeszło, a ile
> bez, i jaki to procent w każdej grupie.

Klucz: nadgodziny **30,5 %** vs bez **10,4 %**. Sprawdźcie tabelą
przestawną (wiersze `OverTime`, kolumny `Attrition`, wartości – licznik).

### 4. Wersja dla przełożonego

> Streść to w 5 punktach po polsku, dla naczelnika wydziału kadr, bez
> żargonu, każdy punkt z jedną liczbą.

Zachowajcie ten tekst – wraca w zadaniu 2 z PowerPointa.

## Klucz dla prowadzącego

1 470 × 35; odejścia 16,1 % (237); 13 pustych komórek w 7 wierszach
(wiersz 8 ma 7); średni wiek 36,9; wynagrodzenie średnia 6 505 / mediana
4 908; nadgodziny 30,5 % vs 10,4 %; `Sales Representative` 39,8 % (33/83);
`StockOptionLevel` 0: 24,4 %; częste podróże 24,9 % vs 8,0 %; single
25,5 %; `JobLevel` 1: 26,3 %; mediana wynagrodzenia odchodzących 3 187 vs
5 206.

## Pamiętaj

- Typowe pomyłki: odsetek z podgrupy podany jako ogólny; „brak braków",
  bo sprawdził część kolumn. Trzy formuły to 2 minuty.
- **Wnioski ≠ przyczyny.** „Z nadgodzinami odchodzą 3× częściej" to fakt;
  „nadgodziny powodują odejścia" to hipoteza. W notatce piszcie
  „współwystępuje".
- Cały arkusz jest w oknie kontekstu – kolejne pytania w tej rozmowie
  są tańsze niż nowa rozmowa.
