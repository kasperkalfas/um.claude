# Zadanie 10: CLAUDE.md z zasadami Wydziału i własna komenda „zamknij miesiąc"

**Cel:** zapisać zasady pracy w `CLAUDE.md` (czytany na starcie każdej
sesji), sprawdzić, że działają, i spiąć Proces 1 + Proces 2 + raport
kontrolny w jedną komendę `/zamknij-miesiac`.
**Poziom:** zaawansowany
**Czas:** ok. 40 minut
**Blok:** Dzień 1 — obsługa błędów i utrwalenie (lub praca własna)

## Dwa mechanizmy pamięci

| Mechanizm | Co to jest | Kiedy działa |
|---|---|---|
| `CLAUDE.md` w folderze | plik tekstowy z zasadami i kontekstem | automatycznie na starcie każdej sesji w tym folderze |
| `.claude/commands/nazwa.md` | zapisany prompt = własna komenda `/nazwa` | gdy wpiszesz `/nazwa`; `$ARGUMENTS` = to, co dopiszesz po nazwie |

Rozmowa znika po `/exit`. **Pliki zostają.**

## Materiały

- Folder roboczy po zadaniach 6–9: `przepis_proces1.md`, `proces2.py`,
  szablon, plik roczny, eksporty, `kopie/`.

## Kroki

1. ```powershell
   cd C:\Szkolenie\dzien-1\praca
   claude
   ```

### Część 1: CLAUDE.md

2. ```
   /init
   ```

   Claude przejrzy folder i zaproponuje `CLAUDE.md`. Zaakceptuj, potem:

   ```
   Przepisz CLAUDE.md po polsku i dodaj sekcję „Zasady Wydziału"
   z punktami:
   - wszystkie dane w tym folderze są fikcyjne; nigdy nie proś
     o prawdziwe dane Urzędu;
   - przed każdą zmianą pliku xlsx/csv zrób kopię do kopie/ z datą
     i godziną;
   - przed zmianą pokaż plan (plik, arkusz, komórki) i czekaj na zgodę;
   - nie nadpisuj komórek, które mają dane – zatrzymaj się i zapytaj;
   - kwoty jako liczby (nie tekst), format PLN z separatorem tysięcy,
     daty RRRR-MM-DD;
   - dopasowuj wiersze po kodzie działu (kolumna A), nigdy po kolejności;
   - duplikaty dokumentów (ten sam nr) zgłaszaj, nie usuwaj bez pytania;
   - liczby w odpowiedziach zawsze ze wskazaniem komórki/źródła;
   - odpowiadaj po polsku.
   Dodaj też sekcję „Pliki" z opisem, czym jest szablon miesięczny, plik
   roczny, eksport ERP, proces2.py i przepis_proces1.md.
   ```

3. **Sprawdź:** otwórz `CLAUDE.md` w Notatniku. Ma być zrozumiały dla
   koleżanki z wydziału, nie tylko dla Claude.

### Część 2: Czy zasady działają?

4. ```
   /exit
   ```

   ```powershell
   claude
   ```

   Nowa sesja – Claude czyta `CLAUDE.md`.

5. ```
   Wpisz 5 do Wykonanie!D6 w pliku rocznym.
   ```

   **Sprawdź:** D6 ma dane (styczeń, dział 600). Claude powinien **zrobić
   kopię, pokazać plan i odmówić nadpisania bez pytania**. Jeśli po prostu
   wpisał – zasada za słaba; dopisz w `CLAUDE.md` „to zasada bezwzględna"
   i powtórz test. Przywróć D6 (= 1 711 000).

### Część 3: Własna komenda

6. ```
   Utwórz plik .claude/commands/zamknij-miesiac.md z instrukcją, która
   dla miesiąca podanego w $ARGUMENTS (np. październik) wykonuje
   po kolei:
   1. znajdź eksport_erp_RRRR-MM.csv dla tego miesiąca – jeśli go nie ma,
      zatrzymaj się;
   2. wykonaj przepis_proces1.md → nowy plik
      zestawienie_miesieczne_RRRR-MM.xlsx;
   3. uruchom proces2.py <miesiąc> <plik miesięczny>;
   4. wygeneruj kontrola_RRRR-MM.md jak w zadaniu 8;
   5. na końcu wypisz podsumowanie: co powstało, wyniki kontroli,
      co wymaga decyzji człowieka (duplikaty, braki).
   Przed każdym krokiem zmieniającym pliki – plan i zgoda, zgodnie
   z CLAUDE.md.
   ```

7. **Sprawdź:** przeczytaj utworzony plik – to zwykły tekst, jak Twoje
   polecenia z tego szkolenia, tylko zapisany.

### Część 4: Zamknięcie miesiąca jednym poleceniem

8. **Czysty test:** przywróć plik roczny z kopii sprzed zadania 8
   (wrzesień wpisany, październik pusty) albo skopiuj z pendrive'a
   i wykonaj `proces2.py wrzesień`. Usuń `zestawienie_miesieczne_2026-10.xlsx`
   i `kontrola_2026-10.md`, jeśli istnieją.

9. ```
   /zamknij-miesiac październik
   ```

   Zatwierdzaj kroki, czytając plany.

   **Sprawdź z kluczem:** `Wykonanie!M14` = 13 240 000 zł, kontrola OK,
   `kontrola_2026-10.md` istnieje.

10. **Test bezpiecznika:**

    ```
    /zamknij-miesiac listopad
    ```

    **Sprawdź:** eksportu za listopad nie ma → komenda zatrzymuje się na
    kroku 1 z jasnym komunikatem, **nic nie zmieniając**.

### Część 5: Przekazanie

11. ```
    Napisz INSTRUKCJA.md dla osoby, która pierwszy raz otwiera ten folder:
    co tu jest, jak uruchomić Claude Code, jak zamknąć miesiąc jedną
    komendą, co sprawdzić ręcznie po zakończeniu, czego nigdy nie robić
    (prawdziwe dane, praca bez kopii). Maks. 1 strona, po polsku.
    ```

12. To Wasz „produkt" z Dnia 1: folder z przepisem, skryptem, zasadami
    i instrukcją – do pokazania IT i adaptacji na prawdziwy proces (po
    ustaleniu zasad bezpieczeństwa danych).

## Na co zwrócić uwagę

- **`CLAUDE.md` to silna sugestia, nie gwarancja.** Przy prawdziwych
  danych bezpieczniki muszą być też w skrypcie – skrypt nie „zapomina".
- Własna komenda to zapisany prompt. Gdy proces się zmieni, edytujesz
  tekst w Notatniku – bez programisty.
- Przeniesienie na prawdziwy proces wymaga: pisemnej zgody na dane Urzędu
  w Claude, ustaleń z IT (folder, dostęp, kopie) i jednej osoby
  odpowiedzialnej za raport kontrolny co miesiąc.

## Notatki własne

- Czy test z Części 2 przeszedł za pierwszym razem?
- Co dopiszesz do `CLAUDE.md` po zadaniach 4–9?
- Kto w Wydziale byłby właścicielem komendy `/zamknij-miesiac` i raportu
  kontrolnego?
