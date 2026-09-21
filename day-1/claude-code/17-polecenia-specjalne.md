# Zadanie 17: Polecenia specjalne (/) w Claude Code

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**, materiał dodatkowy).

**Cel:** poznać kilka poleceń zaczynających się od `/` – jedyną „składnię"
w Claude Code.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## Materiały

- Claude Code w dowolnym folderze (może być `test-claude-code`).

## Kroki

1. Lista wszystkich poleceń:

   ```
   /help
   ```

2. Nowa, czysta rozmowa w tym samym folderze (odpowiednik „New chat"):

   ```
   /clear
   ```

   **Sprawdź:** zapytajcie `O czym rozmawialiśmy przed chwilą?` – Claude
   nie pamięta. To celowe.

3. Powrót do ostatniej rozmowy. Zamknijcie Claude Code (`/exit`)
   i uruchomcie w terminalu:

   ```powershell
   claude --continue
   ```

   **Sprawdź:** Claude wraca do rozmowy sprzed `/clear`? Nie – wraca do
   **ostatniej**, czyli tej pustej po `/clear`. Wcześniejszą znajdziecie
   przez `claude --resume` (lista rozmów do wyboru).

4. Który model pracuje:

   ```
   /model
   ```

5. Ile okna kontekstu jest zajęte i przez co:

   ```
   /context
   ```

## Na co zwrócić uwagę

- Nie trzeba nic zapamiętywać – `/help` zawsze pokaże listę.
- `/clear` = czysta karta; `claude --continue` / `--resume` = powrót do
  pracy. Jak „New chat" i lista rozmów w czacie.
- `/context` i `/compact` (streszczenie rozmowy, żeby zwolnić miejsce)
  omawiamy w [zadaniu 3 o tokenach i oknie kontekstu](../tokeny-i-okno-kontekstu/03-kontekst-w-claude-code.md).
