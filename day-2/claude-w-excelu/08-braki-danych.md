# Zadanie 8: Braki danych – znaleźć, policzyć i zdecydować, co z nimi zrobić (zanim Claude zrobi to za Was)

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok B: Praca na komórkach i strukturze danych w Excelu**;
kontynuacja [zadania 7](07-formatowanie-warunkowe.md)).

**Cel:** poprosić Claude o policzenie pustych komórek w całym arkuszu
(z rozbiciem na kolumny i linkami do każdej), a potem – zamiast od
razu „uzupełnij" – przejść przez trzy możliwe decyzje: usunąć wiersze,
uzupełnić średnią/najczęstszą wartością, oznaczyć do wyjaśnienia. Sedno
zadania: Claude potrafi uzupełnić wszystko jednym poleceniem, i właśnie
dlatego trzeba wiedzieć, **których komórek nie wolno uzupełniać**.
**Poziom:** podstawowy / średni
**Czas:** ok. 12 minut
**Wymaga:** dodatek Claude w Excelu, **świeża kopia** `Human_Resources.xlsx`
(np. `Human_Resources_zad8.xlsx` – krok 5 zmienia dane); Opus lub
Sonnet. To zadanie czyta cały arkusz (1 470 × 35) – patrz uwaga o
zużyciu limitu na końcu.

## Problem, który to rozwiązuje

Eksport z ERP ma puste komórki: pozycja bez kwoty, wiersz bez kodu
działu, rozdział bez nazwy. W 1 470 wierszach ręcznie znajdziecie je
przez filtr „(Puste)" kolumna po kolumnie – 35 razy. Claude znajduje
wszystkie od razu i podaje adresy. Ale potem pyta: „co z nimi zrobić?"
– i to jest pytanie do Was, bo w zestawieniu budżetowym pusta kwota to
**nie jest „średnia z pozostałych"**, tylko brak, który trzeba wyjaśnić
u źródła.

## Materiały

- Świeża kopia `Human_Resources.xlsx` z panelem Claude.
- Z zadania 2 pamiętacie: `=LICZ.PUSTE(A2:AI1471)` → **13**. Teraz
  chodzi o to, **gdzie** i **co dalej**.

## Kroki

1. **Ile i gdzie.** *„Ile pustych komórek jest w tych danych? Podaj
   rozbicie na kolumny i adresy."*
   Obserwujcie panel: Claude czyta arkusz partiami (np. po 500
   wierszy), potem liczy kodem. Klucz: **13 pustych komórek w 10
   kolumnach**, **7 wierszy**:

   | Kolumna | Puste | Wiersze |
   |---|---|---|
   | `B` `MonthlyIncome` | 3 | 3, 8, 949 |
   | `F` `Department` | 1 | 9 |
   | `I` `EducationField` | 1 | 8 |
   | `K` `EmployeeNumber` | 1 | 8 |
   | `M` `Gender` | 1 | 8 |
   | `Q` `JobRole` | 1 | 8 |
   | `S` `MaritalStatus` | 1 | 19 |
   | `T` `MonthlyRate` | 2 | 25, 105 |
   | `X` `PercentSalaryHike` | 1 | 8 |
   | `Y` `PerformanceRating` | 1 | 8 |

   Kliknijcie link do jednej z komórek (np. `B949`) – Excel skoczy do
   pustej komórki. Sprawdźcie sumę: `=LICZ.PUSTE(A2:AI1471)` → 13.
   Wiersz **8** ma 7 pustych kolumn, w tym `EmployeeNumber` –
   zapamiętajcie go.
2. **Zapytajcie o opcje, nie o wykonanie.** *„Jak mogę obsłużyć te
   braki? Wypisz opcje, nic jeszcze nie zmieniaj."*
   Claude powinien podać co najmniej trzy: (a) usunąć wiersze z
   brakami, (b) uzupełnić – liczby średnią/medianą, teksty najczęstszą
   wartością, (c) oznaczyć do ręcznej weryfikacji. Zwykle sam zaproponuje
   wybór. **Nie wybierajcie jeszcze.**
3. **Policzcie, co dałoby usunięcie.** 7 wierszy z 1 470 = **0,5 %**
   – w analizie statystycznej do przeżycia. Ale wiersz 8 to 59-letni
   pracownik z 12 latami pracy – usunięcie oznacza, że w zestawieniu
   „go nie ma". W kadrach czy budżecie wiersz to zwykle konkretna
   osoba albo pozycja planu; **nie usuwa się ich dlatego, że brakuje
   jednej kwoty**.
4. **Zobaczcie, co dałoby uzupełnienie – bez zmiany danych.** *„Pokaż w
   tabeli, jaką wartość wstawiłbyś do każdej pustej komórki przy opcji
   „średnia / najczęstsza wartość" – ale jeszcze nic nie wpisuj."*
   Klucz i **cztery pułapki** do znalezienia w tej tabeli:
   - `K8` `EmployeeNumber` → średnia ≈ **1 026** – Claude wymyśliłby
     **identyfikator**, i to taki, który **już istnieje** w kolumnie
     (`EmployeeNumber` 1026 to inny pracownik). Identyfikatorów nie
     uzupełnia się nigdy.
   - `M8` `Gender` → najczęstsza wartość **Male** – to wymyślona
     cecha osoby, nie oszacowanie.
   - `Q8` `JobRole` → najczęstsze **Sales Executive** – a wiersz 8 to
     dział `Research & Development`, w którym to stanowisko **nie
     występuje** (wszystkie 326 osób na tym stanowisku są w Sales).
     Najczęstsza wartość z całej kolumny ignoruje resztę wiersza.
   - `B8` `MonthlyIncome` → średnia **6 505** – dla pracownika na
     `JobLevel` 1, gdzie mediana to **2 670**. Zawyżenie 2,4×.
   Dobra wiadomość: `F9` `Department` → najczęstsze `Research &
   Development` – i to akurat jest **prawda**, bo wiersz 9 ma
   `JobRole` = `Laboratory Technician`, stanowisko wyłącznie z R&D. Ale
   trafił, nie wywnioskował. Poproście: *„Dla F9 wywnioskuj dział ze
   stanowiska, nie z najczęstszej wartości."*
5. **Wykonajcie właściwą decyzję – selektywnie.** Polecenie, które
   odpowiada praktyce urzędu:
   *„Nie uzupełniaj żadnych braków. Dodaj kolumnę `Uwagi` (AJ) i w
   siedmiu wierszach z brakami wpisz, których kolumn brakuje.
   Pokoloruj puste komórki na żółto (formatowanie warunkowe). W F9
   wpisz `Research & Development` z komentarzem w komórce, że
   wywnioskowano ze stanowiska."*
   Sprawdzian: `=LICZ.PUSTE(A2:AI1471)` → **12** (jedna komórka
   uzupełniona, jedenaście oznaczonych), 7 wpisów w `AJ`, 12 żółtych
   komórek. Kliknijcie link do `F9` – ma być komentarz.
6. **Wariant „na potrzeby analizy" – w osobnym arkuszu.** Jeśli
   liczycie średnie i wykresy (zad. 2–4) i chcecie mieć komplet:
   *„Skopiuj dane do nowego arkusza `Analiza` i tam uzupełnij tylko
   kolumny liczbowe medianą w ramach tego samego JobLevel; pozostaw
   puste: EmployeeNumber, Gender, JobRole, EducationField,
   MaritalStatus. W arkuszu z danymi nic nie zmieniaj."*
   Klucz: `B8` (JobLevel 1) → **2 670**, `B3` (JobLevel 2) → **5 343**,
   `B949` (JobLevel 3) → **9 980** – zamiast 6 505 dla wszystkich
   trzech. Oryginał zostaje nietknięty; wszyscy wiedzą, że `Analiza`
   ma wartości szacowane.

## Na co zwrócić uwagę

- **„Uzupełnij braki" to decyzja merytoryczna, nie techniczna.**
  Claude wykona każdą z trzech opcji równie sprawnie i równie
  pewnie. Różnica między nimi to Wasza odpowiedzialność za
  zestawienie. Nawyk: najpierw *„wypisz opcje"* (krok 2) i *„pokaż,
  co byś wstawił"* (krok 4), dopiero potem polecenie wykonawcze.
- **Trzy rodzaje komórek, których nie uzupełnia się nigdy:**
  identyfikatory (numer pracownika, kod działu, numer dokumentu),
  cechy osób (płeć, stan cywilny, wykształcenie) i kwoty w
  zestawieniach sprawozdawczych. Puste = „do wyjaśnienia u źródła",
  kolumna `Uwagi` i kolor. W ERP brak kwoty często oznacza brak
  księgowania, a nie „mniej więcej tyle co inni".
- **Średnia z kolumny nie zna reszty wiersza.** `Sales Executive` w
  R&D, pensja dyrektorska u pracownika poziomu 1 – to błędy, których
  nie widać w liczbie „13 uzupełnionych". Jeśli już uzupełniacie –
  **w grupie** (ten sam poziom, ten sam dział, ten sam rozdział), jak
  w kroku 6, i zawsze w kopii oznaczonej jako szacunkowa.
- **Link do komórki = ślad każdej zmiany.** Po uzupełnieniu Claude
  wypisuje, które komórki zmienił, z linkami. To Wasza ścieżka
  kontroli – bez niej nie da się odróżnić danych od szacunków. W
  arkuszu, który idzie dalej, dodatkowo: kolor albo komentarz na
  każdej zmienionej komórce.
- **Puste ≠ zero ≠ „brak".** `LICZ.PUSTE` liczy tylko puste komórki.
  Spacja, `-`, `n/d`, `0` wpisane zamiast braku – to dla Excela
  wartości. W realnych eksportach sprawdźcie też te: *„Które komórki
  w kolumnie B zawierają tekst zamiast liczby albo zero?"*
- **Zużycie limitu.** To zadanie czyta cały arkusz partiami i liczy
  kodem – kilka minut i wyraźnie więcej tokenów niż zadania 5–7.
  Zużycie widać w Claude: *Ustawienia → Zużycie* (okno 5-godzinne i
  tygodniowe). Na planie Team Urzędu limit jest per miejsce; jeśli
  dobiegnie końca w trakcie pracy, poczekacie na odnowienie okna –
  nic nie przepada. Szczegóły planów i limitów:
  [`../../day-1/claude-zadania/06-plany-i-limity.md`](../../day-1/claude-zadania/06-plany-i-limity.md).
  Oszczędność: jedna rozmowa na plik (dane są już w kontekście –
  Dzień 1), a do prostych operacji (sortowanie, filtr) – Sonnet.
- **Dane osobowe – ten raz w drugą stronę.** Uzupełnianie płci czy
  stanu cywilnego „najczęstszą wartością" na realnym zbiorze to
  **tworzenie** danych osobowych, których Urząd nie zebrał. Zasada z
  Bloku B (nic realnego do dodatku) obowiązuje; ale nawet za pisemną
  zgodą – tych kolumn nie uzupełnia się.

## Notatki własne

- Czy Claude w kroku 2 sam zaproponował „oznaczyć do weryfikacji",
  czy tylko „usuń" i „uzupełnij"?
- Którą z czterech pułapek z kroku 4 Claude wskazał sam, zanim
  poprosiliście o tabelę?
- Które kolumny w Waszym zestawieniu miesięcznym miewają braki – i
  co dziś z nimi robicie: zero, „–", puste, telefon do wydziału?
