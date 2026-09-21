# Zadanie 5: Operacje na komórkach w języku naturalnym

**Cel:** odczyt, wpis, formuła, przeniesienie między arkuszami i plikami,
formatowanie – po polsku, bez formuł i makr. „Słownik" poleceń do zadań
6–7.
**Poziom:** średni
**Czas:** ok. 30 minut
**Blok:** Dzień 1 — praca na komórkach

## Materiały

- `zestawienie_roczne_2026.xlsx` (Plik 2) i `zestawienie_miesieczne_SZABLON.xlsx`
  (Plik 1). Oba **zamknięte** w Excelu.

## Kroki

1. ```powershell
   cd C:\Szkolenie\dzien-1\praca
   claude
   ```

   ```
   Skopiuj oba pliki xlsx do kopie z datą i godziną w nazwie.
   ```

### Część 1: Pojedyncze komórki

2. ```
   W zestawienie_roczne_2026.xlsx, arkusz Wykonanie: jaka wartość jest
   w komórce K8 i co ona oznacza (który dział, który miesiąc)?
   ```

   **Sprawdź:** 4 627 000 zł – dział 801, sierpień.

3. ```
   Wpisz do komórki L6 wartość 2150000 (to wykonanie działu 600
   za wrzesień). Nie zmieniaj niczego innego.
   ```

   **Sprawdź w Excelu:** P6 (Razem) i Q6 (% planu) przeliczyły się same?
   Zamknij plik.

4. ```
   Cofnij: wyczyść L6.
   ```

### Część 2: Formuły

5. ```
   W arkuszu Wykonanie dodaj w komórce R5 nagłówek „Średnia I–VIII",
   a w R6:R13 formułę liczącą średnią z kolumn D–K dla każdego wiersza.
   Format walutowy jak w kolumnie P.
   ```

6. **Sprawdź w Excelu:** kliknij R6 – ma być **formuła**
   (`=AVERAGE(D6:K6)` / `=ŚREDNIA(...)`), nie liczba. Jeśli liczba:

   ```
   Zamień na formułę, nie na wartość.
   ```

   Zamknij plik.

7. ```
   Czy w tym arkuszu są komórki z formułami, które zwracają błąd albo
   odwołują się do pustych zakresów?
   ```

### Część 3: Między arkuszami i plikami

8. ```
   Porównaj plan roczny w Wykonanie!C6:C13 z planem
   w zestawienie_miesieczne_SZABLON.xlsx, arkusz Zestawienie, C6:C13 –
   dopasowując po kodzie działu z kolumny A, nie po kolejności. Wypisz
   tabelę: dział, plan w rocznym, plan w szablonie, różnica. Jeśli czegoś
   brakuje w szablonie – uzupełnij z pliku rocznego.
   ```

   **Sprawdź:** Claude najpierw porównał kody działów, potem wartości;
   plany identyczne (to celowe – ćwiczymy nawyk „najpierw porównaj, potem
   przenoś", który w zadaniu 7 chroni przed przesunięciem o wiersz).

9. ```
   Wpisz w szablonie miesięcznym B2 = „wrzesień".
   ```

10. ```
    Przepisz z pliku rocznego do szablonu miesięcznego, kolumna E
    (Wykonanie narastająco), sumę miesięcy I–VIII dla każdego działu.
    ```

    **Sprawdź:** E6 = 15 207 000, E8 = 40 124 000, E14 = 101 984 000.
    (To ruch „z Pliku 2 do Pliku 1" – w zadaniu 7 właściwy kierunek.)

### Część 4: Formatowanie

11. ```
    W szablonie miesięcznym: kolumny C–E format "# ##0 zł" bez miejsc
    po przecinku, kolumna F procent z jednym miejscem, nagłówki
    pogrubione, szerokość kolumn dopasuj do treści.
    ```

12. ```
    Sprawdź, czy w obu plikach wszystkie daty są w formacie RRRR-MM-DD,
    a kwoty są liczbami, nie tekstem. Wypisz wyjątki.
    ```

## Na co zwrócić uwagę

- **Adresy komórek są najpewniejsze.** „Wpisz do L6" jest jednoznaczne;
  „wpisz wrzesień dla transportu" wymaga, żeby Claude znalazł wiersz
  i kolumnę – każ pokazać, gdzie wpisze.
- **Formuła kontra wartość** – zawsze mów, czego chcesz. W zestawieniach
  dla banku chcecie formuł.
- Excel po polsku pokazuje `=SUMA`, Claude zapisuje `=SUM` – to samo.
- Zapis przez Python może **zgubić** makra, niektóre wykresy, sprawdzanie
  poprawności. Kolejny powód na kopię.

## Notatki własne

- Które polecenie Claude wykonał inaczej, niż się spodziewałeś/aś?
- Które operacje z Procesu 1 / 2 dałoby się już zapisać jako listę takich
  poleceń?
