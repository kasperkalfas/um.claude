# Zadanie 17: Polecenia specjalne (/) w Claude Code

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** poznać podstawowe polecenia zaczynające się od „/" – to jedyna
„programistyczna" rzecz, jakiej potrzebujecie w Claude Code, i to tylko
kilka prostych słów.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## Materiały

- Claude Code uruchomiony w dowolnym folderze (może być ten sam folder
  testowy co w [zadaniach 7–16](07-pierwszy-kontakt-terminal.md)).

## Kroki

1. Wpiszcie `/help` i zobaczcie listę wszystkich dostępnych poleceń
   specjalnych – to „ściągawka" wbudowana w samo narzędzie, zawsze pod
   ręką.
2. Wpiszcie `/clear`, żeby zacząć **zupełnie nową rozmowę** w tym samym
   folderze – to odpowiednik przycisku „New chat" z Claude Czat
   ([zadanie 2 z Bloku C](../claude-zadania/02-funkcje-interfejsu.md)).
3. Zamknijcie i ponownie uruchomcie Claude Code w tym samym folderze,
   wpisując w terminalu `claude --continue` (albo `-c`) zamiast zwykłego
   `claude` – zobaczcie, że wraca do **ostatniej rozmowy**, tak jak lista
   rozmów po lewej stronie w Claude Czat.
4. Wróćcie do bieżącej rozmowy i wpiszcie `/model`, żeby zobaczyć, jakiego
   modelu Claude aktualnie używacie i jakie są inne opcje.

## Na co zwrócić uwagę

- Nie musicie zapamiętywać wszystkich poleceń – `/help` zawsze pokaże
  pełną listę.
- Polecenia zaczynające się od „/" to jedyna „specjalna składnia" w całym
  Claude Code – reszta to zwykła rozmowa po polsku, dokładnie jak dotąd.
- `/clear` i `claude --continue` to dwie strony tego samego mechanizmu co
  w czacie: czysta karta vs. wracanie do wcześniejszej pracy.
