# Zadanie 19: CLAUDE.md – pamięć projektu, żeby nie tłumaczyć wszystkiego od nowa

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** zrozumieć, jak Claude Code „pamięta" zasady i kontekst projektu
między rozmowami – żeby nie trzeba było za każdym razem od nowa
tłumaczyć tych samych rzeczy.
**Poziom:** podstawowy
**Czas:** ok. 7 minut

## Problem, który to rozwiązuje

W Claude Czat, jeśli chcecie, żeby Claude zawsze pamiętał pewne zasady
(np. „pracujemy tylko na danych fikcyjnych", „kwoty zawsze w PLN"),
musicie je powtarzać w każdej nowej rozmowie albo polegać na funkcji
pamięci z [zadania 2 z Bloku C](../claude-zadania/02-funkcje-interfejsu.md).
W Claude Code jest na to prostszy sposób: **plik `CLAUDE.md`** w folderze
projektu.

## Materiały

- Folder testowy z poprzednich zadań.

## Kroki

1. Poproście Claude Code o pokazanie, czy w folderze, w którym pracujecie
   na tym szkoleniu, istnieje plik `CLAUDE.md`: *„Czy w tym folderze jest
   plik CLAUDE.md? Jeśli tak, pokaż mi jego zawartość."*
2. **Żywy przykład od razu pod ręką**: to repozytorium szkoleniowe ma
   swój własny plik `CLAUDE.md` w folderze głównym – zawiera m.in. fakty
   o szkoleniu, zasadę „nie wklejamy poufnych danych Urzędu" i strukturę
   folderów. Poproście prowadzącego o pokazanie go na ekranie – to
   właśnie ten plik „prowadził" Claude Code przez całą tę rozmowę.
3. W swoim folderze testowym poproście: *„Utwórz plik CLAUDE.md z jedną
   zasadą: 'Wszystkie kwoty w tym projekcie podajemy w PLN z separatorem
   tysięcy'."*
4. Zamknijcie rozmowę (`/clear`) i zacznijcie nową w tym samym folderze.
   Poproście o coś, co wymaga podania kwoty (np. *„Zapisz w nowym pliku
   przykładową kwotę budżetu 112000"*) i sprawdźcie, czy Claude Code
   **sam, bez przypominania**, zastosował zasadę z `CLAUDE.md`.

## Na co zwrócić uwagę

- `CLAUDE.md` to zwykły plik tekstowy – można go otworzyć i edytować jak
  każdy inny dokument, nawet bez Claude Code.
- Zasady z `CLAUDE.md` **obowiązują automatycznie w każdej nowej
  rozmowie** w tym folderze – to jest właśnie ta „pamięć projektu", o
  którą chodziło we wstępie.
- To bardzo przydatne dla Waszej pracy: raz zapiszecie zasady Urzędu
  (format kwot, zakaz danych osobowych, styl komunikatów – jak w
  [zadaniu 8 z Bloku C](../claude-zadania/08-skille-z-internetu.md)) i
  nie musicie ich powtarzać przy każdej kolejnej rozmowie.
- To nie to samo, co pamięć konta z Claude Czat – `CLAUDE.md` jest
  **przypisany do konkretnego folderu/projektu**, a nie do Waszego konta
  w ogóle.

## Notatki własne

- Jakie 2–3 zasady ze swojej pracy zapisał(a)byś w `CLAUDE.md` folderu, w
  którym trzymasz zestawienia swojego wydziału?
