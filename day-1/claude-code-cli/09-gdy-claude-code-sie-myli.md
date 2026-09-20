# Zadanie 9: Gdy Claude Code się myli – obsługa błędów i cofanie

**Cel:** przejść przez najczęstsze sytuacje, w których Claude Code robi
coś nie tak – niejednoznaczne polecenie, zablokowany plik, zmiana w złym
miejscu, zmyślona liczba, „ulepszanie" bez pytania – i nauczyć się pięciu
reakcji, które zawsze działają. Bez tego zadania nie ma bezpiecznej pracy
na prawdziwych plikach.
**Poziom:** średni (ważne dla wszystkich)
**Czas:** ok. 30 minut
**Blok:** Dzień 1 — obsługa błędów i utrwalenie

## Pięć reakcji, które warto mieć w palcach

| Sytuacja | Reakcja |
|---|---|
| Claude zaczyna robić coś, czego nie chcesz | **Esc** – przerywa natychmiast |
| Pyta o zgodę na coś niejasnego | **No**, potem: *„wyjaśnij, co dokładnie zamierzasz i po co"* |
| Zrobił za dużo / nie to | *„Cofnij – przywróć plik z ostatniej kopii w `kopie`"* |
| Podaje liczbę, której nie możesz zweryfikować | *„Pokaż, jak to policzyłeś, i z których komórek"* |
| Rozmowa zaplątała się | `/clear` i zacznij od jasnego, pełnego polecenia (P.K.Z.O.) |

## Materiały

- Pliki z folderu roboczego po zadaniach 6–8 (albo świeże z pendrive'a).
  Wszystkie zamknięte w Excelu – z wyjątkiem kroku 4.

## Kroki

1. `cd C:\Szkolenie\dzien-1\praca`, `claude`. Kopie do `kopie`.

### Sytuacja 1: Niejednoznaczne polecenie

2. Celowo nieprecyzyjnie: *„Popraw daty w `eksport_erp_2026-09.csv`."*
   Obserwuj: Claude wybierze **jakiś** format i być może **nadpisze**
   oryginał. Jeśli spyta o format i o zgodę na nadpisanie – dobrze. Jeśli
   nie – masz przykład, dlaczego doprecyzowujemy: format docelowy, plik
   docelowy, „nie nadpisuj oryginału".
3. Przywróć: *„Przywróć `eksport_erp_2026-09.csv` z ostatniej kopii w
   `kopie`."*

### Sytuacja 2: Plik zablokowany

4. **Otwórz** `zestawienie_roczne_2026.xlsx` w Excelu. Poproś:
   *„Wpisz w `Wykonanie!R1` tekst »test«."* Zobaczysz błąd zapisu
   (`PermissionError`). Claude zwykle sam mówi, że plik jest otwarty.
   Zamknij Excel, *„spróbuj ponownie"*, potem *„usuń R1"*.

### Sytuacja 3: Zmiana w złym miejscu

5. *„W pliku rocznym wpisz 100 000 do komórki wykonania za listopad dla
   ochrony zdrowia."* Sprawdź: dział 851 to wiersz 9, listopad to
   kolumna N – czy trafił w **N9**? Jeśli trafił gdzie indziej (np.
   w wiersz 10 – to dział 852), to najczęstszy realny błąd: opis słowny
   → zły adres. Reakcja: *„Cofnij i od teraz przed każdym wpisem pokaż
   adres komórki i poczekaj na zgodę."* Wyczyść N9.

### Sytuacja 4: Zmyślona liczba

6. *„Ile wyniosło wykonanie działu 600 w lutym 2025?"* – **takich danych
   nie ma** (plik obejmuje 2026). Dobra odpowiedź: „nie ma w pliku".
   Zła: podanie liczby. Jeśli poda – *„Z której komórki to wziąłeś?"* –
   i zobaczysz, jak wygląda halucynacja w praktyce (Blok A, Dzień 1).
7. *„Jaki jest łączny plan roczny?"* Sprawdź z C14 w Excelu. Potem:
   *„Pokaż skrypt, którym to policzyłeś."* – nawyk: liczba bez źródła to
   nie liczba.

### Sytuacja 5: „Ulepszanie" bez pytania

8. *„Dodaj w szablonie miesięcznym wiersz z datą sporządzenia."* Obserwuj,
   czy Claude przy okazji nie zmienił czegoś więcej (formatowanie,
   szerokości kolumn, nazwy arkusza). Poproś: *„Wypisz wszystkie zmiany,
   które wprowadziłeś w tym pliku w tej sesji."* Jeśli jest coś ponad
   proszone – *„Cofnij wszystko poza wierszem z datą"*.

### Sytuacja 6: Skrypt się wysypał

9. *„Uruchom `proces2.py` bez parametrów."* Zobaczysz komunikat
   (brak parametru). Jeśli skrypt ma własną, polską obsługę błędu –
   dobrze, tak ma być. Jeśli zobaczysz techniczny, angielski traceback
   (np. `IndexError`), reakcja: *„Wyjaśnij ten błąd po polsku jednym
   zdaniem i powiedz, co mam zrobić."* Nie musisz czytać błędów – musisz
   umieć poprosić o ich przetłumaczenie.

## Na co zwrócić uwagę

- **Kopia przed zmianą + „pokaż plan i czekaj"** eliminują 90%
  problemów. Reszta to weryfikacja liczb w Excelu.
- Claude Code jest **pewny siebie także wtedy, gdy się myli** – tak samo
  jak czat. Ton odpowiedzi nie jest dowodem poprawności; dowodem jest
  komórka w Excelu.
- Błąd techniczny (czerwony tekst w terminalu) to nie „zepsułam
  komputer" – to informacja. Zawsze da się ją przetłumaczyć na polski
  jednym pytaniem.
- Jeśli po kilku próbach nie wychodzi: `/clear`, świeże polecenie w
  formule P.K.Z.O. z pełnym kontekstem (plik, arkusz, komórki, format,
  czego nie ruszać). To szybsze niż poprawianie w kółko.

## Notatki własne

- Która z sześciu sytuacji zdarzyła się „naprawdę", bez prowokowania,
  w zadaniach 4–8?
- Jaką regułę dopiszesz do `CLAUDE.md` w zadaniu 10, żeby ta sytuacja się
  nie powtórzyła?
