# Zadanie 3: „Otwórz ten Excel i powiedz, co w nim jest"

**Cel:** nauczyć Claude Code czytać Wasze pliki: opisać strukturę arkusza
(arkusze, kolumny, wiersze, formuły), odpowiedzieć na pytania o liczby i
porównać dwa pliki – bez ręcznego otwierania i przewijania.
**Poziom:** podstawowy
**Czas:** ok. 20 minut
**Blok:** Dzień 1 — wprowadzenie (pierwszy kontakt: `../claude-code/`)

## Materiały

W folderze roboczym `C:\Szkolenie\dzien-1\praca\`:

- `zestawienie_roczne_2026.xlsx` – fikcyjny odpowiednik Waszego **Pliku 2**
  (zestawienie roczne): arkusz `Wykonanie` (8 działów × 12 miesięcy, plan,
  formuły Razem i % planu; wypełnione miesiące I–VIII) i arkusz `Prognoza`
  (prognoza roczna dla banku – same formuły).
- `zestawienie_miesieczne_SZABLON.xlsx` – fikcyjny odpowiednik **Pliku 1**
  (zestawienie miesięczne): plan roczny wpisany, kolumny wykonania puste.
- `eksport_erp_2026-09.csv` – fikcyjny eksport z ERP za wrzesień.

## Kroki

1. `cd C:\Szkolenie\dzien-1\praca`, `claude`.

### Część 1: Struktura

2. *„Otwórz `zestawienie_roczne_2026.xlsx` i opisz, co w nim jest: jakie
   arkusze, jakie kolumny, ile wierszy danych, które komórki zawierają
   formuły, a które wpisane liczby. Nic nie zmieniaj."*
3. Sprawdź odpowiedź z tym, co widzisz w Excelu (otwórz plik równolegle –
   do czytania Claude nie przeszkadza otwarty plik). Czy rozpoznał, że
   miesiące IX–XII są puste? Że `Prognoza` odwołuje się do `Wykonanie`?
4. *„Ile miesięcy ma dane? Skąd to wiesz?"* – dobra odpowiedź wskazuje
   komórkę `Prognoza!B2` **i** puste kolumny L–O w `Wykonanie`.

### Część 2: Pytania o liczby

5. *„Który dział ma najwyższe wykonanie narastająco po sierpniu, a który
   najniższy procent planu? Podaj kwoty."*
6. *„Podaj wykonanie działu 801 w każdym miesiącu jako listę i policz
   średnią miesięczną."*
7. Zweryfikuj jedną liczbę w Excelu. Zasada z Dnia 1 obowiązuje: to Wy
   odpowiadacie za liczby.

### Część 3: Porównanie dwóch plików

8. *„Porównaj strukturę `zestawienie_miesieczne_SZABLON.xlsx` z arkuszem
   `Wykonanie` w pliku rocznym: które kolumny odpowiadają sobie nawzajem,
   a czego brakuje w szablonie miesięcznym?"*
   To przygotowanie do zadania 7 – Claude powinien zauważyć, że działy są
   w tej samej kolejności (wiersze 6–13), a „Wykonanie w miesiącu" z
   szablonu odpowiada jednej kolumnie miesiąca w pliku rocznym.
9. *„Otwórz `eksport_erp_2026-09.csv` i powiedz, jakie ma kolumny, ile
   wierszy i czy widzisz coś podejrzanego w danych."*
   Nie poprawiaj jeszcze niczego – do tego wrócimy w zadaniu 6. Zanotuj,
   co Claude zauważył sam (różne formaty dat i kwot? powtórzony
   dokument? brak paragrafu?).

## Na co zwrócić uwagę

- Claude Code czyta Excel przez krótki skrypt w Pythonie (zobaczysz go w
  terminalu przed pytaniem o zgodę). Nie musisz go rozumieć – ale możesz
  zawsze zapytać: *„Wyjaśnij po polsku, co robi ten skrypt, zanim go
  uruchomisz."*
- **Formuły a wartości:** Claude widzi formułę (`=SUM(D6:O6)`) i osobno
  jej ostatnio zapisaną wartość. Jeśli plik był edytowany bez zapisu w
  Excelu, wartości mogą być nieaktualne – dopytaj, na czym bazuje.
- Na pytania o liczby Claude odpowiada na podstawie tego, co policzył
  skryptem – to bardziej wiarygodne niż „szacowanie" z czatu, ale nadal
  sprawdzamy jedną-dwie liczby w źródle.

## Notatki własne

- Czy opis struktury zgadzał się z tym, co widzisz w Excelu? Co pominął?
- Co Claude zauważył „podejrzanego" w eksporcie ERP bez podpowiedzi?
