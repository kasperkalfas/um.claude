# Zadanie 13: Porządkowanie plików – tworzenie folderów i segregacja

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** zrobić porządek w folderze pełnym pomieszanych plików jednym
poleceniem – ale to Wy wybieracie logikę porządkowania.
**Poziom:** podstawowy
**Czas:** ok. 7 minut

## Materiały

- Folder `test-claude-code` (po zadaniu 11): 4 pliki `UM_*.xlsx`
  z września i października „na kupie" w folderze głównym. `archiwum/`
  zostawiamy w spokoju.

## Kroki

1. Poproście o propozycję, jeszcze bez działania:

   ```
   Zobacz, jakie pliki są w tym folderze, i zaproponuj, jak sensownie
   je pogrupować. Na razie nic nie przenoś.
   ```

2. Claude zaproponuje np. „po miesiącu" albo „po wydziale". **Wy
   decydujecie**, co ma sens w Waszej pracy.
3. Zatwierdźcie kierunek i poproście o wykonanie:

   ```
   Utwórz foldery Wrzesien i Pazdziernik i przenieś do nich pliki
   z folderu głównego według miesiąca z danych w środku pliku.
   Archiwum zostaw bez zmian.
   ```

4. Claude pokaże plan: który plik → do którego folderu. Przeczytajcie
   i zatwierdźcie.
5. **Sprawdź** w Eksploratorze:
   - [ ] `Wrzesien/` – 2 pliki (`UM_zestawienie_wrzesien_2026.xlsx`,
         `UM_zestawienie_wrzesien_wydzialy.xlsx`)
   - [ ] `Pazdziernik/` – 2 pliki
   - [ ] folder główny – bez plików `.xlsx`; `archiwum/` bez zmian

## Na co zwrócić uwagę

- Claude **proponuje**, człowiek **decyduje** – to nie automat „po swojemu".
- „Według miesiąca z danych", nie „z nazwy" – nazwa może kłamać, dane nie.
- To samo polecenie działa przy 8 plikach i przy 800.
