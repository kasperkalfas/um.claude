# Zadanie 4: Błędy na poziomie komórek – znajdź i napraw

**Cel:** Claude Code wskazuje błędy z dokładnością do komórki (nie „gdzieś
są scalone komórki", tylko „B10:B11"), a po zrobieniu kopii – naprawia je
na wyraźne polecenie.
**Poziom:** podstawowy → średni
**Czas:** ok. 30 minut
**Blok:** Dzień 1 — praca na komórkach

## Materiały

- `zestawienie_bledy.xlsx` – zestawienie za sierpień z **8 celowymi
  błędami** (klucz w [README](README.md#klucz-odpowiedzi)).
- Plik **zamknięty** w Excelu – otwarty jest zablokowany do zapisu.

## Kroki

1. ```powershell
   cd C:\Szkolenie\dzien-1\praca
   claude
   ```

### Część 1: Diagnoza

2. ```
   Sprawdź zestawienie_bledy.xlsx pod kątem: scalonych komórek, kwot
   zapisanych jako tekst, pustych wierszy w środku danych, brakujących
   nagłówków, ukrytych kolumn lub wierszy, niespójnych formatów dat,
   formuł zwracających błąd oraz brakujących wartości. Wypisz każdy
   problem z adresem komórki lub zakresu. Nic nie zmieniaj.
   ```

3. **Sprawdź z kluczem** – ile z 8 znalazł?

   - [ ] brak nagłówka `F5`
   - [ ] pusty wiersz 9
   - [ ] `D7` kwota jako tekst
   - [ ] scalone `B10:B11` (dział 852 bez nazwy)
   - [ ] `C13` brak planu → `F13` = `#DIV/0!`
   - [ ] kolumna `E` ukryta
   - [ ] daty `A17` vs `A18` w dwóch formatach
   - [ ] sumy `D15` / `C15` błędne (skutek 3 i 5)

4. Dopytaj o pominięte **bez podpowiadania adresu**:

   ```
   Czy suma w wierszu Razem (D15) uwzględnia wszystkie działy? Dlaczego?
   ```

   **Sprawdź:** dobra odpowiedź – nie, bo D7 jest tekstem i `SUM` ją
   pomija.

### Część 2: Kopia, potem naprawa

5. ```
   Zanim cokolwiek zmienisz: skopiuj plik do podfolderu kopie z dopiskiem
   daty i godziny w nazwie.
   ```

   **Sprawdź w Eksploratorze:** kopia istnieje. **To nawyk na całe
   szkolenie.**

6. Naprawiaj po jednym, żeby widzieć każdy krok:

   ```
   Rozdziel scalone komórki B10:B11 i uzupełnij brakującą nazwę
   działu 852 – to „Pomoc społeczna".
   ```

   ```
   Zamień tekst w D7 na liczbę, zachowaj format walutowy jak w D6.
   ```

   ```
   Usuń pusty wiersz 9 i przesuń dane w górę. Uwaga: formuły w kolumnie F
   i w wierszu Razem muszą po tym nadal wskazywać właściwe wiersze.
   ```

   ```
   Odkryj kolumnę E.
   ```

   ```
   Wpisz brakujący nagłówek w F5: „% wykonania planu".
   ```

   ```
   Uzupełnij plan działu 921 w kolumnie C – plan roczny to 7 400 000 zł –
   i sprawdź, czy formuła % w tym wierszu przestała zwracać błąd.
   ```

   ```
   Ujednolić daty w komórkach „Sporządzono" i „Zatwierdzono" do formatu
   RRRR-MM-DD.
   ```

7. ```
   Wypisz jeszcze raz pełną listę kontrolną z kroku 2 – czy coś zostało?
   ```

8. **Sprawdź w Excelu:** `Razem` w D wzrosło o kwotę z D7? `#DIV/0!`
   zniknął?

### Część 3: Jedna komenda zamiast siedmiu

9. Skopiuj **oryginalny** plik (z pendrive'a lub `kopie`) jako
   `zestawienie_bledy_2.xlsx` i poproś:

   ```
   Zrób kopię do kopie, a potem napraw w zestawienie_bledy_2.xlsx
   wszystkie problemy z listy z kroku 2. Po naprawie wypisz tabelę:
   co było, gdzie, co zrobiłeś.
   ```

10. **Sprawdź:** porównaj oba naprawione pliki. Gdzie Claude „domyślił
    się" inaczej niż Ty w Części 2 (format daty, nazwa działu)? Dlatego
    przy zbiorczej naprawie oczekiwania podajemy z góry.

## Na co zwrócić uwagę

- **Plik otwarty w Excelu = `PermissionError`.** Zamknij plik i poproś:

  ```
  Spróbuj ponownie.
  ```

- **Kopia w `kopie/` to Wasze „cofnij".** Claude Code nie ma cofania dla
  plików binarnych.
- Usunięcie pustego wiersza to najbardziej ryzykowna operacja (przesuwa
  wiersze, formuły muszą nadążyć). Po niej **zawsze** sprawdzamy sumy.
- Claude może „ulepszać" bez pytania (np. przeformatować cały arkusz).
  Odmawiaj (**No**) i pisz:

  ```
  Tylko to, o co prosiłem.
  ```

## Notatki własne

- Ile z 8 błędów Claude znalazł za pierwszym razem?
- Który błąd byłby najtrudniejszy do zauważenia ręcznie w prawdziwym
  zestawieniu?
