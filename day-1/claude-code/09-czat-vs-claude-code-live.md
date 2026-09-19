# Zadanie 9: To samo zadanie w czacie i w Claude Code – porównanie na żywo

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** zobaczyć na żywo, obok siebie, tę samą operację wykonaną w
Claude Czat (Blok C) i w Claude Code – żeby różnica przestała być
teoretyczna.
**Poziom:** podstawowy
**Czas:** ok. 8 minut

## Materiały

- Dwa okna obok siebie na ekranie prowadzącego: przeglądarka z Claude
  Czat i Claude Code w folderze testowym.
- Ten sam plik `zestawienie_przykladowe.xlsx` w obu miejscach.

## Kroki

1. **W Claude Czat**: wgrajcie plik ręcznie (ikona wgrywania) i poproście
   o dodanie wiersza „Razem" z sumą – tak jak w
   [zadaniu 8 z Bloku C](../claude-zadania/08-skille-z-internetu.md#część-1-zrozum-wbudowany-skill-xlsx-czytanie-nie-instalacja),
   krok 2. Po odpowiedzi trzeba **pobrać** gotowy plik.
2. **W Claude Code**: bez żadnego wgrywania, poproście o dokładnie to
   samo: *„Dodaj w pliku zestawienie_przykladowe.xlsx wiersz Razem z
   formułą sumującą kolumny Kwota planowana i Kwota wykonana."*
3. Zwróćcie uwagę: Claude Code **zapisuje zmianę od razu w pliku na
   dysku**, w tym samym folderze – nie trzeba niczego pobierać ani
   zamieniać miejscami.
4. Otwórzcie zmieniony plik w Excelu i pokażcie, że wiersz „Razem"
   faktycznie tam jest.

## Na co zwrócić uwagę

- Czat: wgraj → poczekaj → pobierz → zamień plikami. Claude Code:
  poproś → gotowe, w tym samym miejscu.
- Ta różnica staje się dużo ważniejsza, gdy plików jest **wiele naraz** –
  to właśnie zapowiedź tego, co czeka Was w Dniu 2.
- Claude Code, tak jak skill `xlsx` w czacie, i tak wpisuje **formułę**
  (`=SUMA(...)`), a nie gotową liczbę – ta zasada jest taka sama w obu
  miejscach.
