# Zadanie 19: CLAUDE.md – pamięć projektu, żeby nie tłumaczyć wszystkiego od nowa

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**, materiał dodatkowy).

**Cel:** zapisać zasadę w pliku `CLAUDE.md` i sprawdzić, że Claude Code
stosuje ją w nowej rozmowie bez przypominania.
**Poziom:** podstawowy
**Czas:** ok. 7 minut

## Po co

W czacie zasady („kwoty w PLN", „tylko dane fikcyjne") trzeba powtarzać
w każdej rozmowie. W Claude Code wystarczy zapisać je raz w pliku
`CLAUDE.md` w folderze – obowiązują automatycznie w każdej rozmowie
w tym folderze.

## Materiały

- Folder `test-claude-code`.

## Kroki

1. Czy plik już jest?

   ```
   Czy w tym folderze jest plik CLAUDE.md? Jeśli tak, pokaż jego
   zawartość.
   ```

   **Sprawdź:** w folderze testowym go nie ma. Prowadzący pokaże na
   ekranie `CLAUDE.md` z repozytorium szkolenia – ten plik „prowadził"
   Claude Code przy budowaniu tych materiałów.

2. Utwórzcie własny:

   ```
   Utwórz plik CLAUDE.md z jedną zasadą: „Wszystkie kwoty w tym
   projekcie podajemy w PLN z separatorem tysięcy, bez groszy,
   np. 112 000 zł".
   ```

3. Nowa rozmowa:

   ```
   /clear
   ```

4. Poproście o coś z kwotą – **bez wspominania o zasadzie**:

   ```
   Zapisz w nowym pliku kwoty.txt trzy przykładowe kwoty budżetu:
   112000, 2450000 i 98500.
   ```

5. **Sprawdź:** otwórzcie `kwoty.txt`. Kwoty zapisane jako
   `112 000 zł`, `2 450 000 zł`, `98 500 zł` – zasada zadziałała sama.

## Na co zwrócić uwagę

- `CLAUDE.md` to zwykły plik tekstowy – można go edytować w Notatniku.
- Jest **przypisany do folderu**, nie do konta – inaczej niż pamięć
  w czacie.
- Dla Urzędu: raz zapisujecie format kwot, zakaz danych osobowych, styl
  komunikatów – i nie powtarzacie tego przy każdej rozmowie. W Dniu 2
  zbudujecie taki plik dla Procesu 1 i 2.

## Notatki własne

- Jakie 2–3 zasady zapisał(a)byś w `CLAUDE.md` folderu z zestawieniami
  swojego wydziału?
