# Zadanie 6: Instalacja Claude Code CLI

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** zainstalować Claude Code na komputerze (albo obejrzeć instalację
na żywo, jeśli robi ją prowadzący na wspólnym ekranie), zanim przejdziecie
do praktycznych zadań 7–19.
**Poziom:** podstawowy
**Czas:** ok. 5 minut

> To zadanie jest technicznym progiem przed resztą Bloku D – jeśli
> instalację robi centralnie IT Urzędu na wszystkich komputerach z
> wyprzedzeniem, potraktujcie ten plik jako ściągawkę „co się właśnie
> wydarzyło", a nie instrukcję do samodzielnego wykonania na żywo.

## Wymagania

- **Windows 10 (build 1809+)** lub nowszy, min. 4 GB RAM, połączenie z
  internetem.
- Konto **Pro, Max, Team lub Enterprise** – plan darmowy nie obejmuje
  Claude Code. Urząd pracuje na planie **Team**
  (patrz [`../claude-zadania/06-plany-i-limity.md`](../claude-zadania/06-plany-i-limity.md)),
  więc każdy uczestnik jest objęty licencją.

## Kroki

1. Otwórzcie **PowerShell** (nie CMD) – poznacie go po tym, że wiersz
   zaczyna się od `PS C:\...` (w zwykłym CMD nie ma `PS` na początku).
2. Wklejcie i uruchomcie:
   ```powershell
   irm https://claude.ai/install.ps1 | iex
   ```
3. Jeśli macie CMD zamiast PowerShell, użyjcie zamiast tego:
   ```cmd
   curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
   ```
4. Po zakończeniu instalacji sprawdźcie, czy zadziałała:
   ```powershell
   claude --version
   ```
   Powinniście zobaczyć numer wersji, np. `2.1.211 (Claude Code)`.
5. Uruchomcie Claude Code w wybranym, testowym folderze:
   ```powershell
   claude
   ```
   Otworzy się przeglądarka z prośbą o zalogowanie – zaloguj się tym
   samym kontem Claude, którego używacie na planie Team Urzędu. Po
   zalogowaniu wróć do terminala i naciśnij Enter.

## Na co zwrócić uwagę

- Instalator **sam się aktualizuje w tle** – nie trzeba go potem ręcznie
  odświeżać.
- Jeśli coś nie zadziała, komenda diagnostyczna `claude doctor` pokazuje
  pełny raport instalacji i ustawień bez uruchamiania sesji.
- **Alternatywa bez terminala**: jeśli czarne okno onieśmiela, istnieje
  też aplikacja desktopowa z graficznym interfejsem, do pobrania z
  [claude.com/download](https://claude.com/download) – dobra opcja na
  pierwszy kontakt dla osób, które wolą uniknąć terminala na starcie.
- Od tego miejsca zaczynają się zadania 7–19, które zakładają, że Claude
  Code jest już zainstalowany i uruchomiony.
