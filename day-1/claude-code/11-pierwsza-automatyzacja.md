# Zadanie 11: Pierwsza automatyzacja – jedno polecenie zamiast wielu kliknięć

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** jedno polecenie zmienia wiele plików naraz – to jest
„automatyzacja" w najprostszej postaci.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## Materiały

- Folder `test-claude-code` (po zadaniu 10): 4 pliki `.xlsx` w folderze
  głównym, 2 w `archiwum/`.

## Kroki

1. Punkt wyjścia:

   ```
   Ile plików .xlsx jest w tym folderze i jak się nazywają?
   ```

   **Sprawdź:** 4 w folderze głównym (+ 2 w archiwum, jeśli Claude je
   policzy – zapytajcie, czy liczył podfoldery).

2. Działanie na wszystkich naraz:

   ```
   Dodaj do nazwy każdego pliku .xlsx w folderze głównym (nie w archiwum)
   prefiks „UM_", zachowując resztę nazwy.
   ```

3. Claude Code pokaże listę: stara nazwa → nowa nazwa. Przeczytajcie ją
   i zatwierdźcie.
4. **Sprawdź** w Eksploratorze:
   - [ ] 4 pliki w folderze głównym zaczynają się od `UM_`
   - [ ] pliki w `archiwum/` **bez zmian**
5. Policzcie: ile kliknięć „Zmień nazwę" zajęłoby to ręcznie?

## Na co zwrócić uwagę

- **Jedno polecenie, wiele plików.** Przy 4 plikach różnica jest miła,
  przy 40 – ogromna.
- Zmiana masowa nie omija pytania o zgodę z zadania 10.
