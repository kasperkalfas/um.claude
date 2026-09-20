# Zadanie 10: CLAUDE.md z zasadami Wydziału i własna komenda „zamknij miesiąc"

**Cel:** zapisać na stałe zasady pracy (dane fikcyjne, kopie, „pokaż
plan", formaty) w pliku `CLAUDE.md`, który Claude Code czyta przy każdym
uruchomieniu w tym folderze – a potem spiąć Proces 1, Proces 2 i raport
kontrolny w jedną własną komendę `/zamknij-miesiac`. Efekt: zamknięcie
miesiąca jednym poleceniem, z wbudowanymi bezpiecznikami.
**Poziom:** zaawansowany
**Czas:** ok. 40 minut
**Blok:** Dzień 1 — obsługa błędów i utrwalenie (lub praca własna)

## Dwa mechanizmy pamięci Claude Code

| Mechanizm | Co to jest | Kiedy działa |
|---|---|---|
| `CLAUDE.md` w folderze | plik tekstowy z zasadami i kontekstem | czytany automatycznie na starcie każdej sesji w tym folderze |
| `.claude/commands/nazwa.md` | zapisany prompt = własna komenda `/nazwa` | gdy wpiszesz `/nazwa`; `$ARGUMENTS` to to, co dopiszesz po nazwie |

Rozmowa znika po `/exit`. **Pliki zostają** – dlatego wszystko, co ma
działać za miesiąc, wpisujemy do plików.

## Materiały

- Folder roboczy po zadaniach 6–9: `przepis_proces1.md`, `proces2.py`,
  szablon, plik roczny, eksporty, `kopie/`.

## Kroki

1. `cd C:\Szkolenie\dzien-1\praca`, `claude`.

### Część 1: CLAUDE.md

2. Wpisz `/init`. Claude przejrzy folder i zaproponuje `CLAUDE.md`.
   Zaakceptuj, potem: *„Przepisz `CLAUDE.md` po polsku i dodaj sekcję
   »Zasady Wydziału« z punktami:*
   - *wszystkie dane w tym folderze są fikcyjne; nigdy nie proś o
     prawdziwe dane Urzędu;*
   - *przed każdą zmianą pliku xlsx/csv zrób kopię do `kopie/` z datą i
     godziną;*
   - *przed zmianą pokaż plan (plik, arkusz, komórki) i czekaj na zgodę;*
   - *nie nadpisuj komórek, które mają dane – zatrzymaj się i zapytaj;*
   - *kwoty jako liczby (nie tekst), format PLN z separatorem tysięcy,
     daty RRRR-MM-DD;*
   - *dopasowuj wiersze po kodzie działu (kolumna A), nigdy po kolejności;*
   - *duplikaty dokumentów (ten sam nr) zgłaszaj, nie usuwaj bez pytania;*
   - *liczby w odpowiedziach zawsze ze wskazaniem komórki/źródła;*
   - *odpowiadaj po polsku.*
   *Dodaj też sekcję »Pliki« z opisem, czym jest szablon miesięczny, plik
   roczny, eksport ERP, `proces2.py` i `przepis_proces1.md`."*
3. Otwórz `CLAUDE.md` w Notatniku i przeczytaj. To dokument dla Was tak
   samo jak dla Claude – ma być zrozumiały dla koleżanki z wydziału.

### Część 2: Test, czy zasady działają

4. `/exit`, potem `claude` (nowa sesja – Claude czyta `CLAUDE.md`).
5. *„Wpisz 5 do `Wykonanie!D6` w pliku rocznym."* – D6 ma dane (styczeń,
   dział 600). Zgodnie z zasadami Claude powinien **zrobić kopię, pokazać
   plan i odmówić nadpisania bez pytania**. Jeśli po prostu wpisał –
   zasada jest za słabo sformułowana; popraw ją w `CLAUDE.md` (np. „to
   zasada bezwzględna") i powtórz test. Wyczyść / przywróć D6.

### Część 3: Własna komenda

6. *„Utwórz plik `.claude/commands/zamknij-miesiac.md` z instrukcją, która
   dla miesiąca podanego w `$ARGUMENTS` (np. `październik`) wykonuje po
   kolei:*
   1. *znajdź `eksport_erp_RRRR-MM.csv` dla tego miesiąca – jeśli go nie
      ma, zatrzymaj się;*
   2. *wykonaj `przepis_proces1.md` → nowy plik
      `zestawienie_miesieczne_RRRR-MM.xlsx`;*
   3. *uruchom `proces2.py <miesiąc> <plik miesięczny>`;*
   4. *wygeneruj `kontrola_RRRR-MM.md` jak w zadaniu 8;*
   5. *na końcu wypisz podsumowanie: co powstało, wyniki kontroli, co
      wymaga decyzji człowieka (duplikaty, braki).*
   *Przed każdym krokiem zmieniającym pliki – plan i zgoda, zgodnie z
   `CLAUDE.md`."*
7. Przeczytaj utworzony plik – to zwykły tekst, taki sam jak Twoje
   polecenia w tym szkoleniu, tylko zapisany.

### Część 4: Zamknięcie miesiąca jednym poleceniem

8. Przygotuj czysty test: przywróć plik roczny z kopii sprzed zadania 8
   (wrzesień wpisany, październik pusty) albo skopiuj z pendrive'a i
   wykonaj zad. 7 dla września. Usuń `zestawienie_miesieczne_2026-10.xlsx`
   i `kontrola_2026-10.md`, jeśli istnieją.
9. Wpisz: `/zamknij-miesiac październik`. Zatwierdzaj kolejne kroki,
   czytając plany. Na końcu porównaj z kluczem odpowiedzi: `M14` =
   13 240 000 zł, kontrola OK, raport wygenerowany.
10. Test bezpiecznika: `/zamknij-miesiac listopad` – eksportu za listopad
    nie ma. Komenda powinna zatrzymać się na kroku 1 z jasnym
    komunikatem, nic nie zmieniając.

### Część 5: Przekazanie

11. *„Napisz `INSTRUKCJA.md` dla osoby, która pierwszy raz otwiera ten
    folder: co tu jest, jak uruchomić Claude Code, jak zamknąć miesiąc
    jedną komendą, co sprawdzić ręcznie po zakończeniu, czego nigdy nie
    robić (prawdziwe dane, praca bez kopii). Maks. 1 strona, po polsku."*
12. To jest Wasz „produkt" z Dnia 1: folder z przepisem, skryptem,
    zasadami i instrukcją – gotowy do pokazania IT i do adaptacji na
    prawdziwy proces (po ustaleniu zasad bezpieczeństwa danych).

## Na co zwrócić uwagę

- **`CLAUDE.md` to nie gwarancja, to silna sugestia.** Claude zwykle się
  go trzyma, ale przy prawdziwych danych bezpieczniki muszą być też w
  skrypcie (jak w `proces2.py`) – skrypt nie „zapomina".
- Własna komenda to zapisany prompt, nie program. Gdy proces się zmieni
  (nowy dział, inna kolumna), edytujesz tekst w Notatniku – nie
  potrzebujesz programisty.
- Przeniesienie tego na prawdziwy proces wymaga trzech rzeczy poza
  techniką: pisemnej zgody na pracę z danymi Urzędu w Claude, ustaleń z
  IT (gdzie leży folder, kto ma dostęp, kopie zapasowe) i jednej osoby
  odpowiedzialnej za sprawdzanie raportu kontrolnego co miesiąc.
- Wszystko, co powstało w Dniu 1, jest w zwykłych plikach tekstowych i
  jednym skrypcie – da się to przeczytać, zarchiwizować i przekazać.

## Notatki własne

- Czy test z Części 2 przeszedł za pierwszym razem?
- Co dopisałbyś/dopisałabyś do `CLAUDE.md` po doświadczeniach z zadań
  4–9?
- Kto w Wydziale byłby „właścicielem" komendy `/zamknij-miesiac` i
  raportu kontrolnego?
