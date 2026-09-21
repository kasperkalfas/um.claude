# Zadanie 3: „Otwórz ten Excel i powiedz, co w nim jest"

**Cel:** Claude Code opisuje strukturę arkusza, odpowiada na pytania
o liczby i porównuje dwa pliki – bez otwierania Excela.
**Poziom:** podstawowy
**Czas:** ok. 20 minut
**Blok:** Dzień 1 — wprowadzenie

## Materiały

W `C:\Szkolenie\dzien-1\praca\`:

- `zestawienie_roczne_2026.xlsx` – **Plik 2** (roczne): arkusz `Wykonanie`
  (8 działów × 12 miesięcy, I–VIII wypełnione) i `Prognoza` (dla banku,
  same formuły).
- `zestawienie_miesieczne_SZABLON.xlsx` – **Plik 1** (miesięczne): plan
  wpisany, wykonanie puste.
- `eksport_erp_2026-09.csv` – eksport z ERP za wrzesień.

## Kroki

1. ```powershell
   cd C:\Szkolenie\dzien-1\praca
   claude
   ```

### Część 1: Struktura

2. ```
   Otwórz zestawienie_roczne_2026.xlsx i opisz, co w nim jest: jakie
   arkusze, jakie kolumny, ile wierszy danych, które komórki zawierają
   formuły, a które wpisane liczby. Nic nie zmieniaj.
   ```

   **Sprawdź** (otwórz plik równolegle w Excelu – do czytania nie
   przeszkadza): rozpoznał 2 arkusze, puste miesiące IX–XII (kolumny
   L–O), formuły w P i Q, `Prognoza` odwołuje się do `Wykonanie`?

3. ```
   Ile miesięcy ma dane? Skąd to wiesz?
   ```

   **Sprawdź:** dobra odpowiedź wskazuje `Prognoza!B2` = 8 **i** puste
   kolumny L–O.

### Część 2: Pytania o liczby

4. ```
   Który dział ma najwyższe wykonanie narastająco po sierpniu, a który
   najniższy procent planu? Podaj kwoty i wskaż komórki.
   ```

   **Sprawdź:** najwyższe – 801 (40 124 000 zł); najniższy % planu –
   926 (62,6 %).

5. ```
   Podaj wykonanie działu 801 w każdym miesiącu jako listę i policz
   średnią miesięczną.
   ```

   **Sprawdź:** średnia I–VIII = 5 015 500 zł. Zweryfikuj jedną liczbę
   w Excelu – to Wy odpowiadacie za liczby.

### Część 3: Porównanie dwóch plików

6. ```
   Porównaj strukturę zestawienie_miesieczne_SZABLON.xlsx z arkuszem
   Wykonanie w pliku rocznym: które kolumny odpowiadają sobie nawzajem,
   a czego brakuje w szablonie miesięcznym?
   ```

   **Sprawdź:** działy w tej samej kolejności (wiersze 6–13, kody
   w kolumnie A); „Wykonanie w miesiącu" z szablonu = jedna kolumna
   miesiąca w rocznym. To przygotowanie do zadania 7.

7. ```
   Otwórz eksport_erp_2026-09.csv i powiedz, jakie ma kolumny, ile
   wierszy i czy widzisz coś podejrzanego w danych. Nic nie poprawiaj.
   ```

   **Zanotuj**, co Claude zauważył sam: różne formaty dat i kwot?
   powtórzony dokument? brak paragrafu? Wracamy do tego w zadaniu 6.

## Na co zwrócić uwagę

- Claude czyta Excel krótkim skryptem w Pythonie (widać go przed pytaniem
  o zgodę). Zawsze możesz poprosić:

  ```
  Wyjaśnij po polsku, co robi ten skrypt, zanim go uruchomisz.
  ```

- **Formuły a wartości:** Claude widzi formułę i osobno jej ostatnio
  zapisaną wartość. Plik edytowany bez zapisu w Excelu = wartości
  nieaktualne.
- Liczby ze skryptu są wiarygodniejsze niż „szacowanie" z czatu – ale
  nadal sprawdzamy jedną-dwie w źródle.

## Notatki własne

- Czy opis struktury zgadzał się z Excelem? Co pominął?
- Co Claude zauważył „podejrzanego" w eksporcie ERP bez podpowiedzi?
