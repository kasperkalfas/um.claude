# Zadanie 7: Proces 2 – powtarzalny „przepis" z miesięcznego do rocznego

**Cel:** przenieść wykonanie z Pliku 1 do właściwej kolumny Pliku 2 raz
ręcznie, a potem zamienić to w skrypt `proces2.py` z wbudowaną kontrolą
sum i bezpiecznikami – uruchamiany co miesiąc.
**Poziom:** średni → zaawansowany
**Czas:** ok. 40 minut
**Blok:** Dzień 1 — automatyzacja procesu

## Materiały

- `zestawienie_miesieczne_SZABLON.xlsx` z zadania 6 (wrzesień, D6:D13
  wypełnione).
- `zestawienie_roczne_2026.xlsx` – I–VIII wypełnione, IX (kolumna L)
  pusta; `Prognoza!B2` = 8.
- Klucz – [README](README.md#klucz-odpowiedzi).

## Kroki

1. ```powershell
   cd C:\Szkolenie\dzien-1\praca
   claude
   ```

   ```
   Skopiuj oba pliki xlsx do kopie z datą i godziną.
   ```

### Część 1: Raz ręcznie – żeby wiedzieć, co ma robić skrypt

2. ```
   Przenieś wartości z zestawienie_miesieczne_SZABLON.xlsx,
   Zestawienie!D6:D13 do zestawienie_roczne_2026.xlsx, arkusz Wykonanie,
   kolumna miesiąca wrzesień (L6:L13). Dopasuj po kodzie działu
   w kolumnie A obu plików. Zanim zapiszesz, pokaż tabelę: dział,
   wartość źródłowa, komórka docelowa.
   ```

3. ```
   W arkuszu Prognoza zmień B2 z 8 na 9.
   ```

4. ```
   Uzupełnij w szablonie miesięcznym kolumnę E (Wykonanie narastająco)
   sumą miesięcy I–IX z pliku rocznego dla każdego działu.
   ```

5. **Sprawdź w Excelu:**

   - [ ] `Wykonanie!L14` = 13 230 000 zł
   - [ ] `Prognoza` przeliczona (średnia = narastająco ÷ 9)
   - [ ] szablon, dział 600: E6 = 17 357 000, F6 = 72,3 %

   Zamknij pliki.

### Część 2: Zamień to w skrypt

6. Wróć do czystego stanu:

   ```
   Cofnij zmiany z Części 1: wyczyść Wykonanie!L6:L13, ustaw
   Prognoza!B2 = 8, wyczyść E6:E13 w szablonie.
   ```

   (Albo przywróć oba pliki z `kopie`.)

7. ```
   Napisz skrypt proces2.py, który przyjmuje jako parametr nazwę miesiąca
   po polsku (np. wrzesień) i:
   1) robi kopie obu plików do kopie z datą i godziną,
   2) czyta D6:D13 z szablonu miesięcznego,
   3) wpisuje je do właściwej kolumny miesiąca w Wykonanie (wrzesień = L,
      październik = M itd.), dopasowując po kodzie działu,
   4) ustawia Prognoza!B2 na numer miesiąca,
   5) uzupełnia E6:E13 w szablonie sumą miesięcy od stycznia do tego
      miesiąca,
   6) na końcu wypisuje kontrolę: suma D w szablonie, suma wpisanej
      kolumny w rocznym, i OK/BŁĄD, jeśli się różnią.
   Nie nadpisuj kolumny, która już ma dane – zatrzymaj się i zapytaj.
   Wyjaśnij mi po polsku, co robi każdy fragment.
   ```

8. Przeczytaj wyjaśnienie. Nie musisz rozumieć Pythona – musisz rozumieć
   **kroki** i **warunki zatrzymania**.

9. ```
   Uruchom proces2.py wrzesień
   ```

   **Sprawdź:** to samo co w kroku 5 + w terminalu kontrola **OK**.

### Część 3: Test odporności

10. ```
    Uruchom jeszcze raz proces2.py wrzesień
    ```

    **Sprawdź:** kolumna L ma dane → skrypt **odmawia** i pyta. Jeśli
    nadpisał:

    ```
    Popraw: przed zapisem sprawdzaj, czy kolumna docelowa jest pusta.
    ```

11. ```
    Uruchom proces2.py grudzień
    ```

    **Sprawdź:** szablon ma dane września (B2 = „wrzesień") → skrypt
    powinien to wyłapać. Jeśli nie:

    ```
    Dodaj kontrolę: nazwa miesiąca w parametrze musi zgadzać się z B2
    w szablonie.
    ```

12. Przywróć stan z kroku 9 (wrzesień wpisany, grudzień pusty).

## Na co zwrócić uwagę

- **Najpierw raz ręcznie, potem skrypt.** Dopóki nie wiesz dokładnie,
  które komórki dokąd idą, nie opiszesz tego Claude'owi ani nie sprawdzisz
  skryptu.
- **Kontrola sum to sedno, nie dodatek.** Ręczne przepisywanie nie ma
  wbudowanej kontroli – skrypt ma.
- Bezpieczniki „zatrzymaj się i zapytaj" wymyślcie własne: suma
  w szablonie = 0, brak działu, plik otwarty w Excelu.
- Skrypt to plik w folderze – można go pokazać IT, zarchiwizować,
  poprosić o zmianę za miesiąc.

## Notatki własne

- Czy kontrola sum wypisała OK za pierwszym razem?
- Który bezpiecznik zadziałał od razu, a który trzeba było dopisać?
- Jakie warunki zatrzymania dodałbyś/dodałabyś dla prawdziwego Pliku 2?
