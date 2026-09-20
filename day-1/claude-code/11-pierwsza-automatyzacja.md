# Zadanie 11: Pierwsza automatyzacja – jedno polecenie zamiast wielu kliknięć

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** poczuć na prostym przykładzie, czym różni się „automatyzacja"
od zwykłego pytania – jedno polecenie robi to, co ręcznie zajęłoby kilka
osobnych kliknięć.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## Materiały

- Folder `test-claude-code` na Pulpicie (kopia
  `../materialy/test-claude-code/`) – w folderze głównym są 4 pliki
  `.xlsx` z września i października, w podfolderze `archiwum/` kolejne 2.

## Kroki

1. Zapytajcie: *„Ile plików .xlsx jest w tym folderze i jak się
   nazywają?"* – żeby zobaczyć punkt wyjścia.
2. Poproście o działanie na **wszystkich naraz**, jednym poleceniem:
   *„Dodaj do nazwy każdego pliku .xlsx w folderze głównym (nie w
   archiwum) prefiks »UM_«, zachowując resztę nazwy."*
3. Zanim Claude Code coś zmieni, pokaże listę plików, które zamierza
   zmienić i jak będą się nazywać – dopiero po Waszej zgodzie wykonuje
   zmianę na wszystkich naraz.
4. Sprawdźcie wynik w Eksploratorze plików – policzcie, ile osobnych
   kliknięć „Zmień nazwę" musielibyście wykonać ręcznie, żeby uzyskać ten
   sam efekt.

## Na co zwrócić uwagę

- To jest właśnie sedno „automatyzacji": **jedno polecenie, wiele
  plików**, zamiast powtarzania tej samej czynności ręcznie.
- Im więcej plików, tym większa oszczędność czasu – przy 5 plikach różnica
  jest sympatyczna, przy 50 – ogromna.
- To wciąż ten sam mechanizm zgody z [zadania 10](10-zgoda-przed-zmiana.md)
  – zmiana masowa nie omija pytania o potwierdzenie.
