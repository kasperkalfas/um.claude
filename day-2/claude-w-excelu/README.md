# Claude w Excelu — dodatek Claude by Anthropic (Dzień 2)

Materiały do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
prowadzący: Kasper Kalfas).

**Miejsce w agendzie:** Dzień 2, **Blok B (60 min): Praca na komórkach i
strukturze danych w Excelu** – jako wariant „Claude w panelu bocznym
Excela", równolegle do ścieżki Claude Code z
[`../../day-1/claude-code-cli/`](../../day-1/claude-code-cli/README.md).
Oba podejścia robią to samo (czytają arkusz, wskazują błędy na poziomie
komórek, piszą formuły) – różni je miejsce pracy: dodatek działa **w
otwartym skoroszycie**, Claude Code **na plikach w folderze**. Blok C
(automatyzacja miesięczna) i D (obsługa błędów) pozostają w Claude Code.

## Materiały – wszystko w jednym miejscu

Wszystkie pliki do zadań są w [`materialy/`](materialy/) i tam też
zapisujecie kopie robocze – nic na Pulpicie, w *Pobranych* ani w OneDrive
Urzędu. Na laptop kopiuje się cały folder `claude-w-excelu/` (zadania +
`materialy/`), więc linki w zadaniach działają bez zmian.

| Plik | Do czego |
|---|---|
| [`materialy/Human_Resources.xlsx`](materialy/Human_Resources.xlsx) | oryginał, zad. 1–8; po zad. 1 nietknięty |
| `materialy/Human_Resources_zad2.xlsx` … `_zad8.xlsx` | kopia na każde zadanie (*Plik → Zapisz jako* w `materialy/`) |
| [`materialy/termomodernizacja_zalozenia.xlsx`](materialy/termomodernizacja_zalozenia.xlsx) | oryginał, zad. 9 i załącznik do Claude Czat |
| `materialy/termomodernizacja_zalozenia_zad9.xlsx` | kopia robocza zad. 9 |
| [`materialy/generuj_termomodernizacja.py`](materialy/generuj_termomodernizacja.py) | dla prowadzącego – odtwarza plik zad. 9 i wypisuje klucz |

Zepsuty plik = nowa kopia z oryginału w `materialy/`.

## Zadania

- [ ] **[01 – Claude w Excelu – instalacja dodatku i pierwsze uruchomienie](01-claude-w-excelu-instalacja.md)** *(10 min)*
      — Dodatki → Claude by Anthropic → logowanie kontem Urzędu → wybór
      modelu → „co jest w tym arkuszu?" z odwołaniami do komórek.
- [ ] **[02 – „Daj mi ogólne wnioski" – pierwsza analiza danych i jej kontrola](02-pierwsze-wnioski-z-danych.md)** *(15 min)*
      — jedno zdanie → Claude czyta arkusz, liczy kodem, daje wnioski;
      trzy liczby sprawdzamy formułami (odejścia 16,1 %, 13 pustych
      komórek, mediana 4 908); wnioski ≠ przyczyny; wersja dla naczelnika.
- [ ] **[03 – Średnia, mediana, „który wiersz spełnia warunek" – Claude pisze formuły do komórek](03-statystyki-i-szukanie-wierszy.md)** *(12 min)*
      — `=ŚREDNIA` (36,92), `=MEDIANA` (802), najdłuższy staż (wiersz 128,
      EmployeeNumber 165), `LICZ.WARUNKI` (127); link do komórki jako
      kontrola; test „przelicz się sam".
- [ ] **[04 – Wykresy jednym zdaniem – histogram, słupki, punkty, koło](04-wykresy-w-excelu.md)** *(15 min)*
      — natywne wykresy Excela z tabelą pomocniczą; klucz: 30–34 lata = 325,
      zostało 1 233 / odeszło 237, korelacja wiek–płaca 0,50, podróże
      71/19/10 %; test „koło dla 9 kategorii".
- [ ] **[05 – Sortowanie słowami – rosnąco, malejąco, po dwóch kolumnach](05-sortowanie.md)** *(8 min)*
      — cały zakres, nie kolumna; puste komórki na końcu; dwa klucze
      (18-latkowie: 1 051 → 1 904); numer wiersza ≠ identyfikator; kopia
      przed sortowaniem.
- [ ] **[06 – Filtrowanie słowami – jeden warunek, dwa warunki naraz](06-filtrowanie.md)** *(8 min)*
      — filtr = widok, nie zmiana; R&D (960) → R&D i staż ≥ 30 lat (10);
      `SUMY.CZĘŚCIOWE(103;…)` vs `LICZ.WARUNKI` (pułapka: na `K` wyjdzie 959,
      bo `K8` puste); „co najmniej" ≠ „ponad"
      (9); ukryte ≠ usunięte.
- [ ] **[07 – Kolorowanie komórek słowami – tak/nie, skala kolorów, próg](07-formatowanie-warunkowe.md)** *(10 min)*
      — reguła, nie farba (*Zarządzaj regułami*); Yes/No 237/1 233 –
      i kto dostał zielony; skala 18 → 60 lat; próg > 15 000 (133), puste
      komórki osobno; kolor jedzie z wierszem po sortowaniu.
- [ ] **[08 – Braki danych – znaleźć, policzyć i zdecydować, co z nimi zrobić](08-braki-danych.md)** *(12 min)*
      — 13 pustych w 10 kolumnach / 7 wierszach z adresami; „wypisz
      opcje, nic nie zmieniaj"; cztery pułapki uzupełniania (identyfikator
      1026 już istnieje, Sales Executive w R&D, 6 505 vs 2 670); kolumna
      `Uwagi` + żółte zamiast uzupełniania; wariant `Analiza` medianą w
      grupie; zużycie limitu.
- [ ] **[09 – Model finansowy z założeń – czy termomodernizacja szkoły się opłaca i jak ją spłacić](09-model-finansowy-inwestycji.md)** *(20 min)*
      — polecenie w 4 częściach (kontekst / instrukcje / wejście / wyjście);
      arkusze `Model` + `Kredyt` z formuł do `Zalozenia`; klucz: NPV
      1 717 748, zwrot 7 lat, IRR 14,1 %, rata 306 463; bez dotacji NPV
      ujemne; test „zmień założenie – co się rusza"; to samo w Claude Czat.

## Dane w [`materialy/`](materialy/)

[`termomodernizacja_zalozenia.xlsx`](materialy/termomodernizacja_zalozenia.xlsx) (zad. 9) – 11 fikcyjnych założeń
inwestycji (nakład, dotacja, oszczędności energii, stopa, kredyt) w
jednym arkuszu `Zalozenia`; [`generuj_termomodernizacja.py`](materialy/generuj_termomodernizacja.py) odtwarza plik
i wypisuje klucz (NPV, okres zwrotu, IRR, rata, tabela wrażliwości).

[`Human_Resources.xlsx`](materialy/Human_Resources.xlsx) – fikcyjny, anglojęzyczny zbiór kadrowy:
**1 470 pracowników × 35 kolumn** (jeden arkusz `Human_Resources`).
Pracownicy mają tylko numer (`EmployeeNumber`), bez nazwisk. Kolumny w
grupach:

| Grupa | Kolumny |
|---|---|
| osoba (bez identyfikacji) | `Age`, `Gender`, `MaritalStatus`, `DistanceFromHome`, `Education`, `EducationField` |
| stanowisko | `Department` (3: Research & Development 960, Sales 446, Human Resources 63), `JobRole` (9), `JobLevel` 1–5, `BusinessTravel`, `OverTime` |
| wynagrodzenie | `MonthlyIncome` 1 009–19 999, `DailyRate`, `HourlyRate`, `MonthlyRate`, `PercentSalaryHike` 11–25, `StockOptionLevel` |
| staż | `TotalWorkingYears`, `YearsAtCompany`, `YearsInCurrentRole`, `YearsSinceLastPromotion`, `YearsWithCurrManager`, `NumCompaniesWorked` |
| oceny i satysfakcja (skala 1–4/5) | `PerformanceRating`, `JobSatisfaction`, `EnvironmentSatisfaction`, `RelationshipSatisfaction`, `WorkLifeBalance`, `JobInvolvement`, `TrainingTimesLastYear` |
| wynik | **`Attrition`** – czy pracownik odszedł: Yes 237 (16,1%), No 1 233 |
| stałe (bez wartości informacyjnej) | `EmployeeCount` = 1, `StandardHours` = 80, `Over18` = Y |

**Klucz odpowiedzi – braki w danych** (do zadań o jakości danych):
7 wierszy z pustymi komórkami: wiersz 3 (`MonthlyIncome`), **wiersz 8
(7 pustych kolumn, w tym `EmployeeNumber`)**, 9 (`Department`), 19
(`MaritalStatus`), 25 i 105 (`MonthlyRate`), 949 (`MonthlyIncome`).
Duplikatów `EmployeeNumber` nie ma. Trzy kolumny stałe nadają się do
usunięcia.

Dlaczego kadry, a nie budżet: zestawienia budżetowe są już przerobione w
Dniu 1 i w ścieżce Claude Code; kadry to drugi typowy arkusz w urzędzie
i dobry pretekst do rozmowy o **danych osobowych** – ten plik ich nie
zawiera (numer zamiast nazwiska, dane wymyślone), prawdziwy by
zawierał, i właśnie dlatego nie wolno go otwierać z włączonym dodatkiem.
Angielskie nagłówki są celowe: pokazują, że Claude tłumaczy strukturę
„w locie", a Wy pytacie po polsku.

## Wymagania techniczne (sprawdzić przed Dniem 2)

| Co | Uwaga |
|---|---|
| Excel z Microsoft 365 (desktop Windows lub przeglądarka) | starsze Excel 2016/2019 bez sklepu dodatków nie zadziałają |
| Dostęp do sklepu dodatków Office | jeśli administrator M365 blokuje dodatki – IT musi dopuścić *Claude by Anthropic* |
| Konto Claude w organizacji Urzędu (plan Team) | to samo co do czatu i Cowork |
| Folder [`materialy/`](materialy/) skopiowany razem z zadaniami | jedyne pliki otwierane z włączonym dodatkiem |

> Zasada bezpieczeństwa danych z Dnia 1 (Blok B) obowiązuje bez
> wyjątków: dodatek wysyła zawartość otwartego arkusza do dostawcy
> modelu. Realne pliki Urzędu – tylko za pisemną zgodą Zamawiającego.
