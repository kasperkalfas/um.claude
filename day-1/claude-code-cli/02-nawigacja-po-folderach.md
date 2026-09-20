# Zadanie 2: Nawigacja po folderach w języku naturalnym

**Cel:** zobaczyć, że Claude Code potrafi zrobić to, co na co dzień robicie
w Eksploratorze Windows – policzyć, znaleźć, uporządkować pliki – tylko
że na polecenie słowne. Ćwiczymy na celowo zabałaganionym folderze.
**Poziom:** podstawowy
**Czas:** ok. 20 minut
**Blok:** Dzień 1 — wprowadzenie (pierwszy kontakt: `../claude-code/`)

## Materiały

- Folder `01_sandbox/` w folderze roboczym (`C:\Szkolenie\dzien-1\praca\`)
  – 17 plików udających typowy folder „Zestawienia" po kilku miesiącach
  pracy: pliki z 2025 i 2026, duplikaty („Kopia…", „(1)", „poprawione"),
  trzy wersje notatki dla banku, plik TODO i eksport z ERP.

## Kroki

1. W terminalu: `cd C:\Szkolenie\dzien-1\praca\01_sandbox`, potem `claude`.

### Część 1: Tylko czytanie

2. *„Wypisz wszystkie pliki w tym folderze w tabeli: nazwa, typ, rozmiar,
   data modyfikacji. Posortuj po nazwie."*
3. *„Ile jest plików Excel, ile tekstowych, ile CSV?"*
4. *„Które pliki wyglądają na duplikaty albo różne wersje tego samego
   dokumentu? Wypisz je w grupach i uzasadnij."*
   Sprawdź, czy Claude znalazł trzy grupy: marzec 2026 (3 pliki),
   kwiecień 2026 (2 pliki), notatka dla banku (3 wersje).
5. *„Które z tych plików dotyczą roku 2025?"*

### Część 2: Porządkowanie (Claude zmienia folder)

6. *„Utwórz podfolder `archiwum_2025` i przenieś do niego wszystkie pliki
   z 2025 roku. Najpierw pokaż listę plików do przeniesienia i poczekaj
   na moją zgodę."*
   Zwróć uwagę: Claude powinien najpierw pokazać plan, a dopiero po Twoim
   „tak" wykonać przeniesienie (i jeszcze raz spytać o zgodę na polecenie).
7. *„Zmień nazwę pliku `zestawienie_marzec_2026 (1).xlsx` na
   `zestawienie_2026_03_wersja2.xlsx`, żeby pasował do reszty."*
8. *„Porównaj trzy wersje notatki dla banku i powiedz, czym się różnią.
   Nie usuwaj żadnej."*
9. Sprawdź efekt w Eksploratorze Windows: czy folder `archiwum_2025`
   istnieje i ma 3 pliki, czy nazwa się zmieniła.

### Część 3: Cofnięcie

10. *„Przenieś pliki z `archiwum_2025` z powrotem do głównego folderu i
    usuń pusty podfolder."* – tak wygląda „cofnij" w Claude Code: nie ma
    magicznego przycisku, po prostu prosisz o operację odwrotną. Dlatego
    przy ważnych plikach najpierw robi się kopię (zadanie 9).

## Na co zwrócić uwagę

- **Czytanie jest bezpieczne, zmienianie – wymaga uwagi.** Kroki 2–5 nic
  nie zmieniają. Od kroku 6 Claude modyfikuje folder – zawsze każ mu
  najpierw pokazać plan („…i poczekaj na moją zgodę").
- Claude Code nie widzi Kosza Windows. Plik usunięty poleceniem w
  terminalu zwykle **nie trafia do Kosza**. Nie prosimy o usuwanie plików
  bez kopii.
- Określenia typu „z 2025 roku" Claude interpretuje po nazwie pliku,
  dacie modyfikacji albo zawartości – gdy ma to znaczenie, doprecyzuj:
  *„…sądząc po nazwie pliku"*.
- To samo działa na dowolnym folderze fikcyjnym – ale porządkowanie
  prawdziwego folderu Wydziału wymaga wcześniej zgody i kopii zapasowej
  całego folderu.

## Notatki własne

- Czy Claude poprawnie zgrupował duplikaty? Co pominął lub dodał
  nadmiarowo?
- Jaką operację na folderach robisz najczęściej ręcznie i ile by to
  zajęło w Claude Code?
