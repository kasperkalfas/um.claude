# Zadanie 6: Instalacja Claude Code CLI

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** mieć działający Claude Code przed zadaniami 7–19.
**Poziom:** podstawowy
**Czas:** ok. 5 minut

> Jeśli IT Urzędu zainstalowało Claude Code centralnie, ten plik jest
> ściągawką „co się wydarzyło", nie instrukcją do wykonania na żywo.

## Wymagania

- Windows 10 (build 1809+) lub nowszy, min. 4 GB RAM, internet.
- Konto Pro, Max, Team lub Enterprise. Urząd ma **Team** – każdy
  uczestnik jest objęty.

## Kroki

1. **Otwórz PowerShell** (nie CMD). Poznasz go po `PS C:\...` na początku
   wiersza.
2. **Zainstaluj.** Wklej i naciśnij Enter:

   ```powershell
   irm https://claude.ai/install.ps1 | iex
   ```

   Jeśli masz tylko CMD:

   ```cmd
   curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
   ```

3. **Sprawdź instalację:**

   ```powershell
   claude --version
   ```

   Powinien pojawić się numer wersji, np. `2.1.211 (Claude Code)`.

4. **Przejdź do folderu testowego i uruchom.** Folder `test-claude-code`
   skopiowany na Pulpit (patrz README):

   ```powershell
   cd $HOME\Desktop\test-claude-code
   claude
   ```

5. **Zaloguj się.** Otworzy się przeglądarka – zaloguj się kontem Claude
   z planu Team Urzędu, wróć do terminala, naciśnij Enter.

**Sprawdź:**

- [ ] `claude --version` pokazuje numer wersji
- [ ] po `claude` widać pole do wpisywania wiadomości i nazwę folderu
      `test-claude-code`

## Na co zwrócić uwagę

- Instalator sam aktualizuje się w tle.
- Gdy coś nie działa: `claude doctor` pokazuje raport instalacji.
- **Bez terminala:** aplikacja desktopowa z [claude.com/download](https://claude.com/download)
  robi to samo w oknie graficznym – dobra opcja na pierwszy kontakt.
