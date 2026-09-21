# Zadanie 18: Tryby pracy – pytaj / akceptuj automatycznie / tylko planuj

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**, materiał dodatkowy).

**Cel:** przełączyć się między trzema trybami i zobaczyć, co każdy
zmienia.
**Poziom:** podstawowy
**Czas:** ok. 7 minut

## Trzy tryby

| Tryb | Co robi |
|---|---|
| **Domyślny** | pyta przed każdą zmianą pliku (jak w zad. 10) |
| **Plan mode** | **nic nie zmienia** – tylko czyta i opisuje, co by zrobił |
| **Auto-accept edits** | zmienia pliki od razu, bez pytania o każdą z osobna |

Przełącznik: **Shift+Tab** (cyklicznie). Aktualny tryb widać pod polem
wiadomości.

## Materiały

- Folder `test-claude-code`.

## Kroki

1. **Tryb domyślny.** Poproście o prostą zmianę:

   ```
   Utwórz pusty folder o nazwie test-trybow.
   ```

   **Sprawdź:** Claude pyta o zgodę. Zatwierdźcie.

2. **Plan mode.** Naciśnijcie Shift+Tab, aż pod polem pojawi się „plan
   mode". Poproście:

   ```
   Zaproponuj, jak inaczej można by pogrupować pliki w tym folderze,
   i jakie foldery byś utworzył.
   ```

   **Sprawdź:** dostajecie propozycję **słowami**; w Eksploratorze nic
   się nie zmieniło.

3. **Auto-accept edits.** Shift+Tab do „auto-accept edits". Poproście
   o coś niegroźnego:

   ```
   Utwórz w folderze test-trybow pusty plik notatki.txt.
   ```

   **Sprawdź:** plik powstał **od razu**, bez pytania.

4. **Wróćcie do trybu domyślnego** (Shift+Tab) i posprzątajcie:

   ```
   Usuń folder test-trybow razem z zawartością.
   ```

   **Sprawdź:** przy usuwaniu Claude znów pyta o zgodę.

## Na co zwrócić uwagę

- **Domyślny** – na start i do pracy na danych Urzędu (nawet
  zanonimizowanych).
- **Plan mode** – do „burzy mózgów" o dużych zmianach: bezpiecznie, bo
  nic się nie wykona.
- **Auto-accept** – do rutynowych, sprawdzonych zadań; włączać świadomie,
  nie jako domyślne.
