# Zadanie 9: Gdy Claude Code się myli – obsługa błędów i cofanie

**Cel:** sprowokować sześć typowych błędów Claude Code i przećwiczyć
reakcje, które zawsze działają. Bez tego nie ma bezpiecznej pracy na
prawdziwych plikach.
**Poziom:** średni (ważne dla wszystkich)
**Czas:** ok. 30 minut
**Blok:** Dzień 1 — obsługa błędów i utrwalenie

## Pięć reakcji do zapamiętania

| Sytuacja | Reakcja |
|---|---|
| Claude robi coś, czego nie chcesz | **Esc** – przerywa natychmiast |
| Pyta o zgodę na coś niejasnego | **No**, potem: `Wyjaśnij, co dokładnie zamierzasz i po co.` |
| Zrobił za dużo / nie to | `Przywróć plik z ostatniej kopii w kopie.` |
| Podaje liczbę nie do zweryfikowania | `Pokaż, jak to policzyłeś i z których komórek.` |
| Rozmowa się zaplątała | `/clear` i pełne polecenie od nowa (P.K.Z.O.) |

## Materiały

- Folder roboczy po zadaniach 6–8 (albo świeże pliki z pendrive'a).
  Pliki zamknięte w Excelu – poza Sytuacją 2.

## Kroki

1. ```powershell
   cd C:\Szkolenie\dzien-1\praca
   claude
   ```

   ```
   Skopiuj wszystkie pliki xlsx i csv do kopie z datą i godziną.
   ```

### Sytuacja 1: Niejednoznaczne polecenie

2. Celowo nieprecyzyjnie:

   ```
   Popraw daty w eksport_erp_2026-09.csv.
   ```

   **Sprawdź:** spytał o format docelowy i o zgodę na nadpisanie
   oryginału? Jeśli wybrał sam i nadpisał – masz przykład, po co
   doprecyzowujemy format, plik docelowy i „nie nadpisuj oryginału".

3. ```
   Przywróć eksport_erp_2026-09.csv z ostatniej kopii w kopie.
   ```

### Sytuacja 2: Plik zablokowany

4. **Otwórz** `zestawienie_roczne_2026.xlsx` w Excelu. Poproś:

   ```
   Wpisz w Wykonanie!R1 tekst „test".
   ```

   **Sprawdź:** błąd `PermissionError`; Claude zwykle sam mówi, że plik
   jest otwarty. Zamknij Excel:

   ```
   Spróbuj ponownie.
   ```

   ```
   Usuń zawartość R1.
   ```

### Sytuacja 3: Zmiana w złym miejscu

5. ```
   W pliku rocznym wpisz 100000 do komórki wykonania za listopad
   dla ochrony zdrowia.
   ```

   **Sprawdź:** dział 851 = wiersz 9, listopad = kolumna N → **N9**.
   Trafił w wiersz 10 (dział 852)? To najczęstszy realny błąd: opis
   słowny → zły adres.

   ```
   Cofnij. Od teraz przed każdym wpisem pokaż adres komórki i poczekaj
   na zgodę.
   ```

   Wyczyść N9.

### Sytuacja 4: Zmyślona liczba

6. ```
   Ile wyniosło wykonanie działu 600 w lutym 2025?
   ```

   **Sprawdź:** takich danych **nie ma** (plik obejmuje 2026). Dobra
   odpowiedź: „nie ma w pliku". Jeśli podał liczbę:

   ```
   Z której komórki to wziąłeś?
   ```

   Tak wygląda halucynacja w praktyce (Blok A).

7. ```
   Jaki jest łączny plan roczny?
   ```

   **Sprawdź:** 157 500 000 zł (`Wykonanie!C14`). Potem:

   ```
   Pokaż skrypt, którym to policzyłeś.
   ```

   Nawyk: liczba bez źródła to nie liczba.

### Sytuacja 5: „Ulepszanie" bez pytania

8. ```
   Dodaj w szablonie miesięcznym wiersz z datą sporządzenia.
   ```

   ```
   Wypisz wszystkie zmiany, które wprowadziłeś w tym pliku w tej sesji.
   ```

   **Sprawdź:** zmienił coś ponad proszone (formatowanie, szerokości
   kolumn, nazwa arkusza)?

   ```
   Cofnij wszystko poza wierszem z datą.
   ```

### Sytuacja 6: Skrypt się wysypał

9. ```
   Uruchom proces2.py bez parametrów.
   ```

   **Sprawdź:** polski komunikat „brak parametru" = dobrze. Techniczny
   traceback (`IndexError`…):

   ```
   Wyjaśnij ten błąd po polsku jednym zdaniem i powiedz, co mam zrobić.
   ```

   Nie musisz czytać błędów – musisz umieć poprosić o tłumaczenie.

## Na co zwrócić uwagę

- **Kopia przed zmianą + „pokaż plan i czekaj"** eliminują 90 %
  problemów. Reszta to weryfikacja liczb w Excelu.
- Claude jest **pewny siebie także wtedy, gdy się myli.** Dowodem jest
  komórka w Excelu, nie ton odpowiedzi.
- Czerwony tekst w terminalu to informacja, nie „zepsułam komputer".
- Po kilku nieudanych próbach: `/clear` i pełne polecenie (plik, arkusz,
  komórki, format, czego nie ruszać). Szybsze niż poprawianie w kółko.

## Notatki własne

- Która z sześciu sytuacji zdarzyła się „naprawdę" w zadaniach 4–8?
- Jaką regułę dopiszesz do `CLAUDE.md` w zadaniu 10, żeby się nie
  powtórzyła?
