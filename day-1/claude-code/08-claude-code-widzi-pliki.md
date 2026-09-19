# Zadanie 8: Claude Code „widzi" pliki bez wgrywania

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** zobaczyć kluczową różnicę względem Claude Czat: Claude Code
odczytuje pliki bezpośrednio z folderu, bez ręcznego wgrywania.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## Materiały

- Folder testowy z [zadania 7](07-pierwszy-kontakt-terminal.md), z
  wgranymi wcześniej 2–3 fikcyjnymi plikami, np. skopiowanymi z
  `../materialy/` (`zestawienie_przykladowe.xlsx`).

## Kroki

1. Poproście Claude Code: *„Jakie pliki są w tym folderze?"*
2. Porównajcie na głos, jak wyglądałby ten sam krok w Claude Czat –
   trzeba by kliknąć ikonę wgrywania i ręcznie wskazać plik. Tutaj Claude
   Code po prostu **sam sprawdza zawartość folderu**.
3. Poproście o więcej szczegółów bez otwierania pliku w Excelu, np.:
   *„Otwórz plik zestawienie_przykladowe.xlsx i powiedz mi, jakie ma
   kolumny i ile wierszy danych."*
4. Zwróćcie uwagę, że odpowiedź pojawia się od razu w rozmowie – nikt nie
   musiał uruchamiać Excela.

## Na co zwrócić uwagę

- To jest właśnie różnica z tabeli w [zadaniu 2](02-czym-jest-claude-code.md):
  „ręcznie wgrywasz plik" (czat) vs „pracuje bezpośrednio na plikach w
  folderze" (Claude Code).
- Claude Code widzi **tylko pliki w folderze, w którym został
  uruchomiony** (i jego podfolderach) – nie ma dostępu do całego dysku
  ani innych folderów bez wskazania.
- Na razie tylko **czytamy** – nic jeszcze nie zmieniamy w plikach.
