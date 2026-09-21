# Zadanie 8: Claude Code „widzi" pliki bez wgrywania

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** zobaczyć kluczową różnicę względem czatu – Claude Code czyta
pliki prosto z folderu, nikt niczego nie wgrywa.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## Materiały

- Folder `test-claude-code` z zadania 7: 4 pliki `.xlsx`,
  `notatka_do_zestawienia.txt` i podfolder `archiwum/`.

## Kroki

1. Zapytajcie:

   ```
   Jakie pliki są w tym folderze?
   ```

2. **Sprawdź:** lista zawiera 4 pliki `.xlsx`, jeden `.txt` i folder
   `archiwum`. W czacie trzeba by każdy z nich wgrać ręcznie.
3. Poproście o zajrzenie do środka – bez otwierania Excela:

   ```
   Otwórz plik zestawienie_przykladowe.xlsx i powiedz mi, jakie ma
   kolumny i ile wierszy danych.
   ```

4. **Sprawdź:** kolumny **Dział, Kwota planowana, Kwota wykonana,
   Miesiąc**; **7 wierszy** danych.
5. Plik, który nie jest Excelem:

   ```
   Co jest w pliku notatka_do_zestawienia.txt?
   ```

## Na co zwrócić uwagę

- Claude Code widzi **tylko folder, w którym go uruchomiono** (i jego
  podfoldery) – nie cały dysk.
- Na razie tylko **czytamy** – nic nie zmieniamy.
