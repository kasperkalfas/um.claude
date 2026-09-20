# Zadanie 6: Filtrowanie słowami – jeden warunek, dwa warunki naraz (i czym filtr różni się od sortowania)

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok B: Praca na komórkach i strukturze danych w Excelu**;
kontynuacja [zadania 5](05-sortowanie.md)).

**Cel:** zawęzić widok 1 470 wierszy do tych, które spełniają warunek
opisany po polsku – najpierw jeden (dział), potem dwa naraz (dział
**i** staż) – zobaczyć, że Claude zakłada **zwykły filtr Excela**
(lejek w nagłówku), a nie kopiuje wierszy gdzie indziej, i policzyć
przefiltrowane wiersze formułą, żeby mieć pewność, że warunek zadziałał.
**Poziom:** podstawowy
**Czas:** ok. 8 minut
**Wymaga:** dodatek Claude w Excelu, kopia `Human_Resources.xlsx` w
**oryginalnej kolejności wierszy** (np. `Human_Resources_zad6.xlsx` –
nie plik po sortowaniu z zadania 5, bo klucz podaje numery wierszy);
Sonnet wystarczy.

## Problem, który to rozwiązuje

„Pokaż mi tylko dział X", „tylko pozycje powyżej progu", „tylko dział X
z kwotą powyżej progu" – to najczęstsze pytanie do każdego zestawienia.
W Excelu to lejek w nagłówku, lista wartości do odhaczenia, a przy
liczbach jeszcze *Filtry liczb → Większe lub równe…* – dla każdej
kolumny osobno. Claude robi to z jednego zdania. Ważniejsze jednak, że
filtr – w odróżnieniu od sortowania z zadania 5 – **niczego w danych
nie zmienia**: ukrywa wiersze, które nie pasują, i da się go zdjąć
jednym kliknięciem.

## Materiały

- Kopia `Human_Resources.xlsx` z panelem Claude.
- Ściągawka kolumn: `C` = `Attrition` (odejścia), `F` = `Department`
  (dział: `Research & Development`, `Sales`, `Human Resources`),
  `K` = `EmployeeNumber`, `Q` = `JobRole`, `AF` = `YearsAtCompany`
  (lata w firmie). Dane w wierszach 2–1471.

## Kroki

1. **Jeden warunek.** *„Przefiltruj dane tak, żeby zostały tylko osoby
   z działu R&D."*
   W poleceniu jest skrót `R&D` – w kolumnie `F` stoi pełna nazwa
   `Research & Development`. Claude powinien to skojarzyć, założyć filtr
   na całym zakresie (lejki pojawią się we **wszystkich** nagłówkach
   wiersza 1) i w kolumnie `F` zostawić odhaczoną tylko tę wartość.
   Sprawdzian: kliknijcie lejek w `F1` – na liście ma być zaznaczony
   jeden dział; na pasku stanu u dołu Excel pokaże komunikat typu
   *„Znaleziono 960 z 1470 rekordów"*. Klucz: **960** wierszy.
2. **Liczba przefiltrowanych – formułą.** Poproście: *„Wpisz pod danymi
   formułę, która liczy tylko widoczne (przefiltrowane) wiersze."*
   Claude powinien użyć `=SUMY.CZĘŚCIOWE(103;A2:A1471)` (funkcja 103 =
   licz niepuste **z pominięciem ukrytych** wierszy) → **960**. Zwykłe
   `=ILE.NIEPUSTYCH(A2:A1471)` da 1 470 – liczy wszystko, także ukryte.
   To różnica, którą warto znać przy każdym „ile pozycji zostało po
   filtrze".
   **Pułapka:** jeśli Claude policzy na kolumnie `K` (`EmployeeNumber`),
   wyjdzie **959** – bo `K8` jest puste (wiersz 8 z zadania 2 należy do
   R&D), a funkcja 103 liczy tylko niepuste. Liczcie widoczne wiersze na
   kolumnie **bez braków** (`A` = `Age`) albo na tej, po której
   filtrujecie (`F`).
3. **Dwa warunki naraz.** *„Przefiltruj dane tak, żeby zostały tylko
   osoby z działu R&D, które pracują w firmie co najmniej 30 lat."*
   Claude ma dołożyć drugi warunek na kolumnie `AF` (`YearsAtCompany
   ≥ 30`), **nie zdejmując** pierwszego. Klucz: **10** wierszy – w tym
   wiersz **128** (`EmployeeNumber` 165, 40 lat – najdłuższy staż z
   zadania 3), 192 (259, Manager, 33 lata), 272 (374, 36 lat), 475 (638,
   31), 597 (825, 31), 655 (905, 31), 916 (1278, 33), 1088 (1539, 32),
   1113 (1572, 33), 1140 (1606, 30). Przewińcie do kolumny `AF` –
   wszystkie wartości mają być ≥ 30, a lejek w `AF1` ma mieć ikonę
   aktywnego filtru. Formuła z kroku 2 powinna teraz pokazać **10**.
4. **Kontrola niezależna od filtru.** Wpiszcie sami (albo poproście
   Claude) formułę, która liczy to samo **bez** filtru:
   `=LICZ.WARUNKI(F2:F1471;"Research & Development";AF2:AF1471;">=30")`
   → **10**. Jeśli obie liczby się zgadzają, filtr działa tak, jak
   brzmiało polecenie. Jeśli nie – któraś z granic (`≥` czy `>`) albo
   któraś z nazw jest inna, niż myślicie.
5. **„Co najmniej" ≠ „ponad".** Zmieńcie jedno słowo: *„…którzy pracują
   w firmie ponad 30 lat."* Klucz: **9** – wypada `EmployeeNumber` 1606
   (dokładnie 30 lat). Dla Claude „co najmniej 30" to `≥ 30`, „ponad 30"
   to `> 30`; dla Waszego przełożonego często to samo. Przy progach w
   zestawieniach **piszcie granicę wprost** („30 lub więcej”) i
   sprawdzajcie wartość graniczną.
6. **Zdjęcie filtru.** *„Wyczyść wszystkie filtry."* Wszystkie 1 470
   wierszy wracają, wiersz 128 znowu jest wierszem 128 – **dane nie
   ruszyły się z miejsca**. Porównajcie z zadaniem 5: po sortowaniu
   nie było do czego wracać. Sprawdźcie na koniec, czy wiersz **9**
   (pusty `Department` z zadania 2) jest widoczny – po filtrze na dział
   był ukryty, bo pusta komórka nie pasuje do żadnej wartości.

## Na co zwrócić uwagę

- **Filtr to widok, sortowanie to zmiana.** Do oglądania i sprawdzania
  – filtr; do trwałego układu (np. przed wydrukiem) – sortowanie na
  kopii. Filtr da się zdjąć po zapisaniu i ponownym otwarciu pliku;
  sortowania nie.
- **Warunki między kolumnami łączą się przez „i”.** Dwa filtry na dwóch
  kolumnach = obie rzeczy naraz (krok 3). „Dział R&D **lub** staż ≥ 30”
  zwykły filtr nie umie – Claude zaproponuje kolumnę pomocniczą z
  formułą `=LUB(...)` albo filtr zaawansowany. Jeśli w poleceniu piszecie
  „lub”, sprawdźcie, jak to rozwiązał (klucz dla ciekawych: R&D lub
  ≥ 30 lat = 960 + 7 osób z innych działów = **967**).
- **Skrót zadziałał, ale nie musiał.** `R&D` → `Research & Development`
  Claude skojarzył, bo w kolumnie są tylko trzy wartości. W zestawieniu
  z 40 rozdziałami klasyfikacji budżetowej „rozdział z oświatą” może
  trafić w zły. Nazwy wartości, po których filtrujecie, **kopiujcie
  z arkusza**.
- **Ukryte wiersze wciąż są w pliku.** Wysyłacie przefiltrowany plik
  dalej – odbiorca zdejmuje filtr i widzi wszystko. Jeśli ma zobaczyć
  tylko wycinek, poproście: *„Skopiuj widoczne wiersze do nowego arkusza
  Wynik”* – i wyślijcie tylko ten arkusz. To samo dotyczy danych, które
  „ukryliście” przed wklejeniem do Claude: ukryty ≠ usunięty, dodatek
  czyta cały arkusz.
- **Liczby po filtrze liczcie funkcją, która zna filtr.** `SUMY.CZĘŚCIOWE`
  (103 = licz, 109 = suma) i `AGREGUJ` pomijają ukryte wiersze; `SUMA`,
  `ILE.NIEPUSTYCH`, `ŚREDNIA` – nie. Zapytanie „ile wyszło po filtrze”
  zadawane Claude to w praktyce prośba o jedną z tych dwóch pierwszych.
  I druga połowa tej zasady (krok 2): **liczcie na kolumnie bez pustych
  komórek** – inaczej brak danych w jednym wierszu zaniża licznik i nikt
  tego nie zauważy.
- **Filtr na realnym zestawieniu kadrowym to nadal przetwarzanie danych
  osobowych** – nie inaczej niż sortowanie (zadanie 5). Nie ma wyjątku
  „ale ja tylko oglądam”.

## Notatki własne

- Czy po kroku 1 lejki pojawiły się we wszystkich nagłówkach, czy tylko
  w `F1`?
- Czy liczby z kroku 3 (formuła po filtrze) i 4 (`LICZ.WARUNKI`) się
  zgadzały?
- Które z Waszych zestawień filtrujecie najczęściej po dwóch kolumnach
  naraz – i czy wysyłacie je dalej z filtrem, czy jako wycinek?
