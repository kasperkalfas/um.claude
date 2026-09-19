# Zadanie 2: Czym jest Claude Code i czym różni się od zwykłego chatbota?

> **Materiał wprowadzający – przygotowanie do Dnia 2.** Dzień 2 tego
> szkolenia („praca na komórkach Excela i automatyzacja") opiera się na
> Claude Code, nie na Claude Czat z Bloku C w Dniu 1. Ten plik ma za
> zadanie oswoić z tym narzędziem, zanim faktycznie usiądziecie do niego
> na zajęciach – żeby Dzień 2 nie zaczynał się od zera.

**Cel:** zrozumieć, czym jest Claude Code, czym różni się od zwykłej
rozmowy w przeglądarce (`../claude-zadania/`, Blok C) i od Cowork
([zadanie 1](01-czym-jest-cowork.md)) w tym samym folderze.
**Poziom:** podstawowy

## Czym jest Claude Code

Claude Code to narzędzie, które **pracuje bezpośrednio na plikach na
Twoim komputerze** (albo w chmurowym środowisku podpiętym pod Twoje
pliki) – nie tylko rozmawia o nich w oknie czatu. Historycznie
powstało z myślą o programistach (stąd nazwa), ale coraz częściej używa
się go do zwykłej automatyzacji pracy z plikami i danymi – i dokładnie
dlatego pojawia się w Dniu 2 tego szkolenia przy pracy na Excelu.

Dostępne jest w kilku formach – **nie tylko jako czarne okno terminala**:
- CLI w terminalu (klasyczna forma, tego użyjecie w Dniu 2),
- aplikacja desktopowa (Mac/Windows),
- aplikacja webowa (claude.ai/code),
- rozszerzenia do edytorów kodu (VS Code, JetBrains) – to raczej dla
  programistów w Urzędzie, jeśli tacy są.

**Prosta analogia:** Claude Czat w przeglądarce to jak wysłanie maila z
załącznikiem i czekanie na odpowiedź z nowym załącznikiem – Ty pilnujesz
przenoszenia plików tam i z powrotem. Claude Code to jak ktoś, kto siada
przy Twoim komputerze, otwiera wskazany folder i pracuje bezpośrednio na
plikach w nim – czyta je, poprawia, tworzy nowe, na bieżąco pokazując, co
robi.

## Czym różni się od zwykłego chatbota (Claude Czat, Blok C)

| | Claude Czat (przeglądarka, Blok C) | Claude Code |
|---|---|---|
| Gdzie działa | na stronie claude.ai, w przeglądarce | na Twoim komputerze (albo w chmurze), w konkretnym folderze z plikami |
| Dostęp do plików | ręcznie wgrywasz plik do rozmowy, ręcznie pobierasz wynik | pracuje bezpośrednio na plikach w folderze – czyta, edytuje i tworzy je „na miejscu", bez wgrywania/pobierania za każdym razem |
| Wykonywanie poleceń | nie uruchamia niczego na Twoim komputerze | może uruchamiać polecenia/skrypty (np. przeliczyć wszystkie pliki w folderze naraz) |
| Praca wieloetapowa | Ty prowadzisz rozmowę krok po kroku | samo planuje i wykonuje wiele kroków pod rząd, pokazując, co właśnie robi |
| Pierwotnie dla kogo | dla każdego, prosta rozmowa | pierwotnie dla programistów; dziś też do automatyzacji plików/danych – stąd Dzień 2 |

## A czym różni się od Cowork (zadanie 1)?

To „ten sam silnik", inny interfejs:

- **Cowork** ([zadanie 1](01-czym-jest-cowork.md)) – ten sam sposób pracy
  (podajesz cel, nie instrukcję krok po kroku; wiele kroków wykonuje się
  samo), ale w graficznym interfejsie, bez terminala. Łatwiejszy start
  dla osób nietechnicznych.
- **Claude Code** – to samo podejście, ale w terminalu (lub aplikacji
  desktop/web), z pełną kontrolą nad poleceniami i plikami na dysku.
  Właśnie to narzędzie poznacie praktycznie w Dniu 2.
- **Wtyczka Chrome** ([zadanie 3](03-wtyczka-chrome.md)) i wbudowana
  przeglądarka to dodatkowe „ręce", którymi zarówno Cowork, jak i Claude
  Code mogą sięgać do internetu, gdy zadanie tego wymaga.

## Dlaczego to ważne przed Dniem 2

- Terminal wygląda „programistycznie" (czarne okno z tekstem), ale w
  praktyce **piszesz do niego zwykłym, polskim językiem** – tak samo, jak
  w Claude Czat. Różnica jest w tym, **co Claude może zrobić** (dotknąć
  realnych plików na dysku), a nie w tym, **jak** z nim rozmawiasz.
- Claude Code, tak jak Claude Czat, **domyślnie pyta o potwierdzenie**
  przed zmianą pliku czy uruchomieniem polecenia – to Ty decydujesz, czy
  zaakceptować, podobnie jak w trybie Manual we wtyczce Chrome
  (zadanie 3).
- Wymagania planu i limity są opisane w
  [`../claude-zadania/06-plany-i-limity.md`](../claude-zadania/06-plany-i-limity.md)
  – Claude Code wymaga minimum planu Pro (Urząd ma Team, więc jest objęty).

## Kroki

1. Sprawdź w agendzie (`../../agenda/Agenda_szkolenia.md`), co dokładnie
   jest zaplanowane na Dzień 2 – żeby wiedzieć, czego się spodziewać.
2. Jeśli masz taką możliwość, poproś prowadzącego o pokazanie, jak
   wygląda okno Claude Code w praktyce (terminal albo aplikacja
   desktopowa) – zanim usiądziesz do niego samodzielnie.
3. Uporządkuj sobie w głowie trzy narzędzia z tego folderu: Claude Czat
   (Dzień 1) = rozmowa w przeglądarce; Cowork (zadanie 1) = cel + praca w
   tle, graficznie; Claude Code (Dzień 2) = to samo, ale bezpośrednio na
   plikach na dysku, w terminalu lub aplikacji.

## Na co zwrócić uwagę

- **Nie musisz umieć programować**, żeby korzystać z Claude Code –
  piszesz zwykłe polecenia po polsku, tak jak w czacie.
- Ponieważ Claude Code ma bezpośredni dostęp do plików na komputerze,
  obowiązuje ta sama zasada co wszędzie: w Dniu 2 pracujecie na
  **fikcyjnych/zanonimizowanych kopiach** plików, nigdy na oryginalnych
  danych z ERP (`CLAUDE.md`, sekcja o bezpieczeństwie danych).
- Czarne okno terminala bywa onieśmielające na pierwszy rzut oka – to
  normalne. Sama „rozmowa" wygląda identycznie jak w Claude Czat.

## Notatki własne

- Co najbardziej zaskakuje Cię w różnicy między Claude Czat a Claude
  Code?
- Czy widzisz w swojej pracy zadanie, które lepiej pasuje do „rozmowy w
  przeglądarce", a które do „pracy bezpośrednio na plikach na dysku"?
