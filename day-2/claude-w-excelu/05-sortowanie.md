# Zadanie 5: Sortowanie słowami – rosnąco, malejąco, po dwóch kolumnach

**Dzień 2, Blok B** · ok. 8 min · dodatek Claude w Excelu, **świeża kopia**
`Human_Resources.xlsx` (np. `_zad5`) – sortowanie zmienia plik na stałe;
Sonnet wystarczy.

**Cel:** trzy sortowania jednym zdaniem każde i zobaczyć, co sortowanie
robi z numerami wierszy i pustymi komórkami.

**Ściągawka kolumn:** `A` Age · `B` MonthlyIncome · `K` EmployeeNumber.

## Polecenia

### 0. Zapamiętajcie

Z zadania 3: najdłuższy staż = **wiersz 128**, `EmployeeNumber` 165.

### 1. Rosnąco po jednej kolumnie

> Posortuj dane rosnąco według wieku.

Klucz: `A2` = 18, `A1471` = 60. Sprawdźcie wiersz 2: pozostałe kolumny
przesunęły się razem z wiekiem? (Jeśli `B2` nadal = 5 993 – posortowano
samą kolumnę `A`.)

### 2. Malejąco po innej kolumnie

> Posortuj malejąco według wynagrodzenia miesięcznego.

Klucz: `B2` = **19 999** (`EmployeeNumber` 259), potem 19 973, 19 943.
Na dole: trzy wiersze z pustym `MonthlyIncome`.

> Gdzie są teraz wiersze bez wynagrodzenia?

Klucz: wiersze 1469–1471. Puste idą na koniec w obu kierunkach.

### 3. Dwa klucze

> Posortuj rosnąco według wieku, a w ramach tego samego wieku rosnąco
> według wynagrodzenia miesięcznego.

Klucz: `B2:B9` (18-latkowie) = **1 051, 1 200, 1 420, 1 514, 1 569, 1 611,
1 878, 1 904**. *Dane → Sortuj* pokaże dwa poziomy.

### 4. Gdzie jest wiersz 128?

> W którym wierszu jest teraz pracownik o EmployeeNumber 165?

Inny numer niż 128 – **numer wiersza to nie identyfikator**.

### 5. Powrót

> Czy da się wrócić do pierwotnej kolejności wierszy?

Poprawna odpowiedź: nie – nie ma kolumny `Lp.`, a `Ctrl+Z` działa tylko do
zamknięcia pliku. Dlatego kopia.

## Pamiętaj

- Sortowanie = zmiana danych; do oglądania w innej kolejności – **filtr**
  (zadanie 6).
- Po każdym sortowaniu sprawdźcie wiersz 2 (3 sekundy).
- W zestawieniach, które chcecie przywracać – kolumna `Lp.`.
- Formuły na zakresach (`A2:A1471`) przeżyją sortowanie; `=B128` – nie.
