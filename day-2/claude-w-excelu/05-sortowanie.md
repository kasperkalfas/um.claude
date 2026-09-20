# Zadanie 5: Sortowanie słowami – rosnąco, malejąco, po dwóch kolumnach

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok B: Praca na komórkach i strukturze danych w Excelu**;
kontynuacja [zadania 4](04-wykresy-w-excelu.md)).

**Cel:** posortować 1 470 wierszy trzema poleceniami po polsku (rosnąco
po jednej kolumnie, malejąco po innej, po dwóch kolumnach naraz) – i
przy okazji zobaczyć, co sortowanie robi z numerami wierszy, pustymi
komórkami i wynikami z poprzednich zadań.
**Poziom:** podstawowy
**Czas:** ok. 8 minut
**Wymaga:** dodatek Claude w Excelu, **świeża kopia**
`Human_Resources.xlsx` (np. `Human_Resources_zad5.xlsx`) – sortowanie
zmienia kolejność wierszy w całym arkuszu; Sonnet wystarczy.

## Problem, który to rozwiązuje

Sortowanie w Excelu jest proste, dopóki nie trzeba: zaznaczyć całego
zakresu (a nie jednej kolumny – klasyczny błąd rozjeżdżający wiersze),
pamiętać, że nagłówek to nagłówek, i ustawić dwa poziomy w oknie
*Sortowanie niestandardowe*. Claude robi to z jednego zdania i mówi,
co zrobił. Ale sortowanie **przestawia wiersze na stałe** – i o tym jest
połowa tego zadania.

## Materiały

- Kopia `Human_Resources.xlsx` z panelem Claude.
- Ściągawka kolumn: `A` = `Age`, `B` = `MonthlyIncome`,
  `K` = `EmployeeNumber`.

## Kroki

1. **Zanim posortujecie – zapamiętajcie.** Z zadania 3: najdłuższy staż
   miał **wiersz 128** (`EmployeeNumber` 165). Zapiszcie to.
2. **Rosnąco po jednej kolumnie.** *„Posortuj dane rosnąco według
   wieku."* Claude powinien: zidentyfikować kolumnę `A`, posortować
   **cały zakres** (wszystkie 35 kolumn razem, nagłówek na miejscu) i
   napisać, co zrobił. Klucz: `A2` = 18, `A1471` = 60; osiem osób ma
   18 lat, pięć – 60. Sprawdźcie w wierszu 2, czy **pozostałe kolumny
   przesunęły się razem z wiekiem** (jeśli `B2` nadal wynosi 5 993, coś
   poszło nie tak – posortowano samą kolumnę `A`).
3. **Malejąco po innej kolumnie.** *„Posortuj malejąco według
   wynagrodzenia miesięcznego."* Klucz: `B2` = **19 999**
   (`EmployeeNumber` 259, Manager), potem 19 973, 19 943. Przewińcie na
   sam dół: trzy wiersze z **pustym** `MonthlyIncome` (zadanie 2)
   wylądowały na końcu – Excel traktuje puste komórki jako „ostatnie"
   niezależnie od kierunku. Zapytajcie Claude: *„Gdzie są teraz wiersze
   bez wynagrodzenia?"* – powinien wskazać wiersze 1469–1471.
4. **Dwa klucze.** *„Posortuj rosnąco według wieku, a w ramach tego
   samego wieku rosnąco według wynagrodzenia miesięcznego."*
   Klucz: pierwsze osiem wierszy to 18-latkowie z wynagrodzeniem
   **1 051, 1 200, 1 420, 1 514, 1 569, 1 611, 1 878, 1 904** – w tej
   kolejności. Jeśli kolejność w `B2:B9` jest inna, drugi klucz nie
   zadziałał. Otwórzcie *Dane → Sortuj* – zobaczycie, czy Claude
   ustawił dwa poziomy (to samo okno, które klikalibyście ręcznie).
5. **Gdzie jest wiersz 128?** Zapytajcie: *„W którym wierszu jest teraz
   pracownik o EmployeeNumber 165?"* Będzie to inny numer niż 128.
   Wniosek z zadania 3 w praktyce: **numer wiersza to nie identyfikator**.
6. **Powrót do oryginalnej kolejności.** Zapytajcie Claude: *„Czy da się
   wrócić do pierwotnej kolejności wierszy?"* Poprawna odpowiedź: nie
   ma po czym – w tym pliku nie ma kolumny z numerem porządkowym
   (`EmployeeNumber` ma luki: 1…2068), a `Ctrl+Z` działa tylko do
   zamknięcia pliku. Dlatego zaczęliście od kopii.

## Na co zwrócić uwagę

- **Sortowanie to zmiana danych, nie widok.** Po zapisaniu pliku nie ma
  „odsortuj". Trzy nawyki: kopia przed sortowaniem; kolumna `Lp.` z
  numerem porządkowym w zestawieniach, które chcecie móc przywrócić;
  do *oglądania* w innej kolejności – **filtr**, nie sortowanie.
- **Cały zakres, nie kolumna.** Największa szkoda w Excelu to
  posortowanie jednej kolumny bez sąsiednich – wiersze przestają do
  siebie pasować i nikt tego nie widzi. Claude sortuje cały zakres, ale
  **sprawdzajcie wiersz 2** po każdym sortowaniu (krok 2) – zajmuje to
  3 sekundy.
- **Puste komórki idą na koniec** – w obu kierunkach. Przy sortowaniu
  malejącym po kwocie brak kwoty nie jest „najmniejszy", tylko
  „nieznany"; w zestawieniu dla przełożonego takie wiersze trzeba
  wyjaśnić, nie schować na dole.
- **Formuły z zadania 3 przeżyją sortowanie**, bo odwołują się do
  zakresów (`A2:A1471`), a nie do konkretnych wierszy. Formuła typu
  `=B128` (odwołanie do „tego pracownika") – nie. Kolejny argument za
  `EmployeeNumber` zamiast numeru wiersza.
- **Polecenie można też wypowiedzieć** – panel ma mikrofon. Do
  sortowania to wygodne; do polecenia z trzema warunkami i nazwami
  kolumn – lepiej napisać, żeby dało się sprawdzić, co dokładnie
  powiedzieliście.
- **W realnym zestawieniu kadrowym sortowanie po nazwisku to już
  przetwarzanie danych osobowych** – nie inaczej niż każda inna
  operacja. Zasada z Bloku B nie ma wyjątku „ale ja tylko sortuję".

## Notatki własne

- Czy po kroku 2 wiersz 2 miał spójne dane (wiek 18 i „jego" pozostałe
  kolumny)?
- W którym wierszu wylądował `EmployeeNumber` 165 po sortowaniu z
  kroku 4?
- Które z Waszych zestawień sortujecie co miesiąc – i czy mają kolumnę
  `Lp.`?
