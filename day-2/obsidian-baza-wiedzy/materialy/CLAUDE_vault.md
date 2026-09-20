# Baza wiedzy Wydziału Finansowego – zasady dla Claude Code

Ten folder to vault Obsidian: każda notatka to plik `.md`, linki między
notatkami to `[[nazwa notatki]]`. Wszystkie dane są FIKCYJNE (materiał
szkoleniowy). Nigdy nie proś o prawdziwe dane Urzędu ani ich nie wpisuj.

## Struktura

- `00-Start/` – strona startowa, jak korzystać z bazy
- `10-Procedury/` – jedna notatka = jeden proces (szablon: `90-Szablony/procedura.md`)
- `20-Slownik/` – jedna notatka = jedno pojęcie (dział, plik, termin)
- `30-Decyzje/` – dziennik decyzji, jedna notatka = jedna decyzja, nazwa `RRRR-MM-DD – temat`
- `80-Zrodla/` – oryginały (maile, stare instrukcje, notatki) – tylko do czytania, nie edytować
- `90-Szablony/` – szablony notatek

## Zasady pisania

1. Po polsku, zwięźle, w punktach. Jedna notatka = jeden temat.
2. Każda notatka ma frontmatter z szablonu (`typ`, `zrodla`, daty).
3. Każdy fakt pochodzi ze źródła w `80-Zrodla/` – wpisz je w `zrodla:`;
   jeśli źródła nie ma, napisz „(do potwierdzenia)” zamiast zgadywać.
4. Gdy dwa źródła się nie zgadzają – nie wybieraj po cichu: opisz obie
   wersje i oznacz nowszą jako obowiązującą, starszą jako historyczną.
5. Linkuj pojęcia: pierwsze wystąpienie działu, pliku, roli → `[[…]]`.
   Link do notatki, której nie ma, jest OK – to lista rzeczy do opisania.
6. Nie wpisuj danych osobowych (nazwisk, adresów) – role zamiast osób.
7. Przed zmianą istniejącej notatki pokaż, co zmienisz, i czekaj na zgodę.
   Plików w `80-Zrodla/` nie zmieniaj nigdy.
