# Zadanie 2: Nawigacja po folderach w języku naturalnym

**Cel:** policzyć, znaleźć i uporządkować pliki poleceniem słownym –
na celowo zabałaganionym folderze.
**Poziom:** podstawowy
**Czas:** ok. 20 minut
**Blok:** Dzień 1 — wprowadzenie

## Materiały

- `01_sandbox/` w folderze roboczym – 17 plików udających folder
  „Zestawienia" po kilku miesiącach: pliki z 2025 i 2026, duplikaty
  („Kopia…", „(1)", „poprawione"), trzy wersje notatki dla banku, TODO,
  eksport z ERP.

## Kroki

1. W terminalu:

   ```powershell
   cd C:\Szkolenie\dzien-1\praca\01_sandbox
   claude
   ```

### Część 1: Tylko czytanie

2. ```
   Wypisz wszystkie pliki w tym folderze w tabeli: nazwa, typ, rozmiar,
   data modyfikacji. Posortuj po nazwie.
   ```

3. ```
   Ile jest plików Excel, ile tekstowych, ile CSV?
   ```

   **Sprawdź:** 12 xlsx, 4 txt, 1 csv.

4. ```
   Które pliki wyglądają na duplikaty albo różne wersje tego samego
   dokumentu? Wypisz je w grupach i uzasadnij.
   ```

   **Sprawdź:** trzy grupy – marzec 2026 (3 pliki), kwiecień 2026
   (2 pliki), notatka dla banku (3 wersje).

5. ```
   Które z tych plików dotyczą roku 2025, sądząc po nazwie?
   ```

   **Sprawdź:** 3 pliki (`zestawienie_2025_10/11/12.xlsx`).

### Część 2: Porządkowanie (Claude zmienia folder)

6. ```
   Utwórz podfolder archiwum_2025 i przenieś do niego wszystkie pliki
   z 2025 roku. Najpierw pokaż listę plików do przeniesienia i poczekaj
   na moją zgodę.
   ```

   **Sprawdź:** Claude pokazał plan, wykonał dopiero po Twoim „tak"
   (i jeszcze raz spytał o zgodę na samo polecenie).

7. ```
   Zmień nazwę pliku "zestawienie_marzec_2026 (1).xlsx"
   na zestawienie_2026_03_wersja2.xlsx, żeby pasował do reszty.
   ```

8. ```
   Porównaj trzy wersje notatki dla banku i powiedz, czym się różnią.
   Nie usuwaj żadnej.
   ```

9. **Sprawdź w Eksploratorze:** `archiwum_2025` istnieje i ma 3 pliki;
   nazwa z kroku 7 zmieniona.

### Część 3: Cofnięcie

10. ```
    Przenieś pliki z archiwum_2025 z powrotem do głównego folderu
    i usuń pusty podfolder.
    ```

    Tak wygląda „cofnij" w Claude Code: prosisz o operację odwrotną.
    Dlatego przy ważnych plikach najpierw robi się kopię (zadanie 4).

## Na co zwrócić uwagę

- **Czytanie jest bezpieczne, zmienianie wymaga uwagi.** Od kroku 6
  zawsze: „…pokaż plan i poczekaj na moją zgodę".
- Plik usunięty z terminala **nie trafia do Kosza**. Nie prosimy
  o usuwanie bez kopii.
- „Z 2025 roku" Claude może rozumieć po nazwie, dacie modyfikacji albo
  zawartości – doprecyzuj, gdy ma to znaczenie.

## Notatki własne

- Czy Claude poprawnie zgrupował duplikaty? Co pominął lub dodał?
- Jaką operację na folderach robisz najczęściej ręcznie?
