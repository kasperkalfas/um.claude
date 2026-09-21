# Zadanie 15: Podgląd wielu plików naraz

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** dostać jedną odpowiedź z sześciu plików – bez otwierania żadnego
w Excelu.
**Poziom:** podstawowy
**Czas:** ok. 7 minut

## Materiały

- Folder `test-claude-code` (po zadaniach 13–14): 6 plików `.xlsx`
  o tej samej strukturze (Dział, Kwota planowana, Kwota wykonana,
  Miesiąc).

## Kroki

1. Pytanie zbiorcze:

   ```
   Przejrzyj wszystkie pliki .xlsx w tym folderze i podfolderach
   i powiedz, w którym miesiącu suma przekroczeń budżetu (wykonanie
   minus plan, tylko dodatnie) była największa. Pomiń wiersze „Razem".
   ```

   Claude otwiera po kolei każdy plik, liczy i podaje jedną odpowiedź.

   **Sprawdź:** **październik 2026** (393 000 zł przekroczeń).

2. Rozbicie na liczby:

   ```
   Pokaż to w tabeli: miesiąc, suma planu, suma wykonania,
   suma przekroczeń. Napisz, z których plików wziąłeś każdy miesiąc.
   ```

   **Sprawdź** (klucz):

   | Miesiąc | Plan | Wykonanie | Przekroczenia |
   |---|---|---|---|
   | lipiec | 1 980 000 | 1 940 000 | 20 000 |
   | sierpień | 2 381 000 | 2 373 000 | 60 000 |
   | wrzesień | 5 320 000 | 5 216 000 | 98 000 |
   | październik | 6 555 000 | 6 811 000 | 393 000 |

   Jeśli wrzesień wyszedł wyżej – Claude doliczył wiersz „Razem"
   z zadania 9. Dobry moment na zdanie: **zawsze sprawdzaj, co weszło do
   sumy.**

3. Policzcie: ile plików trzeba by otworzyć ręcznie i ile liczb
   przepisać?

## Na co zwrócić uwagę

- Automatyzacja to nie tylko przenoszenie plików – to też **czytanie
  i łączenie danych z wielu plików naraz**. To zapowiedź Procesu 1 i 2
  z Dnia 2.
- **Zawsze proście o rozbicie na pojedyncze liczby** – żeby wiedzieć,
  skąd wziął się wynik.
